[README.md](https://github.com/user-attachments/files/33535526/README.md)
# Nova Client

Modularer Fabric-Client (Minecraft **1.21.11**, Fabric Loader **0.19.5**, Mojang-Mappings) mit ClickGUI.

## Module
| Modul | Kategorie | Beschreibung |
|---|---|---|
| Fullbright | Darstellung | Volle Helligkeit über einen clientseitigen, unsichtbaren Nachtsicht-Effekt (Standardtaste B) |
| Zoom | Darstellung | Taste halten (Standard C), Faktor und sanfter Übergang einstellbar |
| AutoSprint | Bewegung | Sprintet automatisch beim Vorwärtslaufen |
| HUD | HUD | FPS, Ping, Koordinaten, Blickrichtung (oben links) |

## Bedienung
* **Rechts-Shift**: ClickGUI öffnen (Klick auf Modulnamen = an/aus, `...` = Einstellungen)
* Alle Tasten (auch pro Modul) unter *Optionen > Steuerung > Tastenbelegung > Nova Client*
* Config: `.minecraft/config/novaclient.json`

## Bauen
1. JDK 21 installieren.
2. Wrapper erzeugen (die `gradle-wrapper.jar` liegt nicht bei): entweder `gradle wrapper --gradle-version 9.4.1`
   oder `gradlew`/`gradlew.bat` + `gradle/wrapper/gradle-wrapper.jar` aus einem frisch generierten Projekt
   von https://fabricmc.net/develop/template kopieren.
3. `./gradlew build` (Windows: `gradlew.bat build`) - das fertige Jar liegt in `build/libs/novaclient-1.0.0.jar`.
4. Testen: `./gradlew runClient` oder das Jar in den `mods`-Ordner legen (Fabric API wird benötigt).

## Neues Modul hinzufügen
1. Klasse in `module/impl/` anlegen, die `Module` erweitert (Beispiel: `AutoSprintModule`).
2. In `ModuleManager.init()` mit `register(new MeinModul())` eintragen.
3. Übersetzung für die Taste in `assets/novaclient/lang/*.json` ergänzen: `key.novaclient.module.<id>`.

## Falls etwas nicht kompiliert
Das Projekt nutzt Mojang-Namen für 1.21.11. Bei einem Fehler in einer Mixin-Zeile (`GameRendererMixin`) oder einem
Minecraft-Aufruf: Fehlermeldung kopieren und fragen.
