# MINT-CLUB-FLL

## Schnellstart (Windows + VS Code)

1. Git installieren: [Git für Windows](https://git-scm.com/install/)
2. Python installieren: [Python 3](https://www.python.org/downloads/)
3. Projekt klonen (VS Code Seitenleiste -> Quelle): `git clone
git@github.com:account-name/MINT-CLUB-FLL.git`
4. Virtuelle Umgebung erstellen und aktivieren:

```shell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

5. Abhängigkeiten installieren:

```shell
pip install -e .
```

6. Erstes Programm starten:

```shell
python scripts/test.py
```

## Projekt Initialisieren / Aufsetzen

### Git Initialisieren / Aufsetzen (Windows)

Auf jedem Rechner sollte [Git](https://git-scm.com/install/) installiert sein. Ob es
installiert ist, kannst du wie folgt testen:

```shell
git --version
```

Dies sollte die Version von Git anzeigen, wie: `git version 2.53.0.windows.1`. Ansonsten
ist es nicht richtig installiert.

Dann kann für jedes Gerät ein Name (und eine E-Mail) gesetzt werden. Ersetzt einfach
"[Geräte Name]" mit der ID des jeweiligen Laptops

```shell
git config --global user.name "[Geräte Name]"
git config --global user.email "<>"
```

### SSH Key erstellen (für GitHub Zugriff)

Für die einfache Anmeldung zu GitHub sollte man auf dem Gerät einen SSH Key
[erstellen](https://docs.github.com/de/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).
Dafür kann man folgenden Befehl eingeben und mit 3x ENTER den Standardnamen und ein
leeres Passwort bestätigen.

```shell
ssh-keygen -t ed25519 -C "[Geräte Name]"
```

Daraufhin kann der SSH Key dem GitHub Account
[hinzugefügt](https://docs.github.com/de/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
werden. Deinen öffentlichen SSH Key kannst du wie folgt in dein Clipboard kopieren:

```shell
cat ~/.ssh/id_ed25519.pub | clip
```

Füge den Key dann in den Einstellungen deines Accounts unter `SSH and GPG keys` ->
`Neuer SSH-Schlüssel` als Authentifikationsschlüssel hinzu.

### Projekt herunterladen (VS Code)

Nun kann man das Projekt einfach aus der Cloud herunterladen:

```shell
git clone git@github.com:account-name/MINT-CLUB-FLL.git
```

### Python Installation (Windows)

Zuerst sollte [Python](https://www.python.org/downloads/) installiert und zum PATH
hinzugefügt sein. Ob es installiert ist, kannst du wie folgt testen:

```shell
python --version
```

Dies sollte die Version von Python anzeigen, wie: `Python 3.12.10`. Ansonsten ist es
nicht richtig installiert.

Zuerst erstellen wir unsere virtuelle Python-Umgebung.

```shell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

Falls bei der Installation ein Fehler auftritt, der besagt, dass "die Ausführung von
Skripts auf diesem System deaktiviert ist." oder "about_Execution_Policies" falsch ist,
sollten scripts aktiviert werden. Dies muss in einer Administrator Powershell ausgeführt
werden.

```shell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

Nun können wir unsere Pybricks-Bibliotheken etc. installieren:

```shell
pip install -e .
```

## Projekt Struktur

Hier wird erklärt wofür die einzelnen Ordner vorgesehen sind:

### Ordner und Dateien im Projekt

- `src/` Hier liegt der eigentliche Python Code, also das "Herz" des Projekts. Alles was
  später importiert wird (z.B. `import mint_club_ffl`) gehört hier hinein.

- `src/mint_club_ffl/` Das ist der Name unseres Python Pakets. In diesem Ordner liegen
  die Module (Python Dateien) die wir selbst schreiben.

- `scripts/` Kleine Hilfsprogramme oder Tests, die man manuell starten kann. Diese
  Dateien sind nicht Teil des eigentlichen Pakets.

- `tests/` (Falls vorhanden) Automatische Tests. Hier prüfen wir ob unser Code richtig
  funktioniert.

- `README.md` Diese Datei. Sie erklärt wie man das Projekt benutzt und einrichtet.

- `pyproject.toml` Die Projekt-Einstellungen. Hier steht z.B. wie das Paket heißt und
  welche Bibliotheken benötigt werden.

- `.venv/` (Nur lokal) Die virtuelle Python Umgebung. Sie hält die installierten Pakete
  getrennt vom System.

## Mit Git Versionen verwalten und hochladen

Wenn man Änderungen am Projekt bzw. einzelnen Dateien vorgenommen hat und sie auch mit
anderen teilen will, sollte man einen "Commit" erstellen. Ein "Commit" bezeichnet eine
neue Version des Projekts und speichert die Änderungen. Dafür kann man in VS Code links
in der Seitenleiste unter dem Git-Symbol eine Nachricht eingeben und die veränderten
Dateien auswählen. Die Commit-Nachrichten sollten einem einheitlichen Format folgen. Ihr
könnt für euch überlegen, wie ihr das im Projekt machen wollt. Hier wäre ein Vorschlag:

```txt
<Name>: <Kurze Überschrift, was geändert wurde>
```

In der Arbeitswelt benutzt man Nachrichten z.B. wie hier (auf Englisch) beschrieben:
[Commit Message
Conventions](https://gist.github.com/qoomon/5dfcdf8eec66a051ecd85625518cfd13). Das ist
optional.

## Requirements aktualisieren (optional)

Falls man neue Bibliotheken (Libraries/Packages) dem Projekt hinzugefügt hat, sollte man
auch die Requirements aktualisieren. Dies macht man in der `pyproject.toml` Datei unter
`dependencies`. Daraufhin muss dann auf jedem Rechner wieder folgendes ausgeführt
werden:

```shell
pip install -e .
```
