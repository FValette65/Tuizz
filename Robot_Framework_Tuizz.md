Sehr gern, Frederic — ich mache dir jetzt eine spielbereite Robot‑Framework‑Testbasis, vollständig generiert aus den User Stories, die wir zuvor definiert haben.
Das Ergebnis ist so strukturiert, dass du es sofort in ein Robot‑Projekt kopieren und ausführen kannst, sobald du die passenden Keywords implementierst.

Ich halte es bewusst modular, erweiterbar und sauber getrennt nach Features, damit es zu deinem Stil passt.

---

🧠 Robot Framework – Ready‑to‑Play Test Suite für Tuizz

Ich liefere dir:

1. Eine vollständige Projektstruktur
2. Feature‑basierte Testdateien
3. Gherkin‑ähnliche Robot‑Tests
4. Abstrakte Keywords, die du später mit Selenium, Playwright oder API‑Calls füllen kannst
5. Erweiterbarkeit für Video‑Module, Jury, Ranking, Memory, Quiz


Alles ist generisch, aber sofort lauffähig, sobald du die Keywords implementierst.

---

📁 Projektstruktur (empfohlen)

tests/
    participants/
        test_create_participants.robot
        test_create_pairs.robot
    dances/
        test_manage_dances.robot
        test_video_upload.robot
    quiz/
        test_quiz_start.robot
        test_memory_game.robot
        test_video_quiz.robot
    jury/
        test_jury_scoring.robot
        test_video_review.robot
    ranking/
        test_ranking.robot

resources/
    keywords/
        participants_keywords.robot
        dances_keywords.robot
        quiz_keywords.robot
        jury_keywords.robot
        ranking_keywords.robot

    variables.robot


---

🧩 1. Teilnehmer & Paare

test_create_participants.robot

*** Settings ***
Resource    ../../resources/keywords/participants_keywords.robot

*** Test Cases ***
Create New Participant
    Given Teilnehmerverwaltung ist geöffnet
    When Ich lege einen neuen Tänzer mit gültigen Daten an
    Then Der Tänzer erscheint in der Teilnehmerliste


test_create_pairs.robot

*** Settings ***
Resource    ../../resources/keywords/participants_keywords.robot

*** Test Cases ***
Create Pair From Two Participants
    Given Zwei existierende Tänzer
    When Ich sie als Paar speichere
    Then Das Paar erscheint in der Paarauswahl


---

💃 2. Tänze & Playlists

test_manage_dances.robot

*** Settings ***
Resource    ../../resources/keywords/dances_keywords.robot

*** Test Cases ***
Mark Dance As Pflicht
    Given Tanzverwaltung ist geöffnet
    When Ich einen Tanz als Pflicht markiere
    Then Er erscheint in der Pflichtliste

Mark Dance As Favorite
    Given Ein Tanz ist sichtbar
    When Ich ihn als Favorit markiere
    Then Er erscheint in der Favoritenliste


test_video_upload.robot

*** Settings ***
Resource    ../../resources/keywords/dances_keywords.robot

*** Test Cases ***
Upload Dance Video
    Given Ein Tanz ist ausgewählt
    When Ich ein gültiges Video hochlade
    Then Das Video ist im Tanzprofil sichtbar


---

🎮 3. Quiz & Memory

test_quiz_start.robot

*** Settings ***
Resource    ../../resources/keywords/quiz_keywords.robot

*** Test Cases ***
Start Quiz For Selected Pair
    Given Ein Paar ist ausgewählt
    When Ich das Quiz starte
    Then Das Quiz beginnt


test_memory_game.robot

*** Settings ***
Resource    ../../resources/keywords/quiz_keywords.robot

*** Test Cases ***
Play Memory Game
    Given Das Memory ist gestartet
    When Ich zwei Karten aufdecke
    Then Werden sie korrekt verglichen


test_video_quiz.robot

*** Settings ***
Resource    ../../resources/keywords/quiz_keywords.robot

*** Test Cases ***
Play Video Quiz
    Given Ein Videoquiz ist aktiv
    When Ein Clip abgespielt wird
    Then Muss ich den richtigen Tanz auswählen


---

🏆 4. Jury & Bewertung

test_jury_scoring.robot

*** Settings ***
Resource    ../../resources/keywords/jury_keywords.robot

*** Test Cases ***
Score Performance Rounds
    Given Eine Performance ist abgeschlossen
    When Ich R1 und R2 Werte eingebe
    Then Werden die Werte gespeichert

Add Bonus Points
    Given Eine Bewertung ist offen
    When Ich Bonuspunkte vergebe
    Then Werden sie zur Gesamtwertung addiert


test_video_review.robot

*** Settings ***
Resource    ../../resources/keywords/jury_keywords.robot

*** Test Cases ***
Review Performance Video
    Given Ein Performancevideo ist verfügbar
    When Ich es abspiele
    Then Kann ich Kommentare mit Zeitmarken hinzufügen


---

📊 5. Ranking

test_ranking.robot

*** Settings ***
Resource    ../../resources/keywords/ranking_keywords.robot

*** Test Cases ***
Show Ranking
    Given Bewertungen existieren
    When Ich das Ranking öffne
    Then Sehe ich Paar R1Ø R2Ø Bonus Gesamt

Ranking Updates Automatically
    Given Das Ranking ist geöffnet
    When Eine neue Bewertung gespeichert wird
    Then Aktualisiert sich die Anzeige automatisch


---

🔧 Beispiel für Keyword‑Implementierung

participants_keywords.robot

*** Keywords ***
Teilnehmerverwaltung ist geöffnet
    Open Page    ${URL}/participants

Ich lege einen neuen Tänzer mit gültigen Daten an
    Input Text    id=name    Max Mustermann
    Click Button  id=save

Der Tänzer erscheint in der Teilnehmerliste
    Page Should Contain    Max Mustermann

Zwei existierende Tänzer
    Ensure Participant Exists    Alice
    Ensure Participant Exists    Bob

Ich sie als Paar speichere
    Select From List    id=dancer1    Alice
    Select From List    id=dancer2    Bob
    Click Button        id=savePair

Das Paar erscheint in der Paarauswahl
    Page Should Contain    Alice & Bob


---

🚀 Bereit für den nächsten Schritt

Wenn du möchtest, kann ich dir zusätzlich generieren:

• eine komplette Keyword‑Bibliothek
• eine Playwright‑ oder Selenium‑Implementierung
• eine API‑Test‑Suite
• eine CI‑Pipeline für Robot Framework
• eine Datenbank‑Mock‑Schicht
• oder ein vollständiges Test‑Framework mit Tags, Suites, Reports


Sag mir einfach, wie weit du gehen willst — ich begleite dich gern durch die ganze Architektur.