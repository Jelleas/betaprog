# Statistiek #

Als er een onderdeel is dat studenten van verschillende opleidingen verbindt is het wel de 
vrees voor (het gebrek aan kennis over) statistiek. En toch is het in elke wetenschappelijke 
discipline een cruciaal onderdeel omdat het de sleutel is tot het trekken van conclusies uit 
verzamelde gegevens. Wat is de 'waarheid' die verborgen ligt in de data en hoe kunnen 
verschillende hypotheses tegen elkaar afgewogen worden. In deze module zullen we aan de 
hand van een verzonnen casus een paar van de meest voorkomende technieken bekijken.

![](ExampleDenemarken.png){:.inline}{: style="width:35%"}

**De casus:** In Denemarken is een onderzoeksgroep gaan bestuderen of de lengte van volwassen 
vrouwen gecorreleerd is het het inkomens van hun ouders toen ze op de lagere school zaten. 
De inkomenscategorieen van ouders lopen van 0(zeer arm) tot 10(zeer rijk) en in elke categorie 
zijn random een aantal vrouwen geselecteerd van wie de lengte is gemeten. De data is weergegegeven 
in de grafiek hiernaast. Een deel van de onderzoekers vindt dat de data suggereert dat er een 
duidelijk lineair verband te zien is terwijl een ander deel van hun collega's vindt dat er 
helemaal geen afhankelijkheid is. De geobserveerde lichte afhankelijkheid is gewoon het resultaat 
van de fluctuaties in de lengte van vrouwen die in de steekproeven mee genomen zijn. 

We gaan in deze module na een paar korte inleidende oefeningen proberen te achterhalen welke 
conclusies we kunnen trekken: is er nou wel of niet een afhankelijkheid ?
 
## [1] De normaalverdeling in de natuur 

### Theorie: de normaalverdeling en het effect van het aantal metingen

In de natuur komt overal variatie voor: de lengte van mensen in een land, het aantal 
eitjes van een zeepaardje of het gewicht van apen in een populatie om er maar een paar 
te noemen. De afwijkingen van het gemiddelde wordt voor vaak beschreven volgens de 
zogenaamde normaalverdeling:

$$ f(x,|\mu,\sigma) = \frac{1}{\sigma\sqrt{2\pi}} exp^{-\frac{1}{2}\left( \frac{x-\mu}{\sigma} \right)^2}$$

![](ExampleLengte.png){:.inline}{: style="width:35%"}

Deze verdeling, ook wel de Gaussische distributie genoemd, beschrijft wat de relatieve frequentie 
is waarmee waarde $$x$$ voorkomt in de populatie van metingen. Het prettige aan deze verdeling is 
dat hij gekarakteriseerd wordt door maar twee parameters: het gemiddelde ($$\mu$$) en de maat 
voor de spreiding ($$\sigma$$). Er geldt dat ongeveer 68%(95%) van de waarden in het gebied 
$$\mu \pm 1(2) \sigma$$ liggen.

De lengte van mannen (vrouwen) in Nederland wordt bijvoorbeeld beschreven door een 
normaalverdeling met een gemiddelde = 184.0 (170.6) cm en sigma = 7.0 (6.5) cm. De 
(genormeerde) grafieken van de twee verdelingen staan in grafiek. Dit betekent dat 
34% van de mannen langer is dan 191 cm en dan 2.5% van de vrouwen kleiner is dan 
157.6 cm.

### Python: trekken van random getallen uit een normaalverdeling 

We hebben eerder gezien hoe je een random getal trekt in Python tussen 0 en 1. Het is ook mogelijk 
om een random getal te trekken uit een bepaalde verdeling. Omdat de normaalverdeling zo'n prominente 
plek inneemt is er een standaard functie in Python. 

{: .language-python}
    gemiddelde = 170.6
    breedte = 6.5
    x = numpy.random.normal(gemiddelde,breedte)

Als je dit heel vaak herhaalt zullen de waardes van $$x$$ verdeeld zijn volgens de rode grafiek 
hierboven.

### opdracht 1: verdeling lengtes van alle vrouwen.

