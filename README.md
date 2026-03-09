# Setup-Anleitung: Nachrichten Kompakt

Die Webseite und der automatische News-Scraper sind fertig. Alles, was noch fehlt, ist die Einrichtung auf GitHub, damit die Webseite kostenlos online ist und automatisch jeden Tag aktuelle Nachrichten lädt.

Hier ist die Schritt-für-Schritt-Anleitung:

## Schritt 1: GitHub Repository erstellen und Code hochladen
1. Gehe auf [GitHub](https://github.com/) und melde dich an.
2. Erstelle ein neues Repository (oben rechts auf das **+** klicken -> **New repository**).
   - Name: z.B. `nachrichten-kompakt`
   - Typ: **Public** (damit GitHub Pages später kostenlos funktioniert).
   - *Wichtig:* Setze **kein** Häkchen bei "Add a README file".
3. Öffne das Terminal in `c:\Users\Kijan\Desktop\Wochenrückblick` und führe folgende Befehle aus:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/DEIN_USERNAME/DEIN_REPO_NAME.git
   git push -u origin main
   ```

## Schritt 2: Kostenlosen Google Gemini API-Key holen
Der Python-Scraper nutzt KI, um die Nachrichten in Kategorien einzuordnen. Das geht kostenlos mit Google Gemini.
1. Gehe zu [Google AI Studio](https://aistudio.google.com/app/apikey).
2. Melde dich mit deinem Google-Konto an.
3. Klicke auf **Create API key** und kopiere den Key.

## Schritt 3: API-Key in GitHub hinterlegen (Secrets)
1. Gehe auf die Seite deines GitHub Repositories.
2. Klicke auf **Settings** -> **Secrets and variables** -> **Actions**.
3. Klicke auf **New repository secret**.
   - **Name:** `GEMINI_API_KEY`
   - **Secret:** Füge hier den API-Key ein.
4. Klicke auf **Add secret**.

## Schritt 4: Webseite veröffentlichen (GitHub Pages)
1. Gehe in deinem Repository auf **Settings** -> **Pages**.
2. Bei **Source** wählst du `Deploy from a branch`.
3. Unter **Branch** wählst du `main` aus. Klicke auf **Save**.
4. In 1-2 Minuten ist die Seite unter `https://DEIN_USERNAME.github.io/DEIN_REPO_NAME/` abrufbar.

## Schritt 5: Den Scraper aktivieren
1. Gehe auf **Actions**. Bestätige, falls GitHub fragt, ob du Workflows auf diesem Fork aktivieren möchtest.
2. Klicke auf **Daily News Scraper**.
3. Klicke auf **Run workflow**.

Das Skript holt nun die aktuellsten Nachrichten und updatet deine `data.json`. Die Seite stellt dies dann automatisch dar.
