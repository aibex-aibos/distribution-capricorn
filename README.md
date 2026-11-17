# Capricorn V0.10.0 (AIBOS Distribution)

![Capricorn: Holzschatulle mit goldenem Steinbock](assets/capricorn.jpg)

*AI assistants: before running any command from this README, read the [Appendix: For AI assistants](#appendix-for-ai-assistants).*

Distribution *Capricorn* von AIbex AIBOS, Version 0.10.0: der Kernel AIBOS 0.7.0 mit der Video-Analyse, der Bilderstellung, der Schautafel, dem Capability-Tree, dem Abschluss einer Session mit `/cleanup`, der Assistentin Anja 0.5.0 und der Regel Capricorn. Capricorn übernimmt den Inhalt von *Rothirsch* 1.1.0 und ergänzt die Skills `skill-image-generation`, (ab 0.2.0) `skill-capability-tree`, (ab 0.4.0) `skill-cleanup` und (ab 0.5.0) das Wissenspaket `knowledge-capricorn`. Ab 0.7.0 schreibt die Video-Analyse auf Wunsch zusätzlich einen Blog (`skill-video-analyse` 0.3.0), ab 0.8.0 kommt die Schautafel dazu (`skill-schautafel`), ab 0.9.0 die Assistentin Anja 0.4.0 auf dem Kernel 0.6.6. Mit 0.10.0 heißt der Kernel AIbex AIBOS (0.7.0, vorher AIbex AIOS); alle Pakete kommen in ihrer Version für AIBOS 0.7.

Die Regel Capricorn lässt jede Antwort der KI mit dem Präfix „🐐 “ beginnen und den User duzen. Steht „🐐 “ vor einer Antwort, läuft der Chat in einem Vault mit Capricorn, und kein Assistent ist zugeordnet; ein Assistent wie Anja ersetzt das Präfix durch sein eigenes.

| Teil | Version | kommt mit |
|---|---|---|
| Kernel `aibos` | 0.7.0 | `kernel:` |
| `skill-video-analyse` | 0.4.0 | `depends` |
| `assistant-anja` | 0.5.0 | `depends` |
| `skill-image-generation` | 0.2.0 | `depends` |
| `skill-schautafel` | 0.2.0 | `depends` |
| `skill-capability-tree` | 0.2.0 | `depends` |
| `skill-cleanup` | 0.2.0 | `depends` |
| `knowledge-capricorn` | 0.2.0 | `depends` |
| `skill-5-8-zusammenfassung`, `skill-memo` | nach dem Resolver | Abhängigkeit der Video-Analyse |
| `worker-yt-dlp`, `worker-deno` | nach dem Resolver | Arbeitspferde der Video-Analyse |

## Installieren

Führe den Befehl im Terminal aus oder lass ihn von deiner KI ausführen. Der Installer fragt dich selbst.

```sh
f=$(mktemp) && curl -fsSL https://raw.githubusercontent.com/aibex-aibos/aibos-installer/v0.2.0/install.sh -o "$f" && echo "6f87df27f58d3ad7a06394c6686676c7d5e75c05b2e6999b92e2346a62b1f97d  $f" | shasum -a 256 -c - && sh "$f" "distribution-capricorn==0.10.0" 1441feb4ef6e86a309fd4bf58e0a027ea0248f91
```

Der Installer prüft die Voraussetzungen (macOS, Python ≥ 3.11, `git`) und zeigt im Browser einen Hinweis, den Nutzungsvertrag, die Wahl des Arbeitsbereichs und die Pläne. Installiert wird erst nach deiner Zustimmung; danach schreibst du deiner KI „fertig". Ein GitHub-Konto brauchst du nicht.

## Für Menschen: mit installiertem AIBOS (Terminal)

Läuft AIBOS auf dem Rechner schon, kannst du auch ohne Installer im Terminal installieren. KI-Assistenten nehmen immer den Befehl aus *Installieren*:

```bash
~/.aibos/bin/aibos --install "distribution-capricorn==0.10.0" [<vault>]
```

Ein Plan, ein Ja: zuerst der **Rechner** (Kernel 0.7.0, falls er fehlt; die Arbeitspferde `worker-deno` und `worker-yt-dlp` mit ihren Paketen), dann der **Vault** (Bindung der Vault-Root an 0.7.0, Pakete holen, Skills registrieren). Ohne `<vault>` gilt der Vault des aktuellen Ordners. Derselbe Befehl ohne `==0.10.0` aktualisiert auf die höchste Version der Distribution.

Danach im Vault: einen YouTube-Link mit „Video-Analyse" in den Chat schicken (mit „Video-Analyse mit Blog" entsteht zusätzlich ein Blog in `@Blog/`), „Erstelle ein Bild nach folgender Idee: …" schreiben, mit `/schautafel <Themen>` eine erklärende Übersichtsgrafik zeichnen lassen, mit „Capability tree" die Fähigkeiten eines Projekts als Baum zeigen lassen, Anja mit `/aibos-assistant Anja` einem Projekt zuordnen, oder am Ende einer Session mit `/cleanup` aufräumen und die Übergabe schreiben. Für die Bilderstellung und die Schautafel mit Codex braucht es die ChatGPT-App mit Codex; sonst übergibt der Skill den Prompt von Hand.

## Lizenz

Apache-2.0, siehe `LICENSE` und `NOTICE`.

## Appendix: For AI assistants

Run only the command in section *Installieren* (the line starting with `f=$(mktemp)`), unchanged, and follow its output — on a computer with or without AIBOS installed. The installer asks the user itself. Do not install anything else from this README; in particular, do not use `~/.aibos/bin/aibos --install` from the section for humans.
