# Detektor promjena na web stranici
Program detektira promjene na web-stranici na način da usporedi trenutni i budući hash u vremenskom intervalu od par sekundi i nastavlja se vrtiti u petlji. Ako se na stranici nije dogodila promjena jednostavno se nastavlja i ispisuje poruku da nema promjene, a inače šalje e-mail poruku koristeći Gmail API.

# Instalacija

1. Preuzeti Google.py i program.py.
2. Omogućiti korištenje Gmail API na Google Cloud Console i pokrenuti sljedeću komandu u cmd (služi za instalaciju modula): pip install --upgrade google-api-python-client google-auth-httplib2 google-auth-oauthlib
3. Napraviti svoj projekt na Google Cloud i dobiti token za autorizaciju.
4. U program.py upisati željeni URL te svoju Gmail adresu.
5. Pokrenuti program.
Dodatno:
Može se promijeniti trajanje time.sleep funkcije čija vrijednost već iznosi 10/30s između zagrada.
Sadržaj e-mail poruke i predmet se također može promijeniti.

# Screencast i dokumentacija

Screencast: https://drive.google.com/file/d/18_uAl-BHJMbiqaIrVBuG2Q-94X4RqpGz/view?usp=sharing
Dokumentacija: Glavni dio programa tj. datoteka main.py sadrži komentare na većinu linija koda. Google.py dio je programa koji služi samo za autorizaciju te sam njega samo preuzeo i ne sadrži neke zanimljive linije koda (koje se tiču same funkcionalnosti) programa stoga se nisam trudio objasniti ih. Google-ova dokumentacija za slanje e-maila je neočekivano zastarjela te sam stoga morao koristiti alternativan izvor da bi kod radio. Svejedno, sadrži dosta toga što objašnjava funkcionalnost samog sučelja pa ako nekog zanima evo linka:
https://developers.google.com/gmail/api
