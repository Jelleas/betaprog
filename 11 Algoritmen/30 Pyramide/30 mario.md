# Pyramide

Implementeer een programma dat een halve piramide uitprint van een door de gebruiker gegeven hoogte.

	Hoe hoog moet de pyramide zijn? 5
	    ##
	   ###
	  ####
	 #####
	######

	Hoe hoog moet de pyramide zijn? 3
	  ##
	 ###
	####

## Het idee

Aan het einde van wereld 1-1 in Super Mario Brothers moet Mario een halve pyramide van blokken beklimmen voordat hij mag springen naar een vlaggenpost. Dit ziet er zo uit:

![](mario.png)

## Specificatie

* Schrijf in een bestand genaamd `pyramide.py` een programma dat de halve pyramide van Mario nabouwt door middel van hekjes (`#`) en spaties.

* Vraag, om het wat interessanter te maken, eerst aan de gebruiker de gewenste **hoogte** van de halve piramide. Dit moet een positief getal zijn, niet groter dan 23.

* Als de gebruiker een hoogte invult die niet toegestaan is, dan vraag je de gebruiker opnieuw naar de hoogte. Net zo lang tot de gebruiker een goede hoogte invult.

* Je mag wél aannemen dat de gebruiker braaf gehele getallen (integers) invult. We houden dus geen rekening met bijvoorbeeld kommagetallen.

* Als de hoogte bekend is, genereer dan met behulp van één of meer loops de halve pyramide.

* Let goed op dat er geen spatie staat tussen de linker onderhoek van je pyramide en de linkerrand van je scherm!

## Hints

* Tel goed hoe veel spaties en hekjes er op elke regel moeten staan.

* Denk goed na over welke loopstructuur (`for` en `while`) je wilt gebruiken.

* Met `print` kun je niet zomaar losse hekjes of spaties printen. Gebruik daarom de functie `sys.stdout.write()`:

		import sys
		
		sys.stdout.write(' ')    # deze regel print een spatie
		sys.stdout.write('#')    # deze regel print een hekje
		sys.stdout.write('#')    # deze regel print een hekje
		sys.stdout.write('\n')   # deze regel print een enter, gaat naar volgende regel

## Stappen

Is bovenstaande een beetje teveel om in één keer te maken? Doe het dan in stappen, zoals programmeurs meestal doen:

* Pak eerst de invoer aan. Zorg dat een gebruiker een getal kan invoeren en print deze dan weer uit.

* Pas dan het programma aan zodat het geen foutieve invoer meer accepteert, zoals in de specificatie staat.

* Zorg dan dat het programma een aantal hekjes kan printen op één regel.

* Zorg dan dat je een vierkant kunt printen: meerdere hekjes op een regel, en meerdere van zulke regels.

* Nu is het tijd om de pyramide af te maken!

## Testen

Loop weer eerst je eigen programma na. Wat gebeurt er als je 0 voor hoogte invult? Kan je programma alle foute input afhandelen? Test dan je programma door middel van checkpy met:

	checkpy pyramide
