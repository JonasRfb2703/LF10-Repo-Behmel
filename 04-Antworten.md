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
  





  
