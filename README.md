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