Schrijf een programma `Statistiek1.py()` waarin je 100.000 random getallen trekt uit de 
normaalverdeling die de lengte van vrouwen in Nederland beschrijft. Maak een grafiek van 
al deze random lengtes. Gebruik hiervoor een histogram met bins die elk een breedte van 
0.5 cm hebben. Hou bij het trekken van de random lengtes welk percentage vrouwen een lengte hebben 
die meer dan 2 sigma boven het gemiddelde liggen en dus langer zijn dan 183.6 cm. Print 
deze fractie met 3 decimalen nauweurigheid.

## [2] Steekproeven (metingen) en nauwkeurigheid

In de echte wereld kunnen we nooit alles weten. We kunnen niet van elke vrouw in Nederland 
precies achterhalen hoe lang ze is, net zoals Maurice de Hond niet van elke Nederlander weet 
op welke politieke partij hij of zij zal stemmen. We kunnen wel met behulp van steekproeven 
proberen een idee te krijgen van de hele populatie: we bepalen de lengtes van een groep 
vrouwen of de politieke voorkeuren van een groep Nederlanders en maken daarmee een schatting 
van de eigenschappen van de volledige populatie.

Hoe groter de steekproef is, hoe groter de nauwkeurigheid van de schatting en dus een kleinere 
fout (onzekerheid). We gaan dit onderzoeken door met behulp van de computer nep-steekproeven 
te nemen uit de oorspronkelijke distributie en te kijken hoe goed de gemiddelde lengte van een 
kleine groep representatief is voor die van de hele populatie. 

### opdracht 2: impact van meer metingen op de nauwkeurigheid

Schrijf een programma `Statistiek2.py` die uitrekent welke fractie van steekproeven meer dan 5 cm 
afwijkt van het echte gemiddelde. Doe dit voor $$N=2,3,5,10,100$$.

  - Trek N random waardes uit de oorspronkelijke verdeling: een steekproef
  - Bepaal voor elke steekproef het gemiddelde uit van de lengtes van de vrouwen in die 
      groep en bewaar die
  - Herhaal dit voor een groot aantal steekproeven (100.000 bijvoorbeeld)
  - Hou bij in hoeveel steekproeven het gemiddelde meer dan 5 cm afwijkt 
    van het `echte` gemiddelde. (170.6 cm).
    Let op: we bedoelen hier zowel groter dan 175.6 cm en kleiner dan 165.6 cm.
              
Print de fractie in procenten en gebruik 3 decimalen:
{: .language-python}
    Fractie afwijkende steekproeven voor N=2: x.xxx procent 
    Fractie afwijkende steekproeven voor N=5: x.xxx procent 
    ...

Het is zeer inzichtelijk om de distributies van de gemiddeldes te bekijken voor de verschillende keuzes 
van de steekproefgroottee. Gebruik hiervoor de histogram methode. Kies zelf een handige bin-grootte.

**Conclusie:** Hoe groter de steekproef hoe beter je de 'echte' waarde benadert. Dat klinkt logisch, 
want het  maakt nogal uit of Maurice de Hond 10 mensen hun politieke voorkeur vraagt of 10.000. Voor 
elk getal, meting of grafiek die je ziet in de rest van je leven moet je je goed afvragen wat de 
onzekerheid op die schatting is. Een getal zonder foutmarge kan je niet op waarde schatten. Hoe 
kleiner de fout/onzekerheid, hoe belangrijker de meting is en hoe 'zwaarder' je de meting moet 
meewegen als je verschillende resultaten naast elkaar legt en een conclusie probeert te trekken.

## [3] Parameters van je model bepalen uit een serie metingen: fitten

Om de onderliggende fenomenen van verschijnselen bloot te leggen en mogelijke verbanden te 
achterhalen verzamelen wetenschappers data. Dat kan de massa van het Higgs boson zijn, de 
vervaltijd van radioactieve elementen, maar ook het aantal kinderen in een gezin als functie 
van de gemiddelde lengte van de ouders of je reistijd per fiets naar de universiteit als 
functie van het moment op de dag. Elk meetpunt komt met een onzekerheid die de precisie 
aangeeft. Zoals we al gezien hebben: hoe kleiner de fout, hoe nauwkeuriger de meting en 
hoe 'belangrijker' het meetpunt is in het bepalen of dat date met je model overeenkomen. 
Als je eenmaal een goede beschrijving hebt gevonden kan je daarmee vervolgens voorspellingen 
doen en tegelijkertijd werken aan een interpretatie van de reden van de correlatie.

