---
{"dg-publish":true,"permalink":"/1-projects/single-player-tarkov/spt-aki-fika/spt-aki-fika-server-modding-guide/","created":"2024-11-23T16:51:04.000+01:00","updated":"2025-01-18T21:29:24.894+01:00"}
---

# SPT-AKI-FIKA - Server Modding Guide
---
Dieser Guide ist Teil des [[1 Projects/Single Player Tarkov/SPT-AKI-FIKA/SPT-AKI-FIKA\|SPT-AKI-FIKA]] -Projekts und beschreibt schrittweise die Installation eines SPT-AKI-FIKA-Servers.

| PC Specs         | Memory                                   | Graphics                                       | Motherboard                        |
| ---------------- | ---------------------------------------- | ---------------------------------------------- | ---------------------------------- |
| April 2024 Build | WD_Black SN850X 1TB M2.2280              | MSI GAMING X SLIM NVIDIA GeForce RTX 4090 24GB | ASRock B650 PRO RS ATX AM5         |
| Windows 11       | G.Skill Flare X5 64GB DDR5-6000 CL30 RAM | 1440p 31" Screen                               | AMD Ryzen 7 7800X3D 4.2 GHz 7-Core |
*https://pcpartpicker.com/user/Torim98/saved/#view=QQrqbv

| SPT Version | Last Updated    |
| ----------- | --------------- |
| 3.9.8       | August 19, 2024 |
> SPT developers no longer provide old builds and have stated that archived, outdated files should not be shared without explicit permission. Mod developers insist that mod files not be shared between users; always get them through the official Filebase or SPT Pub Discord server from the developers themselves.
## SPT-AKI Installation
---
1. Installiere Live-Tarkov. Solltest du Live-Tarkov bereits installiert haben, update auf die aktuellste Version über den Battlestate-Launcher.
	https://www.escapefromtarkov.com/
	![Pasted image 20241214201639.png](/img/user/6%20System/assets/Pasted%20image%2020241214201639.png)
	![Pasted image 20241214202914.png](/img/user/6%20System/assets/Pasted%20image%2020241214202914.png)
2. Schließe den Battlestate-Launcher vollständig.
3. Lade den automated SPT-AKI-Installer herunter.
	https://sp-tarkov.com/#download
	![Pasted image 20241214203110.png](/img/user/6%20System/assets/Pasted%20image%2020241214203110.png)
4. Führe den Installer aus und installiere SPT-AKI.
	![Pasted image 20241214203248.png](/img/user/6%20System/assets/Pasted%20image%2020241214203248.png)
	![Pasted image 20241214203318.png](/img/user/6%20System/assets/Pasted%20image%2020241214203318.png)
	*Als Installationsverzeichnis wahlweise die schnellste SSD mit ausreichendem Speicherplatz (~50GB) auswählen*
	![Pasted image 20241214203426.png](/img/user/6%20System/assets/Pasted%20image%2020241214203426.png)
	*Alle Pre-Checks müssen erfolgreich sein, exemplarischer Screenshot für SPT-AKI 3.10.2, der Rest dieses Dokuments bezieht sich aber auf SPT-AKI 3.9.8*
	- Der Installer kopiert anschließend automatisch die Live-Tarkov Files in das Zielverzeichnis und installiert SPT-AKI.
	![Pasted image 20241214203651.png](/img/user/6%20System/assets/Pasted%20image%2020241214203651.png)
5. Starte das `SPT.Server.exe` und das `SPT.Launcher.exe` initial.
	![Pasted image 20241214204004.png](/img/user/6%20System/assets/Pasted%20image%2020241214204004.png)
	*Screenshot for 3.10.2*
	![Pasted image 20241214204037.png](/img/user/6%20System/assets/Pasted%20image%2020241214204037.png)
6. Lege ein Test-Profil zum Modden an.
	![Pasted image 20241214204114.png](/img/user/6%20System/assets/Pasted%20image%2020241214204114.png)
	![Pasted image 20241214204145.png](/img/user/6%20System/assets/Pasted%20image%2020241214204145.png)
	*Für diesen Guide gelten Standard-Profile als Basis*
7. Starte das Spiel und teste grundlegende Funktionen.
	![Pasted image 20241214204234.png](/img/user/6%20System/assets/Pasted%20image%2020241214204234.png)
	![Pasted image 20241214204322.png](/img/user/6%20System/assets/Pasted%20image%2020241214204322.png)
	![Pasted image 20241214204345.png](/img/user/6%20System/assets/Pasted%20image%2020241214204345.png)
	![Pasted image 20241214204410.png](/img/user/6%20System/assets/Pasted%20image%2020241214204410.png)
	- Beende anschließend das Spiel und den Server mit `LCrtl+C`
