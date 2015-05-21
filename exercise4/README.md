# Pflichtübung 4: Bundesnachrichtendienst [100 Punkte]

  * Ausgabe: 13.5.2015
  * Abgabe: 09.06.2015 23:59 Uhr (Bereitstellen auf GitHub)
  * Testat: 11.6.2015 (11:45 - 14:00 Uhr)


## Problembeschreibung

Sie erwachen aus einem tiefen Schlaf und merken, dass Metropolis doch nur ein Traum war. Schade, hatten Sie sich doch gerade mit dieser Welt angefreundet.Ihr Magen knurrt, Sie brauchen dringend wieder eine Anstellung, damit Sie Ihr Essen bezahlen können. Glücklicherweise sucht der Bundesnachrichtendienst (BND) im Augenblick dringend Informatiker.

Ihre Aufgabe besteht darin, eine Verschlüsselungssoftware für den BND zu entwickeln. Sie haben zwar den Verdacht, dass damit geheime Unterlagen zur Zusammenarbeit mit der NSA verschlüsselt werden sollen, ignorieren aber alle Skrupel und stürzen sich in Ihre Aufgabe.

Das Interface für die neue Verschlüsselungssoftware ist bereits vor Ihrer Einstellung beim BND definiert worden und befindet sich auf GitHub.

[Crypter.java](src/Crypter.java)

Sie müssen das Interface exakt so verwenden, wie es vorgegeben ist, verändern Sie es also auf keinen Fall. Andernfalls laufen Sie Gefahr, den Geheimdienst gegen sich aufzubringen und was dann passiert kennen Sie bereits sehr gut aus dem Kino.

Implementieren Sie das Interface `Crypter` und stellen Sie verschiedene Verschlüsselungsimplementierungen zur Verfügung und zwar für eine

  * Caesar-Verschlüsselung,
  * Substitutionschiffre und 
  * XOR-Verschlüsselung.

Erstellen Sie eine Factory-Klasse `CrypterFactory` mit der man die verschiedenen Verschlüsselungsimplementierungen erzeugen kann. Verwenden Sie für die Auswahl der Implementierung in der Factory eine _Enumeration_ `CrypterVerfahren` mit den Konstanten `CAESAR`, `SUBSTITUTION` und `XOR`.

Implementieren Sie die im Interface benutzte Ausnahmen `IllegalKeyException` und `IllegalMessageExcpetion` .

Verbergen Sie die Implementierung vor dem Verwender und erlauben Sie ihm nur den Zugriff auf die Factory, das Interface selbst und die Ausnahmen. Wählen Sie entsprechende Pakete gemäß Ihrem Schema.

**Tipp**: Denken Sie daran, keinen Code zu duplizieren und führen Sie gegebenenfalls weitere Klasse ein, um dies zu vermeiden.


### Caesar-Verschlüsselung

