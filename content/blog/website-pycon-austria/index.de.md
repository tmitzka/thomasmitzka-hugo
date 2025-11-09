---
draft: false
title: "Website der PyCon Austria"
slug: "website-pycon-austria"
date: 2025-10-15
summary: "Einblicke in die Website, die ich für die IT-Konferenz PyCon Austria erstellt habe."
tags: ["PyCon Austria", "Python", "Pelican", "WordPress", "Projekt"]
showTableOfContents: true
---

2025 fand erstmals die **PyCon Austria** statt – eine neue IT-Konferenz rund um die Programmiersprache **Python**.
Ich durfte die Website für diese Veranstaltung konzipieren und umsetzen. Mein Ziel: eine Plattform, die sich einfach pflegen lässt und den Spirit der Community widerspiegelt.

## Anforderungen

- Auflistung aller Vorträge und Workshops, verknüpft mit den jeweiligen Vortragenden  
- Einfache Aktualisierung von Inhalten, etwa Portraitfotos oder Beginnzeiten  
- Ein leicht zu bedienendes Backend für das Organisationsteam

---

## Umsetzung mit WordPress

Als technische Grundlage habe ich **WordPress** in Kombination mit dem Plugin-System [**JetPlugins**](https://crocoblock.com/) verwendet.

Damit lassen sich *Custom Post Types* (CPTs) definieren – eigene Inhaltstypen, die über Standard-Beiträge hinausgehen. So konnte ich das CMS genau auf die Anforderungen der Konferenz anpassen. Beispielsweise enthielt der CPT *„Speakers“* Felder für Foto, Biografie und Social-Media-Profile. Der CPT *„Workshops“* speicherte Beginnzeiten und Zielgruppen (z.B. Anfänger, Fortgeschrittene).

Die JetPlugins bieten außerdem die Möglichkeit, den Zusammenhang zwischen CPTs abzubilden. 
Jeder Vortrag oder Workshop konnte im Backend mit den passenden Speakern verknüpft werden, sodass im Frontend automatisch Kurzportraits unterhalb der Vortragsbeschreibung erschienen.

![Ansicht der Website „PyCon Austria 2025“](pycon-austria-2025-website.webp "Website der PyCon Austria 2025 (WordPress)")

Grundsätzlich hat die Website gut funktioniert, ich habe dafür mehrfach positives Feedback von Organisator:innen und Teilnehmer:innen bekommen. Im Betrieb hat sich aber ein Problem gezeigt: Speaker, Talks und Workshops wurden **ausschließlich in WordPress** gepflegt – ohne Schnittstelle zu dem System, über das Einreichungen verwaltet wurden.

Bei Konferenzen wie der PyCon Austria werden Vorträge über einen *Call for Papers* eingereicht.
Diese Beiträge werden auf einer externen Plattform bewertet. Änderungen an Titeln, Beschreibungen oder Personendaten mussten daher manuell in WordPress nachgetragen werden – das war unnötiger Aufwand.

## Relaunch als statische Website

Für die **PyCon Austria 2026** wollte ich die Website einfacher und offener gestalten.  
Die Lösung: ein **Static Site Generator** anstelle eines CMS. Statische Websites benötigen keine Datenbank und keine regelmäßigen Updates, dadurch sind sie schneller und sicherer.

Passend zu Python als Thema der Konferenz, habe ich mich für [**Pelican**](https://getpelican.com/) entschieden, einen Static Site Generator auf Basis von Python. Das Redaktionsteam bearbeitet die Seiten jetzt direkt als **Markdown-Dateien**, ganz ohne Login oder Backend.

In Absprache mit den Organisatoren habe außerdem die Struktur des Webauftritts neu gestaltet:
Die Hauptdomain [**pycon.at**](https://pycon.at) dient als zentrale Landing Page, während die Jahres-Websites über Subdomains erreichbar sind. Das macht die Archivierung einfacher und ermöglicht eigenständige Designs für jede Ausgabe der Konferenz.

Für 2025 und 2026 habe ich das Theme
[pelican-bootstrap3](https://github.com/getpelican/pelican-themes/tree/master/pelican-bootstrap3) verwendet und per CSS angepasst. Statt der voreingestellten Schriftart kommt *Source Sans* zum Einsatz, eine gut lesbare Open-Source-Schriftart.

![Ansicht der Website „PyCon Austria 2026“](pycon-austria-2026-website.webp "Website der PyCon Austria 2026 (Pelican)")

Über ein Plugin importiert Pelican Details zu den Vortragenden aus einer YAML-Datei, um sie in den statischen Seiten anzuzeigen. Die Beziehungen zwischen Vorträgen, Workshops und Personen werden in den **Metadaten der Markdown-Dateien** definiert. Damit die Änderungen nachvollziehbar bleiben, läuft das Projekt in einem **Git-Repository**.

### Vorteile der neuen Website

- Inhalte liegen als Textdateien vor – Markdown für Seiten, YAML für Speaker-Daten.  
- Änderungen erscheinen in unter einer Minute online: Inhalte in Pelican generieren, deployen, fertig.  
- Die Versionierung über Git erleichtert die Zusammenarbeit im Team.  
- Keine Logins, keine Datenbank, keine Updates — insgesamt weniger Wartungsaufwand.