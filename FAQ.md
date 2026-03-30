# FAQ für Teilnehmer – Tuizz 💃🕺

Herzlich willkommen bei Tuizz! Hier findest du Antworten auf die häufigsten Fragen, damit du das Beste aus deinem Tanzerlebnis herausholen kannst.

---

## 1. Wie funktioniert Tuizz eigentlich?

Tuizz ist ein interaktives System, das dein Tanzen in zwei Schritten bewertet:

1.  **Deine Selbsteinschätzung:** Nach deinem Tanz wählst du im "Tänzer-Modus" auf einer Skala von 1 bis 4 aus, wie du dich selbst gefühlt hast (1 = Passabel bis 4 = Sehr gut).
2.  **Die Jury-Bewertung:** Parallel dazu bewertet dich eine Jury in vier Kategorien: Kreativität, Rhythmus, Ausstrahlung und Technik (jeweils 1 bis 10 Punkte).

**Der Clou:** Das System vergleicht am Ende beide Bewertungen. Wenn deine eigene Einschätzung nah an der Meinung der Profis liegt, erhältst du wertvolle **Bonuspunkte**!

---

## 2. Was habe ich davon, Tuizz zu nutzen?

Die Nutzung von Tuizz bietet dir mehrere Vorteile:

*   **Bessere Selbstwahrnehmung:** Du lernst, dein eigenes Tanzen realistischer einzuschätzen. Das ist eine der wichtigsten Fähigkeiten, um als Tänzer(in) schnell Fortschritte zu machen.
*   **Faires Feedback:** Du erhältst nicht nur eine einfache Note, sondern detailliertes Feedback in vier verschiedenen Bereichen. So weißt du genau, wo deine Stärken liegen und woran du noch arbeiten kannst.
*   **Spielerischer Wettbewerb:** Das Ranking motiviert und macht Spaß, ohne den Druck eines klassischen Turniers. Der Fokus liegt auf der persönlichen Entwicklung und der Übereinstimmung mit der Jury.
*   **Transparenz:** Du siehst sofort, wie deine Punkte zustande kommen und wie du im Vergleich zu anderen abschneidest.

*   **Vorbereitung auf Abzeichnungen (z.B. ADTV):** Tuizz ist das ideale Training für offizielle Tanzabzeichen. Durch die gezielte Arbeit an Technik, Rhythmus und Ausstrahlung sowie die ständige Selbstreflexion bist du bestens auf die Anforderungen von Verbänden wie dem ADTV vorbereitet.


---

## 3. Wie werden die Bonuspunkte berechnet?

Wir belohnen "Ehrlichkeit" und "Selbstkenntnis". So funktioniert es:

*   Wir rechnen die Jury-Bewertung (Durchschnitt aus 10 Punkten) auf unsere 4er-Skala um.
*   **0 Punkte Abweichung:** Wenn du dich exakt so einschätzt wie die Jury, bekommst du **+3 Bonuspunkte**.
*   **1 Punkt Abweichung:** Liegst du nur knapp daneben, gibt es immer noch **+2 Bonuspunkte**.
*   **Mehr Abweichung:** Du erhältst deine regulären Jury-Punkte, aber keinen zusätzlichen Bonus.

---

## 4. Werden meine Daten gespeichert?

Ja, aber nur **lokal in deinem Browser**. Das bedeutet:
*   Keine Registrierung notwendig.
*   Keine Daten werden an einen Server gesendet.
*   Wenn du den Browser-Cache löschst, sind die Daten weg – also schau dir dein Ranking am Ende des Abends gut an!

---

## 5. Kann ich Tuizz auch alleine zum Üben nutzen?

Absolut! Du kannst Tuizz auch nutzen, um deine eigenen Fortschritte zu tracken. Lass einfach einen Freund oder deinen Tanzlehrer die Jury-Rolle übernehmen, während du dich selbst einschätzt.

---

**Hast du noch weitere Fragen?**
Wende dich einfach an dein Tanzschul-Team oder erstelle einen Vorschlag in unserem GitHub-Repository!

---
Das ist die Kernfrage bei einer dezentralen Offline-App. Es gibt drei mögliche Ansätze:
Problem: Jedes Gerät hat seinen eigenen localStorage → keine automatische Synchronisation.

Option A – Manuelles Zusammenführen (einfachste Lösung)
Jede Jury-Person exportiert am Abend ihre JSON-Datei. Eine Zentralperson importiert alle Dateien nacheinander in eine “Merge”-Funktion die ich in Tuizz einbauen kann. Die App berechnet dann automatisch den Durchschnitt aller Jury-Bewertungen pro Paar.
Option B – Gemeinsame JSON-Vorlage als “Schnittstelle”
Vor dem Abend: Zentralperson erstellt die Vorlage mit allen Paaren und Playlists → verteilt per E-Mail. Nach dem Abend: Alle exportieren → Zentralperson merged.
Option C – Zentraler Server (aufwändig)
Eine Person betreibt einen lokalen Server oder nutzt z.B. Google Sheets als Backend. Deutlich mehr Aufwand, funktioniert aber in Echtzeit.

Für eure Situation wäre Option A + B kombiniert am sinnvollsten — alles bleibt offline und in einer einzigen HTML-Datei.​​​​​​​​​​​​​​​​
Jetzt baue ich die vollständige Merge-Funktion ein — mehrere JSON-Dateien gleichzeitig auswählen, automatisch zusammenführen:​​​​​​​​​​​​​​​​

Jetzt die Merge-Logik in JS einfügen:​​​​​​​​​​​​​​​​

Fertig! So funktioniert der E-Mail-Workflow:

Ablauf an einem Tanzabend:

'''
Vorbereitung

  └─ Zentralperson erstellt Vorlage-JSON → per E-Mail an alle

Während des Abends (jede Person für sich)

  
└─ tuizz_final.html öffnen
  
└─ Vorlage importieren
  
└─ Paare bewerten (Jury) oder einschätzen (Tänzer)
  
└─ Am Ende: Exportieren → JSON per E-Mail zurück an Zentralperson

Auswertung (Zentralperson)
  
└─ Alle empfangenen JSONs auf einmal auswählen (🔀 Mehrere JSON-Dateien wählen)
  
└─ Vorschau prüfen: Tabelle zeigt gemittelte Jury-Wertungen + Anzahl Dateien pro Paar
  
└─ "Zusammenführen & Speichern" → fertiges Ranking
'''

Was die Merge-Funktion macht:
	∙	Mittelt alle Jury-Bewertungen über alle Dateien pro Paar (z.B. 3 Jurymitglieder → Durchschnitt)
	∙	Selbsteinschätzungen der Tänzer bleiben erhalten
	∙	Vorschau zeigt wie viele Dateien pro Paar gefunden wurden
	∙	Kein Datenverlust — erst Vorschau, dann bestätigen​​​​​​​​​​​​​​​​



Viel Spaß beim Tanzen! ✨