## Despre gap-ul din audio-iot-sentry

Cred că piața pare saturată pentru că o compari cu fog computing „clasic”, care se măsoară în milisecunde. Proiectul tău e într-un regim diferit. Trei lucruri pe care s-ar putea să le scapi (sunt ipoteze, n-am făcut încă o căutare în literatură):

1. **SLA de minute, nu de milisecunde.** O limită de 20 de minute îți permite să grupezi datele (batching) și să trimiți doar când e bine (store-and-forward), iar asta e principala sursă de economie de baterie. Literatura despre offloading optimizează aproape mereu latența de ordinul ms. Literatura de delay-tolerant networking (DTN) acoperă probabil o parte din spațiul ăsta, deci trebuie verificat ce rămâne neacoperit.
2. **Criptarea pe fiecare flux creează o problemă de plasare.** Nodul fog nu poate clasifica fără să decripteze. Variantele sunt: clasificare pe dispozitiv înainte de criptare (cost de baterie), decriptare pe un fog de încredere (TEE / confidential computing) sau doar în cloud (cost de bandă). Compromisul confidențialitate–energie–SLA e un unghi mult mai precis decât „fog computing” în general.
3. **DANUBIUS îți dă un context real.** Stațiile din Deltă au conectivitate intermitentă, Murighiol are rolul de fog, iar A-M5 cere explicit clasificare audio (xeno-canto, adică înregistrări de păsări). Bănuiala mea, pe care ar trebui s-o confirme coordonatorul: înregistratoarele bioacustice prind accidental și voci umane. Asta ar justifica criptarea prin GDPR.

## Cele 3 teme pe care le recomand

Am aplicat skill-ul `writing-dissertation`, adaptat. El e gândit pentru lucrări de business, cu interviuri și chestionare, așa că la o temă de informatică „matricea de justificare a întrebărilor” devine: fiecare experiment și fiecare metrică trebuie să pornească de la o sursă din literatură.

| | **1. A-M5: Plasare adaptivă edge–Murighiol–cloud** (Dobre) | **2. T4 (+T5): Pipeline-uri de streaming fiabile pentru monitorizarea mediului** (Costan, MobyLab) | **3. A-M4: AIOps, loguri + LLM** (Dobre) |
|---|---|---|---|
| De ce ți se potrivește | Infrastructură, Raspberry Pi, ML opțional (Î2 întreabă chiar dacă euristicile simple sunt suficiente). Cea mai apropiată de audio-iot-sentry | Kafka, Docker, fără ML deloc | Securitate operațională (prima ta preferință la securitate), bancul de test e infrastructură, LLM-ul e folosit ca unealtă |
| Scopul, într-o frază | Să evaluezi dacă o politică de plasare adaptivă bate politicile fixe în latența alertelor, energie și date livrate, cu conectivitate intermitentă | Să evaluezi cum influențează checkpointing-ul, buffering-ul și recovery-ul corectitudinea și întârzierea pentru date întârziate, lipsă sau duplicate | Să evaluezi când merită un LLM pentru incidente: varianta clasică vs. doar LLM vs. hibridă, ca acuratețe, cost și explicații corecte |
| Recomandarea finală pentru organizație | „Pentru stațiile DANUBIUS: procesați X pe edge când bateria e sub Y și legătura e Z” | „Pentru Centrul de Date DANUBIUS: folosiți configurația X de streaming, care costă Y” | „Pentru WP3: LLM-ul se apelează doar peste pragul X, cu economie de Y%” |
| Riscul | Se suprapune cu Moby T5. Simulatorul (iFogSim sau EdgeSimPy) are curba lui de învățare | Mai puțin original. Ar trebui legat de T5 sau de cazul tău (SLA de minute) ca să iasă în evidență | Lista de cunoștințe cere „ML, NLP și LLM”. Metodele clasice (Drain, DeepLog) se folosesc din implementări existente, dar tot trebuie înțelese |

**Variante de rezervă:** A-M6 (spații de date vs. smart contracts) dacă vrei guvernanță, și Moby T6 (calitatea datelor), care are ceva mai mult ML.

**Cum le-aș ordona:** A-M5 pe primul loc. E singura care îți folosește toate punctele forte și oferă cel mai direct loc pentru unghiul „SLA de minute + criptare”. T4 e varianta sigură, iar A-M4 e varianta orientată spre securitate.

## Pașii următori

- Scrie-le coordonatorilor (ciprian.dobre@upb.ro nu apare în fișier, deci adresa trebuie verificată; pentru T4: alexandru.costan@upb.ro) și întreabă dacă temele mai sunt libere. Întreabă-i și dacă poți aduce în A-M5 unghiul cu criptarea și SLA-ul de minute.
- Spune-mi pe care 2–3 le păstrezi și le dezvolt pe fiecare după schema din skill: scop, 3–5 obiective, temele din literatură și matricea de experimente.

Am salvat în memorie profilul tău și descrierea audio-iot-sentry, ca să nu le reiau în sesiunile următoare.
