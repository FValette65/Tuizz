Alles klar! Damit dein GIF richtig beeindruckend wirkt, lassen wir Playwright eine "perfekte Performance" hinlegen. Wir nutzen "SlowMo", damit die Zuschauer sehen, wie sich die Regler wie von Geisterhand bewegen, und wir fügen ein paar visuelle Highlights hinzu.
Hier ist das optimierte "Demo-Storyboard"-Skript.
1. Das "Perfect Demo" Skript
Erstelle eine Datei namens demo_video.spec.js in deinem tests-Ordner:
import { test, expect } from '@playwright/test';

// Wir schalten Video und SlowMo ein
test.use({ 
  video: 'on',
  launchOptions: { slowMo: 600 } // Jede Aktion dauert etwas, damit man folgen kann
});

test('🎬 Tuizz App Showcase', async ({ page }) => {
  // 1. App laden
  await page.goto(`file://${process.cwd()}/index.html`);
  
  // 2. Teilnehmer anlegen (mit Fokus-Effekt)
  await page.click('#add-participant-btn');
  await page.type('#new-participant-name', 'Tanz-Duo "Blitz"', { delay: 100 });
  await page.click('#save-participant');

  // 3. Auswahl-Prozess (Tänzer-Perspektive)
  await page.selectOption('#participant-dropdown', { label: 'Tanz-Duo "Blitz"' });
  await page.click('#start-btn');
  await page.click('#round-favorite');
  
  // Einen coolen Tanz wählen
  await page.click('text=Wiener Walzer');
  await page.click('#confirm-song-select');
  
  // Selbsteinschätzung wählen
  await page.selectOption('#self-rating', '4');
  await page.click('#tanzer-submit');
  await page.click('#back-to-start');

  // 4. Jury-Perspektive (Das Highlight für das GIF)
  await page.click('#role-jury');
  await page.selectOption('#participant-dropdown', { label: 'Tanz-Duo "Blitz"' });
  await page.click('#start-btn');
  await page.click('#round-favorite');

  // Die Slider bewegen sich nacheinander – sieht im Video toll aus!
  const criteria = ['#creativity', '#rhythm', '#presence', '#technique'];
  const scores = ['9', '8', '10', '9'];

  for (let i = 0; i < criteria.length; i++) {
    await page.locator(criteria[i]).fill(scores[i]);
    await page.waitForTimeout(300); // Kurze Pause zwischen den Slidern
  }

  await page.click('#jury-submit');
  
  // 5. Das Finale: Das Ranking
  await page.click('#back-to-start');
  
  // Das Ranking kurz hervorheben (scrollen falls nötig)
  await page.locator('table').scrollIntoViewIfNeeded();
  
  // 3 Sekunden stehen lassen für das Ende des GIFs
  await page.waitForTimeout(3000); 
});

2. So machst du das GIF fertig
 * Test ausführen:
   npx playwright test tests/demo_video.spec.js

 * Video finden:
   Gehe in den Ordner test-results. Suche den Unterordner deines Tests – dort liegt die Datei video.webm.
 * In GIF umwandeln:
   Zieh die Datei einfach auf ezgif.com/video-to-gif.
   * Tipp: Wähle dort eine Framerate (FPS) von 20, damit die Bewegungen der Slider schön flüssig aussehen.
Was diese Demo zeigt (Storyboard-Value):
 * Dynamik: Man sieht, wie die App auf Eingaben reagiert.
 * Logik: Der Wechsel von Gelb (Tänzer) zu Lila (Jury) zeigt das Rollenkonzept.
 * Ergebnis: Das Ranking am Ende beweist, dass die Mathematik dahinter funktioniert.
Soll ich dir noch zeigen, wie du im Code eine kleine Animation einbaust (z.B. ein Konfetti-Effekt), wenn die Jury ihre Bewertung abgibt? Das würde im GIF am Ende richtig gut aussehen!
