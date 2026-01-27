# HW/SW integration test instructions

## Förutsättningar 
* Bygg och flasha ATmega328p processorn.
* Kör systemet och öppna serial terminal.

## 1. Togglefunktion 
* Tryck på knappen för togglefunktionen.
* LEDen ska då börja blinka.
* Tryck på knappen igen.
* LEDen ska då släckas.
* Testa att trycka upprepade gånger för att de till att debounce fungerar korrekt.
* Knapptryckningar som sker oftare än 300 ms kommer ignoreras.

## 2. Mät blinkhastigheten på togglefunktionen
* Tryck på knappen för togglefunktionen igen.
* LEDen ska då börja blinka.
* Mät hur snabbt den blinkar, det ska vara ca 5/s.
* Tryck på knappen igen för att släcka LEDen.

## 3. Temperaturläsning
* Tryck på knappen för avläsning av temperatur, se till att
detta skrivs ut i terminalen.
* Jämnför med rumstemperaturen och se till att det är rimligt.
* Värm sensorn med handen.
* Den nya temperaturen ska då skrivas ut när knappen trycks.
* Se till att temperatuen skrivs ut var 60 sekund efter att knappen tryckts.
* Testa att trycka upprepade gånger för att de till att debounce fungerar korrekt.
* Knapptryckningar som sker oftare än 300 ms kommer ignoreras.

## 4 Watchdog timer 
* Se till att watchdog timern är aktiverad vid uppstart.
* Detta görs genom att kolla i terminalen och se att den inte 
startar om hela tiden.
* För att testa watchdog timer ändra i koden: 
    * Kommentera ut myWatchdog.reset(); i logic och flasha sedan igen.
    * Nu kommer inte watchdog timern att fungera och programmet kommer bara startas om, om och om igen.
    * När systemet starar om hela tiden är det för att watchdog-timeout timear ut hela tiden.
* Ändra tillbaka koden och se till att watchdog timer fungerar igen.

## 5 EEPROM 
* Tryck på toggleknappen så att LEDen börjar blinka
* Stäng av systemet
* Sätt på systemet och se till att LEDen fortsätter blinka.
* "toggletimer enabled" ska skrivas ut i terminalen.
* Tryck på toggleknappen igen så att LEDen släcks.
* Starta om igen och se till att LEDen är släckt.

## 6 Komplett test 
* Kör ett komplett scenario:
1. Starta systemet från reset.
2. Tryck på toggle-knappen → lysdioden ska blinka.
3. Tryck på temperaturknappen → temperatur ska skrivas ut.
4. Vänta på automatisk temperaturavläsning.
5. Tryck på toggle-knappen igen → lysdioden ska sluta blinka.
6. Tryck på toggle-knappen igen → lysdioden ska börja blinka.
7. Resetta systemet och verifiera att toggle-tillståndet är aktivt vid start, dvs. lysdioden ska börja blinka efter omstart.
8. Tryck på toggle-knappen igen → lysdioden ska sluta blinka.
9. Resetta systemet och verifiera att toggle-tillståndet är inaktivt vid start, dvs. lysdioden ska vara släckt efter omstart.
