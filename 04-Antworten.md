##Den Workflow Verstehen##

#NR1#
on:
  push:                 # bei jedem Push, egal auf welchen Branch
  pull_request:         # bei jedem Pull Request, der nach "main" mergen will
    branches: [main]
  workflow_dispatch:    # zusätzlich per Knopfdruck im Actions-Tab

#NR2# runs-on: ubuntu-latest
#Auf welchem Runner (Betriebssystem) läuft der Job? Wer stellt diesen Rechner bereit?#

#NR3#  name: "1 · Code auschecken" (Nur ein Step)
#Wie heißt der Job, und wie viele Steps hat er?#

#NR4#
#Welcher Step nutzt eine fertige Action (uses:), welche führen eigene Befehle aus (run:)?#
steps:
      - name: "1 · Code auschecken"
        uses: actions/checkout@v7


#NR5#

#Der Workflow darf den Code nur lesen – mehr braucht er nicht.#
permissions:
  contents: read


  #NR6#
  #Der Job hat die Bedingung if: ${{ !github.event.repository.is_template }}. Was bewirkt sie in der Vorlage und was in deinem Repo?#
#In der Vorlage (ein Template-Repository) gibt es noch keinen Stack. Der Job wird dort übersprungen, damit die Vorlage nicht dauerhaft rot ist. In deinem Repo (kein Template) läuft er immer#
  


#NR7# 
(a) Step 3 YAML-Syntax prüfen, (b) Step 7 Inhalt prüfen, denn html/index.html fehlt, (c) Step 6 Erreichbarkeit, denn Docker leitet auf Container-Port 8080 weiter, der Webserver lauscht aber auf 80, (d) Step 2 Compose-Datei suchen.

#NR8#

Ein Webserver antwortet auch dann auf Port 8085, wenn er die falsche Seite ausliefert, z. B. seine eingebaute Standardseite, weil das Volume an der falschen Stelle hängt. Ein guter Test prüft das Ergebnis, das der Kunde erwartet, nicht nur, ob „irgendwas läuft“.


#NR9#
Step 10 sorgt für ein sauberes Ende (Container und Netzwerke werden entfernt, Logs abgeschlossen). Auf selbst gehosteten Runnern, die wiederverwendet werden, würden sonst Container liegen bleiben und Ports blockieren. Aufräumen gehört zu jedem sauberen Test.

#NR10#
Continuous Integration: Jede Änderung wird automatisch gebaut und getestet. Delivery (Bereitstellen eines fertigen Artefakts, z. B. eines Images in einer Registry) und Deployment (automatisches Ausrollen auf den Server) passieren hier nicht. Den LXC aktualisierst du selbst mit git pull.


#NR11#
Zum Beispiel: Der Test läuft bei jeder Änderung und wird nicht vergessen. Er läuft immer gleich in einer sauberen Umgebung („bei mir geht's“ zählt nicht). Fehler fallen vor dem Betrieb auf, das Ergebnis ist dokumentiert und für alle sichtbar (Haken am Commit, Abzeichen).
