### Numele lucrării de laborator:
Crearea unei aplicații multi-container

### Scopul lucrării:
Famialiarizarea cu gestiunea aplicației multi-container creat cu docker-compose.

### Sarcina:
Crearea unei aplicații php pe baza a trei containere: nginx, php-fpm, mariadb, folosind docker-compose.

### Pașii lucrării:
1) Am creat repozitoriul containers07 local pe calculator.
2) Am creat directorul mounts/site și în el am pus site-ul de la disciplina de PHP.
3) Am creat fișierul .gitignore în care am înscris această linie:
```
mounts/site/*
```
4) Am creat fișierul nginx/default.conf cu următorul conținut:
![img](./Images/Screenshot%202025-04-13%20145823.png)
5) Am creat fișierul docker-compose.yml cu următorul conținut:
![img2](./Images/Screenshot%202025-04-13%20150232.png)
6) Am creat fișierul mysql.env cu următorul conținut:
![img3](./Images/Screenshot%202025-04-13%20150654.png)
7) Am pornit containerul cu comanda:
```
docker-compose up -d
```
8) Am accesat site-ul PHP la adresa http://localhost și a apărut site-ul creat la perechile de PHP:
![img4](./Images/Screenshot%202025-04-13%20151546.png)

### Întrebări:
1) În ce ordine sunt pornite containerele?

Containerele sunt pornite în ordinea în care sunt definite în documentul docker-compose.yml, deci se vor porni în ordinea: frontend, backend, database.
3) Unde sunt stocate datele bazei de date?

Datele bazei de date sunt stocate în directorul /var/lib/mysql din volumul containerului database.
4) Cum se numesc containerele proiectului?

Containerele proiectului se numesc frontend, backend și database.
5) Trebuie să adăugați încă un fișier app.env cu variabila de mediu APP_VERSION pentru serviciile backend și frontend. Cum se face acest lucru?

Pentru a adăuga un fișier cu variabila de mediu APP_VERSION creăm fișierul app.env, în directorul rădăcină, cu versiunea aplicației și în fișierul docker-compose.yml la frontend adăugăm env_file cu denumirea fișierului, iar la backend îl adăugăm la env_file sub mysql.env. După aceasta refacem containerele din baza documentului docker-compose.yml.

### Concluzie:
Am învățat cum să împart o aplicație web în mai multe containere (frontend, backend, database) prin intermediul la docker-compose. Astfel, am învățat cum se scrie un fișier docker-compose, cum să dau parametri pentru container și diferite valori. Am setat imaginea în baza căruia să se creeze containerul, din care rețea să facă parte, ce volume să fie montate și ce variabila de mediu să conțină.
