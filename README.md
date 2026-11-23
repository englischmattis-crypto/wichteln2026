# 🎄 Wichteln

Statische Wichtel-Auslosung für GitHub Pages – kein Server nötig.

## So funktioniert's

1. **`setup.html` lokal öffnen** (Doppelklick, im Browser). Namen prüfen, optional pro Person ein Profilbild wählen, deine GitHub-Pages-Adresse eintragen, „Jetzt auslosen“.
2. **`data.json` herunterladen** und die Linkliste sichern. Die Zuordnung wird dir *nicht* angezeigt – sie steht nur verschlüsselt in `data.json`.
3. **Ins Repo hochladen:** `index.html` + `data.json` (`setup.html` musst du nicht hochladen).
4. **GitHub Pages aktivieren:** Repo → *Settings* → *Pages* → Source: *Deploy from a branch* → Branch `main`, Ordner `/ (root)` → *Save*. Nach ca. 1 Minute läuft die Seite unter `https://<username>.github.io/<repo>/`.
5. **Jedem seinen persönlichen Link schicken** – selbst nur deinen eigenen öffnen.

## Technik

- Niemand zieht sich selbst (Derangement, kryptografisch zufällig).
- Jedes Ziel ist einzeln mit AES-GCM verschlüsselt, Schlüssel per PBKDF2 aus dem geheimen Token im Link. `data.json` enthält keine Namen und keine Bilder im Klartext – jeder sieht nur Name und Bild seines eigenen Partners. Ohne Link sieht man nichts.
- Ergebnis ist fest: Wer die Seite nochmal öffnet, bekommt dieselbe Person – „nochmal ziehen“ ändert also nichts.
- Neu auslosen = `setup.html` erneut ausführen und neue `data.json` hochladen (alte Links werden ungültig).

Hinweis: Wer alle Links hat (also du), könnte theoretisch alles entschlüsseln – gedacht ist es gegen versehentliches Spicken, nicht als Hochsicherheit.
