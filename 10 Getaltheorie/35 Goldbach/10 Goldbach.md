# Goldbach

Schrijf een programma dat laat zien dat het vermoeden van Goldbach inderdaad correct is voor de even getallen tot en met 1000.

	# python goldbach.py
	16 = ...
	18 = 5 + 13 
	20 = 3 + 17 
	22 = 5 + 17
	24 = ...

## Achtergrond

Het vermoeden van Goldbach is een van de oudste onopgeloste problemen in de wiskunde. Goldbach stelde:

*"Elk even getal groter dan 2 kan geschreven worden als de som van twee priemgetallen."*

Een priemgetal mag hierbij ook twee keer gebruikt worden (6=3+3). Hoewel dit inderdaad blijkt te kloppen voor alle getallen tot $$4\cdot10^{18}$$ is er nog altijd geen analytisch bewijs voor de stelling. Omdat je niet tot oneindig kan tellen met een computer zal je zo nooit het bewijs kunnen geven. Je zou wel het vermoeden kunnen ontkrachten door een enkel tegenvoorbeeld te geven van een even getal dat niet te schrijven is als de som van twee priemgetallen. We gaan ons steentje bijdragen in de zoektocht.

## Specificatie

Laat met een programma **goldbach.py** zien dat alle even getallen tot 1000 inderdaad te schrijven zijn als de som van twee priemgetallen. Concreet: laat voor elk even getal ook expliciet zien dat het te schrijven is als de som van twee priemgetallen, zoals in het voorbeeld hierboven.

Nog belangrijker is natuurlijk als je een getal vindt dat *niet* aan het vermoeden (*conjecture*) van Goldbach voldoet. Zorg dat jouw programma zo'n ontdekking duidelijk op het scherm aangeeft. Bingo!

## Hints

- Bepaal altijd met pen en papier je strategie en ga dus niet gelijk tikken. De 5-10 minuten die je hieraan besteedt verdien je dik terug tijdens het omzetten naar programmacode.

- Gebruik weer een lijst priemgetallen. Bedenk zelf tot waar de lijst moet lopen om de even getallen tot 1000 van delers te voorzien.

- Je mag in deze opgave de onderstaande Python constructie gebruiken die kijkt of een element wel of niet in een in een lijst voorkomt. De volgend constructie zal op het scherm printen dat 7 inderdaad een priemgetal is.

		priemen = [2,3,5,7,11]
		x = 7
		if x in priemen:
		    print "Ja, het getal %d komt voor in mijn priemlijst" % x

  En als je voor elk van de getallen 1 tot en met 40 wilt bekijken of ze in de lijst staan gebruik je dus:

		priemen = [2,3,5,7,11]
		for x in range(1,41):
		    if x in priemen:
		        print "Ja, het getal %d komt voor in mijn priemlijst" % x

## Testen

Loop nu de specificatie bovenaan de opdracht goed door en zorg dat je programma precies zo werkt als daar beschreven is.

Nu ben je klaar om te testen:

	checkpy goldbach
