# Kast

[English](README.md) | **Deutsch**

Ein schlanker, portabler Videoplayer für Windows, der fast jedes Format abspielt und auf **Chromecast-, DLNA- und AirPlay-Geräte streamt**.

![Kast](docs/screenshot.png)

- Spielt MP4, M4V, MKV, AVI, MOV, WebM, WMV, TS und mehr ab – angetrieben von [mpv](https://mpv.io) mit Hardware-Dekodierung
- **Cast-Button** im Player: Chromecast / Google TV, DLNA-Smart-TVs und AirPlay-Empfänger im eigenen Netzwerk
- **Tonspur** und **Untertitel** wählen (eingebettet oder externe `.srt`/`.ass`/`.vtt`, werden automatisch geladen), am PC und auf dem Fernseher
- **Untertitel-Stil**-Editor: Schriftart, Größe, Farbe, fett/kursiv, Rand, Schatten, Hintergrundbox, Position – wird live übernommen
- Wiedergabeliste aus dem Ordner, zuletzt geöffnete Dateien, Fortsetzen an der letzten Position, Untertitel-/Tonverzögerung, Wiedergabegeschwindigkeit, Bildschirmfotos, URLs
- **Tastenkürzel**, die sich in den Einstellungen ändern lassen
- Portabel: keine Installation, Einstellungen in `settings.json` neben der EXE
- Deutsche und englische Oberfläche (folgt der Windows-Sprache), helles und dunkles Design, Windows-Akzentfarbe

## Download

- **[Neueste Version](https://github.com/naderi/kast/releases/latest)** – `Kast-<version>-win-x64.7z` herunterladen, in einen beliebigen Ordner entpacken und `Kast.exe` starten.
- Oder mit [Scoop](https://scoop.sh):

  ```
  scoop bucket add naderi https://github.com/naderi/scoop-bucket
  scoop install naderi/kast
  ```

## Bedienung

- **Öffnen** eines Videos per Button, Drag & Drop, Kommandozeile oder (optional) über „Öffnen mit“ im Explorer
- **Stopp:** der ■-Knopf neben Wiedergabe beendet die Wiedergabe und kehrt zum Startbildschirm zurück (die Position bleibt zum Fortsetzen erhalten)
- **Maus:** Klick = Pause, Doppelklick = Vollbild, Mausrad = Lautstärke, Video ziehen = Fenster verschieben
- **Tasten** (alle in den Einstellungen änderbar): Leertaste Pause · ←/→ 5 s (Umschalt: 1 s) · ↑/↓ Lautstärke · M Ton an/aus · F Vollbild · S Untertitel an/aus · V nächste Untertitelspur · A nächste Tonspur · Z/X Untertitelverzögerung · Strg+Plus/Minus Geschwindigkeit (Strg+0 normal) · R Bild um 90° drehen · Strg+Umschalt+S Bildschirmfoto · N/P nächstes/vorheriges · Strg+O öffnen · Strg+R zuletzt geöffnet · Strg+, Einstellungen
- Das Fenster behält das Seitenverhältnis des Videos bei, es gibt also keine schwarzen Balken; *Fenster füllen (zuschneiden)* im ⚙-Menü füllt es vollständig aus
- *Bild drehen* (Rechtsklick-Menü oder R) dreht ein seitlich liegendes oder auf dem Kopf stehendes Video um 90° pro Schritt, auch auf dem Fernseher; Videos mit Drehungsinformation (Handyvideos) werden automatisch aufrecht angezeigt

## Streamen

Auf den Cast-Button in der Steuerleiste unten klicken und ein Gerät wählen. Das Video am PC pausiert, und die Bedienelemente des Players – Pause, Spulen, Lautstärke, Tonspur, Untertitel, Untertitelverzögerung und -stil – steuern jetzt den Fernseher. Weiter/Zurück wechselt die Datei auf dem Fernseher, und am Ende eines Videos folgt die nächste Datei aus dem Ordner. Beim Streamen wird der Stopp-Knopf neben Wiedergabe zu einem Cast-Symbol mit Stopp-Zeichen und beendet das Streamen; am PC geht es dort weiter, wo der Fernseher aufgehört hat.

Kast streamt die Datei vom PC über das lokale Netzwerk:

| Gerät | Spielt direkt ab | Wird live umgewandelt |
|---|---|---|
| Chromecast / Google TV | MP4 / WebM mit H.264, VP8 (HEVC/VP9 bei 4K-Modellen) und AAC, MP3, Opus, FLAC | andere Container werden ohne Qualitätsverlust umverpackt; andere Videocodecs werden mit dem GPU-Encoder (NVENC, Quick Sync, AMF oder Media Foundation) neu kodiert |
| DLNA-Fernseher | MP4 mit H.264 und AAC/MP3 | umverpackt oder neu kodiert nach MPEG-TS |
| AirPlay | MP4 mit H.264/HEVC und AAC | umverpackt oder neu kodiert nach HLS |

Untertitel zeichnet der Chromecast selbst, mit deinem Untertitel-Stil. DLNA- und AirPlay-Geräte bekommen sie ins Bild eingebrannt (das gilt auch für Bild-Untertitel wie PGS auf dem Chromecast).

Hinweise:
- PC und Gerät müssen im selben Netzwerk sein. Erscheint nichts auf dem Fernseher, Kast in der Windows-Firewall für private Netzwerke erlauben.
- AirPlay: Geräte, die eine Kopplung per PIN verlangen (neuere Apple TVs), werden noch nicht unterstützt.

## Optionen

⚙-Menü → *Einstellungen*:

- Sprache, Design
- Fortsetzen, Hardware-Dekodierung, Untertitel automatisch anzeigen, bevorzugte Ton- und Untertitelsprachen (Standard: Englisch, dann Deutsch)
- *Ruhezustand während des Streamens verhindern* – der Fernseher streamt vom PC, der Ruhezustand würde die Wiedergabe abbrechen; der Bildschirm darf sich trotzdem ausschalten
- Ordner für Bildschirmfotos (Standard: `Bilder\Kast`)
- Untertitel-Stil
- *Integration* – standardmäßig alles aus, Kast ändert nichts außerhalb seines Ordners, solange du nichts davon einschaltest: „Öffnen mit“ für Videodateien, Verknüpfung auf dem Desktop, Verknüpfung im Startmenü
- Updates

## Programm-Updates

Kast aktualisiert sich selbst aus den [Releases dieses Repositorys](https://github.com/naderi/kast/releases):

- Einmal täglich sucht es im Hintergrund nach einer neuen Version (abschaltbar: *Automatisch suchen (einmal täglich)*). Eine neue Version zeigt einen orangen Punkt am ⓘ-Button.
- Im Info-Fenster (ⓘ): *Nach Updates suchen* → *Update herunterladen* → *Neu starten & aktualisieren*.
- Ein Download wird nur verwendet, wenn seine Signatur (`.sig`) zum in Kast eingebauten Schlüssel passt; alles andere wird abgelehnt. `settings.json` bleibt unangetastet.
- Das Update ersetzt nur `Kast.exe`. Bringt ein Release neuere `libmpv-2.dll` / `ffmpeg.exe` mit, weist das Info-Fenster darauf hin: `Kast-x.y.z-win-x64.7z` herunterladen, Kast beenden und in den Kast-Ordner entpacken (vorhandene Dateien ersetzen).
- Mit Scoop installiert, verweist Kast nur auf `scoop update kast`.

## Lizenz

Freeware – kostenlos nutzbar, aber **Verkauf verboten**. Siehe [LICENSE](LICENSE).
Die enthaltenen `libmpv-2.dll` (mpv) und `ffmpeg.exe` (FFmpeg) sind eigenständige LGPL-Komponenten, siehe [LICENSE](LICENSE) und `THIRD-PARTY-NOTICES.txt`.

© 2026 [Ali Naderi](https://github.com/naderi) · [digitalent.dev](https://digitalent.dev/de/)