We gaan in dit stuk van de module de de resultaten van een onderzoek in detail bestuderen: de 
lengte van vrouwen als functie van het inkomen van haar ouders. Is er nou wel of niet verband 
te zien in de data? Om dat te bestuderen moeten we eerst van de verschillende hypotheses (wel 
of niet een verband) de parameters en hun onzekerheid bepalen. Het is inzichtelijk om de discussie 
over de manier waarop je de beste waarde van je parameters bepaald (en de onzekerheid) te voeren 
aan de hand van een voorbeeld. 

### Voorbeeld: Bepalen kookpunt van alcohol tijdens het prakticum

Een groep studenten heeft tijdens een prakticum het kookpunt van alcohol proberen 
te bepalen. De studenten hadden alleen genoeg tijd om 1 keer een meting te doen. Er 
waren zes thermometer die de temperatuur tot op 1 graad Celcius nauwkeurig konden bepalen 
en vier die dat konden met een hogere precisie, namelijk 0.5 graden. De lijst met 
metingen is de volgende:

groepnummer (x)                 |  1   |  2   |  3   |  4   |  5   |  6   |  7   |  8   |  9   | 10 
gemeten kookpunt (y)            | 78.2 | 80.2 | 78.7 | 78.9 | 77.5 | 79.7 | 78.1 | 79.0 | 79.6 | 78.4 
onzekerheid ($$\sigma$$, fout op y)  |  1   |  1   |  1   |  0.5 |  1   |  1   |  0.5 |  0.5 |  1   | 0.5


#### voorbeeld [stap 1]: Model en doel van de exercitie
In dit geval is het 'model' dat we hebben een vlakke lijn. Het kookpunt van alcohol is een 
natuurconstante en hangt niet af van et groepje studenten dat de meting verricht. Eigenijk 
proberen we dus de waarde van het kookpunt van alcohol te bepalen dat het best in overeenstemming 
is met de gemeten punten. Het is duidelijk dat 78$$^\circ$$ een betere schatting is dan 70$$^\circ$$ 
en 79$$^\circ$$ een betere dan 81$$^\circ$$, maar wat is nou precies de 'beste' waarde? Kortom: 
wat is het gemiddelde van de hele klas?

#### voorbeeld [stap 2]: Een maat voor 'hoe goed' het model de data beschrijft: $$\chi^2$$: 

Om de 'beste' waarde te vinden hebben we een maat (metriek) nodig die de *goedheid* van 
de fit beschrijft. We doen dat hier met de zogenaamde $$\chi^2$$-maat: de som van de 
gemiddelde afwijking van de meetpunten tot het model gewogen met hun fout. Voor elk 
punt bepalen we de afstand van de meting (uitgedrukt in de meetfout op het punt) tot 
de waarde die het model voorspelt op die plek. De som die afwijkingen voor elk meetpunt 
noemen we de $$\chi^2$$.

Iets formeler:
$$\chi^2(\vec{\alpha}) = \sum_{i~ {\rm (datapunten)}}  \left(\frac{  y_i - f(x_i|\vec{\alpha}) }{\sigma_i}\right)^2$$

In deze uitdrukking is $$\vec{\alpha}$$ de vector met de parameters die je gebruikt in je
model. Voor elke keuze van de parameters in je model verandert de afstand van elk meetpunt 
tot je model en krijg je dus een nieuwe $$\chi^2$$. Ter volledigheid: de $$\chi^2$$ is 
gewoon een getal. In ons model is het model simpel. Er is meer 1 vrije parameter, namelijk 
het kookpunt van alcohol en ons model kunnen we beschrijven als $$f(x) = \alpha$$, 
met $$\alpha$$ een constante.

#### voorbeeld [stap 3]: De beste waarde van de model-parameters vinden

