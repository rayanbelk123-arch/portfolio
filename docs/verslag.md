# Verslag — Portfolio Website

**Naam:** Rayan  
**Opleiding:** Software Development, ROC Midden Nederland  
**Project:** Portfolio website op een lokale Apache-server  
**Datum:** november 2026

## Wat ik heb gebouwd

Ik heb een portfolio website gemaakt met drie pagina's: Home, Over mij en Contact. De site is volledig met de hand geschreven in HTML en CSS en draait op de lokale Apache-server van XAMPP. De bestanden staan in `htdocs/portfolio/` en zijn bereikbaar via `http://localhost/portfolio/`.

De website heeft een responsive design, een eigen favicon, een actieve navigatie en een consistente donkere stijl. Op de homepage staan uitgelichte projecten en een korte introductie. De pagina Over mij bevat mijn achtergrond, skills, interesses en een tijdlijn. Op de contactpagina staan een formulier, contactgegevens en veelgestelde vragen.

## Gebruikte Apache-features

- **DocumentRoot / htdocs:** de website wordt via `http://localhost/portfolio/` geserveerd.
- **.htaccess:** toegang tot het `.htaccess`-bestand zelf en andere verborgen bestanden wordt geblokkeerd met `Require all denied`.
- **ErrorDocument 404:** bezoekers krijgen een eigen foutpagina in plaats van de standaardpagina van Apache.
- **Options -Indexes:** directory listing is uitgeschakeld, zodat mappen zonder indexbestand niet zichtbaar zijn.
- **Beveiligingsheaders:** via `mod_headers` zijn `X-Content-Type-Options`, `X-Frame-Options` en `Referrer-Policy` ingesteld.
- **Bestandstypen blokkeren:** bestanden zoals `.md`, `.log`, `.bak`, `.ini` en `.conf` zijn niet via de browser bereikbaar.

## Problemen en oplossingen

**1. De 404-pagina verwees naar de verkeerde map.**  
Mijn eerste `ErrorDocument`-regel verwees naar `/404.html`. Daardoor zocht Apache in de hoofdmap van `htdocs` in plaats van in de portfolio-map. Ik heb dit opgelost door `/portfolio/404.html` te gebruiken. Daarna werd de juiste pagina getoond.

**2. De stylesheet werkte niet op de 404-pagina.**  
Omdat de foutpagina vanuit een andere URL wordt geladen, werkten relatieve paden naar de CSS niet betrouwbaar. Ik heb de stylesheet en afbeeldingen daarom met een absoluut pad vanaf de site-root gekoppeld, bijvoorbeeld `/portfolio/css/style.css`.

**3. Controleren of .htaccess echt werkte.**  
Een aangepaste foutpagina kan ook verschijnen zonder dat de regel goed is ingesteld. Daarom heb ik apart getest of `http://localhost/portfolio/.htaccess` een **403 Forbidden** geeft. Dat was het geval, waarmee de beveiliging aantoonbaar werkt.

**4. Testen via localhost in plaats van het bestand openen.**  
Als je een HTML-bestand direct opent, worden Apache-regels zoals `.htaccess` en `ErrorDocument` niet uitgevoerd. Ik ben de site daarom altijd via `http://localhost/portfolio/` blijven testen.

## Bonus

Ik heb drie bonusonderdelen toegevoegd: een responsive design voor mobiel en tablet, een eigen favicon en een custom 404-pagina. De site gebruikt geen framework of externe bibliotheek; alle vormgeving komt uit één eigen CSS-bestand.

## Conclusie

Met dit project heb ik geleerd hoe Apache bestanden serveert, hoe je met `.htaccess` beveiliging en foutafhandeling regelt en waarom testen via een echte webserver anders is dan een bestand lokaal openen. De portfolio is klaar om in de les te presenteren.
