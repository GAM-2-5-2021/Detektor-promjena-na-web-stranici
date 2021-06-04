# Detektor promjena na web stranici
Program detektira promjene na web-stranici na način da usporedi trenutni i budući hash u vremenskom intervalu od par sekundi i nastavlja se vrtiti u petlji. Ako se na stranici nije dogodila promjena jednostavno se nastavlja i ispisuje poruku da nema promjene, a inače šalje e-mail poruku koristeći Gmail API.

# Instalacija

1. Preuzeti Google.py i program.py.
2. Napravit svoj projekt na Google Cloud Console platformi.
3. Dodati svoj Gmail kao test korisnika i dobiti token za autorizaciju (OAuth 2.0).
4. Omogućiti korištenje Gmail API
5. U program.py upisati željeni URL te svoju Gmail adresu
6. Pokrenuti program.

Dodatno:
Može se promijeniti trajanje time.sleep funkcije čija vrijednost već iznosi 10/30s između zagrada.
Sadržaj e-mail poruke i predmet se također može promijeniti.