In de fitprocedure zoeken we naar de waarde van de parameters in je model die
de kleinste $$\chi^2$$ oplevert omdat met die waarde van de parameters de 
meetpunten het dichtst bij het model in de buurt liggen. Met behulp van de computer 
gaan we verschillende waardes van $$\alpha$$ proberen en voor elk de 
$$\chi^2$$ uitrekenen.
 
Als we bijvoorbeeld als hypothese $$\alpha=78.0$$ nemen dan hoort daar de 
volgende $$\chi^2$$ bij:
$$
\begin{eqnarray}
   \chi^2(\alpha=78.0)&=&    
   \tiny{
   \left( \frac{(78.2-78.0)}{1.0} \right)^2+
   \left( \frac{(80.2-78.0)}{1.0} \right)^2+
   \left( \frac{(78.7-78.0)}{1.0} \right)^2+
   \left( \frac{(78.9-78.0)}{0.5} \right)^2+
   \left( \frac{(77.5-78.0)}{1.0} \right)^2}\\
   &~& 
   \tiny{+
  +\left( \frac{(79.7-78.0)}{1.0} \right)^2+
   \left( \frac{(78.1-78.0)}{0.5} \right)^2+
   \left( \frac{(79.0-78.0)}{0.5} \right)^2+
   \left( \frac{(79.6-78.0)}{1.0} \right)^2+
   \left( \frac{(78.4-78.0)}{0.5} \right)^2
   }\\
   &=&19.0
\end{eqnarray}
$$

Je kan nu verschillende waardes van $$\alpha$$ proberen en voor elk de $$\chi^2$$
berekenen. De distributie is getekend in de rechterplot hieronder. Er is een
duidelijk minimum zichtbaar en de waarde van $$\alpha$$ waarvoor de $$\chi^2$$ 
minimaal is noemen we $$\alpha_{\rm best}=78.2$$.

#### voorbeeld [stap 4]: De onzekerheid op de parameters in je model

Elke waarde van je parameters die anders is dat $$\alpha_{\rm best}$$ zal de waarde
van de $$\chi^2$$ veranderen (die wordt groter wat een slechtere overeenkomst
met de data betekent). Het verschil tussen de waarde van de $$\alpha$$ waarbij
de $$\chi^2$$ precies 1 unit toeneemt en $$\alpha_{\rm best}$$ noemen we de
onzekerheid op $$\alpha$$. Dit wordt vaak omschreven als $$\Delta \alpha$$. 
Bij het berekenen van de $$\chi^2$$ zien we dat er is het gebied is $$ 78.5 < \alpha <78.9$$ 
waarvoor de $$\chi^2$$ minder dan 1 unit verschilt van $$\chi^2_{min}$$. Het resultaat 
van de fit, en dus het result van de gecombineerde schattig van het kookpunt van alcohol 
door de hele groep  studenten samen wordt gegeven door:

   Kookpunt alcohol = $$78.2 \pm 0.2 ^\circ C$$
   
**Let op:** Hoewel we hier aannemen dat de fout in $$\alpha$$ symmetrisch is hoeft dat niet
altijd het geval te zijn. Evalueer dus altijd de negatieve en positieve fout afzonderlijk 
door te kijken hoe de $$\chi^2$$ verandert als je de parameters respectievelijk kleiner en 
groter maakt.

#### voorbeeld [stap 5]: de bijbehorende plots

![](FitExampleWebsite.png){: style="width:90%"}


### opdracht 3: Gemiddelde lengte vrouwen in Denemarken

In Denemarken is een onderzoeksgroep gaan onderzoeken of de lengte van vrouwen 
gecorreleerd is het het inkomens van hun ouders toen ze een peuter waren.

Inkomenscategorie(x)        |  1   |  2   |  3   |  4   |  5   |  6   |  7   |  8   |  9   | 10 
gemiddelde lengte (y)       | xx.x | xx.x | xx.x | xx.x | xx.x | xx.x | xx.x | xx.x | xx.x | xx.x 
onzekerheid (fout op y)     |  4   |  4   |  2   |  2   |  2   |  2   |  2   |  2   |  4   |  4