## SPT-AKI-Installation Tweaks
---
Die folgenden Tweaks beschreiben grundlegende Perfomance- und Spieleinstellungen, bevor im Anschluss die Installation und Konfiguration von Mods beschrieben wird.
### boot.config
Passe die boot.config im Verzeichnis `EFT-SPT-AKI-FIKA/EscapeFromTarkov_Data/boot.config` an, um die Performance zu verbessern:
```JSON
gfx-enable-gfx-jobs=1
gfx-enable-native-gfx-jobs=1
gfx-disable-mt-rendering=1
wait-for-native-debugger=0
vr-enabled=0
hdr-display-enabled=0
gc-max-time-slice=10
job-worker-count=15 (1 fewer than your CPU thread total)
single-instance=
```
*Diese Konfiguration kann auch für die Clients angewendet werden, es ist aber auf die Anzahl der CPU-Threads zu achten.*
![Pasted image 20250102182726.png](/img/user/6%20System/assets/Pasted%20image%2020250102182726.png)
Setze im Anschluss in den Tarkov-Settings "Only use physical cores":
![Pasted image 20250102183023.png](/img/user/6%20System/assets/Pasted%20image%2020250102183023.png)
### CONFIGURATION folder
---
Lege im Tarkov-Verzeichnis einen CONFIGURATION-Ordner an.
![Pasted image 20250102183121.png](/img/user/6%20System/assets/Pasted%20image%2020250102183121.png)
In diesem Verzeichnis werden alle Modding-Utilities, die in [[1 Projects/Single Player Tarkov/SPT-AKI-FIKA/SPT-AKI-FIKA - Server Modding Guide#Mod-Installation und -konfiguration\|#Mod-Installation und -konfiguration]] installiert werden und zur Konfiguration von Mods verwendet werden, genauso wie wichtige .ini-Files und Kommentare abgelegt.
![Pasted image 20250102183320.png](/img/user/6%20System/assets/Pasted%20image%2020250102183320.png)
*Späterer Aufbau des Verzeichnisses*
Es biet sich an zunächst die `boot.config` zu verlinken. Gleiches gilt für den profiles-Ordner (liegt unter `EFT-SPT-AKI-FIKA\user\profiles`) indem alle Spielerprofile abliegen. In der `ingame_shortcuts.txt` werden alle Mod-Config-Shortcuts beschrieben.
```ingame_shortcuts.txt
F12 - Mod config menu
F9 - Donuts config
F8 - Alternative mod config screen
F6 - SAIN config
F5 - Ingame browser for raid-review, alternatively open http://127.0.0.1:7829/ in browser
```
Sollte es zu einer Mod mehrere Config-Files und Utilities geben, sind diese in einem Unterordner (siehe RaidOverhaulConfig) abzulegen.
### Ingame-Settings
---
Anschließend die Ingame-Settings gem. der folgenden Screenshots anpassen.
*Ggf. sind auf den Screenshots bereits Mod-Settings enthalten, die in der Sektion [[1 Projects/Single Player Tarkov/SPT-AKI-FIKA/SPT-AKI-FIKA - Server Modding Guide#Mod-Installation und -konfiguration\|#Mod-Installation und -konfiguration]] aber nochmal aufgeführt sind.*
![Pasted image 20250118212445.png](/img/user/6%20System/assets/Pasted%20image%2020250118212445.png)
![Pasted image 20250118212507.png](/img/user/6%20System/assets/Pasted%20image%2020250118212507.png)
![Pasted image 20250118212525.png](/img/user/6%20System/assets/Pasted%20image%2020250118212525.png)
![Pasted image 20250118212547.png](/img/user/6%20System/assets/Pasted%20image%2020250118212547.png)
![Pasted image 20250118212603.png](/img/user/6%20System/assets/Pasted%20image%2020250118212603.png)
- Wahlweise können die folgenden oben aufgeführten PostFX-Settings auch aktiviert werden
![Pasted image 20250118212631.png](/img/user/6%20System/assets/Pasted%20image%2020250118212631.png)
![Pasted image 20250118212646.png](/img/user/6%20System/assets/Pasted%20image%2020250118212646.png)
![Pasted image 20250118212713.png](/img/user/6%20System/assets/Pasted%20image%2020250118212713.png)
![Pasted image 20250118212731.png](/img/user/6%20System/assets/Pasted%20image%2020250118212731.png)
![Pasted image 20250118212748.png](/img/user/6%20System/assets/Pasted%20image%2020250118212748.png)
![Pasted image 20250118212801.png](/img/user/6%20System/assets/Pasted%20image%2020250118212801.png)
## FIKA Installation
---
## Mod-Installation und -konfiguration
---
<?xml version="1.0" encoding="UTF-8"?><svg xmlns="http://www.w3.org/2000/svg" width="15" height="205" version="1.1" viewBox="0 0 39.688 54.24"> <g transform="translate(-69.7 -93.956)" fill="none" stroke="#008000">  <path d="m69.7 146.87h39.688" stroke-width="2.6458"/>  <g transform="translate(-.36252)">   <path d="m89.544 146.87v-6.794" stroke-width="2.6458"/>   <path d="m88.77 141.34 6.6272-8.1886" stroke-width="2.3347"/>   <path d="m89.919 141.46-5.5766-5.8386" stroke-width="2.3102"/>  </g>  <circle cx="100.95" cy="126.47" r="6.9136" stroke-width="2.6458"/>  <circle cx="79.351" cy="130.4" r="5.0854" stroke-width="2.6458"/> </g></svg> #seedling 