Implementieren Sie die _Caesar-Verschlüsselung_ mit Hilfe einer Klasse `CrypterCaesar`, die das Interface `Crypter` implementiert. Das Verschlüsselungsverfahren funktioniert wie folgt [Quelle Wikipedia](https://de.wikipedia.org/wiki/Caesar-Verschl%C3%BCsselung):

Ordnet man den Buchstaben des Alphabets Zahlen zu, wie beispielsweise in der folgenden Tabelle, so lässt sich mithilfe eines "Schlüsselbuchstabens" angeben, um wie viele Zeichen das Standardalphabet verschoben werden muss, um das Geheimalphabet zu erhalten:

    A B C D E F G H I J  K  L  M  N  O  P  Q  R  S  T  U  V  W  X  Y  Z
    1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26

Beispielsweise entspricht der Schlüssel "C" einer zyklischen Verschiebung um drei Zeichen. Folglich wird beispielsweise der Klarbuchstabe "R" als Geheimbuchstabe "U" verschlüsselt. Somit ergibt sich folgende Zuordnung:

    Klar:    A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
    Geheim:  D E F G H I J K L M N O P Q R S T U V W X Y Z A B C

Aus dem Klartext "CAESAR" wird bei Verschlüsselung mit dem Schlüssel "C" der Geheimtext "FDHVDU".

Im Falle der Caesar-Verschlüsselung enthält der Schlüssel nur ein einziges Zeichen, das den Verschiebefaktor angibt.


### Subsitutionschiffre

Implementieren Sie einen _Substitutionschiffre_ mit Hilfe der Klasse `CrypterSubstitution`, die das Interface `Crypter` implementiert. Das Verschlüsselungsverfahren funktioniert wie folgt [Quelle Wikipedia](https://de.wikipedia.org/wiki/Monoalphabetische_Substitution):

Ein Beispiel für eine monoalphabetische Verschlüsselung [Substitutions-Chiffre] ist das folgende Verfahren. Hierbei werden einzelne Buchstaben des Klartextes mithilfe des Schlüsselalphabets in einzelne Zeichen des Geheimtextes substituiert. 

    Klartext:   A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
    Schlüssel:  U F L P W D R A S J M C O N Q Y B V T E X H Z K G I

Aus dem Klartext "WIKIPEDIAISTINFORMATIV" wird nach Verschlüsselung der Geheimtext "ZSMSYWPSUSTESNDQVOUESH". Der Klartext lässt sich durch Entschlüsselung wieder aus dem Geheimtext rekonstruieren, indem man dort die Buchstaben in der zweiten Zeile durch die der ersten Zeile ersetzt. 

Im Falle der Substitutions-Chiffre enthält der Schlüssel genau 26 Zeichen, wobei jedes Zeichen (A-Z) nur ein mal vorkommen darf.


### XOR-Verschlüsselung

Implementieren Sie ein Verschlüsselung, die auf der Verknüpfung von Text und Schlüssel per XOR basiert. Die Implementierung nennen Sie bitte `CrypterXOR`. Das Verfahren funktioniert wie folgt: 

Bei der XOR-Verschlüsselung werden Klartext und Schlüssel per XOR miteinander verknüpft. Der Schlüssel kann ein beliebig langer Text sein. Wenn der Klartext länger als der Schlüssel ist, wird der Schlüssel einfach wiederholt. Die Zahlenwerte von Schlüssel und Klartext werden per XOR miteinander verknüpft. Die Entschlüsselung funktioniert genauso, indem wieder der verschlüsselte Text und der Schlüssel per XOR miteinander verknüpft werden. 

Beispielsweise würde beim Schlüssel "TPERULES" bei der Verschlüsselung folgendes passieren:

    Klartext:
        A  B  C  D  E  F  G  H  I  J  K  L  M  N  O  P  Q  R  S  T  U  V  W  X  Y  Z  
        1  2  3  4  5  6  7  8  9  10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 
    Schlüssel:
        T  P  E  R  U  L  E  S  T  P  E  R  U  L  E  S  T  P  E  R  U  L  E  S  T  P  
        20 16 5  18 21 12 5  19 20 16 5  18 21 12 5  19 20 16 5  18 21 12 5  19 20 16 
    Ergebnis:
        U  R  F  V  P  J  B  [  ]  Z  N  ^  X  B  J  C  E  B  V  F  @  Z  R  K  M  J  
        21 18 6  22 16 10 2  27 29 26 14 30 24 2  10 3  5  2  22 6  0  26 18 11 13 10 

Bei der Entschlüsselung wird der Schlüssel erneut per XOR auf den verschlüsselten Text angewendet:

    Verschlüsselter Text:
        U  R  F  V  P  J  B  [  ]  Z  N  ^  X  B  J  C  E  B  V  F  @  Z  R  K  M  J  
        21 18 6  22 16 10 2  27 29 26 14 30 24 2  10 3  5  2  22 6  0  26 18 11 13 10 
    Schlüssel:
        T  P  E  R  U  L  E  S  T  P  E  R  U  L  E  S  T  P  E  R  U  L  E  S  T  P  
        20 16 5  18 21 12 5  19 20 16 5  18 21 12 5  19 20 16 5  18 21 12 5  19 20 16 
    Ergebnis:
        A  B  C  D  E  F  G  H  I  J  K  L  M  N  O  P  Q  R  S  T  U  V  W  X  Y  Z  
        1  2  3  4  5  6  7  8  9  10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26  

Das Ergebnis entsteht durch das XOR-Verknüpfen der Zahlenwerte, z.B. wird "A" mit "T" verschlüsselt, indem man `1 ^ 20 = 21` rechnet. Die Entschlüsselung erfolgt dann umgekehrt, d.h. `21 ^ 20 = 1`, womit sich wieder ein "A" ergibt.

Beachten Sie, dass bei der XOR-Verschlüsselung der Schlüssel beliebig lang werden kann. Außerdem brauchen Sie zur Darstellung des verschlüsselten Textes mehr als 26 Buchstaben, nämlich 32. Nehmen Sie daher einfach noch die folgenden Zeichen mit auf: `@=0, [=27, \=28, ]=29, ^=30 und _=31`


## Test

Schreiben Sie automatisierte JUnit-Tests mit denen Sie die korrekte Funktionsweise der Implementierungen und der Factory-Klasse überprüfen. Legen Sie die Tests in ein anderes Paket als die Verschlüsselungsklassen. Denken Sie daran, auch die Ausnahmen zu testen.


## Entschlüsseln einer geheimen Botschaft

Entschlüsseln Sie nun eine geheime Botschaft und geben Sie den Klartext aus.

Die Botschaft lautet:

    RXZL_FO\W_UXX_S]KPOVQCTLTQZVG]^L_FXWWIYYVDQD\PQTQAEXAODQAXZRQBQEA[HLZW

Der Klartext wurde zuerst mit dem Schlüssel "POIUZTREWQMNBVCXYLKJHGFDSA" mit einer Subsitituionschiffre verschlüsselt, danach mit einer Caesar-Verschlüsselung mit dem Schlüssel "T" und abschließend durch eine XOR-Verschlüsselung mit dem Schlüssel "WINTERISCOMING".


## Abgabe

Laden Sie Ihre Quelltexte zum Testat auf GitHub hoch. Ihre Tests und die entschlüsselte, geheime Botschaft müssen Sie im Testat vorführen.
