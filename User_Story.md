Alles klar, Frederic — ich formuliere dir jetzt eine vollständige User‑Story‑Sammlung, die gleichzeitig als automatisierte Testbasis dienen kann.
Das bedeutet: Jede User Story ist vollständig nach INVEST‑Kriterien formuliert, enthält Akzeptanzkriterien im Given‑When‑Then‑Format und ist so präzise, dass sie direkt in automatisierte Tests (z. B. Cypress, Playwright, Jest, Robot Framework, Gherkin) überführt werden kann.

Ich zitiere kurz zwei Stellen aus deinem Dokument, um klarzumachen, worauf sich die Stories beziehen:

• „Tanz Memory/Quiz“
• „Paar auswählen: – Wähle ein Paar –“


---

Tuizz – User‑Story‑Sammlung als automatische Testbasis

1. Teilnehmer & Paare

US‑01 – Teilnehmer anlegen

Als Administrator möchte ich neue Tänzer anlegen können, damit sie an Quiz, Memory und Bewertungen teilnehmen können.

Akzeptanzkriterien (Gherkin):

Given die Teilnehmerverwaltung ist geöffnet
When ich einen neuen Tänzer mit gültigen Daten anlege
Then wird der Tänzer gespeichert
And erscheint in der Teilnehmerliste


---

US‑02 – Paare bilden

Als Trainer möchte ich zwei Tänzer zu einem Paar verbinden können, damit sie gemeinsam bewertet werden können.

Akzeptanzkriterien:

Given zwei existierende Tänzer
When ich sie als Paar speichere
Then erscheint das Paar in der Paarauswahl


---

US‑03 – Paar auswählen

Als Nutzer möchte ich ein Paar auswählen können, um ein Quiz oder eine Bewertung zu starten.

Akzeptanzkriterien:

Given die Paarauswahl ist sichtbar
When ich ein Paar auswähle
Then wird das Paar für den nächsten Schritt übernommen


---

2. Tänze & Playlists

US‑04 – Pflicht‑Tänze verwalten

Als Trainer möchte ich Pflicht‑Tänze definieren können, damit sie im Unterricht und im Quiz verfügbar sind.

Akzeptanzkriterien:

Given die Tanzverwaltung ist geöffnet
When ich einen Tanz als Pflicht markiere
Then erscheint er in der Liste der Pflicht‑Tänze


---

US‑05 – Lieblingstänze markieren

Als Nutzer möchte ich Tänze als Favoriten markieren, um sie schneller im Quiz auszuwählen.

Akzeptanzkriterien:

Given ein Tanz ist sichtbar
When ich ihn als Favorit markiere
Then erscheint er in der Favoritenliste


---

US‑06 – Video‑Material zu Tänzen hinzufügen

Als Trainer möchte ich Videos zu Tänzen hochladen, damit Lernende Schrittfolgen sehen können.

Akzeptanzkriterien:

Given ein Tanz ist ausgewählt
When ich ein gültiges Video hochlade
Then wird das Video gespeichert
And ist im Tanzprofil sichtbar


---

3. Quiz & Memory

US‑07 – Quiz starten

Als Nutzer möchte ich ein Quiz starten können, um mein Wissen über Tänze zu testen.

Akzeptanzkriterien:

Given ein Paar ist ausgewählt
When ich „Quiz starten“ drücke
Then beginnt das Quiz


---

US‑08 – Memory spielen

Als Nutzer möchte ich ein Memory spielen können, bei dem Tanzkarten zugeordnet werden müssen.

Akzeptanzkriterien:

Given das Memory ist gestartet
When ich zwei Karten aufdecke
Then werden sie verglichen
And bei Übereinstimmung bleiben sie offen


---

US‑09 – Video‑Quiz

Als Nutzer möchte ich kurze Tanzvideos erkennen müssen, um mein Wissen zu vertiefen.

Akzeptanzkriterien:

Given ein Video‑Quiz ist aktiv
When ein Clip abgespielt wird
Then muss ich den richtigen Tanz auswählen


---

4. Jury & Bewertung

US‑10 – Jury bewertet Runden

Als Jury‑Mitglied möchte ich Rundenwerte eingeben können, damit die Leistung eines Paars bewertet wird.

Akzeptanzkriterien:

Given ein Paar hat eine Performance abgeschlossen
When ich R1 und R2 Werte eingebe
Then werden die Werte gespeichert


---

US‑11 – Bonuspunkte vergeben

Als Jury‑Mitglied möchte ich Bonuspunkte vergeben können, um besondere Leistungen zu honorieren.

Akzeptanzkriterien:

Given eine Bewertung ist offen
When ich Bonuspunkte eingebe
Then werden sie zur Gesamtwertung addiert


---

US‑12 – Video‑Performance bewerten

Als Jury‑Mitglied möchte ich ein Performance‑Video ansehen und kommentieren können.

Akzeptanzkriterien:

Given ein Performance‑Video ist verfügbar
When ich es abspiele
Then kann ich Kommentare mit Zeitmarken hinzufügen


---

5. Ranking

US‑13 – Ranking anzeigen

Als Nutzer möchte ich ein Ranking sehen, um die Ergebnisse der Paare vergleichen zu können.

Akzeptanzkriterien:

Given Bewertungen existieren
When ich das Ranking öffne
Then sehe ich Paar, R1 Ø, R2 Ø, Bonus und Gesamt


---

US‑14 – Ranking aktualisiert sich automatisch

Als Nutzer möchte ich, dass das Ranking automatisch aktualisiert wird, wenn neue Bewertungen eingehen.

Akzeptanzkriterien:

Given das Ranking ist geöffnet
When eine neue Bewertung gespeichert wird
Then aktualisiert sich die Anzeige automatisch


---

6. Medien & Erweiterungen

US‑15 – Video‑Upload für Paare

Als Paar möchte ich Trainingsvideos hochladen können, um Fortschritte zu dokumentieren.

Akzeptanzkriterien:

Given ein Paarprofil ist geöffnet
When ich ein Video hochlade
Then wird es gespeichert
And im Profil angezeigt


---

US‑16 – Video als Memory‑Karte

Als Nutzer möchte ich Videos im Memory verwenden können, um das Spiel abwechslungsreicher zu gestalten.

Akzeptanzkriterien:

Given ein Memory‑Spiel wird konfiguriert
When ich „Video‑Karten aktivieren“ auswähle
Then erscheinen Video‑Karten im Spiel


---

US‑17 – KI‑Analyse (optional)

Als Nutzer möchte ich, dass Videos automatisch analysiert werden, um Feedback zu erhalten.

Akzeptanzkriterien:

Given ein Video wurde hochgeladen
When die Analyse abgeschlossen ist
Then erhalte ich Feedback zur Ausführung


---

Was du jetzt hast

Du besitzt jetzt eine vollständige User‑Story‑Sammlung, die:

• vollständig ist
• modular aufgebaut ist
• alle Kernfunktionen von Tuizz abdeckt
• direkt als automatisierte Testbasis nutzbar ist
• Gherkin‑kompatibel ist
• erweiterbar bleibt


Wenn du möchtest, kann ich daraus auch:

• ein komplettes Gherkin‑Feature‑Set generieren
• eine Test‑Suite für Cypress, Playwright oder Robot Framework
• ein Epic‑/Feature‑Backlog
• eine Roadmap
• oder ein Datenmodell passend zu den Stories


Sag mir einfach, welchen nächsten Schritt du willst.