Er is gekozen voor 10 categorieen en hoewel er geprobeerd is zoveel mogelijk gelijke aantallen 
vrouwen per categorie op te nemen in de studie is het aantal vrouwen met ouders in de extremen 
van de inkomsten van de ouders (erg rijk en erg arm) helaas beperkt. Dit is duidelijk door de 
grotere fout op de schatting van de gemiddelde lengte.

Schrijf een programma `Statistiek3.py()` waarin je het gemiddelde vindt van de lengte van vrouwen 
in Denemarken door een fit te maken aan de hierboven gegeven data. Volg hierbij de stappen in 
het voorbeeld over het maten van het kookpunt van alcohol zoals hierboven is besproken. Zorg dat 
je programma de data (met fouten) op het scherm weergeeft en ook de beste waarde van de fit die 
je gevonden hebt. Dus net zoals de linkerplot in het voorbeeld hierboven. Gebruik voor het 
plotten van de data met fouten de Python functie `plt.errorbar(x,y, yerr=yerror)`. Zoek op internet 
op hoe je deze functie moet gebruiken. 

Print je resultaat, met 1 decimaal, op de volgende manier naar het scherm:
{: .language-python}
    De fit (vlakke lijn) geeft een gemiddelde lengte van xxx.x cm


## [4] Een nieuwe hypothese: fitten van een lineaire afhankelijkheid

Een vlakke lijn fitten is alleen toepasselijk als er geen afhankelijkheid is tussen de variabelen. 
In de meeste gevallen is dat wel het geval: hoogte zeeniveau als functie van de tijd (sinus), aantal 
vervallen van een radioactief element (exponent) of de snelheid van planeten als functie van hun afstand 
tot de zon (wortel). Ook in die gevallen volgen we hetzelfde procede: varieer de parameters tot de 
$$\chi^2$$ minimaal is. Het fitten van een model aan metingen is een standaard procedure die je als 
onderzoeker vaak tegen zult komen. Hoewel we in deze cursus deze functionaliteit en alle bijbehorende 
details zullen gebruiken door gebrek aan tijd willen we hier toch een voorbeeld geven waarin 
je ziet hoe dat in de praktijk gaat.

Iemand in de onderzoeksgroep heeft geopperd dat er welleens een (lineair) verband zou kunnen zijn tussen 
de lengte van mensen en het inkomen van hun ouders. Dat zou verschillende oorzaken kunnen hebben. Dat is 
voor later. De eerste stap in het onderzoek is om eerst te bekijken of er uberhaupt een verband is. We 
gaan proberen een 


#### Fitten in Python: rechte lijn (1 vrijheidsgraad)

    # import the module that contains the fit-tool
    from scipy.optimize import curve_fit

    # Define our model. In our case a constant function: f(x) = a 
    def MyFitFunction(x, a):
        return a

    # define data and errors
    L_data_x       = [1,2,3,4,5,6,7,8,9,10]
    L_data_y       = [xx,xx,xx,xx,xx,xx,xx,xx,xx,xx]
    L_data_y_error = [4,4,2,2,2,2,2,2,4,4]
    
    popt, pcov = curve_fit(MyFitFunction, L_data_x, L_data_y, None, L_data_y_error)
    print "Best value: f(x) = %5.2f" % popt[0]

De laatste regel blijft nu nog magie, maar *popt* is een lijst met de 'optimale' 
parameters van de functie die je aan de data hebt gefit. In ons geval is dat maar 
1 parameter omdat we een constante functie aanhouden als model. Je kan zelf in de 
documentatie opzoeken hoe je zelf uit *pcov* de onzekerheid op de parameter kan bepalen. 

#### Fitten in Python: lineair verband (2 vrijheidsgraden)

Als je nu in plaats van een constante functie een lineaire functie wilt fitten 
$$f(x) = ax+b$$ en je wilt de resultaten printen dan hoef je maar op 2 plekken een 
verandering aan te brengen. Op de plek waar je de functie die je fit definieert en 
op de plek waar je de resultaten print naar het scherm. Zoek ze maar op.

    # import the module that contains the fit-tool
    from scipy.optimize import curve_fit

    # Define our model. In our case a constant function: f(x) = a*x + b 
    def MyFitFunction(x, a, b):
        return a * x + b

    # define data and errors
    L_data_x       = [1,2,3,4,5,6,7,8,9,10]
    L_data_y       = [xx,xx,xx,xx,xx,xx,xx,xx,xx,xx]
    L_data_y_error = [4,4,2,2,2,2,2,2,4,4]
    
    popt, pcov = curve_fit(MyFitFunction, L_data_x, L_data_y, None, L_data_y_error)
    print "Best value: f(x) = %5.2f * x + %5.2f" % (popt[0], popt[1])

