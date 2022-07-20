# Modellübertragung von Transkribus nach eScriptorium

Die Modellübertragung ist an sich nicht direkt möglich, jedoch kann die GT also die, in Transkribus erstellte Transkription und die dazugehörigen Bilder in eScriptorium importiert werden. Anschließend kann das Modell in eScriptorium erneut trainiert werden.
 
## Daten aus Transkribus exportieren und in eScriptorium importieren 

### Daten aus Transkribus exportieren

- Für die Daten-Übertragung wird **XML PAGE**-Format empfohlen
- Zunächst Export aus Transkribus einrichten: Collection auswählen, im Reiter „HTR Model Data“ → Rechtsklick auf gewünschtes Set → Ziel-Collection auswählen → bestätigen



- Nun in Ziel-Collection wechseln: Dokument markieren → Exportieren → PAGE exportieren → IMAGE exportieren. Wichtig: Dateibenennungsmuster auf den Standardwert ("${Dateiname}") einstellen (einige Daten gehen verloren, da das ALTO XML Format nicht alle von Transkribus verwendeten Daten enthält)

Bild

**Hinweis:** wenn die Seitenbenennung in Transkribus nicht fortlaufend ist, dann „Filename pattern“ wählen: „docId+pageNr+pageID“ → Seiten werden dann in eScriptorium gleich nummeriert wie in Transkribus (funktioniert nicht, wenn man Einstellung pageNr.+filename auswählt, dann werden Seiten willkürlich geordnet)

### Daten in eScriptorium importieren  

- Zunächst ein neues „Dokument“ in eScriptorium erstellen
- In der Zwischenzeit entpacken des von Transkribus erzeugten „Archivs“ und extrahieren der Bilder auf dem Rechner
- Unter dem Reiter „Bilder“ im Dokument, müssen nun die Dateien hochgeladen werden 
- Die Bilder können einfach per Drag-and-Drop hochgeladen werden bzw. über einen Links-Klick in das entsprechende Feld öffnet sich der Explorer
- Sobald Upload abgeschlossen: „Import“ (ebenfalls Reiter „Bilder“) → „Transcriptions („XML“); hier einfach von Transkribus erstelltes „Archiv“ unverändert hochladen (falls dies zu lange dauert, können auch Bilder zuerst entfernt werden)
- Mögliche Dateiarten für die Transkriptionen sind: **ALTO XML**, **PAGE XML** oder **ZIP-Datei**, die **ALTO** oder **PAGE XML** enthält
- **Wichtig:** Qualität der importierten Abschrift überprüfen, durch Kontrolle jeder einzelnen Seite (manchmal muss manuell XML-Quelldatei bearbeitet werden)

### Neuberechnung der Linienmasken  
- Bevor Modell trainiert werden kann, müssen mit Grundlinien verbundene Masken an Kraken angepasst werden
- dafür im Reiter „Bilder“ einfach alle Bilder des Dokuments markieren ->  „Segmentieren“ -> „Nur Zeilenmasken“
- Aktivierung der Option „override“

Bild

- Wenn eScriptorium bei Verarbeitung auf Fehler stößt, müssen diese händisch korrigiert werden
- Nach diesen Schritten kann ein Kraken-Modell in eScriptorium trainiert werden und die Leistung mit Transkribus verglichen werden
- Hinweise für die richtige Zusammenstellung von Trainings- und Auswertungssets in Transkribus: konsultieren Sie den Bereich "Details" und die Abschnitte "Show Train Set" und "Show Validation Set". Dieser Bereich ist über die Registerkarte "Tools/Text/Recognition Models" von Transkribus zugänglich.

Weitere Informationen zum Training von Modellen in eScriptorium finden Sie [hier](https://github.com/UB-Mannheim/eScriptorium_Dokumentation/blob/gh-pages/Nutzungsanleitung_eScriptorium.md#18-modelle-trainieren).

## Bekannte Probleme
	
- Es ist nicht möglich, ein Transkript zu importieren, dessen Segmentierung auf der Verwendung von Tabellen in Transkribus basiert
- Die Segmentierung mit eScriptorium schlägt bei einigen Bildern fehl, weil die Basislinien-/Maskenpaare beim Import schlecht erzeugt werden.
**Ad-hoc-Lösungen:**
- Direkt in die betreffende XML-Datei eingreifen, die Zeile zu löschen, die Datei erneut zu importieren und die Zeile manuell neu zu erstellen
- oder das Problem in eScriptorium-Umgebung beheben

Die Anleitung basiert auf einer [Dokumentation von Alix Chague](https://lectaurep.hypotheses.org/documentation/de-transkribus-a-escriptorium), die ins Deutsche übersetzt und ergänzt wurde.
