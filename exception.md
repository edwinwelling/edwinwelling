Ik zou nog even terugkomen op de `assigment operator` (`T& operator=(T& right)`) en het exception safe zijn van die operator.

Op [https://godbolt.org/z/sYvoM9qKh](https://godbolt.org/z/sYvoM9qKh) vind je links boven twee tabbladen met de source van twee varianten voor het stukje dat met de exceptie in de `assigment operator`.

Eén variant is zoals ik jullie al het getoond (alleen met commentaar dat er een exceptie kan plaats vinden).

De tweede variant heeft een `try-catch` block. Waar volgens mij de vraag van Raoul over ging. 

Aan de rechterkant staat de assembly van beide varianten in een `diff`. Rond regel 90 van de assembly ze een het verschil. Op zich
is de assembly niet heel veel anders, op wat extra jumps en labels om de `rethrow` in de `try-catch` te regelen. Zoals ik het nu snel kan bekijken zal in er geen (meetbaar) verschil in `performance` zijn aangezien de extra assembly alleen maar in een exception situatie voordoet.

Dus de vraag is alleen levert de `try-catch` een betere communicatie richting een andere software developer? Is alleen een stukje
commantaar voldoende of vind je dat de try-catch meerwaarde bied? Ik weet het niet. Ik kan niet voor jullie spreken. Ik zelf ben van mening dat voor mij een commentaar regel prima werkt.

Bob kwam nog met de clean-coding rule om code voor zich zelf te laten spreken, door een methode te gebruiken. Die sitatie staat hier: 

[https://godbolt.org/z/nc138EEno](https://godbolt.org/z/nc138EEno)

Ook hier aan de rechterkant de assembly van de oude en de Bob-situatie. Door de extra method zijn er nu in het happy-patch steds een instructie of 10 extra nodig in de `assignment` actie. Eerlijk gezegd weet ik niet of die 10 extra instructies tot een meetbaar verschil zou kunnen leiden.

Een echt antwoord op de vragen kan ik dus net formuleren. Als reviewer zou ik prima uit de weg kunnen met een stukje 
commantaar en waarschijnlijk zou ik vragen om het swappie-idioom uit te werken.

Doe er je voordeel mee en discuseer het eens in je team en leer van elkaar.
