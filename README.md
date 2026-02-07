# MINT-CLUB-FLL

## Projekt Initialisieren / Aufsetzen

### Git Initialisieren / Aufsetzen

Auf jedem Rechner sollte [Git](https://git-scm.com/install/) installiert sein. Ob es installiert ist kannst du wie folgt testen:
```shell
git --version
```
Dies sollte die Version von Git anzeigen, wie: `git version 2.53.0.windows.1`. Ansonsten ist es nicht richtig installiert.

Dann können für jedes Gerät ein Name (und eine EMail) gesetzt werden. 
Ersetzt einfach "[Geräte Name]" mit der ID des jeweiligen Laptops
```shell
git config --global user.name "[Geräte Name]"
git config --global user.email "<>"
```

### SSH Key erstellen

Für die einfache Anmeldung zu Github sollte man auf dem Gerät einen SSH Key [erstellen](https://docs.github.com/de/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent). Dafür kann man folgenden Befehl eingeben und mit 3x ENTER den standard Namen und ein leeres Passwort bestätigen.
```shell
ssh-keygen -t ed25519 -C "[Geräte Name]"
```
Daraufhin kann der SSH Key dem Git Cloud Account [hinzugefügt](https://docs.github.com/de/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) werden. Deinen öffentlichen SSH Key kannst du wie folgt in dein Clipboard copieren:
```shell
cat ~/.ssh/id_ed25519.pub | clip
```
Füge den Key dann in den Einstellungen deines Accounts unter `SSH and GPG keys` -> `Neuer SSH-Schlüssel` als Authentifikationsschlüssel hinzu.

### Projekt herunterladen

Nun kann man das Projekt einfach aus der Cloud herunterladen:
```shell
git clone git@github.com:account-name/MINT-CLUB-FLL.git
```

### Python Installation

Zuerst sollte [Python](https://www.python.org/downloads/) installiert und zum PATH hinzugefügt sein. Ob es installiert ist kannst du wie folgt testen:
```shell
python --version
```
Dies sollte die Version von Python anzeigen, wie: `Python 3.12.10`. Ansonsten ist es nicht richtig installiert.

Zuerst installieren wir unser virtuelle Python Umgebung (environment).
```shell
python -m venv .env
.venv\Scripts\Activate.ps1
```

Falls bei der Installation ein Fehler auftritt, der besagt, dass "die Ausführung von Skripts auf diesem System 
deaktiviert ist." oder "about_Execution_Policies" falsch ist, sollten scripts aktiviert werden. Dies muss in einer 
Administrator Powershell ausgeführt werden.
```shell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

Nun können wir unsere Pybricks Bibliotheken etc. installieren:
```shell
pip install -e .
```

## Projekt Struktur

Hier wird erklärt wofür die einzelnen Ordner vorgesehen sind:

## Mit Git Versionen verwaten und hochladen

Wenn man änderungen am Projekt bzw. einzelenen Datein vorgenommen hat und sie auch mit anderen Teilen will, sollte man einen "Commit" erstellen. Ein "Commit" bezeichnet eine neue Version des Projekts und speichert die Änderungen. Dafür kann man links in der Zeile unter dem Git Symbol eine Nachricht eingeben und die veränderten Datein auswählen. Die Commit-Nachrichten sollten einem einheitlichen Format folgen. Ihr könnt für euch überlegen, wie Ihr das im Projekt machen wollt. Hier wäre ein Vorschlag:
```
Name: Kurze Überschrift dazu was geändert wurde
```

In der Arbeitswelt benutzt man Nachrichten z.B. wie hier (auf Englisch) beschrieben: https://gist.github.com/qoomon/5dfcdf8eec66a051ecd85625518cfd13.

## Requirements aktualisieren (optional)

Falls man neue Bibliotheken (Libaries/Packages) dem Projekt hinzugefügt hat sollte man auch die requirements aktualisieren. Dies macht man in der `pyproject.toml` Datei unter `dependencies`
Daraufhin muss dann auf jedem Rechner wieder folgendes ausgeführt werden:
```shell
pip install -e .
```