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
  


(a) Step 3 YAML-Syntax prüfen, (b) Step 7 Inhalt prüfen, denn html/index.html fehlt, (c) Step 6 Erreichbarkeit, denn Docker leitet auf Container-Port 8080 weiter, der Webserver lauscht aber auf 80, (d) Step 2 Compose-Datei suchen.
Ein Webserver antwortet auch dann auf Port 8085, wenn er die falsche Seite ausliefert, z. B. seine eingebaute Standardseite, weil das Volume an der falschen Stelle hängt. Ein guter Test prüft das Ergebnis, das der Kunde erwartet, nicht nur, ob „irgendwas läuft“.
Step 10 sorgt für ein sauberes Ende (Container und Netzwerke werden entfernt, Logs abgeschlossen). Auf selbst gehosteten Runnern, die wiederverwendet werden, würden sonst Container liegen bleiben und Ports blockieren. Aufräumen gehört zu jedem sauberen Test.
Continuous Integration: Jede Änderung wird automatisch gebaut und getestet. Delivery (Bereitstellen eines fertigen Artefakts, z. B. eines Images in einer Registry) und Deployment (automatisches Ausrollen auf den Server) passieren hier nicht. Den LXC aktualisierst du selbst mit git pull.
Zum Beispiel: Der Test läuft bei jeder Änderung und wird nicht vergessen. Er läuft immer gleich in einer sauberen Umgebung („bei mir geht's“ zählt nicht). Fehler fallen vor dem Betrieb auf, das Ergebnis ist dokumentiert und für alle sichtbar (Haken am Commit, Abzeichen).
Ein Abzeichen zeigt den letzten Lauf auf einem Branch. DoD 3 soll anzeigen, ob es dev gibt, also muss die Prüfung dort laufen, wo dev gepusht wird, und das Abzeichen muss die Läufe auf dev anzeigen. Solange es keinen dev gibt, gibt es keinen Lauf, dann ist das Abzeichen grau. Apache und Pull Request betreffen dagegen den Betriebsstand, also main.
Den zuletzt gemergten Pull Request von dev nach main mit seinem Merge-Zeitpunkt (merged_at) und seinem letzten Commit (head.sha). Dazu das Ergebnis des Checks „Compose-Stack testen (Port 8085)“ für genau diesen Commit, mit Zeitpunkt (completed_at). Grün ist DoD 5 nur, wenn der Check erfolgreich war und vor dem Merge fertig war.


  
