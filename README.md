Jonadeals – Platformë Inteligjente për Tregti Online

Jonadeals është një aplikacion inovativ për tregti online që synon të ofrojë një eksperiencë unike për blerësit dhe shitësit. Me arkitekturë moderne, performancë të lartë dhe integrim me teknologjitë më të fundit si Docker, WSL, GitHub dhe CI/CD, Jonadeals është projektuar për të qenë i shpejtë, i sigurt dhe i shkallëzueshëm.


---

1. Instalimi dhe Konfigurimi

1.1. Klonimi i Projektit

Për të filluar, klono repository-n nga GitHub:

git clone git@github.com:Web8kameleon-hub/jonadeals.git
cd jonadeals

1.2. Përdorimi me Docker

Nëse përdor Docker, sigurohu që ai është i instaluar dhe ekzekuto:

docker compose up -d --build

Për të parë kontejnerët aktivë:

docker ps

Për të ndaluar:

docker compose down

1.3. Instalimi Manual

Nëse nuk përdor Docker, instalo paketat manualisht:

npm install

Starto serverin:

npm start


---

2. Struktura e Projektit

/jonadeals
│── /backend        # API dhe shërbimet backend
│── /frontend       # Aplikacioni frontend (React)
│── /config         # Konfigurimet për databazën dhe mjedisin
│── /scripts        # Skriptet për konfigurim dhe automazim
│── Dockerfile      # Konfigurimi për Docker
│── docker-compose.yml # Shërbimet Docker
│── package.json    # Dependencat e Node.js
│── README.md       # Ky dokument


---

3. Konfigurimi i Mjedisit

1. Krijo një skedar .env në rrënjën e projektit me variablat e nevojshme:

DB_HOST=localhost
DB_USER=root
DB_PASS=password
JWT_SECRET=mysecret


2. Inicjalizo databazën (nëse ka një backend me databazë):

npm run db:init




---

4. Deploy në Server

1. Build frontend-in dhe backend-in:

npm run build


2. Deploy me Docker:

docker-compose up -d --build


3. Deploy në server (p.sh. në një VPS me SSH):

ssh user@server "cd jonadeals && git pull && npm install && npm start"




---

5. Skriptet e Rëndësishme

5.1. Skripti për Setup Automatik (scripts/setup.sh)

#!/bin/bash
echo "🚀 Po instalohet Jonadeals..."
sudo apt update && sudo apt upgrade -y
sudo apt install -y git curl unzip docker-compose
echo "✅ Instalimi përfundoi!"

5.2. Skripti për Start Automatik (scripts/start.sh)

#!/bin/bash
echo "🚀 Startimi i shërbimeve..."
docker-compose up -d
echo "✅ Jonadeals është online!"


---

6. CI/CD me GitHub Actions

Për të automatizuar deploy-in, shto një skedar .github/workflows/deploy.yml:

name: Deploy to Server

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v2

      - name: Build Docker Image
        run: docker build -t jonadeals .

      - name: Push to Server
        run: ssh user@server "cd jonadeals && git pull && docker-compose up -d --build"


---

7. Kontributi

Nëse dëshiron të kontribuosh:

1. Fork repository-n.


2. Krijo një branch të ri:

git checkout -b feature/emri-funksionit


3. Bëj ndryshimet dhe bëj commit:

git commit -m "Shtova funksionalitetin X"


4. Dërgo një pull request për shqyrtim.




---

