import time # modul za vrijeme (timeout)
import hashlib # modul koji se koristi za uspoređivanje hasha između trenutnog i budućeg stanja web-stranice
from urllib.request import urlopen, Request # koristi se za GET zahtjev i dobivanje sadržaja stranice
from Google import Create_Service 
import base64
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText # moduli za slanje e-maila putem Gmail API
import sys # za izlazak iz programa u slučaju greške
url = Request('ovdje upišite neki url', headers={'User-Agent': 'Mozilla/5.0'}) # koristi se za GET zahtjev, u zagradu se upisuje URL za stranicu
response = urlopen(url).read() # zahtjev se pohranjuje u varijablu response
trenutniHash = hashlib.sha224(response).hexdigest() # dobiva se trenutni SHA-2 hash sa 224 bita za web-stranicu 
print("Pokrenuto...")
time.sleep(10) # .sleep funkcija služi za čekanje prije nego što se izvrši naredba, u ovom slučaju to iznosi 10 sekundi, to je iz razloga da se ne pinga previše stranica
while True: #beskonačna petlja
    try:
        response = urlopen(url).read() # događa se GET zahtjev i dobiva sadržaj stranice
        trenutniHash = hashlib.sha224(response).hexdigest() # dobiva se hash
        time.sleep(30) # čekanje od 30 sekundi, očekuje se da će se stranica u tom razdoblju promijeniti
        response = urlopen(url).read()
        noviHash = hashlib.sha224(response).hexdigest() # opet se dobiva hash stranice koji se pohranjuje u drugu varijablu newhHash
        if noviHash == trenutniHash: # ako su hashevi isti onda se izjavom continue vraća na početak programa i tako se ponavlja petlja
            print ("Trenutno nema promjene.")
            continue
        else: #inače dobivamo e-mail poruku da se dogodila promjena
            
            print("Dogodila se promjena.")
            
            CLIENT_SECRET_FILE = 'client_secret.json'
            API_NAME = 'gmail'
            API_VERSION = 'v1'
            SCOPES = ['https://mail.google.com/']

            service = Create_Service(CLIENT_SECRET_FILE, API_NAME, API_VERSION, SCOPES)

            emailMsg = 'Dogodila se promjena na web-stranici.'
            mimeMessage = MIMEMultipart()
            mimeMessage['to'] = 'ovdje upišite svoju Gmail adresu'
            mimeMessage['subject'] = 'Detektor promjena'
            mimeMessage.attach(MIMEText(emailMsg, 'plain'))
            raw_string = base64.urlsafe_b64encode(mimeMessage.as_bytes()).decode()

            message = service.users().messages().send(userId='me', body={'raw': raw_string}).execute()
            print(message)

            response = urlopen(url).read()
            trenutniHash = hashlib.sha224(response).hexdigest()
            time.sleep(30)
            continue
    except Exception as e: # u slučaju iznimaka tj. greški šalje e-mail poruku
        print("Greška u programu.")

        CLIENT_SECRET_FILE = 'client_secret.json'
        API_NAME = 'gmail'
        API_VERSION = 'v1'
        SCOPES = ['https://mail.google.com/']

        service = Create_Service(CLIENT_SECRET_FILE, API_NAME, API_VERSION, SCOPES)

        emailMsg = 'Greška u programu.'
        mimeMessage = MIMEMultipart()
        mimeMessage['to'] = 'ovdje upišite svoju Gmail adresu'
        mimeMessage['subject'] = 'Detektor promjena'
        mimeMessage.attach(MIMEText(emailMsg, 'plain'))
        raw_string = base64.urlsafe_b64encode(mimeMessage.as_bytes()).decode()

        message = service.users().messages().send(userId='me', body={'raw': raw_string}).execute()
        print(message)
        sys.exit()
