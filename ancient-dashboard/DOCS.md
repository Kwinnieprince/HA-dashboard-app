# Ancient Home Assistant installeren

Vereist Home Assistant OS met de app-/add-onwinkel, internet voor de installatie
en een 64-bits apparaat. Raspberry Pi 5 wordt ondersteund via `aarch64`.
Deze experimentele verpakking is nog niet op een echte Supervisor-installatie getest.

1. Publiceer deze repository op GitHub (de map `ancient-dashboard` moet erin staan).
2. Open **Instellingen → Apps → Appwinkel** (of **Add-ons → Add-onwinkel**).
3. Kies **⋮ → Repositories** en voeg toe:
   `https://github.com/Kwinnieprince/HA-dashboard-app`
4. Vernieuw de winkel en installeer **Ancient Home Assistant**.
   De container wordt op je Pi gebouwd; er hoeft niets naar een containerregister
   gepubliceerd te worden. De eerste installatie kan enkele minuten duren.
5. Start de app, zet automatisch starten aan en open de webinterface.
6. Open op de iPad `http://JOUW_HA_IP:8095`, bijvoorbeeld
   `http://192.168.0.21:8095` als dat het adres van je HA-machine is.
7. Vul in de Ancient-wizard het bereikbare HA-adres en een langlevend toegangstoken
   van een afzonderlijke, niet-beheerder HA-gebruiker in. Gebruik een IP-adres of
   DNS-naam die de app kan bereiken, niet `localhost`.
8. Maak een eigen dashboardwachtwoord, kies entiteiten en sla de indeling op.
9. Voeg de pagina via Safari toe aan het beginscherm en stel Begeleide toegang in.

## Opslag, back-ups en updates

De database staat in `/data/dashboard/dashboard.sqlite3`. Supervisor bewaart `/data`
bij herstarten en app-updates. Selecteer deze app in je HA-back-up. Verwijderen van
de app kan de opslag verwijderen: maak eerst een back-up. Back-ups bevatten ook
het HA-token en moeten vertrouwelijk blijven. De upstream app bewaart dit token
op de server; het dashboardwachtwoord wordt gehasht opgeslagen.

Deze versie gebruikt een vastgezette upstream-container. Nieuwe upstream-releases
worden pas gebruikt wanneer deze repository expliciet wordt bijgewerkt. Verhoog
bij elke gepubliceerde wijziging ook `version` in `config.yaml`.

## Netwerk

Poort 8095 is bedoeld voor je vertrouwde lokale netwerk. Stel geen port-forwarding
in naar deze app. HTTP versleutelt het wachtwoord en sessieverkeer niet; gebruik
voor toegang buiten je LAN een geschikte beveiligde oplossing. Ingress en een
zijbalkpaneel zijn niet inbegrepen. De iPad opent de app rechtstreeks.

Bij een poortconflict kun je de externe poort in de netwerkopties wijzigen.
Bewaar de interne poort 8095. Als je HA alleen via HTTPS van buitenaf opent, open
het lokale HTTP-adres op de iPad zelf in plaats van de knop Webinterface.

## Eerste praktijktest

- App starten; logboek controleren op een succesvolle start.
- Wizard voltooien en één sensor en één lamp toevoegen.
- Pagina verversen en op de echte iPad testen.
- App herstarten: verbinding en indeling moeten bewaard blijven.
- HA-back-up maken en herstel eerst op een testinstallatie controleren.

Bij problemen: deel de foutmelding uit het logboek, zonder tokens/wachtwoorden.