### opdracht 4: Maak een fit aan de data met behulp van lineair verband

Schrijf een programma `Statistiek4.py()` waarin je zowel een rechte lijn als een lineair 
verband fit aan de data. Gebruik hiervoor de tools in Python zoals hierboven beschreven 
en plot zowel de data als beide functies op het scherm. Gebruik als voorbeeld de plot 
bovenaan de pagina, maar zorg dat de waardes van $$a$$, $$b$$ en $$c$$ netjes op het 
scherm verschijnen. 

## [5] Hypothese testen

Een deel van de onderzoekers vindt dat de data suggereert dat er een lineair verband te 
zien is in de data terwijl een ander deel vindt dat er geen afhankelijkheid is en dat de 
geobserveerde lichte afhankelijkheid gewoon toeval is door de steekproeven die genomen zijn. 
We kunnen wat quantitatieve data toevoegen aan deze discussie. 

De vraag is eigenlijk: **"hoe zeldzaam is dat, gegeven dat er in het echt geen verband bestaat, 
een serie steekproeven (van deze grootte in elke categorie) een waarde van de richtingscoefficient 
geeft die net zo groot is als in de data?"** Deze fractie kom je vaak tegen in de literatuur 
en wordt ook wel de p-waarde genoemd.

### opdracht 5: Simuleer random data-sets en bereken de p-waarde

Schrijf een programma `Statistiek5.py()` waarin je de zeldzaamheid van de geobserveerde 
richtingscoefficient bepaalt, de zogenaamde p-waarde.

Gebruik hiervoor de volgende strategie:

   1. Simuleer een random data-set uit een vlakke verdeling
      Trek voor elke categorie een random getal uit de verdeling die als centrale waarde
      de waarde heeft die je bijopdracht 3 (of 4) hebt gevonden. Gebruik hiervoor de 
      voor die geldende onzekerheid als input voor de breedte in de Python functie.      
   2. Fit een lineaire functie en bepaal de richtingscoefficient (a in f(x) = ax+b).
   3. Doe bovenstaande een groot aantal keer (100.000 keer bijvoorbeeld). Onthoud voor elke 
      data set de richtingscoefficient en hou ook bij welke fractie van de gesimuleerde data-sets 
      een richtingscoefficient heeft die groter is dan die je in de 'echte' data hebt gevonden 
      (zie opdracht 4).  
   4. Maak een grafiek (histogram, zie hieronder) van alle richtingscoefficenten en geef duidelijk 
      aan wat de gevonden waarde in de data en de bijbehorende p-waarde. Print de p-waarde ook uit 
      aan het eind van het programma, in procenten, met 2 decimalen.
      
![](ExamplePvalue.png){: style="width:80%"}

In de regel houden we vast aan de regel dat als de p-waarde kleiner is dan 5 procent we nog van 
'toeval' spreken. Is de p-waarde groter dan 5% dan zeggen we dat de geobserveerde trend niet goed 
te verklaren valt met ene vlakke hypothese en dat we bewijs hebben gevonden voor een verband.

*Let op:* Een gevonden verband is nog geen causaal verband. Stel dat er een verband is gevonden 
(en hou altijd in het achterhoofd dat het geobserveerde effect alsnog toeval kan zijn), wat zou 
dan de onderliggende oorzaak kunnen zijn ? Rijkere mensen: eten gezonder, wonen in huizen die 
in een buurt liggen met betere luchtkwaliteit, of andersom dat in onze maatschappij de 
lengte juist zorgt voor een hogere inkomen ? Etc etc. Graven graven graven tot je doordringt tot 
de kern en iets nieuws ontdekt dat nog niemand voor jou gezien heeft. Dat is wetenschap!





	
	
	
