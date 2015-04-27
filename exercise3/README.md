# Pflichtübung 3: Metropolis [100 Punkte]

  * Ausgabe: 27.4.2015
  * Abgabe/Testat: 7.5.2015 (11:45 - 14:00 Uhr)

**Achtung Livetestat**: Am 7.5 wird die Lösung zu diesem Blatt testiert _und_ ein Live-Übung mit Testat stattfinden.  Sie wird auf diesem Übungsblatt basieren. Sie müssen ausgehend von Ihrer mitgebrachten Lösung eine zusätzliche Aufgabe bearbeiten und während der Laborstunde abgeben. Die 100 Punkte entfallen auf beide Teile - Bearbeitung dieses Übungsblattes und der Live-Übung.


## Problembeschreibung

Irgendwie ist es Ihnen gelungen, aus Rapture zu entkommen, wobei die Flucht sehr anstrengen war. Völlig erschöpft fallen Sie in einen tiefen, traumlosen Schlaf. Als Sie erwachen, befinden Sie sich in einer düsteren Stadt namens Metropolis, die Ihnen seltsam bekannt und doch fremd vorkommt. Sie sind sich nicht sicher, ob es sich um einen Traum oder die Realität handelt.

Metropolis zeichnet sich zum einen durch sein komplexes Steuersystem und zum anderen durch die Tatsache aus, dass es neben Menschen auch Mutanten als Einwohner gibt. Dank der unermüdlichen Arbeit des berühmten Professor Xavier, leben Menschen und Mutanten mehr oder weniger harmonisch als Einwohner von Metropolis zusammen, wobei sich einige Mutanten als Schurken, andere als Superhelden verdingen. Jeder Einwohner hat einen Namen und ein Einkommen (in Metro-Dollar).


### Menschen

Bei den Menschen gibt es zwei wichtige Gruppen: die normalen _Bürger_ und die _Richter_. Die Richter haben die Aufgabe Schurken zu verurteilen (`verurteilen`), die Bürger gehen anderen Arbeiten nach. Leider sind einige der Richter korrupt und sprechen jeden Schurken frei. Dafür sind die nicht korrupten Richter gnadenlos und verurteilen (ganz Ihrem Vorbild Judge Dredd folgend) jeden Schurken. Unabhängig von ihrer Tätigkeit haben alle Menschen ein Alter.


### Mutanten

Die Mutanten sind unsterblich und haben daher auch kein Alter, denn Unsterbliche interessiert diese Information nicht. Dafür hat jeder Mutant eine charakteristische Mutation, die ihn auszeichnet. Die Mutationen werden einfach durch deren Namen (`String`) bezeichnet.

Es gibt zwei Arten von Mutanten: _Superhelden_ und _Schurken_. Die Superhelden haben eine oder mehrere Superkräfte (`Superkraft`) und können mit Schurken kämpfen (`kaempfe`), wobei der Ausgang des Kampfes von der Superkraft abhängt. Ein Superheld kann einen Kampf entweder gewinnen oder verlieren. 

Jeder Schurke hat eine einzige Superkraft (`Superkraft`), die seine Schwäche ist. Trifft er auf einen Superhelden, der diese Kraft besitzt, verliert der den Kampf. Besitzt der Superheld die Kraft nicht, gewinnt der Schurke. Schurken können ebenfalls einen Kampf mit einem Superhelden initiieren (`kaempfe`) und den Kampf nach denselben Regeln genauso entweder verlieren oder gewinnen.

Schurken können sich in Schurkensyndikaten (`Syndikat`) zusammenschließen. Ein Syndikat hat einen Namen (z.B. "The Fantastic 5") und eine beliebige Anzahl von Schurken, die sich in dem Syndikat organisieren. Ein Schurke kann durchaus in mehreren Syndikaten organisiert sein, was aber wegen des Steuersystems (siehe unten) nicht von vielen Schurken wahrgenommen wird. 


### Unternehmen

