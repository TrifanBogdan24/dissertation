# Propuneri de teme
**Proiecte de diplomă (licență) și lucrări de dizertație (master)**
**Anul universitar 2026-2027**
**Prof. dr. ing. Ciprian Dobre**
*Facultatea de Automatică și Calculatoare, UNSTPB MobyLab*

---

# 1. DANUBIUS-RO-2: infrastructură digitală pentru sistemul fluviu-deltă-mare

---

## A-M1 Detecția anomaliilor în serii de timp de la senzori de mediu: defect de senzor sau eveniment real?

- **Nivel:** Dizertație
- **Proiect/ancoră:** DANUBIUS-RO-2: alertare pentru intervenție rapidă în caz de poluare și detecție
  timpurie a incidentelor
- **Co-îndrumare:** -
- **Context proiect:** DANUBIUS-RO-2 (PNCDI IV, 11.2025-12.2028) pregătește componentele românești ale
  infrastructurii europene de cercetare DANUBIUS-RI pentru sistemele fluviu-deltă-mare (Hub-ul de la
  Murighiol, Supersite-urile, Centrul de Date). UPB este partener și răspunde de infrastructura
  digitală (WP3).

### Despre ce este vorba
Senzorii de calitate a apei din teren se murdăresc, se decalibrează, rămân fără baterie sau sunt loviți
de bușteni. Rezultatul: valori aberante, salturi, platouri suspecte. Uneori însă o valoare aberantă este
exact ce căutăm: începutul unei poluări, o viitură, o înflorire algală. Un sistem care alertează la orice
abatere devine repede ignorat (prea multe alarme false). Unul care filtrează agresiv ratează
evenimentele reale.

Ideea centrală a temei este că cele două situații lasă amprente diferite în date. Un defect de senzor este
de obicei local: stația vecină din aval nu vede nimic, ceilalți parametri ai aceleiași stații arată normal,
iar forma semnalului este „nefizică" (salt instantaneu, valoare constantă). Un eveniment real se propagă:
apare cu întârziere la stațiile din aval, afectează mai mulți parametri corelați (turbiditate, oxigen,
conductivitate) și se corelează adesea cu meteo sau cu debitul.

Studentul analizează metodele existente de detecție a anomaliilor în serii de timp (statistice, ML clasic,
autoencodere, modelele de fundație recente) și construiește o metodă care folosește această consistență
spațio-temporală pentru a clasifica anomaliile. Evaluarea folosește date reale de pe Dunăre, în care se
injectează controlat defecte de senzor de tipuri cunoscute. Astfel se știe exact ce ar trebui detectat.

### De ce este interesantă tema
Problema este reală, nerezolvată satisfăcător și relevantă pentru orice rețea de senzori (mediu,
industrie, clădiri). Metodologia (date reale plus anomalii sintetice controlate) este una corectă
științific și la îndemâna unui student de master. Rezultatul are o componentă de cercetare clară (metoda
și evaluarea) și una aplicată (integrarea în pipeline-ul DANUBIUS).

### Întrebări de cercetare
- **Î1.** Cât de bine separă metodele existente defectele de senzor de evenimentele reale, atunci când
  sunt aplicate stație cu stație?
- **Î2.** Cât câștigă detecția dacă folosește informația de la stațiile vecine și din amonte/aval, plus
  variabilele exogene (meteo, debit)?
- **Î3.** Merită rulată detecția pe edge (rapid, cu informație locală) sau doar central (mai lent, cu
  context complet)?

### Etape și livrabile
- **1.** Studiu de literatură structurat: tipologia anomaliilor și a defectelor de senzor, metode
  statistice, Isolation Forest, autoencodere, modele de prognoză cu reziduuri, modele de fundație pentru
  serii de timp.
- **2.** Construirea setului de lucru: stații TNMN de pe Dunărea inferioară, cu parametri corelați,
  aliniate cu debitul și meteo.
- **3.** Generator de defecte de senzor (drift, salt, blocare la valoare constantă, zgomot, valori
  lipsă) cu parametri controlați, plus o listă de evenimente reale documentate (ex. viituri) din date
  publice.
- **4.** Implementarea a 3-4 metode de referință, stație cu stație.
- **5.** Metoda propusă: un clasificator „defect vs. eveniment" bazat pe consistența spațio-temporală
  (de exemplu propagare amonte-aval, corelații între parametri, reziduuri față de prognoză).
