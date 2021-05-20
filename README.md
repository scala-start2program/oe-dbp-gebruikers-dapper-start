# Oefening Gebruikers met ADO.Net  

  ![demo](assets/demo.gif)

De bedoeling is om een applicatie te maken rond gebruikersbeheer en aan de gebruikers toegangsrechten te verlenen.  

Voer eerst en vooral het script scalagebruikers.sql uit op je SQL server zodat je over de database met wat testgegevens beschikt.  
Het script zelf kan je terugvinden op het leerplatform.  

Het programma moet gebruikers kunnen afbeelden, toevoegen, wijzigen en/of verwijderen en je moet toegang kunnen verlenen tot bepaalde onderdelen.  

In de starterscode is al heel wat aanwezig : 
  * Voor elke tabel in de database is al een entiteitsklasse gemaakt : je moet uiteraard wel nog invulling geven.  
    Denk er vooral aan dat wanneer je een nieuw object aanmaakt in je app er automatisch een GUID wordt toegekend aan de Id eigenschappen.  
  * De service klassen DBService en Helper zijn reeds aanwezig (alsook de nodige bibliotheken en referenties) , dus daar hoef je niets meer voor te doen.  
  * Er is ook een service klasse GebruikersService aanwezig maar die je nog volledig in te vullen.  Deze service klasse vormt de brug tussen de code behind van je WPF venster en het database gebeuren (dus je klasse DBService).  
    Deze GebruikersService klasse dient over volgende methoden te beschikken : 
    * public List&lt;Gebruiker&gt; GetAlleGebruikers()  
      deze methode haalt alle gebruikers, gesorteerd op naam en voornaam uit de tabel en levert de inhoud af als een list van gebruiker objecten.  
    * public List&lt;Gebruiker&gt; GetGebruikersMetToegangTotOnderdeel(Onderdeel onderdeel)    
      deze methode haalt alle gebruikers, gesorteerd op naam en voornaam uit de tabel die toegang hebben tot een opgegeven onderdeel en levert de inhoud af als een list van gebruiker objecten.
    * public List&lt;Gebruiker&gt; GetGebruikersZonderToegangTotOnderdeel(Onderdeel onderdeel)  
      deze methode haalt alle gebruikers, gesorteerd op naam en voornaam uit de tabel die GEEN toegang hebben tot een opgegeven onderdeel en levert de inhoud af als een list van gebruiker objecten.    
    * public bool IsGebruikersnaamUniek(string gebruikersnaam)  
      Deze methode zoekt in de tabel gebruikers of de opgegeven gebruikersnaam al of niet bestaat en geeft TRUE terug wannneer die gevonden wordt, anders FALSE  
    * public List&lt;Onderdeel&gt; GetOnderdelen()
      Deze methode haalt alle onderdelen, gesorteerd op onderdeelnaam op uit de tabel en levert de inhoud af als een list van onderdeel objecten.  
    * public List&lt;Onderdeel&gt; GetOnderdelenMetToegangVoorGebruiker(Gebruiker gebruiker)
      Deze methode haalt alle onderdelen, gesorteerd op onderdeelnaam, op uit de tabel waartoe de meegeleverde gebruiker toegang heeft en levert de inhoud af als een list van onderdeel objecten. 
    * public List&lt;Onderdeel&gt; GetOnderdelenZonderToegangVoorGebruiker(Gebruiker gebruiker)
      Deze methode haalt alle onderdelen, gesorteerd op onderdeelnaam, op uit de tabel waartoe de meegeleverde gebruiker GEEN toegang heeft en levert de inhoud af als een list van onderdeel objecten. 
    * public bool GebruikerToevoegen(Gebruiker gebruiker)   
      Deze methode gebruikt het meegeleverde object gebruiker om een record toe te voegen aan de tabel gebruikers en geeft aan of dat al dan niet gelukt is.  
    * public bool GebruikerWijzigen(Gebruiker gebruiker)  
      Deze methode gebruikt het meegeleverde object gebruiker om een record (op basis van de Id waarde) aan te passen in de tabel gebruikers en geeft aan of dat al dan niet gelukt is.  
    * public bool GebruikerVerwijderen(Gebruiker gebruiker)
      Deze methode gebruikt het meegeleverde object gebruiker om een record (op basis van de Id waarde) te verwijderen uit de tabel gebruikers en geeft aan of dat al dan niet gelukt is.  
    * public bool KenRechtToeAanGebruiker(Gebruiker gebruiker, Onderdeel onderdeel)  
      Deze methode gebruikt de meegeleverde gebruiker en onderdeel objecten om een record toe te voegen aan de tabel rechten en geeft aan of dat al dan niet gelukt is.  
    * public bool OntneemRechtVanGebruiker(Gebruiker gebruiker, Onderdeel onderdeel)  
      Deze methode gebruikt de meegeleverde gebruiker en onderdeel objecten om een record te verwijderen uit de tabel rechten en geeft aan of dat al dan niet gelukt is.  
  
In je code behind van je WPF venster zijn alle event handlers reeds aanwezig maar die je uiteraard zelf nog de correcte invullen te geven.   
Zorg er uiteraard voor dat er geen enkele databaseverwijzing in je code behind komt en gebruik enkel de functionaliteiten van de service klasse GebruikersService.  

Succes!