Weiterhin gibt es in Metropolis noch Unternehmen. Diese sind entweder als _Personengesellschaften_ oder _Kapitalgesellschaften_ organisiert. Die Personengesellschaften haben eine beliebige Anzahl von Bürgern als Inhaber, die Kapitalgesellschaften eine beliebige Anzahl als Gesellschafter. Jedes Unternehmen hat einen Namen und einen Gewinn (in Metro-Dollar).

Mutanten und Richter sind von der Teilhabe an Unternehmen ausgeschlossen. 


### Steuern

Es gibt drei verschiedene Steuern in Metropolis:

  * __Körperschaftsteuer__: Eine lineare Steuer in Höhe von 15%. Sie muss nur von Kapitalgesellschaften und Schurken-Syndikaten abgeführt werden. Bei den Kapitalgesellschaften bemisst sie sich nach dem Gewinn, bei den Syndikaten nach der Summe der Einkommen aller in dem Syndikat organisierten Schurken. Da Schurken auch noch Einkommensteuer bezahlen müssen, werden sie doppelt belastet - was aber wegen ihres schlechten Charakters alle anderen Bürger von Metropolis vollkommen OK finden.
  * __Einkommensteuer__: Eine progressive Steuer auf das Einkommen von Bürgern, Personengesellschaften und Schurken. Die Superhelden und Richter sind von der Einkommensteuer befreit, weil sie soviel Gutes für Metropolis tun. Die Steuer wird wie folgt berechnet:
    * die ersten 20.000 Metro-Dollar werden mit 8% besteuert
    * die nächsten 40.000 Metro-Dollar werden mit 15% besteuert
    * die nächsten 60.000 Metro-Dollar werden mit 25% besteuert
    * jeder weitere Metro-Dollar wird mit 40% besteuert
  * __Gewerbesteuer__: Eine lineare Steuer von 15% auf den Gewinn aller Unternehmen, unabhängig von der Rechtsform. Natürliche Personen, d.h. Schurken und Bürger müssen diese Steuer _nicht_ abführen. Personengesellschaften haben noch eine Steuerermäßigung von 800 Metro-Dollar auf den Betrag der Steuer (nicht die Bemessungsgrundlage). Die Steuer kann hierbei niemals negativ werden.
 
 Die folgende Tabelle zeigt einige Beispiele für die Berechnung der _Einkommensteuer_.

Einkommen | Steuer
---------:|-------:
10000     | 8000
20000     | 16000
30000     | 17500
40000     | 19000
50000     | 20500
60000     | 22000
80000     | 27000
100000    | 32000
120000    | 37000
140000    | 45000
150000    | 49000
200000    | 69000

Die einzelnen Steuern können nicht gegeneinander verrechnet werden, sondern werden einfach aufsummiert.

Einkommen, Gewinne und Steuern werden grundsätzlich in ganzen Metro-Dollar gemessen. Es gibt keine Untereinheit, d.h. es gibt _keine_ Metro-Cent.


### Finanzamt

Das _Finanzamt_ von Metropolis kennt alle Steuerpflichtigen (Bürger, Unternehmen und Syndikate), aber auch nur diese, und kann jederzeit die gesamten Steuereinnahmen für Metropolis berechnen.


## Aufgabe

### UML-Diagramm

Erstellen Sie ein Klassendiagramm, das die im Text genannten Entitäten, Eigenschaften und Methoden in einem objektorientierten Modell abbildet. Lesen Sie den Text sorgfältig, um keine Klassen oder Interfaces bzw. Beziehungen zu vergessen.

Nutzen Sie Vererbung, abstrakte Klassen und Interfaces, um keine Information und kein Verhalten mehr als einmal abbilden zu müssen. Sie werden höchstwahrscheinlich noch eigene, über die im Text genannten Entitäten herausgehende Abstraktionen einführen müssen, um das Design zu vervollständigen

Teilen Sie die entworfenen Strukturen in verschiedene Pakete auf, und wählen Sie sinnvolle Sichtbarkeitsattribute.

**Abgabe:** Erzeugen Sie ein PDF-Dokument von Ihrem UML-Diagramm und bringen Sie es *ausgedruckt* zum Testat mit.
