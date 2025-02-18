# Ce este React?
**React** este o bibliotecă JavaScript pentru construirea de interfețe de utilizator interactive.\
Prin **interfețe de utilizator (UI)**, ne referim la elementele pe care utilizatorii ș văd și cu care interacționează.

![image](./images/learn-react-components.avif)

Prin bibliotecă, înțelegem că **React** oferă funcții utile (API-uri) pentru a construi UI, dar lasă pe seama dezvoltatorului unde să folosească acele funcții în aplicații.

O parte din succesul lui **React** este că nu are o opinie despre celelalte aspecte ale construcției de aplicații.

Implicit, **React** este utilizat pentru crearea de **SPA (Single Page Applications)**, adică aplicații web care rulează într-o singură pagină HTML și actualizează conținutul dinamic, fără a necesita reîncărcarea paginii. 

Pentru a vedea mai multe tehnici de randare vizionați [acest video](https://youtu.be/Dkx5ydvtpCA?si=84VpseNmHIu-uNE0).
# Randarea UI
Pentru a înțelege cum funcționează **React**, avem nevoie mai întâi de o înțelegere de bază a modului în care browserele interpretează codul nostru pentru a crea (sau a reda) interfețe de utilizator (UI).

Când un utilizator vizitează o pagină web, serverul returnează browserului un fișier HTML care poate arăta astfel:

![img](./images/learn-html-and-dom.avif)

Browserul citește apoi HTML-ul și construiește așa numitul **Document Object Model (DOM)**
# Ce este DOM-ul ?
**DOM-ul** este o reprezentare sub formă de obiect a elementelor HTML. Acționează ca o punte între codul și interfața de utilizator și are o structură arborescentă cu relații părinți-copii.

![img](./images//learn-dom-and-ui.avif)

Putem folosi metodele **DOM** și **JavaScript**, pentru a asculta evenimentele utilizatorului și pentru a manipula **DOM-ul**
prin selectarea, adăugarea, actualizarea și ștergerea anumitor elemente de interfața. Manipularea **DOM-ului** ne permite nu numai să obținem anumite elemente, ci și să le schimbăm stilul și conținutul.
### *Analizează  fișierul `.html` din branch-ul `1_Manipulare_DOM_JS`*.
# HTML vs DOM
Dacă ne uităm la elementele **DOM** din instrumentele de dezvoltare ale browserului, observăm că **DOM** include elementul `<h1>`. **DOM-ul** paginii este diferit de codul sursă - sau cu alte cuvinte, fișierul HTML original creat.

![img](./images/learn-dom-and-source.avif)

Acest lucru se datorează faptului că HTML reprezintă conținutul inițial al paginii, în timp ce **DOM** reprezintă conținutul actualizat al paginii care a fost modificat de codul **JavaScript** scris.

Actualizarea **DOM-ului** prin simpla utilizare a **JavaScript** este foarte puternică, dar detaliată, anevoioasă și cere multe instrucțiuni. Ai de scris tot acest cod doar pentru a adăuga un element `<h1>` cu careva text:
```js
<script type="text/javascript">
  const app = document.getElementById('app');
  const header = document.createElement('h1');
  const text = 'Develop. Preview. Ship.';
  const headerContent = document.createTextNode(text);
  header.appendChild(headerContent);
  app.appendChild(header);
</script>
```
Pe măsură ce dimensiunea unei aplicații sau a unei echipe crește, poate deveni din ce în ce mai dificil să construiești aplicații în acest fel.

Cu această abordare, dezvoltatorii petrec mult timp scriind instrucțiuni pentru a spune computerului cum ar trebui să facă lucrurile. Dar nu ar fi frumos să descriem ceea ce vrem să arătăm și să lăsăm computerul să-și dea seama singur cum să actualizeze **DOM-ul**?
# Programare Imperativă vs Declarativă
Codul de mai sus este un bun exemplu de programare imperativă. Fiecare pas pentru cum ar trebui să fie actualizată interfața cu utilizatorul este descris. Dar când vine vorba de construirea de interfețe, o abordare declarativă este adesea preferată, deoarece poate accelera procesul de dezvoltare. În loc să fie nevoie să scriem metode a **DOM-ului**, ar fi util dacă dezvoltatorii ar fi capabili să declare ceea ce doresc să fie afișat (în acest caz, o etichetă `h1` cu careva text).

Cu alte cuvinte, programarea imperativă este ca și cum ai oferi bucătarului instrucțiuni pas cu pas despre cum să faci o pizza. Programarea declarativă este ca și cum ai comanda o pizza fără a fi îngrijorat de pașii necesari pentru prepararea acesteia. 🍕

**React** este o **bibliotecă declarativă** populară pe care o putem utiliza pentru a construi interfețe. În calitate de dezvoltator, putem spune lui React ce dorim să se întâmple cu interfața, iar React se va descurca singur cu pașii cum să actualizeze **DOM-ul** pentru noi.
# Începând cu React
### *Analizează  fișierul `.html` din branch-ul `2_Manipulare_DOM_React`*.
Pentru a utiliza **React** într-o formă foarte simplă într-un proiect nou creat, putem încărca două scripturi de pe un site web extern numit *unpkg.com*:\
*react*
: este biblioteca de bază **React**.\
*react-dom* 
: oferă metode specifice **DOM** care permite să utilizăm **React** cu **DOM**.

În loc să manipulăm direct **DOM-ul** cu **JavaScript** simplu, putem elimina metodele **DOM** pe care le-am utilizat anterior și să adăugăm `ReactDOM.createRoot()`, metodă de a obține un anumit element **DOM** și de a crea o rădăcină în care să vă afișăm componente **React**. Apoi, putem adăuga `root.render()`, metoda de a randa codul **React** în **DOM**. Acest lucru va spune **React** să randeze titlul nostru `<h1>` în elementul nostru cu id-ul `#app`.
# Ce este JSX?
**JSX** este o extensie de sintaxă pentru **JavaScript** care ne permite să descriem interfața într-o sintaxă familiară asemănătoare **HTML** ([exemple de transformare JSX->JS](@babel/plugin-transform-react-jsx)). Lucrul frumos despre **JSX** este că, în afară de respectarea a trei reguli **JSX**, nu trebuie să învățăm simboluri sau sintaxă noi în afara de **HTML** și **JavaScript**.

Browserele implicit nu înțeleg **JSX**, așa că avem nevoie de un compilator/transpilator **JavaScript**, cum ar fi **Babel**, pentru a transforma codul **JSX** în **JavaScript** obișnuit.
### Cele 3 reguli JSX despre care se menționa mai sus sunt:
1. Returnează un singur element rădăcină
2. Închide toate etichetele
3. scrim în **camelCase** ~~toate~~ majoritatea lucrurilor (excepție fac tag-urile `aria-*` și `data-*` care se scriu cu liniuță ca și în **HTML**)
   
Comparând codul **React** declarativ:
```js
<script type="text/jsx">
  const domNode = document.getElementById("app")
  const root = ReactDOM.createRoot(domNode);
  root.render(<h1>Develop. Preview. Ship.</h1>);
</script>
```
cu codul **JavaScript** imperativ din secțiunea anterioară:
```js
<script type="text/javascript">
  const app = document.getElementById('app');
  const header = document.createElement('h1');
  const text = 'Develop. Preview. Ship.';
  const headerContent = document.createTextNode(text);
  header.appendChild(headerContent);
  app.appendChild(header);
</script>
```
Putem începe să vedem cum utilizarea **React** permite reducerea a unei mulțime de cod repetitiv.

Aceasta și este exact ceea ce face **React**, este o bibliotecă care conține fragmente reutilizabile de cod care îndeplinesc sarcini pentru dezvoltator - în acest caz, actualizarea UI-ului.
# Concepte de bază React
Există trei concepte de bază ale React cu care va trebui să ne familiarizăm pentru a începe să construim aplicații **React**. Acestea sunt:
- Componente
- Props
- State

Interfețele utilizator pot fi împărțite în blocuri mai mici numite componente.
Componentele ne permit să construim fragmente de cod autonome și reutilizabile. Dacă ne gândim la componente ca fiind cărămizi LEGO, putem lua aceste cărămizi individuale și le combinăm împreună pentru a forma structuri mai mari. Dacă trebuie să actualizăm o parte din interfața de utilizare, putem actualiza componenta sau "cărămida specifică".

![img](./images/learn-components.avif)
Această modularitate permite codului nostru să fie mai ușor de întreținut pe măsură ce crește, deoarece putem adăuga, actualiza și șterge componenta specifică fără a atinge restul aplicației noastre.

Lucrul frumos despre componentele **React** este că sunt doar cod **JavaScript**. 
# Crearea Componentelor
În **React**, componentele sunt funcții. O componentă este o funcție care returnează elemente UI. În interiorul instrucțiunii `return` a funcției, putem scrie **JSX**.

Pentru a randa această componentă în **DOM**, o transmitem ca primul argument în metoda `root.render()`.

Careva reguli pentru crearea corectă a componentelor sunt:

- În primul rând, componentele **React** ar trebui să fie scrise cu majuscule pentru a le distinge de **HTML** simplu și **JavaScript**.
- Iar în al doilea rând, utilizăm componentele **React** în același mod în care folosim etichetele **HTML** obișnuite, cu paranteze unghiulare `<>`
### *Analizează  fișierul `.html` din branch-ul `3_Componente_React`*.
# Imbricarea componentelor
Aplicațiile includ de obicei mai mult conținut decât o singură componentă. Putem imbrica componentele **React** una în cealaltă, așa cum facem cu elemente HTML obișnuite. Putem imbrica componentele **React** în 
acest fel pentru a forma arbori de componente.

![img](./images/learn-component-tree.avif)

De exemplu, componenta `HomePage` de nivel superior poate conține un `Header`, un `Article` și o componentă `Footer`. Și fiecare dintre aceste componente ar putea avea, la rândul său, propriile componente copil și așa mai departe. De exemplu, componenta `Header` poate conține o componentă `Logo`, `Title` și `Nav`.

Acest format modular ne permite să reutilizăm componente în diferite locuri în aplicație.

### *Analizează  fișierul `.html` din branch-ul `4_Imbricarea_Componentelor`*.

# Afișarea datelor cu props
Până acum, dacă ar fi să reutilizăm componenta `<Header />`, ar afișa același conținut de ambele ori.

Dar dacă dorim să afișam texte diferite sau nu cunoaștem informația din timp, deoarece o obținem dintr -o sursă externă?

Elementele obișnuite HTML au atribute pe care le putem utiliza pentru a transmite informații care schimbă comportamentul acestor elemente. De exemplu, schimbarea atributului `src` al unui element `<img>` modifică imaginea care este prezentată. Modificarea atributului `href` al unei etichete `<a>` modifică destinația link-ului. 

În același mod, putem transmite informații ca proprietăți și componentele **React**. Acestea sunt numite **props**. Luăm de exemplu, posibilele variații ale unui buton:

![img](./images/learn-props.avif)

Similar cu o funcție **JavaScript**, putem proiecta componentele să accepte argumente personalizate (sau **props**) care modifică comportamentul componentei sau ceea ce este afișat în mod vizibil când este randat pe ecran. Putem transmite aceste elemente **props** de la componentele părinte la componentele copii.

În **React**, datele "curg" de sus în jos în arborele de componente. Acest lucru este denumit flux de date unidirecțional.

Pentru a utiliza valorile transmise ca **props** la afișare e necesar să utilizăm aceste variabile în **JSX**. Acest lucru se face cu acolade `{}`. Acestea sunt o sintaxă **JSX** specială care permite să scrim **JavaScript** obișnuit direct în marcajul **JSX**.

### *Analizează  fișierul `.html` din branch-ul `5_Props`*.

Ne putem gândi la acolade ca o modalitate de a intra în *„Tărâmul JavaScript”* în timp ce ne aflăm în *„Tărâmul JSX”*. Putem adăuga orice expresie **JavaScript** (ceva care se evaluează la o singură valoare) în interiorul acoladelor. De exemplu:
1. O proprietate a unui obiect:
   ```jsx
   function Header(props) {
    return <h1>{props.title}</h1>;
   }
   ```
2. Un șablon literal:
    ```jsx
    function Header({ title }) {
      return <h1>{`Titlul: ${title}`}</h1>;
    }
    ```
3. Valoarea returnată de o funcție:
    ```jsx
    function createTitle(title) {
      if (title) {
        return title;
      } else {
        return 'Default title';
      }
    }
 
    function Header({ title }) {
      return <h1>{createTitle(title)}</h1>;
    }
    ```
4. Sau operator ternar:
    ```jsx
    function Header({ title }) {
      return <h1>{title ? title : 'Default Title'}</h1>;
    }
    ```
Este obișnuit să avem date pe care trebuie să le afișăm ca o listă. Putem folosi metode ale array-ului pentru a manipula datele și pentru a genera elemente de UI care sunt identice ca stil, dar care conțin informații diferite.

Putem utiliza metode ca `array.map()` pentru a itera peste o listă și să folosim o funcție săgeată pentru a mapa o careva proprietate la un element din listă.

Dacă rulăm un astfel de cod, **React** ne va da un avertisment despre o cheie lipsă. Acest lucru se datorează faptului că **React** are nevoie de ceva pentru a identifica în mod unic elementele dintr-un array, astfel încât să știe ce elemente să actualizeze în **DOM**.

### *Analizează  fișierul `.html` din branch-ul `6_Randarea_Listelor`*.

# Gestionare de evenimente

Să explorăm modul în care **React** ne ajută să adăugăm interactivitate cu state și gestionatori de evenimente.

Pentru a face butonul să facă ceva atunci când este făcut un click, putem utiliza evenimentul `onClick`. În **React**, numele evenimentelor sunt camelCase. Evenimentul `onClick` este unul dintre multele evenimente posibile pe care le putem utiliza pentru a răspunde la interacțiunea utilizatorului. De exemplu, putem utiliza `onChange` pentru câmpurile de introducere (input-uri) sau `onSubmit` pentru formulare.

Putem defini o funcție care să *„gestioneze”* evenimentele ori de câte ori acestea sunt declanșate. Apoi, putem apela  această funcție, atunci când evenimentul `onClick` este declanșat.

### *Analizează  fișierul `.html` din branch-ul `7_Gestionarea_Evenimentelor`*.

# State și hook-uri
**React** are un set de funcții numite **hook-uri** ("cârlige"). **Hook-urile** ne permit să adăugăm componente logice suplimentare, cum ar fi state-ul. Ne putem gândi la state ca orice informație din interfața de utilizare care se modifică în timp, de obicei declanșată de interacțiunea utilizatorului.

![img](./images/learn-state.avif)

**Hook-ul React** folosit pentru a gestiona starea se numește: `useState()`.

Hook-ul returnează un array de 2 valori pe care putem să le accesăm și utiliza  interiorul componentei utilizând destructurarea array-ului. Primul element este valoarea de **state**, pe care o putem numi orice. Se recomandă să-i dăm un nume descriptiv, iar al doilea element este o funcție de actualizare a valorii. Putem denumi funcția de actualizare orice, dar este obișnuit să o prefixăm cu `set` urmat de numele variabilei de state pe care o actualizăm.

Spre deosebire **props** care sunt transmise componentelor ca parametru de funcție, **state-ul** este inițiat și stocat în interiorul unei componente. Putem transmite informațiile despre **state** componentelor copii ca **props**, dar logica pentru actualizarea stării ar trebui să fie păstrată în componenta în care a fost creată inițial starea.

### *Analizează  fișierul `.html` din branch-ul `8_State`*.