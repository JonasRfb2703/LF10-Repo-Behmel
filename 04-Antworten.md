##Den Workflow Verstehen##

#NR1#
on:
  push:                 # bei jedem Push, egal auf welchen Branch
  pull_request:         # bei jedem Pull Request, der nach "main" mergen will
    branches: [main]
  workflow_dispatch:    # zusätzlich per Knopfdruck im Actions-Tab

#NR2# runs-on: ubuntu-latest

#NR3#  name: "1 · Code auschecken" (Nur ein Step)







#Der Workflow darf den Code nur lesen – mehr braucht er nicht.#
permissions:
  contents: read



  
