
## **VARIABILI**
```dart
String ill
String recover
String death
String earth
```
Stringhe contenenti il percorso dei png omonimi
##
```dart
List<Data> dataList
```
Lista che contiene tutti i dati del json del sito
##
```dart
String country
```
Stringa contenente il nome del paese da cercare. Di default è vuota
##
```dart
List<String> countries
```
Lista di stringhe che contiene i paesi inseriti dal metodo **_autocomplete()_**
##
```dart
TextEditingController text
```
Serve per modificare ciò che è stato scritto all'interno di un TextField
## **METODI**
```dart
Widget buildTextField()
```
Questo metodo costruisce un TextField, che ha un IconButton, che ha come icona una ImageIcon, una icona contenente un png, creato grazie alla classe AssetImage e alla varibile _earth_. Quando il bottone viene cliccato, imposta le variabile  _country_ e _text_ vuote.

Quando viene cambiato il paese inserito all'interno, va a richiamare il metodo
**_autocomplete(country)_**.

Quando il paese inserito è inviato, alla variabile _country_ viene impostato il paese cercato.
##
```dart
void autocomplete(String country)
```
E' un metodo che serve per l'autocompletamento, infatti viene chiamato ogni volta che si sta inserendo il nome di un paese nel TextField. 

La prima cosa che fa è svuotare la lista _countries_, poi crea una variabile chiamata _endIndex_ a cui viene applicato un valore pari alla lunghezza del nome del paese inserito.

Nel caso in cui il nome del paese non sia vuoto, allora va a confrontare tutti i paesi all'interno del _dataList_.

Questo metodo non prende tutto il nome del paese, ma solo le lettere comprese tra 0 e _endIndex_, e nel caso in cui la porzione del nome del paese sia uguale al nome inserito nel TextField, allora il nome intero del paese viene aggiunto all'interno della lista _countries_
##
```dart
Widget buildList()
```
Questo metodo viene chiamato solo nel caso in cui la lista _countries_ non sia vuota.

Quando viene richiamato costruisce una ListView che contiene una GestureDetector,  con all'interno i nomi dei paesi contenuti nella lista _countries_.

E' stato utilizzato un GestureDetector, così che quando il nome di un paese viene cliccato, allora alle variabili _country_ e _text_ vengono assegnati il nome del paese.

Infine la lista _countries_ viene svuotata, così che l'autocompletamento della parola  non sia più visibile e la tastiera viene chiusa
##
```dart
Widget buildCountry()
```
Questo metodo serve a mostrare il nome del paese che è stato cercato.
			
Nel caso in cui il nome sia vuoto, allora viene scritto "All Countries"

Nel caso in cui il nome del paese sia inesistente, allora viene scritto "This country doesn't exists"
##
```dart
Widget buildCases()
Widget buildDeaths()
Widget buildRecovered()
```
Questi metodi servono a mostrare gli infetti, le morti e i guariti all'interno di un container.

Richiamano i metodi **_buildText(String type)_** e **_buildInfo(String type)_**
##
```dart
Widget buildText(String type)
```
in base alla stringa "type", mostra una stringa con scritto "Cases", "Deaths"  oppure "Recovered" e al di sotto della stringa, i png _ill.png_, _deaths.png_  oppure _recovered.png_
##
```dart
Widget buildInfo(String type)
```
In base alla stringa _type_, vengono mostrati dei valori ricavati grazie all'utilizzo del metodo 
**_getTotal(String type, String country)_**
##
```dart
int getTotal(String type, String country)
```
Serve a ricavare i valori degli infetti, delle morti e dei guariti, in base al paese 
inserito. Per fare ciò, abbiamo bisogno della posizione del paese selezionato, all'interno
della lista _dataList_, quindi viene utilizzato un metodo di supporto, chiamato **_getIndex(String country)_**

Nel caso in cui l'indice sia pari a -2, allora il paese inserito non esiste, se l'indice è pari a -1 allora bisogna ricavare i dati di tutti i paesi, mentre se l'indice ha un numero diverso da -2 e -1, si ricavano i dati di quel determinato paese
##
```dart
int getIndex(String country)
```
l'indice di default è -2, se l'argomento country è vuoto, allora l'index viene posto a -1, mentre se il paese inserito esiste, la variabile index assume un valore pari alla posizione di quel paese all'interno della lista _dataList_. 
Infine index viene restituito.