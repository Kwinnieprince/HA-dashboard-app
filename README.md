# HA Dashboard Apps

Een Home Assistant-apprepository met **Ancient Home Assistant**, een licht
webdashboard voor oudere iPads. Dit is een zelfstandige verpakking van het
[upstreamproject](https://github.com/leodenglovescode/ancienthomeassistant),
niet een officiële uitgave van de oorspronkelijke maker of Home Assistant.

## Installeren

Voeg deze repository toe via de repositories in de Home Assistant-appwinkel:

```text
https://github.com/Kwinnieprince/HA-dashboard-app
```

Installeer **Ancient Home Assistant**, start de app en open lokaal poort **8095**.
De dashboardwizard vraagt om je HA-adres, een toegangstoken en een eigen
wachtwoord. [Volledige handleiding](ancient-dashboard/DOCS.md).

## Status

Versie **0.1.0 — experimenteel**. Ondersteunt ARM64 (Raspberry Pi 5) en AMD64.
De verpakking wordt door Supervisor lokaal gebouwd. Er is geen Docker-runtime
beschikbaar op de ontwikkelmachine: de containerbuild, installatie en back-upherstel
moeten nog op Home Assistant worden gevalideerd. Alleen de verpakkingscode wordt
hier beheerd; upstream applicatiebroncode wordt niet gekopieerd.

## Onderhoud

De Dockerfile verwijst naar een onveranderlijke multi-platform upstream-digest.
Zie [UPSTREAM.md](UPSTREAM.md) voor versie, herkomst en updateprocedure.
Er is geen Ingress of automatische toegang tot de Supervisor-API; deze eerste
versie gebruikt de bestaande Ancient-installatiewizard.

Controleer de verpakking lokaal met:

```sh
python3 -m unittest discover -s tests -v
```