- **6.** Evaluare experimentală cu analiza erorilor; studiu edge vs. central.
- **7.** Integrarea pilot într-un pipeline simplu de ingestie (redarea seriilor ca flux în timp real), cu
  alerte explicate („anomalie probabil cauzată de senzor: stația vecină nu confirmă").

### Date folosite (seturi publice)
- **ICPDR Water Quality Database (TNMN)**
  - *Ce conține:* Date din Rețeaua Transnațională de Monitorizare (TNMN) a bazinului Dunării: stații pe
    Dunăre și afluenți, inclusiv în România, cu parametri fizico-chimici. Anuarele TNMN descriu stațiile
    și metodele.
  - *Cum se folosește în temă:* Serii reale multi-parametru de la stații succesive pe Dunăre.
  - *Acces:* Bază de date online ICPDR; condițiile de export se verifică la începutul proiectului.
  - *Link:* wq-db.icpdr.org, Anuarele TNMN
- **EEA Waterbase - Water Quality ICM**
  - *Ce conține:* Date dezagregate de calitate a apelor (râuri, lacuri, ape subterane) raportate de
    statele membre, inclusiv România: nutrienți, oxigen dizolvat, metale, pesticide. Fiecare
    înregistrare are stația, data și parametrul.
  - *Cum se folosește în temă:* Stații suplimentare din România pentru generalizare.
  - *Acces:* Descărcare liberă (CSV/bază de date) de pe portalul EEA.
  - *Link:* www.eea.europa.eu/en/datahub
- **GloFAS - reanaliza debitelor (Copernicus EMS)**
  - *Ce conține:* Reanaliză zilnică a debitului râurilor la nivel global, inclusiv Dunărea, la rezoluție
    de $0.05^{\circ}$ (versiunea 4), pe mai multe decenii.
  - *Cum se folosește în temă:* Debitul, ca variabilă exogenă și pentru estimarea timpilor de propagare.
  - *Acces:* Gratuit, cu cont, prin Copernicus Early Warning Data Store.
  - *Link:* ewds.climate.copernicus.eu
- **ERA5/Open-Meteo**
  - *Ce conține:* ERA5 este reanaliza climatică ECMWF, orară, din 1940 (temperatură, precipitații,
    vânt). Open-Meteo oferă un API simplu peste reanalize și prognoze.
  - *Cum se folosește în temă:* Precipitații și temperatură.
  - *Acces:* Gratuit: Copernicus Climate Data Store (cu cont) sau API Open-Meteo.
  - *Link:* cds.climate.copernicus.eu, Open-Meteo
- **Modele de fundație pentru serii de timp**
  - *Ce conține:* Modele pre-antrenate deschise (ex. Chronos, TimesFM, Moirai), folosibile zero-shot sau
    cu fine-tuning.
  - *Cum se folosește în temă:* Modele de fundație pentru prognoză și reziduuri.
  - *Acces:* Open-source.
  - *Link:* Chronos, TimesFM, Moirai (uni2ts)

### Validare
Precizie și recall pe tipuri de defecte injectate și pe evenimentele reale documentate, întârzierea
detecției, costul computațional (inclusiv pe Raspberry Pi pentru varianta edge) și o evaluare calitativă a
explicațiilor cu un specialist de mediu.

### Cunoștințe necesare
ML pentru serii de timp, statistică, Python (pandas, scikit-learn, PyTorch).

---

## A-M2 Fuziunea datelor Sentinel-1/2/3 cu măsurători in situ pentru estimarea calității apei în Deltă

- **Nivel:** Dizertație
- **Proiect/ancoră:** DANUBIUS-RO-2: temele de cercetare DANUBIUS-RI (sedimente, nutrienți, poluanți) și
  digital twin
- **Co-îndrumare:** Vladislav Tiftilov (doctorand)
- **Context proiect:** DANUBIUS-RO-2 (PNCDI IV, 11.2025-12.2028) pregătește componentele românești ale
  infrastructurii europene de cercetare DANUBIUS-RI pentru sistemele fluviu-deltă-mare (Hub-ul de la
  Murighiol, Supersite-urile, Centrul de Date). UPB este partener și răspunde de infrastructura
  digitală (WP3).

### Despre ce este vorba
Stațiile de monitorizare măsoară calitatea apei în câteva puncte. Delta are însă mii de kilometri de
canale și sute de lacuri. Sateliții văd totul, dar nu măsoară direct turbiditatea, clorofila sau
sedimentele: le estimează din culoarea apei, iar estimarea e influențată de atmosferă, de fundul apei
vizibil în zonele puțin adânci, de vegetație și de nori.

Tema combină cele două surse: imaginile satelitare (Sentinel-2 optic la rezoluție fină, Sentinel-3 OLCI
dedicat culorii apei, Sentinel-1 radar pentru măștile de apă) și măsurătorile in situ publice.
Măsurătorile servesc la calibrarea și validarea unui model care produce hărți continue de calitate a apei,
fiecare cu o hartă de incertitudine asociată. Incertitudinea contează: un administrator trebuie să știe
unde estimarea e solidă și unde e o simplă presupunere.

Tema se aliniază direct cu teza doctorandului Tiftilov, care tratează fuziunea multi-sursă a imaginilor,
generalizarea la zone noi și cuantificarea statistică a incertitudinii (de exemplu prin conformal
prediction). Studentul lucrează pe un pilot concret, iar doctorandul îl ajută metodologic.

### De ce este interesantă tema
Tema dă o introducere solidă în învățarea automată pentru observarea Pământului, un domeniu în creștere
rapidă (Copernicus, Destination Earth), pe o problemă cu valoare științifică și practică. Componenta de
incertitudine o diferențiază de multe lucrări aplicative. Studentul învață să lucreze riguros cu date
spațiale și cu validarea pe zone și perioade noi.

### Întrebări de cercetare
- **Î1.** Ce combinație de surse satelitare și ce arhitectură de model dau cea mai bună estimare a
  turbidității sau clorofilei în Deltă?
- **Î2.** Cât de bine se transferă modelul la o zonă sau la un an nevăzut la antrenare?
- **Î3.** Sunt intervalele de incertitudine produse corect calibrate, adică acoperă valoarea reală în
  proporția promisă?

### Etape și livrabile
- **1.** Delimitarea zonei pilot (de exemplu un complex lacustru și brațul Sfântu Gheorghe) și a
  parametrilor (turbiditate și/sau clorofilă-a).
- **2.** Pipeline de preluare și preprocesare: mascare nori și umbre, mască de apă din Sentinel-1,
  extragerea reflectanțelor la punctele și momentele măsurătorilor (potrivire în timp $\pm$1-3 zile).
- **3.** Construirea setului de antrenare din perechi satelit-in situ; completarea cu produse Copernicus
  Marine/OLCI ca referință unde lipsesc măsurători.
- **4.** Modele comparate: algoritmi empirici publicați, ML clasic (random forest, gradient boosting), o
  rețea neuronală mică.
- **5.** Cuantificarea incertitudinii prin conformal prediction sau ansambluri, cu verificarea calibrării.
- **6.** Validare pe zonă și pe an nevăzute; analiza erorilor (ape puțin adânci, vegetație).
- **7.** Hărți lunare cu incertitudine, publicate ca straturi web (de exemplu Cloud Optimized GeoTIFF
  vizualizat într-o hartă MapLibre).

### Date folosite (seturi publice)
- **Copernicus Sentinel-2 (L2A)**
  - *Ce conține:* Imagini multispectrale (13 benzi, 10-60 m), cu revizitare la aproximativ 5 zile,
    corectate atmosferic. Permit calculul indicilor de apă și vegetație (NDWI, NDVI) și estimări de
    turbiditate.
  - *Cum se folosește în temă:* Reflectanțe la 10-20 m pentru canale și lacuri.
  - *Acces:* Gratuit, cu cont, prin Copernicus Data Space Ecosystem (interfață web, API, Sentinel Hub,
    openEO).
  - *Link:* dataspace.copernicus.eu
- **Copernicus Sentinel-3 OLCI**
  - *Ce conține:* Senzor de culoare a apei (300 m, aproape zilnic). Are produse derivate de calitate a
    apei: clorofilă, materie în suspensie.
  - *Cum se folosește în temă:* Produse de culoare a apei, ca a doua sursă și referință.
  - *Acces:* Gratuit, prin Copernicus Data Space Ecosystem.
  - *Link:* dataspace.copernicus.eu
- **Copernicus Sentinel-1 (GRD)**
  - *Ce conține:* Imagini radar în bandă C (~10 m), independente de nori și de lumina zilei. Utile
    pentru delimitarea apei, inundații și umiditate.
  - *Cum se folosește în temă:* Mască de apă independentă de nori.
  - *Acces:* Gratuit, cu cont, prin Copernicus Data Space Ecosystem.
  - *Link:* dataspace.copernicus.eu
- **Joint Danube Survey 4 (2019)**
  - *Ce conține:* Campanie științifică pe tot cursul Dunării: chimie, biologie, hidromorfologie,
    poluanți emergenți, inclusiv în sectorul românesc și în Deltă.
  - *Cum se folosește în temă:* Măsurători in situ pe Dunăre și în Deltă.
  - *Acces:* Portal de date public.
  - *Link:* data.danubesurvey.org
- **ICPDR Water Quality Database (TNMN)**
  - *Ce conține:* Date din Rețeaua Transnațională de Monitorizare (TNMN) a bazinului Dunării: stații pe
    Dunăre și afluenți, inclusiv în România, cu parametri fizico-chimici. Anuarele TNMN descriu stațiile
    și metodele.
  - *Cum se folosește în temă:* Serii in situ la stațiile TNMN.
  - *Acces:* Bază de date online ICPDR; condițiile de export se verifică la începutul proiectului.
  - *Link:* wq-db.icpdr.org, Anuarele TNMN
- **Copernicus Marine Service (Marea Neagră)**
  - *Ce conține:* Produse de analiză, prognoză și reanaliză pentru fizica și biogeochimia Mării Negre
    (temperatură, salinitate, curenți, clorofilă, oxigen, nutrienți), plus observații in situ
    (geamanduri, stații) și satelitare.
  - *Cum se folosește în temă:* Produse de turbiditate și clorofilă pentru zona costieră.
  - *Acces:* Gratuit, cu cont; descărcare prin interfață web sau biblioteca Python „copernicusmarine".
  - *Link:* marine.copernicus.eu

### Validare
RMSE, MAE și bias față de măsurătorile in situ (pe un set de test separat spațial și temporal), acoperirea
efectivă a intervalelor de incertitudine față de cea nominală și comparația cu produsele Copernicus
existente.

### Cunoștințe necesare
Machine learning, Python geospațial (rasterio, xarray), procesare de imagini; noțiunile de optică a apei
se învață pe parcurs.

---

## A-M3 Digital twin „lite": model surogat ML pentru debit și nivel pe sectorul Porțile de Fier - Delta

- **Nivel:** Dizertație
- **Proiect/ancoră:** DANUBIUS-RO-2: digital twin (stratul de aplicații); noul Supersite Porțile de Fier
- **Co-îndrumare:** -
- **Context proiect:** DANUBIUS-RO-2 (PNCDI IV, 11.2025-12.2028) pregătește componentele românești ale
  infrastructurii europene de cercetare DANUBIUS-RI pentru sistemele fluviu-deltă-mare (Hub-ul de la
  Murighiol, Supersite-urile, Centrul de Date). UPB este partener și răspunde de infrastructura
  digitală (WP3).

### Despre ce este vorba
Un digital twin al unui râu este o reprezentare digitală care urmărește starea reală și permite întrebări
de tipul „ce s-ar întâmpla dacă?": o ploaie extremă în bazinul superior, o secetă prelungită, o schimbare
de exploatare la baraj. Modelele hidrologice și hidrodinamice fizice răspund bine la astfel de întrebări,
dar sunt complexe și lente, deci greu de folosit interactiv.

O alternativă tot mai folosită este modelul surogat: o rețea neuronală antrenată să reproducă, mult mai
rapid, comportamentul unui model fizic sau al reanalizelor. Tema construiește un astfel de surogat pentru
sectorul Dunării dintre Porțile de Fier (unde DANUBIUS-RO-2 dezvoltă un nou Supersite) și Deltă. Modelul
învață din reanaliza GloFAS și din datele meteo ERA5 cum evoluează debitul la câteva puncte cheie, apoi
rulează scenarii modificate.

Partea „lite" este intenționată: nu se reconstruiește hidrodinamica Dunării, ci se demonstrează lanțul
complet (date $\rightarrow$ model $\rightarrow$ scenarii $\rightarrow$ vizualizare) și se discută onest
limitele unui model învățat față de unul fizic.

### De ce este interesantă tema
Digital twin-urile sunt un subiect fierbinte (Destination Earth, Digital Twin of the Ocean), iar tema
oferă o intrare accesibilă: modelare de serii de timp, scenarii și evaluarea onestă a unui model folosit
pentru decizii. Studentul învață și noțiuni de hidrologie, utile în orice proiect de mediu.

### Întrebări de cercetare
- **Î1.** Cât de bine reproduce un model surogat evoluția debitului la stațiile alese, inclusiv
  evenimentele extreme?
- **Î2.** Cum se comportă surogatul în scenarii aflate în afara datelor de antrenare (extrapolare) și
  cum poate fi semnalat acest risc?

### Etape și livrabile
- **1.** Alegerea punctelor de interes (ex. aval de Porțile de Fier, la intrarea în Deltă) și extragerea
  seriilor GloFAS pe câteva decenii.
- **2.** Construirea variabilelor de intrare: precipitații și temperatură agregate pe sub-bazine din ERA5,
  debite din amonte.
- **3.** Modele comparate: LSTM, un model de fundație pentru serii de timp (zero-shot și cu
  fine-tuning), o referință simplă (persistență, regresie).
- **4.** Evaluare pe perioade de test separate, cu accent pe viituri și secete.
- **5.** Modul de scenarii: modificarea precipitațiilor sau temperaturilor (de exemplu +30% precipitații
  într-o lună), cu detectarea extrapolării (intrări în afara distribuției de antrenare).
- **6.** Vizualizare web interactivă a scenariilor (hidrografe comparate, hartă cu punctele de interes).
- **7.** Discuție despre limite și despre diferența față de un digital twin complet.

### Date folosite (seturi publice)
- **GloFAS - reanaliza debitelor (Copernicus EMS)**
  - *Ce conține:* Reanaliză zilnică a debitului râurilor la nivel global, inclusiv Dunărea, la rezoluție
    de $0.05^{\circ}$ (versiunea 4), pe mai multe decenii.
  - *Cum se folosește în temă:* Debitele zilnice de reanaliză, ca țintă și ca intrare din amonte.
  - *Acces:* Gratuit, cu cont, prin Copernicus Early Warning Data Store.
  - *Link:* ewds.climate.copernicus.eu
- **ERA5/Open-Meteo**
  - *Ce conține:* ERA5 este reanaliza climatică ECMWF, orară, din 1940 (temperatură, precipitații,
    vânt). Open-Meteo oferă un API simplu peste reanalize și prognoze.
  - *Cum se folosește în temă:* Precipitații și temperatură pe sub-bazine.
  - *Acces:* Gratuit: Copernicus Climate Data Store (cu cont) sau API Open-Meteo.
  - *Link:* cds.climate.copernicus.eu, Open-Meteo
- **ICPDR Water Quality Database (TNMN)**
  - *Ce conține:* Date din Rețeaua Transnațională de Monitorizare (TNMN) a bazinului Dunării: stații pe
    Dunăre și afluenți, inclusiv în România, cu parametri fizico-chimici. Anuarele TNMN descriu stațiile
    și metodele.
  - *Cum se folosește în temă:* Date de stație pentru validare suplimentară, unde există.
  - *Acces:* Bază de date online ICPDR; condițiile de export se verifică la începutul proiectului.
  - *Link:* wq-db.icpdr.org, Anuarele TNMN
- **Modele de fundație pentru serii de timp**
  - *Ce conține:* Modele pre-antrenate deschise (ex. Chronos, TimesFM, Moirai), folosibile zero-shot sau
    cu fine-tuning.
  - *Cum se folosește în temă:* Modele de fundație pentru serii de timp.
  - *Acces:* Open-source.
  - *Link:* Chronos, TimesFM, Moirai (uni2ts)

### Validare
Nash-Sutcliffe efficiency (NSE) și Kling-Gupta efficiency (KGE), erori la vârfurile de debit, timp de
inferență (secunde vs. orele unui model fizic) și comportamentul la scenarii extreme, cu semnalarea
extrapolării.

### Cunoștințe necesare
ML pentru serii de timp, Python (xarray, PyTorch); noțiunile de hidrologie se învață.

---

## A-M4 AIOps: analiza logurilor și detecția incidentelor de securitate cu LLM în infrastructuri distribuite

- **Nivel:** Dizertație
- **Proiect/ancoră:** DANUBIUS-RO-2, WP3: monitorizare, logging, securitate la nivel de aplicație
- **Co-îndrumare:** -
- **Context proiect:** DANUBIUS-RO-2 (PNCDI IV, 11.2025-12.2028) pregătește componentele românești ale
  infrastructurii europene de cercetare DANUBIUS-RI pentru sistemele fluviu-deltă-mare (Hub-ul de la
  Murighiol, Supersite-urile, Centrul de Date). UPB este partener și răspunde de infrastructura
  digitală (WP3).

### Despre ce este vorba
O infrastructură distribuită produce zilnic milioane de linii de log. Când apare un incident,
operatorul caută acul în carul cu fân: ce s-a întâmplat, unde a început, e o defecțiune sau un atac?
Cercetarea în AIOps a produs metode bune de detecție a anomaliilor în loguri (parsarea logurilor în
template-uri, apoi modele care învață secvențele normale), dar rezultatul lor este un scor greu de
interpretat.

Modelele de limbaj mari citesc logurile aproape ca un om: pot explica ce s-a întâmplat și pot propune
cauze. Sunt însă scumpe la volume mari, lente și uneori inventează explicații plauzibile, dar greșite. Tema
propune o arhitectură hibridă: metodele clasice, rapide, filtrează volumul și semnalează ferestrele
suspecte, iar LLM-ul este chemat doar pentru acestea, ca să le explice și să le clasifice.

Studentul compară riguros trei variante (pur clasic, pur LLM, hibrid) pe seturi publice de loguri cu
incidente etichetate și pe logurile unui banc de test propriu, care imită infrastructura DANUBIUS
(noduri edge, server de agregare, servicii cloud). Accentul cade pe cost, acuratețe și fiabilitatea
explicațiilor.

### De ce este interesantă tema
Tema combină două direcții de mare actualitate (LLM și operarea sistemelor) cu o întrebare practică:
când merită să folosești un LLM și când nu? Studentul învață metodologie experimentală, evaluarea
modelelor generative și noțiuni de securitate operațională.

### Întrebări de cercetare
- **Î1.** Cât de bine detectează și clasifică incidentele fiecare variantă (clasic, LLM, hibrid)?
- **Î2.** Cât reduce arhitectura hibridă costul față de folosirea exclusivă a LLM-ului, la ce pierdere
  de calitate?
- **Î3.** Cât de des sunt explicațiile LLM greșite sau nesusținute de loguri și cum poate fi redus acest
  risc (de exemplu prin citarea liniilor relevante)?

### Etape și livrabile
- **1.** Studiu al metodelor de parsare (ex. Drain) și de detecție a anomaliilor în loguri (ex. DeepLog,
  LogAnomaly), plus al abordărilor recente cu LLM.
- **2.** Pregătirea seturilor de evaluare: seturi LogHub etichetate și loguri dintr-un banc de test propriu
  (3-5 mașini virtuale sau Raspberry Pi cu servicii tipice), cu incidente injectate (căderi,
  configurări greșite, atacuri simulate de tip brute-force).
- **3.** Implementarea liniei clasice: parsare, detecție de anomalii.
- **4.** Implementarea liniei LLM: prompturi structurate, context limitat, cerința de a cita liniile de
  log pe care se bazează.
- **5.** Arhitectura hibridă cu praguri configurabile și buget de cost.
- **6.** Evaluarea calității explicațiilor: verificare automată a citărilor, plus evaluare umană pe un
  eșantion.
- **7.** Integrare pilot cu o stivă de observabilitate standard (OpenTelemetry, Loki, Grafana) în
  bancul de test.

### Date folosite (seturi publice)
- **LogHub/Loghub-2.0**
  - *Ce conține:* Colecție de loguri reale de sistem (HDFS, BGL, Thunderbird, OpenSSH, Apache, Linux
    etc.). Unele au etichete de anomalie; Loghub-2.0 are template-uri adnotate pentru evaluarea parserelor.
  - *Cum se folosește în temă:* Seturi reale de loguri cu etichete de anomalie (HDFS, BGL) și
    template-uri adnotate.
  - *Acces:* Descărcare liberă (GitHub/Zenodo).
  - *Link:* github.com/logpai/loghub
- **OpenLLM-Ro**
  - *Ce conține:* Familie de modele de limbaj deschise adaptate pentru română (RoLlama, RoMistral,
    RoGemma), cu benchmark-uri de evaluare în română.
  - *Cum se folosește în temă:* Modele deschise rulate local, ca alternativă la API-urile comerciale.
  - *Acces:* Modele descărcabile de pe Hugging Face.
  - *Link:* huggingface.co/OpenLLM-Ro

### Validare
Precizie, recall și F1 la nivel de incident, timp și cost per incident analizat, rata explicațiilor
corecte și bine fundamentate (evaluare umană pe un eșantion) și timpul economisit de un operator într-un
mic experiment.

### Cunoștințe necesare
Machine learning, NLP și LLM, Python, noțiuni de securitate.

---

## A-M5 Plasarea adaptivă a procesării pe continuumul edge-Murighiol-cloud cu conectivitate intermitentă

- **Nivel:** Dizertație
- **Proiect/ancoră:** DANUBIUS-RO-2: arhitectura pe straturi edge $\rightarrow$ agregare (Murighiol)
  $\rightarrow$ cloud
- **Co-îndrumare:** -
- **Context proiect:** DANUBIUS-RO-2 (PNCDI IV, 11.2025-12.2028) pregătește componentele românești ale
  infrastructurii europene de cercetare DANUBIUS-RI pentru sistemele fluviu-deltă-mare (Hub-ul de la
  Murighiol, Supersite-urile, Centrul de Date). UPB este partener și răspunde de infrastructura
  digitală (WP3).

### Despre ce este vorba
În arhitectura DANUBIUS fiecare prelucrare poate rula în mai multe locuri: direct pe gateway-ul de la
punctul de observare, pe serverul de la Murighiol sau în cloud. Fiecare alegere are un preț. Pe edge
răspunsul e rapid și nu consumă bandă, dar resursele și energia sunt limitate. În cloud resursele sunt
mari, dar datele trebuie transmise printr-o legătură care uneori lipsește.

O decizie fixă (de exemplu „totul se procesează în cloud") e suboptimală: într-o noapte cu baterie slabă
și conexiune bună merită trimise datele brute, iar în timpul unei furtuni, cu legătura căzută, detecția unei
alerte trebuie făcută local. Tema studiază politici de plasare adaptivă care decid dinamic, pentru fiecare
tip de sarcină (filtrare, compresie, detecție de anomalii, clasificare audio sau de imagine), unde rulează,
în funcție de starea rețelei, de energie și de urgență.

Studiul se face întâi în simulare, cu trace-uri reale de conectivitate, apoi pe un pilot mic cu 2-3
dispozitive reale.

### De ce este interesantă tema
Este o problemă clasică de sisteme distribuite (computation offloading, edge-cloud continuum) într-un
context concret, cu constrângeri reale. Studentul învață modelare, optimizare și evaluarea prin
simulare, competențe esențiale pentru cercetarea în sisteme, și poate compara euristici simple cu învățarea
prin întărire.

### Întrebări de cercetare
- **Î1.** Cât câștigă o politică adaptivă față de politicile fixe (totul pe edge, totul în cloud), în
  latența alertelor, energie și date livrate?
- **Î2.** Sunt suficiente euristici simple sau aduce învățarea prin întărire un câștig semnificativ în
  condiții de conectivitate variabilă?

### Etape și livrabile
- **1.** Formalizarea problemei: sarcini (cost computațional, volum de date, termen-limită), resurse
  (CPU, energie, bandă variabilă) și obiective.
- **2.** Profilarea reală a 3-4 sarcini tipice pe Raspberry Pi și pe server (timp, energie).
- **3.** Simulator (extinderea unui simulator existent, ex. iFogSim sau EdgeSimPy, sau unul propriu
  simplu), alimentat cu trace-uri reale de conectivitate.
- **4.** Politici comparate: fixe, euristici bazate pe prag, optimizare pe orizont scurt, învățare
  prin întărire.
- **5.** Experimente pe scenarii: zi normală, furtună cu întreruperi, baterie limitată.
- **6.** Pilot cu 2-3 dispozitive reale și comparație simulare-realitate.

### Date folosite (seturi publice)
- **Trace-uri publice de conectivitate mobilă**
  - *Ce conține:* Măsurători de debit 4G/5G în mobilitate (ex. logurile LTE de la Universitatea din Gent,
    setul Lumos5G), folosite pentru a simula conectivitatea intermitentă.
  - *Cum se folosește în temă:* Trace-uri de conectivitate mobilă pentru simularea legăturii.
  - *Acces:* Publicate de autori, cu descărcare liberă.
  - *Link:* Logurile 4G/LTE - Univ. Gent, Lumos5G
- **ICPDR Water Quality Database (TNMN)**
  - *Ce conține:* Date din Rețeaua Transnațională de Monitorizare (TNMN) a bazinului Dunării: stații pe
    Dunăre și afluenți, inclusiv în România, cu parametri fizico-chimici. Anuarele TNMN descriu stațiile
    și metodele.
  - *Cum se folosește în temă:* Fluxurile de senzori redate ca sarcină de lucru.
  - *Acces:* Bază de date online ICPDR; condițiile de export se verifică la începutul proiectului.
  - *Link:* wq-db.icpdr.org, Anuarele TNMN
- **xeno-canto**
  - *Ce conține:* Colecție de sute de mii de înregistrări de păsări, etichetate pe specii și localizate
    geografic.
  - *Cum se folosește în temă:* Clipuri audio ca sarcină grea de clasificare.
  - *Acces:* API public; licențe Creative Commons, de respectat per înregistrare.
  - *Link:* xeno-canto.org

### Validare
Latența alertelor, procentul de date livrate, energia consumată pe nod, comparativ între politici, plus
diferența dintre rezultatele din simulare și cele din pilot.

### Cunoștințe necesare
Sisteme distribuite, optimizare, simulare, Python; noțiunile de învățare prin întărire se pot învăța în
temă.

---

## A-M6 Politici executabile de utilizare a datelor: conectori de spații de date versus smart contracts

- **Nivel:** Dizertație
- **Proiect/ancoră:** DANUBIUS-RO-2: smart contracts (stratul de aplicații), colaborări cu alte
  infrastructuri ERIC, interoperabilitate EOSC
- **Co-îndrumare:** Andrei Buhnici (doctorand)
- **Context proiect:** DANUBIUS-RO-2 (PNCDI IV, 11.2025-12.2028) pregătește componentele românești ale
  infrastructurii europene de cercetare DANUBIUS-RI pentru sistemele fluviu-deltă-mare (Hub-ul de la
  Murighiol, Supersite-urile, Centrul de Date). UPB este partener și răspunde de infrastructura
  digitală (WP3).

### Despre ce este vorba
Datele unei infrastructuri de cercetare nu sunt toate la fel de deschise. Unele sunt publice imediat. Altele
sunt sub embargo până la publicarea articolelor. Altele pot fi folosite doar în scop de cercetare, nu
comercial, sau doar de partenerii unui proiect. Astăzi aceste reguli sunt scrise în acorduri juridice și
aplicate manual. Tendința europeană (spațiile comune de date, Gaia-X, International Data Spaces) este ca
regulile să devină executabile: datele circulă împreună cu politica lor, iar sistemul o aplică automat.

Există două mari familii de soluții. Conectorii de spații de date (de exemplu Eclipse Dataspace Components)
exprimă politicile în limbajul standard ODRL și le negociază între parteneri înainte de transfer. Smart
contracts pe un registru distribuit codifică regulile ca program executat de toți participanții.
Arhitectura DANUBIUS menționează explicit smart contracts. Tema compară cele două abordări pe un scenariu
realist și formulează o recomandare.

Scenariul de lucru: un partener extern (de exemplu un institut din altă infrastructură ERIC) cere acces la
un set de date de mediu cu embargo, numai pentru cercetare și pentru o perioadă limitată, cu obligația de
a cita sursa.

### De ce este interesantă tema
Tema atinge un subiect strategic pentru Europa (suveranitatea datelor, spațiile de date) și cere o
analiză comparativă riguroasă, nu doar o implementare. Studentul învață să evalueze arhitecturi după
criterii explicite (încredere, expresivitate, cost operațional, interoperabilitate). Doctorandul
Buhnici lucrează pe arhitecturi descentralizate de încredere și pe guvernanță multi-instituțională.

### Întrebări de cercetare
- **Î1.** Ce tipuri de reguli de utilizare pot fi exprimate și aplicate în fiecare abordare, și ce
  rămâne inevitabil în afara controlului tehnic?
- **Î2.** Care sunt costurile (operaționale, de performanță, de guvernanță) ale fiecărei abordări
  pentru o infrastructură ca DANUBIUS?

### Etape și livrabile
- **1.** Catalog de cerințe de politică derivate din practicile reale de partajare a datelor de mediu
  (embargo, scop, durată, atribuire, re-partajare).
- **2.** Studiul arhitecturilor: IDS/Gaia-X și Eclipse Dataspace Components (ODRL), respectiv smart
  contracts pe un ledger permisionat.
- **3.** Implementarea scenariului de referință în ambele abordări, cu doi „parteneri" simulați.
- **4.** Matrice de comparație: ce se poate exprima, ce se aplică automat, ce doar se jurnalizează
  pentru audit.
- **5.** Măsurători: latența negocierii și a transferului, complexitatea operațională (componente,
  configurare).
- **6.** Recomandări pentru infrastructura DANUBIUS și pentru interoperabilitatea cu EOSC.

### Date folosite (seturi publice)
- **EEA Waterbase - Water Quality ICM**
  - *Ce conține:* Date dezagregate de calitate a apelor (râuri, lacuri, ape subterane) raportate de
    statele membre, inclusiv România: nutrienți, oxigen dizolvat, metale, pesticide. Fiecare
    înregistrare are stația, data și parametrul.
  - *Cum se folosește în temă:* Seturi de date reale cu „embargo" simulat, ca obiect al partajării.
  - *Acces:* Descărcare liberă (CSV/bază de date) de pe portalul EEA.
  - *Link:* www.eea.europa.eu/en/datahub
- **Copernicus Marine Service (Marea Neagră)**
  - *Ce conține:* Produse de analiză, prognoză și reanaliză pentru fizica și biogeochimia Mării Negre
    (temperatură, salinitate, curenți, clorofilă, oxigen, nutrienți), plus observații in situ
    (geamanduri, stații) și satelitare.
  - *Cum se folosește în temă:* Seturi mari, pentru testul de transfer.
  - *Acces:* Gratuit, cu cont; descărcare prin interfață web sau biblioteca Python „copernicusmarine".
  - *Link:* marine.copernicus.eu

### Validare
Acoperirea catalogului de cerințe în fiecare abordare, latența și costul operațional, plus o evaluare
calitativă cu specialiști în guvernanța datelor.

### Cunoștințe necesare
Arhitecturi distribuite, securitate, noțiuni de blockchain; standardele se învață.

---

# 2. BioMedLake: date medicale interoperabile și AI clinic

---

## B-M1 AI.1: maparea automată a termenilor clinici locali (inclusiv în română) la SNOMED CT, LOINC și ICD cu LLM și regăsire semantică

- **Nivel:** Dizertație
- **Proiect/ancoră:** BioMedLake AI.1: curarea, armonizarea și standardizarea semantică a datelor
  clinice (sarcină UNSTPB)
- **Co-îndrumare:** -
- **Context proiect:** BioMedLake (FEDR/STEP, 2026-2029, lider UMF „Carol Davila") construiește un Data
  Lake medical cu infrastructură HPC, o platformă de cercetare clinică și trei module AI. UNSTPB
  răspunde de arhitectura de date (FHIR, OMOP), de platformă și de modulele AI.

### Despre ce este vorba
Fiecare laborator își numește analizele cum vrea: „Glicemie", „GLU ser", „Glucoza a jeun", „GLUC-S".
Pentru ca datele de la 30 de spitale să poată fi analizate împreună, toate trebuie legate de același concept
standard (în acest caz un cod LOINC). La fel pentru diagnostice (SNOMED CT, ICD), medicamente și
proceduri. Această mapare se face astăzi în mare parte manual, cu instrumente care propun candidați pe baza
asemănării literelor (de exemplu Usagi în ecosistemul OHDSI), iar experții validează mii de termeni. Este
lent, scump și se repetă la fiecare spital nou.

LLM-urile combinate cu regăsirea semantică promit să schimbe asta. Sistemul caută în vocabularele standard
conceptele apropiate ca sens (nu doar ca litere), apoi un model de limbaj alege candidatul potrivit folosind
contextul (unitatea de măsură, intervalul de valori, tipul probei). Studii publicate în 2025 raportează
rezultate promițătoare, dar și erori subtile. Pentru română, cu abrevieri locale și terminologie mixtă,
aproape nimic nu este evaluat.

Tema construiește și evaluează riguros un astfel de sistem, cu un principiu important: sistemul nu
trebuie să mapeze tot, ci să știe când nu e sigur și să lase acele cazuri expertului. Măsura succesului
este cât efort uman economisește, fără să introducă erori.

### De ce este interesantă tema
Problema este centrală pentru AI.1 și pentru orice proiect de date medicale. Tema are o componentă de
cercetare clară (comparația metodelor, calibrarea încrederii, transferul la română) și una aplicată
(integrarea în ETL). Rezultatele, mai ales pe partea de română, sunt publicabile.

### Întrebări de cercetare
- **Î1.** Cât de mult îmbunătățește regăsirea semantică combinată cu un LLM maparea față de metodele
  lexicale, pentru analize, diagnostice și medicamente?
- **Î2.** Cât de bine funcționează metodele pe termeni în română (abrevieri, diacritice lipsă,
  terminologie mixtă)?
- **Î3.** Poate sistemul să-și estimeze corect încrederea, astfel încât expertul să revizuiască doar
  cazurile incerte?

### Etape și livrabile
- **1.** Studiu de literatură: metode lexicale, embeddings biomedicale, LLM cu RAG, abordări
  multi-agent pentru maparea în OMOP.
- **2.** Construirea setului de evaluare: termeni locali cu mapare corectă cunoscută. Surse: denumiri de
  analize generate în stilul laboratoarelor românești (cu abrevieri reale, validate de un medic), mapări
  publice existente, termeni din corpusul MoNERo.
- **3.** Linii de bază: potrivire lexicală (tip Usagi), embeddings (modele biomedicale multilingve).
- **4.** Sistemul propus: regăsire semantică în vocabulare, plus LLM care alege candidatul folosind
  contextul (unitate, valori, tip probă) și produce un scor de încredere.
- **5.** Calibrarea încrederii și politica de abținere (sub prag, cazul merge la expert).
- **6.** Experimente separate pe engleză și română și pe tipuri de concepte.
- **7.** Integrare pilot într-un flux de transformare către OMOP (de exemplu peste ETL-Synthea): codurile
  nemapate primesc propuneri ordonate, cu interfață de validare pentru expert.

### Date folosite (seturi publice)
- **OHDSI Athena - vocabulare standardizate**
  - *Ce conține:* Vocabularele OMOP (SNOMED CT, LOINC, RxNorm, RxNorm Extension, ICD-10 etc.) cu relațiile
    dintre concepte.
  - *Cum se folosește în temă:* Vocabularele țintă (LOINC, SNOMED CT, ICD-10, RxNorm) cu relațiile dintre
    concepte.
  - *Acces:* Descărcare gratuită cu cont. Unele vocabulare cer licență separată; condițiile SNOMED CT
    pentru România trebuie verificate.
  - *Link:* athena.ohdsi.org
- **LOINC**
  - *Ce conține:* Terminologie standard pentru analize de laborator și observații clinice, cu zeci de mii
    de coduri și nume detaliate pe axe (componentă, proprietate, timp, sistem, scală, metodă).
  - *Cum se folosește în temă:* Denumirile detaliate pe axe, utile pentru regăsire.
  - *Acces:* Gratuit, după înregistrare.
  - *Link:* loinc.org
- **MoNERo**
  - *Ce conține:* Corpus biomedical adnotat pentru limba română (texte din publicații medicale), cu
    entități precum boli, anatomie, substanțe.
  - *Cum se folosește în temă:* Terminologie biomedicală reală în română.
  - *Acces:* Liber, inclusiv prin colecția BigBIO pe Hugging Face.
  - *Link:* huggingface.co/datasets/bigbio/monero
- **Synthea**
  - *Ce conține:* Generator open-source de pacienți sintetici realiști, cu istoric complet de-a lungul
    vieții (consultații, diagnostice, medicație, analize, proceduri). Exportă FHIR R4, CSV și C-CDA,
    pentru populații de orice mărime. Nu conține date reale, deci nu ridică probleme de confidențialitate.
  - *Cum se folosește în temă:* Coduri și denumiri de analize, din care se generează variante locale.
  - *Acces:* Open-source (Java), rulare locală.
  - *Link:* synthetichealth.github.io/synthea, Cod sursă (GitHub)
- **OpenLLM-Ro**
  - *Ce conține:* Familie de modele de limbaj deschise adaptate pentru română (RoLlama, RoMistral,
    RoGemma), cu benchmark-uri de evaluare în română.
  - *Cum se folosește în temă:* Modele deschise pentru română.
  - *Acces:* Modele descărcabile de pe Hugging Face.
  - *Link:* huggingface.co/OpenLLM-Ro

### Validare
Acuratețe top-1 și top-5 pe tipuri de concepte și pe limbă, curba risc-acoperire (acuratețea pe cazurile
acceptate automat, în funcție de procentul acceptat) și estimarea efortului economisit (termeni pe oră
validați de expert, cu și fără sistem) într-un mic experiment.

### Cunoștințe necesare
NLP și LLM, Python, interes pentru terminologii medicale.

---

## B-M2 AI.2: interogarea în limbaj natural a datelor OMOP (text-to-SQL) cu verificare, explicare și abținere

- **Nivel:** Dizertație
- **Proiect/ancoră:** BioMedLake AI.2: interogare semantică și meta-căutare clinică cu LLM (sarcină
  UNSTPB)
- **Co-îndrumare:** -
- **Context proiect:** BioMedLake (FEDR/STEP, 2026-2029, lider UMF „Carol Davila") construiește un Data
  Lake medical cu infrastructură HPC, o platformă de cercetare clinică și trei module AI. UNSTPB
  răspunde de arhitectura de date (FHIR, OMOP), de platformă și de modulele AI.

### Despre ce este vorba
BioMedLake promite cercetătorilor „interogarea naturală a datelor": medicul scrie o întrebare în română,
iar sistemul răspunde pe baza Data Lake-ului. În spate, întrebarea trebuie tradusă într-o interogare SQL
corectă peste modelul OMOP, cu conceptele medicale corecte și cu logica temporală corectă. LLM-urile sunt
surprinzător de bune la generarea SQL, dar în medicină o interogare „aproape corectă" este periculoasă:
un cod greșit, o condiție uitată sau o fereastră de timp interpretată altfel dau un număr plauzibil,
dar fals.

Cercetarea recentă propune abordări în doi pași: întâi se regăsesc conceptele medicale potrivite din
vocabulare, apoi se generează SQL-ul folosindu-le. Benchmark-uri dedicate, precum EHRSQL, au arătat că o
calitate esențială este abținerea: sistemul trebuie să recunoască întrebările la care nu poate răspunde
(ambigue sau în afara datelor) în loc să inventeze. Lucrarea „Why Language Models Hallucinate" (2025)
explică de ce modelele tind să ghicească și de ce evaluările trebuie să recompenseze abținerea.

Tema construiește un astfel de sistem peste OMOP, cu trei mecanisme de siguranță: verificarea interogării
înainte de execuție (concepte existente, schemă validă, plauzibilitatea rezultatului), explicarea în
limbaj natural a ce s-a calculat efectiv și abținerea motivată.

### De ce este interesantă tema
Tema e la frontiera aplicării LLM-urilor în medicină și are o cerință de fiabilitate care o face
interesantă științific. Studentul învață să evalueze riguros un sistem generativ (nu doar „pare că
merge") și construiește un benchmark în română, util comunității.

### Întrebări de cercetare
- **Î1.** Cât de corect generează SQL un sistem în doi pași (concepte, apoi SQL) față de generarea
  directă, pe întrebări clinice în engleză și română?
- **Î2.** Cât de bine își recunoaște sistemul limitele (întrebări fără răspuns sau ambigue) și cât costă
  abținerea în acoperire?
- **Î3.** Ajută explicațiile generate utilizatorul să detecteze o interogare greșită?

### Etape și livrabile
- **1.** Studiu al literaturii text-to-SQL pentru dosare medicale (EHRSQL, abordări cu RAG în doi pași)
  și al metodelor de abținere.
- **2.** Benchmark: întrebări din EHRSQL adaptate la OMOP plus un set nou de întrebări în română
  (traduse și originale), cu SQL de referință și întrebări intenționat fără răspuns.
- **3.** Pipeline: regăsirea conceptelor din vocabulare, generare SQL, validare (schemă, concepte,
  execuție de probă), reparare automată la erori.
- **4.** Mecanism de abținere bazat pe estimarea încrederii și pe verificări.
- **5.** Explicarea rezultatului: reformularea interogării în limbaj natural și afișarea conceptelor
  folosite.
- **6.** Comparație între cel puțin două LLM-uri (unul comercial, unul deschis rulat local).
- **7.** Interfață web simplă: întrebarea, SQL-ul generat, explicația și rezultatul, cu posibilitatea de a
  corecta interogarea.

### Date folosite (seturi publice)
- **EHRSQL (inclusiv ediția 2024)**
  - *Ce conține:* Benchmark de întrebări în limbaj natural despre dosare medicale, cu interogările SQL
    corecte. Ediția 2024 (pe MIMIC-IV demo) conține și întrebări fără răspuns, pentru evaluarea abținerii.
  - *Cum se folosește în temă:* Întrebări cu SQL de referință, inclusiv întrebări fără răspuns (ediția
    2024).
  - *Acces:* Descărcare liberă (GitHub).
  - *Link:* github.com/glee4810/EHRSQL
- **MIMIC-IV demo în OMOP CDM**
  - *Ce conține:* Subset de 100 de pacienți MIMIC-IV transformat în OMOP CDM, inclusiv rezultatele
    Achilles și Data Quality Dashboard.
  - *Cum se folosește în temă:* Bază OMOP reală, deschisă, pentru execuție.
  - *Acces:* Acces deschis (fără acreditare) pe PhysioNet.
  - *Link:* physionet.org/content/mimic-iv-demo-omop
- **MIMIC-IV (PhysioNet)**
  - *Ce conține:* Date clinice anonimizate de la Beth Israel Deaconess Medical Center (Boston) pentru
    internări în terapie intensivă și urgențe: diagnostice, medicație, analize, semne vitale.
  - *Cum se folosește în temă:* Baza completă, pentru testul la scară (după acreditare).
  - *Acces:* Acces după acreditare PhysioNet (curs online CITI, gratuit) și semnarea acordului de
    utilizare; studentul face acreditarea în primele săptămâni.
  - *Link:* physionet.org/content/mimiciv
- **Synthea**
  - *Ce conține:* Generator open-source de pacienți sintetici realiști, cu istoric complet de-a lungul
    vieții (consultații, diagnostice, medicație, analize, proceduri). Exportă FHIR R4, CSV și C-CDA,
    pentru populații de orice mărime. Nu conține date reale, deci nu ridică probleme de confidențialitate.
  - *Cum se folosește în temă:* Populație sintetică mare în OMOP, pentru testele de performanță.
  - *Acces:* Open-source (Java), rulare locală.
  - *Link:* synthetichealth.github.io/synthea, Cod sursă (GitHub)
- **OHDSI Athena - vocabulare standardizate**
  - *Ce conține:* Vocabularele OMOP (SNOMED CT, LOINC, RxNorm, RxNorm Extension, ICD-10 etc.) cu relațiile
    dintre concepte.
  - *Cum se folosește în temă:* Vocabularele pentru regăsirea conceptelor.
  - *Acces:* Descărcare gratuită cu cont. Unele vocabulare cer licență separată; condițiile SNOMED CT
    pentru România trebuie verificate.
  - *Link:* athena.ohdsi.org

### Validare
Acuratețea la execuție (rezultat identic cu SQL-ul de referință), precizia și recall-ul abținerii, curbe
risc-acoperire, rezultate separate pentru engleză și română și un mic studiu cu utilizatori: detectează
ei interogările greșite cu ajutorul explicațiilor?

### Cunoștințe necesare
LLM, SQL, evaluare experimentală, Python.

---

## B-M3 AI.3: eligibility screening automat pentru studii clinice

- **Nivel:** Dizertație
- **Proiect/ancoră:** BioMedLake AI.3: registre clinice, cohortare, eligibility screening (sarcină
  UNSTPB)
- **Co-îndrumare:** -
- **Context proiect:** BioMedLake (FEDR/STEP, 2026-2029, lider UMF „Carol Davila") construiește un Data
  Lake medical cu infrastructură HPC, o platformă de cercetare clinică și trei module AI. UNSTPB
  răspunde de arhitectura de date (FHIR, OMOP), de platformă și de modulele AI.

### Despre ce este vorba
Multe studii clinice întârzie sau eșuează pentru că nu găsesc la timp suficienți pacienți eligibili.
Criteriile de eligibilitate sunt scrise în text liber pe ClinicalTrials.gov („pacienți adulți cu
insuficiență cardiacă, fracție de ejecție sub 40%, fără insuficiență renală severă, care nu au primit X în
ultimele 6 luni") și trebuie verificate manual, pacient cu pacient, de medici care nu au timp pentru asta.

Automatizarea are două părți. O parte din criterii poate fi tradusă în interogări peste datele structurate
(diagnostice, analize, medicație în OMOP). Studii recente arată că LLM-urile pot face această traducere
cu rezultate bune, dar imperfecte. Altă parte a informației există doar în notele clinice (simptome,
istoric, decizii), unde trebuie extrasă din text. Un sistem util combină cele două surse și explică
decizia pe fiecare criteriu, ca medicul să poată verifica rapid.

Tema construiește și evaluează un astfel de sistem pe date publice: studii reale de pe ClinicalTrials.gov,
pacienți reali anonimizați din MIMIC-IV și descrierile de pacienți cu judecăți de eligibilitate din
competiția TREC Clinical Trials.

### De ce este interesantă tema
Tema are impact direct (accelerarea studiilor clinice este o prioritate a BioMedLake) și o componentă de
cercetare solidă: combinarea datelor structurate cu textul și explicabilitatea pe criterii. Există
benchmark-uri publice, deci rezultatele sunt comparabile cu literatura.

### Întrebări de cercetare
- **Î1.** Ce proporție din criteriile de eligibilitate reale poate fi tradusă automat corect în
  interogări OMOP?
- **Î2.** Cât îmbunătățește extragerea din note clinice decizia de eligibilitate față de folosirea
  exclusivă a datelor structurate?
- **Î3.** Ajută explicațiile pe criteriu medicul să valideze rapid și corect?

### Etape și livrabile
- **1.** Analiza criteriilor din câteva sute de studii reale (tipuri de criterii, proporția
  structurabilă).
- **2.** Traducerea criteriilor în interogări OMOP cu LLM, cu regăsirea conceptelor și validarea
  interogărilor.
- **3.** Extragerea informației din note pentru criteriile nestructurate (LLM cu citarea fragmentului
  relevant).
- **4.** Agregarea deciziei pe pacient: eligibil, neeligibil sau incert, cu motivul pe fiecare criteriu.
- **5.** Evaluare pe două niveluri: criteriu și pacient, pe colecțiile publice.
- **6.** Interfață de revizuire pentru medic, cu decizia și dovezile pe fiecare criteriu.

### Date folosite (seturi publice)
- **ClinicalTrials.gov și AACT**
  - *Ce conține:* Registrul mondial de studii clinice: titlu, intervenții, criterii de eligibilitate în
    text liber, stare. AACT este o copie relațională (PostgreSQL) actualizată zilnic.
  - *Cum se folosește în temă:* Studii reale cu criterii de eligibilitate (API sau AACT).
  - *Acces:* API v2 public; AACT liber după înregistrare.
  - *Link:* clinicaltrials.gov, AACT
- **TREC Clinical Trials Track (2021-2023)**
  - *Ce conține:* Descrieri de pacienți (cazuri sintetice), o colecție de studii de pe ClinicalTrials.gov
    și judecăți de experți despre eligibilitate.
  - *Cum se folosește în temă:* Descrieri de pacienți și judecăți de eligibilitate făcute de experți.
  - *Acces:* Liber, de pe site-ul TREC.
  - *Link:* www.trec-cds.org
- **MIMIC-IV (PhysioNet)**
  - *Ce conține:* Date clinice anonimizate de la Beth Israel Deaconess Medical Center (Boston) pentru
    internări în terapie intensivă și urgențe: diagnostice, medicație, analize, semne vitale.
  - *Cum se folosește în temă:* Date structurate reale (după acreditare).
  - *Acces:* Acces după acreditare PhysioNet (curs online CITI, gratuit) și semnarea acordului de
    utilizare; studentul face acreditarea în primele săptămâni.
  - *Link:* physionet.org/content/mimiciv
- **MIMIC-IV-Note**
  - *Ce conține:* Scrisori de externare și rapoarte radiologice anonimizate, legate de pacienții din
    MIMIC-IV.
  - *Cum se folosește în temă:* Note clinice reale pentru criteriile nestructurate.
  - *Acces:* Aceleași condiții ca MIMIC-IV.
  - *Link:* physionet.org/content/mimic-iv-note
- **n2c2 2018 - Cohort Selection**
  - *Ce conține:* Dosare a 288 de pacienți, adnotate pentru 13 criterii de selecție pentru studii clinice.
  - *Cum se folosește în temă:* Opțional: pacienți adnotați pe 13 criterii (necesită acord de utilizare).
  - *Acces:* Acces cu acord de utilizare (portalul DBMI, Harvard); opțional.
  - *Link:* portal.dbmi.hms.harvard.edu

### Validare
Precizie și recall la nivel de criteriu și de pacient, metricile TREC pentru clasarea studiilor, timpul
economisit de un evaluator uman într-un mic experiment și calitatea explicațiilor.

### Cunoștințe necesare
NLP și LLM, SQL, Python.

---

## B-M4 NLP clinic pentru limba română fără date reale: corpus sintetic și transfer

- **Nivel:** Dizertație
- **Proiect/ancoră:** BioMedLake AI.1/AI.2: date nestructurate; UNSTPB dezvoltă module NLP și LLM
- **Co-îndrumare:** -
- **Context proiect:** BioMedLake (FEDR/STEP, 2026-2029, lider UMF „Carol Davila") construiește un Data
  Lake medical cu infrastructură HPC, o platformă de cercetare clinică și trei module AI. UNSTPB
  răspunde de arhitectura de date (FHIR, OMOP), de platformă și de modulele AI.

### Despre ce este vorba
O mare parte din informația medicală valoroasă stă în text: scrisori medicale de externare, buletine de
investigații, note de evoluție. Pentru engleză există corpusuri publice de note clinice (de exemplu
MIMIC-IV-Note) pe care s-au antrenat zeci de modele. Pentru română nu există niciun corpus public de
note clinice, din motive evidente de confidențialitate. Asta blochează dezvoltarea instrumentelor NLP
clinice în română, inclusiv în BioMedLake, până la obținerea accesului la date reale.

Tema investighează o soluție de ocolire: generarea unui corpus sintetic. Pornind de la pacienți
Synthea (cu diagnostice, analize și tratamente cunoscute), un LLM scrie scrisori de externare în română,
în stilul real al documentelor medicale românești. Pentru că știm exact ce conține fiecare pacient,
adnotările (unde e diagnosticul, ce medicament, ce doză) se pot genera automat. Pe acest corpus se
antrenează modele de extragere a entităților și de de-identificare.

Întrebarea de cercetare este dacă ce se învață pe text sintetic funcționează pe text real. Evaluarea
folosește MoNERo (text medical real în română, din publicații) și un set mic de scrisori scrise manual de
studenți la medicină, în condiții realiste, fără date reale de pacienți.

### De ce este interesantă tema
Tema abordează o problemă reală a NLP-ului pentru limbi cu resurse puține și are o întrebare de
cercetare clară și actuală (cât valorează datele sintetice). Rezultatul (corpusul, modelele, evaluarea)
este util comunității românești de NLP.

### Întrebări de cercetare
- **Î1.** Cât de bine se transferă un model de extragere a entităților clinice antrenat pe scrisori
  sintetice la text medical real în română?
- **Î2.** Ce caracteristici ale generării (diversitatea stilului, erori introduse, mărimea corpusului)
  influențează cel mai mult transferul?
- **Î3.** Cum se compară abordarea cu modelele multilingve folosite direct, fără antrenare suplimentară
  (zero-shot)?

### Etape și livrabile
- **1.** Studiul literaturii despre NLP clinic cu date sintetice și despre resursele existente pentru
  română.
- **2.** Generatorul de corpus: din pacienți Synthea, prompturi cu stiluri variate (secții, abrevieri,
  greșeli tipice), cu adnotări derivate automat și verificate prin eșantionare.
- **3.** Schema de adnotare (diagnostic, medicament, doză, analiză și valoare, procedură, date personale
  pentru de-identificare).
- **4.** Antrenarea modelelor (ex. pornind de la modele românești sau multilingve) pentru extragerea
  entităților și de-identificare.
- **5.** Set de evaluare manual: 50-100 de scrisori scrise de studenți la medicină după cazuri fictive,
  adnotate independent.
- **6.** Experimente de ablație pe parametrii generării și comparație cu LLM-uri folosite direct.
- **7.** Publicarea corpusului sintetic și a modelelor (licență deschisă).

### Date folosite (seturi publice)
- **Synthea**
  - *Ce conține:* Generator open-source de pacienți sintetici realiști, cu istoric complet de-a lungul
    vieții (consultații, diagnostice, medicație, analize, proceduri). Exportă FHIR R4, CSV și C-CDA,
    pentru populații de orice mărime. Nu conține date reale, deci nu ridică probleme de confidențialitate.
  - *Cum se folosește în temă:* Pacienți cu conținut medical cunoscut, ca bază a generării.
  - *Acces:* Open-source (Java), rulare locală.
  - *Link:* synthetichealth.github.io/synthea, Cod sursă (GitHub)
- **OpenLLM-Ro**
  - *Ce conține:* Familie de modele de limbaj deschise adaptate pentru română (RoLlama, RoMistral,
    RoGemma), cu benchmark-uri de evaluare în română.
  - *Cum se folosește în temă:* Modele deschise pentru română, pentru generare și ca model de bază.
  - *Acces:* Modele descărcabile de pe Hugging Face.
  - *Link:* huggingface.co/OpenLLM-Ro
- **MoNERo**
  - *Ce conține:* Corpus biomedical adnotat pentru limba română (texte din publicații medicale), cu
    entități precum boli, anatomie, substanțe.
  - *Cum se folosește în temă:* Text biomedical real în română, adnotat, pentru evaluarea transferului.
  - *Acces:* Liber, inclusiv prin colecția BigBIO pe Hugging Face.
  - *Link:* huggingface.co/datasets/bigbio/monero
- **MIMIC-IV-Note**
  - *Ce conține:* Scrisori de externare și rapoarte radiologice anonimizate, legate de pacienții din
    MIMIC-IV.
  - *Cum se folosește în temă:* Opțional: structura reală a scrisorilor de externare (în engleză), ca
    model de stil.
  - *Acces:* Aceleași condiții ca MIMIC-IV.
  - *Link:* physionet.org/content/mimic-iv-note

### Validare
F1 pe entități (potrivire exactă și parțială) pe setul manual și pe MoNERo, comparativ între modelul
antrenat pe sintetic, LLM-uri zero-shot și combinații, plus analiza erorilor pe tipuri de entități.

### Cunoștințe necesare
NLP, LLM, Python (Hugging Face).

---

## B-M5 Integrarea datelor multi-omics și clinice în condiții de date incomplete

- **Nivel:** Dizertație
- **Proiect/ancoră:** BioMedLake: date genomice (ICDG) și clinice în Data Lake; medicină personalizată
- **Co-îndrumare:** Ana-Mihaela Vasilevschi (doctorandă)
- **Context proiect:** BioMedLake (FEDR/STEP, 2026-2029, lider UMF „Carol Davila") construiește un Data
  Lake medical cu infrastructură HPC, o platformă de cercetare clinică și trei module AI. UNSTPB
  răspunde de arhitectura de date (FHIR, OMOP), de platformă și de modulele AI.

### Despre ce este vorba
Medicina personalizată se bazează pe combinarea mai multor „straturi" de informație despre un pacient:
genomul, expresia genelor (transcriptomica), metilarea ADN-ului, proteinele, plus datele clinice. Fiecare
strat surprinde altă parte a biologiei, iar împreună pot prezice mai bine evoluția unei boli sau răspunsul
la tratament.

Problema practică este că foarte puțini pacienți au toate straturile. Unii au doar date clinice și
expresie genică, alții și metilare, alții doar o parte. Metodele clasice elimină pacienții incompleți,
pierzând informație și introducând distorsiuni (pacienții cu profil complet nu sunt reprezentativi). În
plus, datele omics au mii de variabile pentru câteva sute de pacienți (problema „high-dimensional,
low-sample-size"), ceea ce face supraînvățarea foarte ușoară.

Tema studiază metode de integrare care tolerează lipsa unor straturi, pe date publice TCGA pentru un tip de
cancer ales. Tema se suprapune direct cu teza doctorandei Ana-Mihaela Vasilevschi, care tratează exact
integrarea datelor clinice și multi-omics incomplete, eterogene și de dimensiune mare. Studentul
lucrează pe un caz concret, cu îndrumarea ei metodologică.

### De ce este interesantă tema
Tema oferă o intrare structurată în bioinformatică și AI pentru medicina personalizată, un domeniu de
vârf. Studentul învață să lucreze riguros cu date de dimensiune mare și puține exemple (validare
corectă, scurgeri de informație, robustețe) și contribuie la o teză doctorală în curs.

### Întrebări de cercetare
- **Î1.** Cât pierd metodele standard când elimină pacienții incompleți, față de metodele care tolerează
  straturi lipsă?
- **Î2.** Ce contribuție are fiecare strat (clinic, expresie, metilare, CNV) la predicție și cât de
  stabilă este această contribuție?
- **Î3.** Cât de robuste sunt rezultatele la rate diferite de lipsă și la schimbarea cohortei?

### Etape și livrabile
- **1.** Alegerea tipului de cancer și a sarcinii de predicție (de exemplu subtip molecular sau
  supraviețuire) din TCGA, cu justificare.
- **2.** Pipeline reproductibil de descărcare și preprocesare pentru fiecare strat (normalizare,
  filtrarea variabilelor, efecte de lot).
- **3.** Linii de bază: modele pe un singur strat, concatenare simplă, metode publicate de integrare (de
  exemplu MOGONET).
- **4.** O metodă care tolerează straturi lipsă (de exemplu reprezentări învățate pe strat cu fuziune
  care ignoră straturile absente, sau imputare în spațiul latent).
- **5.** Experimente cu lipsă simulată la rate diferite și pe pacienții incompleți reali.
- **6.** Analiza contribuției straturilor și a stabilității variabilelor importante.
- **7.** Schiță de integrare a pipeline-ului în Data Lake (de exemplu extensia genomică a OMOP).

### Date folosite (seturi publice)
- **TCGA (portalul GDC)**
  - *Ce conține:* Atlasul genomic al cancerului: circa 33 de tipuri de cancer și peste 10.000 de pacienți,
    cu date deschise de expresie genică, metilare, variații de număr de copii, mutații (versiune
    filtrată) și date clinice.
  - *Cum se folosește în temă:* Date omics (expresie, metilare, CNV, mutații) și clinice pentru tipul de
    cancer ales, cu lipsă naturală între straturi.
  - *Acces:* Datele „open access" se descarcă liber; datele controlate nu sunt necesare.
  - *Link:* portal.gdc.cancer.gov, GDC date deschise

### Validare
AUC sau F1 (clasificare) și C-index (supraviețuire), cu validare încrucișată corectă (fără scurgeri),
robustețe la ratele de lipsă și stabilitatea variabilelor importante între rulări.

### Cunoștințe necesare
Machine learning, Python, interes pentru biologie (noțiunile de bază se învață).

---

## B-M6 Analiză și învățare federată între noduri spitalicești (utilizarea secundară a datelor în EHDS)

- **Nivel:** Dizertație
- **Proiect/ancoră:** BioMedLake: interconectarea a $\ge 30$ de unități medicale
- **Co-îndrumare:** -
- **Context proiect:** BioMedLake (FEDR/STEP, 2026-2029, lider UMF „Carol Davila") construiește un Data
  Lake medical cu infrastructură HPC, o platformă de cercetare clinică și trei module AI. UNSTPB
  răspunde de arhitectura de date (FHIR, OMOP), de platformă și de modulele AI.

### Despre ce este vorba
Regulamentul european privind Spațiul European al Datelor de Sănătate (EHDS) creează cadrul pentru
utilizarea secundară a datelor medicale în cercetare, prin organisme de acces la date și noduri naționale.
Nu toate datele pot sau trebuie să fie centralizate: uneori e mai sigur ca analiza să meargă la date, nu
datele la analiză. Așa funcționează analiza federată (fiecare spital calculează local statistici agregate)
și învățarea federată (fiecare spital antrenează local un model, iar doar parametrii modelului sunt
combinați).

În teorie e simplu. În practică, spitalele au populații foarte diferite (un spital de oncologie, unul de
pediatrie, unul județean general), deci datele nu sunt „identic distribuite", iar modelele federate se
degradează. În plus, chiar și parametrii modelelor pot dezvălui informații, de unde nevoia de
confidențialitate diferențială, care la rândul ei scade calitatea.

Tema simulează o rețea de 5-10 spitale cu populații realist diferite și studiază ce merge și ce nu:
analize federate de bază (numărări de cohorte, statistici descriptive) și un model predictiv federat, cu
și fără confidențialitate diferențială. Discuția include scenariul în care antrenarea folosește
infrastructuri HPC partajate, ca în lucrarea despre învățarea federată între centre de supercalcul
(Colonnelli et al.) din lecturile recente.

### De ce este interesantă tema
Tema continuă direcția de învățare federată a grupului și o aplică acolo unde contează cel mai mult:
datele de sănătate. Studentul învață sisteme distribuite pentru ML, confidențialitate diferențială și
evaluarea compromisului utilitate-confidențialitate.

### Întrebări de cercetare
- **Î1.** Cât pierde un model federat față de unul centralizat când spitalele au populații foarte
  diferite, și ce metode de agregare reduc pierderea?
- **Î2.** Care este costul în calitate al confidențialității diferențiale pentru bugete de
  confidențialitate realiste?
- **Î3.** Ce analize federate simple sunt suficiente pentru nevoile curente de cercetare și cu ce cost de
  comunicare?

### Etape și livrabile
- **1.** Studiu: framework-uri de învățare federată (ex. Flower, Vantage6), metode de agregare pentru
  date non-IID, confidențialitate diferențială.
- **2.** Construirea rețelei simulate: partiționarea datelor pe „spitale" după criterii realiste
  (specialitate, vârstă, regiune).
- **3.** Analize federate: numărări de cohorte, statistici descriptive, cu suprimarea celulelor mici.
- **4.** Un model predictiv (de exemplu risc de reinternare sau de mortalitate), antrenat centralizat,
  local și federat.
- **5.** Metode de agregare comparate (FedAvg și cel puțin una pentru date eterogene) și
  confidențialitate diferențială cu bugete diferite.
- **6.** Măsurarea costului de comunicare și a timpului.
- **7.** Discuție despre integrarea cu infrastructura HPC și cu cerințele EHDS.

### Date folosite (seturi publice)
- **MIMIC-IV (PhysioNet)**
  - *Ce conține:* Date clinice anonimizate de la Beth Israel Deaconess Medical Center (Boston) pentru
    internări în terapie intensivă și urgențe: diagnostice, medicație, analize, semne vitale.
  - *Cum se folosește în temă:* Date reale pentru sarcina predictivă (după acreditare), partiționate pe
    spitale simulate.
  - *Acces:* Acces după acreditare PhysioNet (curs online CITI, gratuit) și semnarea acordului de
    utilizare; studentul face acreditarea în primele săptămâni.
  - *Link:* physionet.org/content/mimiciv
- **Synthea**
  - *Ce conține:* Generator open-source de pacienți sintetici realiști, cu istoric complet de-a lungul
    vieții (consultații, diagnostice, medicație, analize, proceduri). Exportă FHIR R4, CSV și C-CDA,
    pentru populații de orice mărime. Nu conține date reale, deci nu ridică probleme de confidențialitate.
  - *Cum se folosește în temă:* Populații sintetice diferite pe spital, pentru experimente la scară mare.
  - *Acces:* Open-source (Java), rulare locală.
  - *Link:* synthetichealth.github.io/synthea, Cod sursă (GitHub)
- **MIMIC-IV demo în OMOP CDM**
  - *Ce conține:* Subset de 100 de pacienți MIMIC-IV transformat în OMOP CDM, inclusiv rezultatele
    Achilles și Data Quality Dashboard.
  - *Cum se folosește în temă:* Pentru analizele federate pe OMOP.
  - *Acces:* Acces deschis (fără acreditare) pe PhysioNet.
  - *Link:* physionet.org/content/mimic-iv-demo-omop

### Validare
Performanța modelului (AUC, calibrare) pentru antrenarea centralizată, locală și federată, la bugete de
confidențialitate diferite, plus costul de comunicare și timpul.

### Cunoștințe necesare
ML distribuit, Python (PyTorch, Flower).

---

## B-M7 Date clinice sintetice: utilitate versus risc de confidențialitate

- **Nivel:** Dizertație
- **Proiect/ancoră:** BioMedLake: dezvoltarea și testarea modulelor AI înainte de accesul la date reale
- **Co-îndrumare:** -
- **Context proiect:** BioMedLake (FEDR/STEP, 2026-2029, lider UMF „Carol Davila") construiește un Data
  Lake medical cu infrastructură HPC, o platformă de cercetare clinică și trei module AI. UNSTPB
  răspunde de arhitectura de date (FHIR, OMOP), de platformă și de modulele AI.

### Despre ce este vorba
Accesul la date medicale reale durează luni (avize etice, acorduri, anonimizare). Datele sintetice promit o
scurtătură: date artificiale care păstrează proprietățile statistice ale celor reale, dar nu corespund
niciunei persoane reale. Pot fi folosite pentru dezvoltare, testare, predare și, uneori, pentru cercetare.

Promisiunea are două riscuri opuse. Datele sintetice pot fi „prea curate" (pierd corelațiile rare, dar
importante clinic), caz în care modelele antrenate pe ele eșuează pe date reale. Sau pot fi prea fidele: un
generator care a „memorat" pacienți rari poate reproduce aproape identic o persoană reală, ceea ce
constituie o scurgere de date personale.

Tema compară sistematic mai multe generatoare (metode statistice, rețele generative tabulare, modele de
difuzie, LLM-uri) pe date reale anonimizate din MIMIC-IV și măsoară ambele fețe: utilitatea (antrenare pe
sintetic, testare pe real) și riscul (atacuri care încearcă să determine dacă o anumită persoană a fost
în datele de antrenare). Rezultatul este un set de recomandări concrete pentru proiect.

### De ce este interesantă tema
Datele sintetice sunt un subiect fierbinte în sănătate, finanțe și administrație, iar evaluarea lor
corectă este încă o problemă deschisă. Studentul învață modele generative și metode de evaluare a
confidențialității.

### Întrebări de cercetare
- **Î1.** Ce generator oferă cel mai bun compromis între utilitate și risc de confidențialitate pentru
  date clinice tabulare?
- **Î2.** Ce proprietăți clinic relevante (subgrupuri rare, corelații temporale) se pierd în generare?
- **Î3.** Cât de bine prezic metricile simple de fidelitate statistică utilitatea reală pentru o sarcină
  concretă?

### Etape și livrabile
- **1.** Studiu al generatoarelor de date tabulare și al metodelor de evaluare (fidelitate, utilitate,
  confidențialitate).
- **2.** Extragerea unui set tabular din MIMIC-IV (de exemplu internări cu variabile demografice,
  diagnostice, analize și rezultat).
- **3.** Antrenarea a 3-4 generatoare (statistic, CTGAN sau similar, difuzie tabulară, LLM).
- **4.** Evaluarea fidelității (distribuții, corelații, subgrupuri rare).
- **5.** Evaluarea utilității: antrenare pe sintetic, testare pe real (TSTR), pentru o sarcină predictivă.
- **6.** Evaluarea riscului: atacuri de membership inference și distanța până la cel mai apropiat pacient
  real.
- **7.** Recomandări pentru BioMedLake: când și cum se folosesc datele sintetice.

### Date folosite (seturi publice)
- **MIMIC-IV (PhysioNet)**
  - *Ce conține:* Date clinice anonimizate de la Beth Israel Deaconess Medical Center (Boston) pentru
    internări în terapie intensivă și urgențe: diagnostice, medicație, analize, semne vitale.
  - *Cum se folosește în temă:* Date reale anonimizate ca referință pentru antrenarea generatoarelor
    (după acreditare).
  - *Acces:* Acces după acreditare PhysioNet (curs online CITI, gratuit) și semnarea acordului de
    utilizare; studentul face acreditarea în primele săptămâni.
  - *Link:* physionet.org/content/mimiciv
- **Synthea**
  - *Ce conține:* Generator open-source de pacienți sintetici realiști, cu istoric complet de-a lungul
    vieții (consultații, diagnostice, medicație, analize, proceduri). Exportă FHIR R4, CSV și C-CDA,
    pentru populații de orice mărime. Nu conține date reale, deci nu ridică probleme de confidențialitate.
  - *Cum se folosește în temă:* Ca termen de comparație: date sintetice generate din reguli, nu învățate
    din date reale.
  - *Acces:* Open-source (Java), rulare locală.
  - *Link:* synthetichealth.github.io/synthea, Cod sursă (GitHub)

### Validare
Metrici de fidelitate, utilitate (performanța TSTR față de antrenarea pe real) și risc (succesul atacurilor
față de o linie de bază), sintetizate într-un tabel comparativ.

### Cunoștințe necesare
Machine learning, statistică, Python.

---

## B-M8 Guvernanța modulelor AI clinice: AI Act și EHDS în practică (model cards, audit trail, monitorizarea drift-ului)

- **Nivel:** Dizertație
- **Proiect/ancoră:** BioMedLake: conformitatea modulelor AI.1-AI.3 cu AI Act, GDPR și EHDS
  (responsabilitate UNSTPB inclusiv în perioada de sustenabilitate)
- **Co-îndrumare:** -
- **Context proiect:** BioMedLake (FEDR/STEP, 2026-2029, lider UMF „Carol Davila") construiește un Data
  Lake medical cu infrastructură HPC, o platformă de cercetare clinică și trei module AI. UNSTPB
  răspunde de arhitectura de date (FHIR, OMOP), de platformă și de modulele AI.

### Despre ce este vorba
Un sistem AI folosit în context medical intră, de regulă, în categoria „cu risc ridicat" din AI Act.
Asta înseamnă obligații concrete: documentație tehnică, gestionarea riscurilor, jurnalizarea automată a
funcționării, supraveghere umană, monitorizare după punerea în funcțiune. Cerințele sunt cunoscute în
principiu, dar traducerea lor în artefacte tehnice (ce se jurnalizează, cum se documentează un model, cum
se detectează degradarea) este puțin standardizată.

Modelele se degradează în timp: un laborator schimbă aparatul și valorile se deplasează, apare un cod nou
de diagnostic, se schimbă populația de pacienți. Fenomenul se numește drift și, nedetectat, face ca un model
validat ieri să greșească azi fără ca nimeni să observe.

Tema construiește un set de instrumente MLOps pentru guvernanța modulelor AI din BioMedLake: registru de
modele cu versiuni, documentație generată automat (model cards și o structură inspirată de cerințele de
documentație tehnică ale AI Act), jurnalizarea predicțiilor și a deciziilor umane, monitorizarea
drift-ului de date și de performanță, cu alerte. Totul se aplică pilot pe unul dintre modelele dezvoltate
în celelalte teme.

### De ce este interesantă tema
Tema leagă ingineria ML de reglementare, o combinație rară și foarte căutată acum, când AI Act intră în
aplicare. Studentul învață MLOps, metode statistice de detecție a drift-ului și să citească un text de
reglementare cu ochi de inginer.

### Întrebări de cercetare
- **Î1.** Ce cerințe din AI Act și EHDS pot fi acoperite automat prin instrumente MLOps și ce rămâne
  inevitabil proces uman?
- **Î2.** Cât de repede și de fiabil detectează metodele de monitorizare drift-uri realiste (schimbare
  de aparat, de populație, de codificare)?

### Etape și livrabile
- **1.** Analiza cerințelor relevante din AI Act (sisteme cu risc ridicat), GDPR și EHDS și maparea lor pe
  artefacte tehnice concrete.
- **2.** Registru de modele cu versionare (ex. MLflow) și legătura cu datele de antrenare.
- **3.** Generarea automată a documentației: model card, date de antrenare, performanță pe subgrupuri,
  limitări.
- **4.** Jurnalizarea predicțiilor, a explicațiilor și a deciziilor umane de acceptare sau
  respingere, cu păstrarea confidențialității.
- **5.** Monitorizarea drift-ului de date și de performanță (metode statistice), cu praguri și alerte.
- **6.** Scenarii de drift simulate pe date publice: schimbarea unității sau calibrării unei analize,
  schimbarea populației, cod nou.
- **7.** Aplicarea pilot pe un model predictiv antrenat în temă pe MIMIC-IV (de exemplu risc de
  reinternare) și un raport de conformitate generat automat.

### Date folosite (seturi publice)
- **MIMIC-IV (PhysioNet)**
  - *Ce conține:* Date clinice anonimizate de la Beth Israel Deaconess Medical Center (Boston) pentru
    internări în terapie intensivă și urgențe: diagnostice, medicație, analize, semne vitale.
  - *Cum se folosește în temă:* Date reale pe mai mulți ani, în care se pot studia drift-uri naturale
    între perioade (după acreditare).
  - *Acces:* Acces după acreditare PhysioNet (curs online CITI, gratuit) și semnarea acordului de
    utilizare; studentul face acreditarea în primele săptămâni.
  - *Link:* physionet.org/content/mimiciv
- **Synthea**
  - *Ce conține:* Generator open-source de pacienți sintetici realiști, cu istoric complet de-a lungul
    vieții (consultații, diagnostice, medicație, analize, proceduri). Exportă FHIR R4, CSV și C-CDA,
    pentru populații de orice mărime. Nu conține date reale, deci nu ridică probleme de confidențialitate.
  - *Cum se folosește în temă:* Populații generate cu parametri diferiți, pentru drift controlat.
  - *Acces:* Open-source (Java), rulare locală.
  - *Link:* synthetichealth.github.io/synthea, Cod sursă (GitHub)

### Validare
Acoperirea cerințelor (matrice cerință $\rightarrow$ artefact), timpul de detecție și rata de alarme false
pentru drift-urile simulate și overhead-ul jurnalizării asupra sistemului.

### Cunoștințe necesare
MLOps, statistică, Python; reglementarea se învață în temă.

---

# 3. Teme actualizate

---

## C-M1 Analiză de securitate formală pentru un protocol de verificare a actelor de studii

- **Nivel:** Dizertație
- **Proiect/ancoră:** Teza doctorandului Buhnici (securitate formală pentru acte de studii digitale)
- **Co-îndrumare:** Andrei Buhnici (doctorand)

### Despre ce este vorba
Blockcerts, unul dintre primele și cele mai răspândite sisteme de certificate pe blockchain, a fost folosit
ani de zile de universități din mai multe țări. O analiză formală publicată în 2019 a arătat că un atacator
putea fabrica un profil fals de emitent și produce certificate pe care protocolul nu le putea distinge de
cele autentice. Vulnerabilitatea a scăpat tuturor testelor funcționale obișnuite și a fost găsită doar
prin modelare formală.

Lecția este generală: protocoalele criptografice au atacuri subtile, care apar din combinarea mesajelor și
a presupunerilor de încredere, nu din bug-uri de implementare. Instrumentele de verificare formală
(ProVerif, Tamarin) permit descrierea precisă a protocolului și a capacităților atacatorului, apoi
demonstrează automat proprietăți (de exemplu „un verificator acceptă un act doar dacă a fost emis de
universitatea legitimă") sau găsesc contra-exemple.

Tema modelează formal un protocol de emitere și verificare a actelor de studii (Open Badges 3.0 cu W3C
Verifiable Credentials și listă de revocare, sau un alt sistem existent ales cu îndrumătorul), formulează
proprietățile de securitate, le verifică automat și corectează atacurile găsite.

### De ce este interesantă tema
Verificarea formală este o competență rară și foarte apreciată în securitate. Tema are un obiect concret
și delimitat, potrivit pentru un master: nu cere inventarea unei teorii noi, ci aplicarea riguroasă a unor
instrumente mature. Rezultatul poate face parte din teza doctorandului Buhnici și poate duce la o
publicație.

### Întrebări de cercetare
- **Î1.** Ce proprietăți de securitate (autenticitatea emitentului, integritatea, revocarea,
  confidențialitatea titularului) are protocolul și în ce ipoteze despre atacator?
- **Î2.** Ce atacuri apar când una dintre ipoteze cade (de exemplu cheie compromisă, registru de emitenți
  indisponibil)?

### Etape și livrabile
- **1.** Studiul metodelor formale pentru protocoale (modelul Dolev-Yao, ProVerif și/sau Tamarin) și al
  analizei Blockcerts.
- **2.** Descrierea precisă a protocolului ales: actori, mesaje, chei, ipoteze de încredere.
- **3.** Modelarea în instrumentul ales și formularea proprietăților.
- **4.** Verificarea automată, interpretarea rezultatelor și a contra-exemplelor.
- **5.** Variații ale modelului atacatorului (chei compromise, canale nesigure, emitent rău-intenționat).
- **6.** Propunerea și verificarea corecțiilor.
- **7.** Comparația cu o analiză informală a aceluiași protocol: ce a găsit în plus analiza formală.

### Date folosite (seturi publice)
- **Specificații pentru acte de studii digitale**
  - *Ce conține:* Open Badges 3.0 (1EdTech), W3C Verifiable Credentials Data Model 2.0, European Digital
    Credentials for Learning (Europass), W3C DID, Bitstring Status List.
  - *Cum se folosește în temă:* Specificațiile protocoalelor modelate.
  - *Acces:* Specificații publice.
  - *Link:* Open Badges 3.0, W3C VC Data Model 2.0, Europass / EDC

### Validare
Lista proprietăților demonstrate și a ipotezelor necesare, atacurile găsite (cu urma de execuție) și
verificarea că versiunea corectată elimină atacurile.

### Cunoștințe necesare
Securitate, criptografie, logică; instrumentul de verificare se învață în temă.

---

## C-M2 Abținere calibrată în asistenți RAG: când trebuie să spună „nu știu"

- **Nivel:** Dizertație
- **Proiect/ancoră:** Lectura „Why Language Models Hallucinate" (2025); legătură cu BioMedLake (AI.2)
- **Co-îndrumare:** -

### Despre ce este vorba
Lucrarea „Why Language Models Hallucinate" (2025) are o explicație simplă: modelele de limbaj ghicesc
când nu știu pentru că aproape toate evaluările le recompensează pentru asta, la fel ca un student la un
test grilă fără depunctare. Un răspuns greșit dat cu încredere costă la fel de mult ca „nu știu", deci
ghicitul e strategia optimă. Autorii propun schimbarea regulilor de scor, astfel încât abținerea să fie
preferabilă unui răspuns greșit.

Pentru un asistent folosit într-un domeniu critic (un asistent pentru ghiduri medicale, un asistent pentru
regulamente universitare) contează mai puțin să răspundă la tot și mai mult să nu răspundă greșit.
Arhitectura RAG (regăsire de documente plus generare) ajută, dar nu rezolvă: modelul poate ignora
documentele, le poate interpreta greșit sau poate răspunde când documentele nu conțin răspunsul.

Tema construiește un asistent RAG pe un domeniu delimitat și studiază metode prin care acesta estimează
dacă răspunsul este susținut de surse, abținându-se altfel. Evaluarea folosește reguli de scor care
penalizează greșelile mai mult decât abținerea.

### De ce este interesantă tema
Tema transformă o idee teoretică recentă într-un experiment concret, la îndemâna unui student de master.
Rezultatele sunt relevante pentru BioMedLake (AI.2), pentru asistenții care răspund pe baza
regulamentelor și pentru orice asistent instituțional.

### Întrebări de cercetare
- **Î1.** Ce metode de estimare a încrederii (consistența între mai multe răspunsuri, verificarea
  fiecărei afirmații față de surse, scoruri ale modelului) prezic cel mai bine corectitudinea?
- **Î2.** Cum se schimbă comportamentul optim al asistentului sub reguli de scor diferite (penalizări
  diferite pentru greșeli)?
- **Î3.** Se transferă rezultatele între domenii (biomedical vs. administrativ) și între limbi?

### Etape și livrabile
- **1.** Studiu de literatură: calibrare, predicție selectivă, verificarea afirmațiilor, RAG.
- **2.** Două domenii de lucru: biomedical (de exemplu PubMedQA sau ghiduri publice) și administrativ
  (regulamente UPB publice), cu seturi de întrebări care includ intenționat întrebări fără răspuns în
  documente.
- **3.** Asistent RAG de referință, cu citarea surselor.
- **4.** Implementarea a 3-4 metode de estimare a încrederii și a politicii de abținere.
- **5.** Evaluare cu reguli de scor parametrizate, curbe risc-acoperire, calibrare.
- **6.** Analiza erorilor: tipuri de răspunsuri greșite care trec de filtre.

### Date folosite (seturi publice)
- **Seturi de întrebări pentru evaluarea halucinațiilor**
  - *Ce conține:* SimpleQA (întrebări factuale scurte cu răspuns verificabil), PubMedQA (întrebări
    biomedicale cu context din rezumate), TruthfulQA.
  - *Cum se folosește în temă:* PubMedQA și SimpleQA pentru întrebări cu răspuns verificabil.
  - *Acces:* Descărcare liberă.
  - *Link:* SimpleQA (simple-evals), PubMedQA, TruthfulQA
- **Regulamente și metodologii UPB**
  - *Ce conține:* Regulamente, metodologii și hotărâri publicate pe site-ul universității.
  - *Cum se folosește în temă:* Regulamente publice ca domeniu administrativ în română.
  - *Acces:* Publice.
  - *Link:* upb.ro
- **OpenLLM-Ro**
  - *Ce conține:* Familie de modele de limbaj deschise adaptate pentru română (RoLlama, RoMistral,
    RoGemma), cu benchmark-uri de evaluare în română.
  - *Cum se folosește în temă:* Modele deschise pentru română.
  - *Acces:* Modele descărcabile de pe Hugging Face.
  - *Link:* huggingface.co/OpenLLM-Ro

### Validare
Curbe risc-acoperire, eroarea de calibrare, scorul sub reguli diferite de penalizare și comparația cu
asistentul fără abținere.

### Cunoștințe necesare
LLM, evaluare experimentală, statistică de bază, Python.

---

## C-M3 Robustețea marcajelor de tip watermark pentru text generat de AI în limba română

- **Nivel:** Dizertație
- **Proiect/ancoră:** Codul de bune practici pentru transparență (AI Act, art. 50): marcarea și
  detectarea textului generat
- **Co-îndrumare:** -

### Despre ce este vorba
Metadatele de proveniență funcționează pentru imagini, dar textul se copiază fără metadate. Pentru text,
soluția studiată intens este watermark-ul statistic: în timpul generării, modelul este împins discret să
prefere anumite cuvinte dintr-o „listă secretă", stabilită pseudo-aleator. Un detector care cunoaște cheia
poate apoi verifica statistic dacă un text conține prea multe cuvinte „preferate" ca să fie întâmplător.
Mai multe scheme au fost publicate, iar unele sunt deja integrate în biblioteci deschise.

Aproape toate evaluările sunt pe engleză. Româna are morfologie bogată (un cuvânt are multe forme
flexionare), ordinea cuvintelor e mai liberă, iar tokenizarea modelelor e mai puțin eficientă. Nu se știe
cât de bine supraviețuiesc watermark-urile parafrazării, traducerii dus-întors sau corecturii manuale în
română și nici cât de mult afectează calitatea textului.

Tema implementează 1-2 scheme publicate pe un model de limbaj deschis cu suport bun pentru română,
construiește atacuri realiste și compară sistematic robustețea în română față de engleză.

### De ce este interesantă tema
Tema are o întrebare de cercetare clară și bine delimitată, cu metodologie experimentală standard, și
produce rezultate noi pentru o limbă puțin studiată. Este direct relevantă pentru implementarea AI Act în
România.

### Întrebări de cercetare
- **Î1.** Cât de detectabile rămân watermark-urile în textul românesc după parafrazare, traducere
  dus-întors și editare manuală, comparativ cu engleza?
- **Î2.** Care este costul în calitate (fluență, fidelitate) al watermark-ului pentru română?
- **Î3.** Ce parametri ai schemei (puterea marcajului, lungimea textului) dau cel mai bun compromis?

### Etape și livrabile
- **1.** Studiul schemelor de watermark pentru text (de exemplu familia Kirchenbauer et al., variante
  robuste, SynthID-Text) și al atacurilor publicate.
- **2.** Implementarea a 1-2 scheme pe un model deschis cu suport pentru română.
- **3.** Generarea unui corpus de test în română și engleză pe aceleași subiecte.
- **4.** Atacuri: parafrazare automată cu alt model, traducere dus-întors, înlocuire de sinonime, editare
  umană pe un eșantion.
- **5.** Evaluarea detectabilității (rate de detecție la rate de fals pozitiv fixate) și a calității
  textului (metrici automate și evaluare umană).
- **6.** Analiza parametrilor și recomandări pentru detectoare în română.

### Date folosite (seturi publice)
- **OpenLLM-Ro**
  - *Ce conține:* Familie de modele de limbaj deschise adaptate pentru română (RoLlama, RoMistral,
    RoGemma), cu benchmark-uri de evaluare în română.
  - *Cum se folosește în temă:* Modele deschise pentru română, pe care se aplică watermark-ul.
  - *Acces:* Modele descărcabile de pe Hugging Face.
  - *Link:* huggingface.co/OpenLLM-Ro
- **Corpusuri publice de text în română**
  - *Ce conține:* Wikipedia în română (dump), CC-100 și OSCAR (text web), Monitorul Oficial și texte
    legislative publice.
  - *Cum se folosește în temă:* Texte umane în română ca referință negativă (nu trebuie detectate ca
    generate).
  - *Acces:* Descărcare liberă.
  - *Link:* Wikipedia RO - dumps, OSCAR, CC-100, Portal legislativ

### Validare
Rata de detecție la 1% fals pozitiv, înainte și după fiecare atac, comparativ română-engleză, plus
impactul asupra calității (perplexitate, evaluare umană pe un eșantion).

### Cunoștințe necesare
NLP, statistică, Python (PyTorch, Hugging Face).

---

## C-M6 Free-riding și stimulente în învățarea federată: o abordare prin teoria jocurilor

- **Nivel:** Dizertație
- **Proiect/ancoră:** Lecturile „The Tragedy of the Commons" și „Game Theory. A Nontechnical
  Introduction"
- **Co-îndrumare:** -

### Despre ce este vorba
Garrett Hardin a descris în 1968 „tragedia bunurilor comune": o pășune comună pe care fiecare cioban are
interes să-și aducă încă o oaie, deși suma acestor decizii raționale distruge pășunea. Aceeași logică
apare într-o federație de învățare automată. Modelul comun este bunul comun. Fiecare participant
(spital, firmă, telefon) beneficiază de el, dar contribuția (date de calitate, putere de calcul, bandă)
are un cost. Un participant rațional poate fi tentat să contribuie puțin sau deloc (free-riding) sau chiar
să trimită actualizări false, păstrând totuși accesul la model.

Dacă destui participanți fac asta, calitatea modelului scade și participanții onești pleacă: federația
se prăbușește. Literatura propune mecanisme de stimulare: recompense proporționale cu contribuția
(estimată de exemplu prin valori Shapley), reputație, contracte, eventual înregistrate pe un registru
distribuit pentru transparență.

Tema formalizează problema ca joc, simulează federații cu participanți onești și oportuniști și
compară mecanismele de stimulare.

### De ce este interesantă tema
Tema leagă un subiect clasic al științelor sociale de o problemă tehnică actuală și îmbină teoria
(jocuri, mecanisme) cu experimentul (simulări de învățare federată). Rezultatele sunt relevante pentru
rețelele de spitale care antrenează modele împreună și pentru orice spațiu de date partajat.

### Întrebări de cercetare
- **Î1.** În ce condiții devine free-riding-ul strategia dominantă într-o federație și cum afectează
  calitatea modelului?
- **Î2.** Ce mecanisme de stimulare (Shapley aproximativ, reputație, recompense prin registru)
  restabilesc cooperarea și cu ce cost computațional?
- **Î3.** Cât de robuste sunt mecanismele la participanți care mint despre contribuția lor?

### Etape și livrabile
- **1.** Studiu: teoria jocurilor de bază (echilibru Nash, dilema prizonierului, bunuri publice),
  mecanisme de stimulare în învățarea federată, estimarea contribuției.
- **2.** Modelul formal: jucători, strategii (contribuție completă, parțială, nulă, malițioasă),
  costuri, beneficii.
- **3.** Simulator de federație (ex. peste Flower) cu tipuri de participanți configurabile.
- **4.** Implementarea a 3 mecanisme de stimulare și detecție.
- **5.** Experimente: proporții diferite de oportuniști, date eterogene, participanți care mint.
- **6.** Analiza stabilității și recomandări de proiectare.

### Date folosite (seturi publice)
- **PlantVillage și PlantDoc**
  - *Ce conține:* PlantVillage are circa 54.000 de imagini de frunze în 38 de clase (fotografiate în
    laborator). PlantDoc are câteva mii de imagini din teren, în condiții reale.
  - *Cum se folosește în temă:* Sarcină de clasificare de imagini cu distribuții eterogene între
    participanți.
  - *Acces:* Descărcare liberă.
  - *Link:* PlantVillage, PlantDoc
- **MIMIC-IV (PhysioNet)**
  - *Ce conține:* Date clinice anonimizate de la Beth Israel Deaconess Medical Center (Boston) pentru
    internări în terapie intensivă și urgențe: diagnostice, medicație, analize, semne vitale.
  - *Cum se folosește în temă:* Opțional: o sarcină clinică tabulară (de exemplu risc de reinternare),
    pentru un scenariu de federație între spitale.
  - *Acces:* Acces după acreditare PhysioNet (curs online CITI, gratuit) și semnarea acordului de
    utilizare; studentul face acreditarea în primele săptămâni.
  - *Link:* physionet.org/content/mimiciv

### Validare
Calitatea modelului comun, rata de detecție a free-riderilor și a participanților malițioși, echitatea
recompenselor (corelația cu contribuția reală) și costul computațional al mecanismelor.

### Cunoștințe necesare
ML distribuit, Python; noțiunile de teoria jocurilor se învață în temă.

---

# 4. Direcții de cercetare și din proiectele în curs

---

## D2-M1 Agenți LLM ca șoferi într-un simulator de trafic

- **Nivel:** Dizertație
- **Proiect/ancoră:** Experiența grupului în simularea mobilității urbane (Sim2Car) și rutarea
  inteligentă a traficului
- **Co-îndrumare:** -

### Despre ce este vorba
Simulatoarele de trafic modelează alegerea rutei și a orei de plecare prin reguli relativ simple: șoferul
alege drumul cel mai rapid, eventual cu puțin zgomot aleator. Oamenii reali sunt mai complicați. Au
obiceiuri, evită anumite străzi, reacționează diferit la o alertă de trafic, schimbă ora de plecare,
renunță la mașină când e aglomerat. Comportamentul agregat al acestor decizii determină dacă o măsură de
trafic funcționează sau nu.

Modelele de limbaj mari pot juca rolul unor „șoferi" cu personalitate și memorie: primesc o descriere a
situației (ruta obișnuită, informațiile de trafic, preferințele) și decid. Cercetări recente au început
să folosească LLM-uri în simulări sociale, dar validitatea lor pentru comportamentul în trafic este puțin
studiată și costul computațional e mare.

Tema integrează un LLM în simulatorul open-source SUMO pentru un subset de agenți (deciziile de rută și
de plecare), compară comportamentul emergent cu modelele clasice pe scenarii realiste și studiază efectul
informațiilor de trafic. Este continuarea naturală, la nivel de cercetare, a direcției Sim2Car.

### De ce este interesantă tema
Tema e nouă și provocatoare, la intersecția dintre LLM, simulare și știința transporturilor, dar bine
delimitată (un scenariu, un subset de agenți, metrici clare). Studentul învață simulare de trafic și
metodologie experimentală cu modele generative.

### Întrebări de cercetare
- **Î1.** Diferă comportamentul agregat (distribuția traficului, timpi de parcurs) când o parte din
  agenți sunt LLM-uri, față de modelele clasice de alegere a rutei?
- **Î2.** Reacționează agenții LLM la informații de trafic (alerte, recomandări) într-un mod mai realist
  sau doar diferit, și cum se poate verifica?
- **Î3.** Care este costul computațional și cum poate fi redus (agenți tipizați, cache de decizii)?

### Etape și livrabile
- **1.** Studiu: modele de alegere a rutei, simularea cu agenți, utilizarea LLM-urilor în simulări
  sociale.
- **2.** Integrarea LLM $\rightarrow$ SUMO (prin interfața TraCI) pentru deciziile unui subset
  configurabil de agenți.
- **3.** Definirea „personalităților" agenților și a informației disponibile pentru fiecare decizie.
- **4.** Scenarii pe rețele SUMO deschise (de exemplu LuST): zi normală, accident, alertă de trafic.
- **5.** Comparația cu modelele clasice și analiza sensibilității la promptare și la model.
- **6.** Optimizarea costului (agenți tipizați, cache) și discuția despre validitate.

### Date folosite (seturi publice)
- **Scenarii SUMO deschise**
  - *Ce conține:* Scenarii de trafic validate pentru simulatorul SUMO: LuST (Luxemburg), MoST (Monaco),
    TAPASCologne.
  - *Cum se folosește în temă:* Scenarii de trafic deschise și validate (LuST, MoST, TAPASCologne).
  - *Acces:* Liber.
  - *Link:* eclipse.dev/sumo, Scenariul LuST
- **OpenStreetMap**
  - *Ce conține:* Hartă colaborativă deschisă: drumuri, clădiri, ape, puncte de interes. Baza pentru rutare
    și simulare de trafic.
  - *Cum se folosește în temă:* Rețele rutiere pentru un scenariu românesc, opțional.
  - *Acces:* Licență ODbL; extrase regionale (ex. Geofabrik).
  - *Link:* www.openstreetmap.org

### Validare
Indicatori de trafic (timpi de parcurs, distribuția pe rute, congestie) comparați între modele,
reproductibilitatea, costul per simulare și o analiză calitativă a deciziilor agenților.

### Cunoștințe necesare
Simulare, LLM, Python.

---

## D3-M1 Învățare federată pe dispozitive edge pentru detecția bolilor plantelor în ferme mici

- **Nivel:** Dizertație
- **Proiect/ancoră:** Publicația grupului despre învățare federată pentru detecția bolilor culturilor;
  proiectele NETIoT și SmartAgriHubs
- **Co-îndrumare:** -

### Despre ce este vorba
Detecția timpurie a bolilor plantelor poate salva o recoltă, iar modelele de viziune computerizată
recunosc bine bolile din fotografii de frunze. Problema este că modelele antrenate pe imagini de laborator
(fundal uniform, lumină perfectă) greșesc mult în câmp. Fiecare fermă are culturile, soiurile,
condițiile și bolile ei, iar o fermă mică are puține imagini etichetate.

Învățarea federată permite fermelor să antreneze împreună un model fără să-și trimită imaginile într-un
loc central: fiecare dispozitiv (telefon, cameră în seră, mic computer pe tractor) învață local și
trimite doar actualizări ale modelului. Grupul a publicat deja rezultate în această direcție. Ce rămâne
dificil: distribuțiile foarte diferite între ferme (date non-IID), participarea intermitentă
(conectivitate slabă la țară) și resursele limitate ale dispozitivelor.

Tema studiază aceste trei probleme și testează personalizarea: un model comun adaptat local la fiecare
fermă.

### De ce este interesantă tema
Tema continuă direct o direcție publicată a grupului și are o aplicație cu impact. Studentul învață
învățare federată în condiții realiste, optimizarea modelelor pentru dispozitive și evaluarea pe
distribuții eterogene.

### Întrebări de cercetare
- **Î1.** Cât pierde învățarea federată când fermele au culturi și condiții foarte diferite și ce metode
  de personalizare compensează pierderea?
- **Î2.** Cum afectează participarea intermitentă convergența și calitatea modelului?
- **Î3.** Ce compromis acuratețe-cost oferă modelele compacte pe dispozitivele edge?

### Etape și livrabile
- **1.** Studiu: învățarea federată personalizată, date non-IID, modele compacte pentru edge.
- **2.** Simularea fermelor: partiționarea imaginilor pe culturi și boli, cu amestec de imagini de
  laborator și de teren.
- **3.** Model compact (de exemplu familia MobileNet sau EfficientNet-Lite) și versiuni cuantizate.
- **4.** Algoritmi comparați: FedAvg, cel puțin un algoritm pentru date eterogene, personalizare locală.
- **5.** Simularea participării intermitente și a legăturilor lente.
- **6.** Pilot pe 3-5 dispozitive reale (telefoane sau Raspberry Pi) și măsurarea costului.

### Date folosite (seturi publice)
- **PlantVillage și PlantDoc**
  - *Ce conține:* PlantVillage are circa 54.000 de imagini de frunze în 38 de clase (fotografiate în
    laborator). PlantDoc are câteva mii de imagini din teren, în condiții reale.
  - *Cum se folosește în temă:* Imagini de laborator (PlantVillage) și de teren (PlantDoc), pentru
    generalizarea din laborator în câmp.
  - *Acces:* Descărcare liberă.
  - *Link:* PlantVillage, PlantDoc

### Validare
Acuratețea per fermă (medie și cea mai slabă fermă), în special pe imagini de teren, costul de comunicare,
timpul și energia pe dispozitiv și robustețea la participarea intermitentă.

### Cunoștințe necesare
Machine learning, Python (PyTorch, Flower), noțiuni de edge computing.

---

## D6-M1 Fidelitatea terminologică a traducerii automate medicale în română cu LLM

- **Nivel:** Dizertație
- **Proiect/ancoră:** Teoria traducerii (echivalența funcțională a lui Nida, teoria Skopos a lui
  Vermeer); BioMedLake; e-prescripțiile transfrontaliere
- **Co-îndrumare:** -

### Despre ce este vorba
Traducerea automată a devenit foarte fluentă, iar LLM-urile traduc texte medicale aparent impecabil. Dar
în medicină o traducere „frumoasă" poate fi periculoasă: o doză greșită, o contraindicație omisă, o
denumire comună internațională tradusă greșit, un „nu" pierdut. Metricile automate uzuale (BLEU și
succesorii lui) măsoară asemănarea de suprafață cu o traducere de referință și nu surprind aceste
erori critice.

Teoria traducerii oferă un cadru mai bun. Pentru Nida, contează echivalența de efect asupra cititorului.
Pentru teoria Skopos (Vermeer), traducerea se judecă după scopul ei: un prospect pentru pacient și un
rezumat al caracteristicilor produsului pentru medic au scopuri și cititori diferiți. O evaluare corectă
trebuie să combine verificarea terminologică (DCI, doze, unități, contraindicații) cu cea
funcțională (își atinge textul scopul pentru cititorul vizat?).

Informațiile despre medicamente publicate de EMA în toate limbile oficiale ale UE formează un corpus
paralel natural, cu traduceri profesionale verificate. Tema îl folosește ca referință pentru a evalua
mai multe sisteme de traducere în română, cu o metodologie de evaluare care pornește din teoria
traducerii.

### De ce este interesantă tema
Tema leagă NLP-ul de lingvistică și teoria traducerii, o combinație rară. Are o întrebare de
cercetare clară (ce erori fac sistemele actuale și cât de bine le prind metricile) și impact practic
(siguranța pacienților, e-prescripțiile transfrontaliere).

### Întrebări de cercetare
- **Î1.** Ce tipuri de erori terminologice și funcționale fac LLM-urile și sistemele de traducere
  automată în textele medicale traduse în română, și cât de frecvente sunt erorile critice?
- **Î2.** Cât de bine corelează metricile automate cu evaluarea umană a erorilor critice?
- **Î3.** Poate o verificare automată ancorată în terminologii (DCI, termeni EDQM) să detecteze erorile
  critice?

### Etape și livrabile
- **1.** Construirea corpusului paralel engleză-română din informațiile de produs EMA (aliniere pe
  secțiuni și propoziții), completat cu corpusul EMEA din OPUS.
- **2.** Selectarea sistemelor evaluate: 2-3 LLM-uri (inclusiv unul deschis, adaptat pentru română) și
  1-2 sisteme de traducere automată.
- **3.** Grila de evaluare: erori terminologice (DCI, doze, unități, forme), erori de sens (negații,
  condiții), adecvare funcțională pe tip de text (prospect vs. RCP), după cadrul Skopos.
- **4.** Evaluare umană pe un eșantion (ideal cu un traducător sau un farmacist) și metrici automate.
- **5.** Verificator automat ancorat în terminologii, pentru erorile critice.
- **6.** Analiză și recomandări pentru utilizarea traducerii automate în context medical.

### Date folosite (seturi publice)
- **EMA - date despre medicamente**
  - *Ce conține:* Baza de date a medicamentelor autorizate centralizat (export Excel), EPAR-uri și
    informații despre produs (rezumatul caracteristicilor produsului și prospectul) în toate limbile
    oficiale ale UE.
  - *Cum se folosește în temă:* Informațiile de produs în engleză și română, cu traduceri profesionale.
  - *Acces:* Acces liber.
  - *Link:* www.ema.europa.eu/en/medicines/download-medicine-data, EPAR-uri și informații despre produs
- **Corpusul paralel EMEA (OPUS)**
  - *Ce conține:* Documente EMA aliniate la nivel de propoziție în 22 de limbi, inclusiv română.
    Versiunea este mai veche, dar e utilă ca bază de pornire.
  - *Cum se folosește în temă:* Corpusul paralel aliniat (versiune mai veche).
  - *Acces:* Descărcare liberă de pe OPUS.
  - *Link:* opus.nlpl.eu
- **EDQM Standard Terms**
  - *Ce conține:* Termeni standard europeni pentru forme farmaceutice, căi de administrare și ambalaje,
    cu coduri și traduceri.
  - *Cum se folosește în temă:* Termenii standard pentru forme și căi, în ambele limbi.
  - *Acces:* Acces online gratuit după înregistrare.
  - *Link:* standardterms.edqm.eu
- **OpenLLM-Ro**
  - *Ce conține:* Familie de modele de limbaj deschise adaptate pentru română (RoLlama, RoMistral,
    RoGemma), cu benchmark-uri de evaluare în română.
  - *Cum se folosește în temă:* LLM-uri deschise pentru română.
  - *Acces:* Modele descărcabile de pe Hugging Face.
  - *Link:* huggingface.co/OpenLLM-Ro

### Validare
Frecvența erorilor pe tipuri și pe sisteme (evaluare umană), corelația metricilor automate cu evaluarea
umană și precizia și recall-ul verificatorului automat pentru erorile critice.

### Cunoștințe necesare
NLP, Python, interes pentru lingvistică și traducere.

---

## D7-M1 Tutor socratic cu LLM care nu dă răspunsul: experiment pilot la un curs UPB

- **Nivel:** Dizertație
- **Proiect/ancoră:** Manifestul pentru educația în era AI
- **Co-îndrumare:** -

### Despre ce este vorba
Studenții folosesc deja zilnic asistenți AI. Întrebarea nu mai este dacă îi folosesc, ci cum îi afectează.
Un asistent care dă direct rezolvarea poate crea iluzia înțelegerii: studentul trece tema, dar nu învață.
Un tutor care ghidează prin întrebări (metoda socratică), cere studentului să explice și îl lasă să
greșească și să se corecteze ar putea, în schimb, să îmbunătățească învățarea. Primele studii
internaționale arată rezultate amestecate, iar efectul depinde mult de cum e configurat tutorul.

Tema construiește un tutor socratic pentru un subiect delimitat dintr-un curs UPB (de exemplu un capitol de
structuri de date sau de algoritmi) și realizează un experiment controlat. Un grup învață cu tutorul
socratic, altul cu un asistent obișnuit (care răspunde direct), eventual un al treilea fără AI. Se
măsoară învățarea prin pre-test și post-test, inclusiv la distanță de câteva săptămâni, și se
analizează interacțiunile.

Experimentul cere aviz de la comisia de etică și consimțământul participanților. Metodologia se
stabilește cu atenție de la început.

### De ce este interesantă tema
Tema răspunde unei întrebări pe care și-o pune toată lumea educațională și oferă studentului o
experiență rară: un experiment real cu participanți umani, cu tot rigoarea metodologică. Rezultatele
pot fi publicate și pot informa politica universității privind AI-ul în educație.

### Întrebări de cercetare
- **Î1.** Învață mai bine (și mai durabil) studenții care folosesc un tutor socratic față de cei care
  folosesc un asistent care răspunde direct?
- **Î2.** Ce tipare de interacțiune (cereri de soluție, explicații proprii, persistență) prezic învățarea?
- **Î3.** Cum percep studenții cele două tipuri de asistent (utilitate, frustrare, încredere)?

### Etape și livrabile
- **1.** Studiu: literatura despre tutori inteligenți, metoda socratică, primele studii despre LLM-uri
  în învățare.
- **2.** Proiectarea tutorului: politica de răspuns (întrebări, indicii, fără soluție), adaptarea la
  nivelul studentului, protecția împotriva „ocolirii" prin prompturi.
- **3.** Proiectarea experimentului: subiect, grupuri, randomizare, pre-test, post-test, test întârziat,
  chestionare.
- **4.** Obținerea avizului etic și a consimțământului.
- **5.** Desfășurarea experimentului și colectarea datelor de interacțiune (anonimizate).
- **6.** Analiza statistică și analiza calitativă a interacțiunilor.

### Date folosite (seturi publice)
- **Probleme de programare publice**
  - *Ce conține:* HumanEval, MBPP și temele proprii ale cursului, cu teste automate.
  - *Cum se folosește în temă:* Exerciții de programare pentru subiectul ales.
  - *Acces:* Liber.
  - *Link:* HumanEval, MBPP
- **Seturi de probleme de matematică**
  - *Ce conține:* RoMath (benchmark de probleme de matematică în română, inclusiv de nivel olimpiadă),
    GSM8K (probleme de nivel școlar, în engleză).
  - *Cum se folosește în temă:* Exerciții de raționament, dacă subiectul ales e de matematică.
  - *Acces:* Liber (Hugging Face).
  - *Link:* arxiv.org/abs/2409.11074, GSM8K

### Validare
Diferența de câștig de învățare între grupuri (cu teste statistice adecvate și mărimea efectului),
retenția la testul întârziat și analiza calitativă a interacțiunilor.

### Cunoștințe necesare
LLM, dezvoltare web, statistică și metodologie experimentală (se învață).

---

## D9-M1 Alocarea echitabilă a GPU-urilor partajate într-o universitate

- **Nivel:** Dizertație
- **Proiect/ancoră:** Infrastructura HPC din BioMedLake și din alte proiecte; lecturile despre teoria
  jocurilor și bunurile comune; AI Factories EuroHPC
- **Co-îndrumare:** -

### Despre ce este vorba
GPU-urile sunt cea mai disputată resursă dintr-o universitate care face AI. Fără reguli, se întâmplă
două lucruri simultan: câțiva utilizatori monopolizează resursele (joburi lungi, rezervări de
siguranță), în timp ce alte GPU-uri stau nefolosite pentru că aparțin altui proiect. Este exact
„tragedia bunurilor comune" a lui Hardin, într-o formă modernă.

Centrele de calcul folosesc diverse mecanisme: cote fixe pe grup, „fair-share" (prioritatea scade cu
consumul recent), priorități pe proiecte, mecanisme de piață (licitații cu credite). Fiecare are
compromisuri între eficiență (GPU-uri ocupate), echitate (fiecare primește partea corectă) și
stimulente (nimeni nu are interes să mintă despre nevoile lui).

Tema compară aceste mecanisme prin simulare pe trace-uri reale de clustere GPU și, unde sunt disponibile,
pe date de utilizare ale serverelor universității, cu o analiză inspirată de teoria jocurilor (ce
strategii au utilizatorii sub fiecare mecanism).

### De ce este interesantă tema
Tema leagă teoria (jocuri, proiectarea mecanismelor, echitate) de o problemă practică a universității.
Studentul învață simulare de sisteme de planificare, metrici de echitate și analiza stimulentelor.

### Întrebări de cercetare
- **Î1.** Ce compromis între utilizare, timp de așteptare și echitate oferă fiecare mecanism de alocare
  pe încărcări realiste?
- **Î2.** Sub ce mecanisme au utilizatorii interes să-și declare greșit nevoile și cum se poate preveni?

### Etape și livrabile
- **1.** Studiu: planificarea pe clustere (cote, fair-share, priorități), alocarea echitabilă (de exemplu
  Dominant Resource Fairness), mecanisme de piață, noțiuni de teoria jocurilor.
- **2.** Analiza trace-urilor reale de joburi GPU (distribuția duratelor, a cerințelor, a
  comportamentului utilizatorilor).
- **3.** Simulator de planificare pe cluster cu mecanisme interschimbabile.
- **4.** Implementarea a 4-5 mecanisme și a unor utilizatori „strategici" (care își umflă cererile).
- **5.** Experimente pe trace-uri publice și, unde sunt disponibile, pe date de utilizare ale serverelor
  universității.
- **6.** Recomandări de politică pentru universitate.

### Date folosite (seturi publice)
- **Trace-uri de clustere GPU**
  - *Ce conține:* Alibaba cluster-trace-gpu-v2020 (joburi ML pe mii de GPU-uri), trace-urile Microsoft
    Philly.
  - *Cum se folosește în temă:* Trace-uri publice de joburi GPU (Alibaba, Microsoft Philly).
  - *Acces:* Liber (GitHub).
  - *Link:* github.com/alibaba/clusterdata, Microsoft Philly traces

### Validare
Gradul de utilizare, timpul de așteptare pe tipuri de joburi, indicatori de echitate (de exemplu indicele
Jain), robustețea la utilizatori strategici.

### Cunoștințe necesare
Simulare, optimizare, Python; teoria jocurilor se învață.
