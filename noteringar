# Det är en evighetsmaskin

Maskinen har en skärm som visar hur länge den har varit igång sedan start.

# Design

## Strömförsörjning

Maskinen drivs av en solpanel som laddar en bunt superkondensatorer. Kondensatorerna dimensioneras för att kunna driva maskinen utan ljus i upp till två dygn. Solpanelen dimensioneras för dubbla strömförsörjningen så att det finns energi över att ladda kondensatorerna.

### Spänning

De flesta LED-displayer (se Skärm nedan) vill ha en spänning mellan ca 1,5 och 2,5 V. Det finns flera mikrochip, typ Arduino Pro Mini, som kan köras på 3,3 V, och även RTC-moduler med samma spänning.



### Kondensatorer

Hur mycket ström som kan tas ut ur fulladdade kondensatorer ges av formeln:

    I = C * U / t
    C = I*t/U

till exempel

    I = 1.5 Farad * (5-1)V / (2 dagar) = 35 uA
    C = (300 uA * 2 days)/(5-1)V = 13 F

Kondensatorerna kan sättas parallellt. Då summeras kapacitansen. Sätts de i serie blir kapacitansen istället:

    1/C_tot = 1/C_1 + 1/C_2 + ... + 1/C_n => C/n om alla har samma kapacitans.

Den totala energin ges av:

    E = (1/2) * Kapacitans * Spänning^2

Antag två kondensatorer på 100F och 2.7V (eftersom jag hittat sådana). Säg att vi kan ladda dem till 2.7V i serie eller 5V parallellt, och att vi inte kan få ut de sista 0.5V:en. Vilket ger mest användbar energi?

    E_serie = (1/2)*50*(5-0.5)^2 = 506 J
    E_parallellt = (1/2)*200*(2.7-0.5)^2 = 484 J

Så serie ger mest oss energi, och också en enklare krets. Hur stor effekt ger det oss om vi plockar ut det över två dagar?

    P = 506 J / 2 dagar = 2,92 mW
    I = 2,92 mW / 5V = 584 uA

#### Läckström

Denna 100F-kondensator läcker hela 280 uA: http://www.robotmesh.com/super-capacitor-100f-2-7v

### Solpanel

Som tur är har någon gjort mätningar på hur mycket energi som går att få ut!

> in december, it is a fair assumption to expect more than 20uW if you place your 55*70mm solar panel less than 2m from a window with the curtains partially shut
- http://www.limpkin.fr/index.php?post/2012/03/20/Indoor-solar-energy-harvesting%3A-3-months-data

Eftersom jag måste planera för värsta scenariot är detta hållpunkten jag kan gå efter. I testet användes en polykrystallin 5V-panel på 55*70 mm och en märkeffekt på 1W. 0.5W gav bra precis halva effekten.

## Livslängd

### Solpanel

Polykrystallina solpaneler beräknas degradera till ca 80% på 20 år, om de sitter utomhus på tak. De klarar sig betydligt bättre när de är skyddade. Så låt oss lägga på 25% effekt.

### Skärm

OLED har kort livslängd, ca 14000 timmar. Lysdioder används i punktmatriser, 7-segmentsskärmar och bakgrundsbelyst LCD. De har en livslängd på 25000 till 100000 timmar, men det är oklart när de tappat halva ljusstyrkan. LED fungerar längre och lyser starkare kylda. LCD verkar ha en livslängd på omkring 50000 timmar.

Det krävs alltså någon form av viloläge på evighetsmaskinens skärm. Kan den vara avstängd när ingen är i närheten? Nej, det förtar syftet. Men LED tål PWM som då kan förlänga livslängden flera gånger om.

Vad drar en 7-segmentsskärm?

Vilka lösningar finns det med e-papper?

# Länkar

* https://www.maximintegrated.com/en/app-notes/index.mvp/id/1883
* https://en.wikipedia.org/wiki/Light-emitting_diode#Lifetime_and_failure
* http://www.hpmuseum.org/cgi-sys/cgiwrap/hpmuseum/archv019.cgi?read=157392
* http://www.lrc.rpi.edu/programs/NLPIP/lightingAnswers/LED/life.asp
* http://www.lrc.rpi.edu/programs/nlpip/lightinganswers/led/dimmingLampLife.asp
* http://electronics.stackexchange.com/questions/207233/does-and-when-how-the-lifetime-of-a-led-depend-on-the-pwm-frequency
* http://www.waitingforfriday.com/index.php/Controlling_LED_brightness_using_PWM
* http://ams.com/eng/Products/Lighting-Management/LED-Driver-ICs/AS1130
* http://ams.com/eng/Products/Lighting-Management/LED-Driver-ICs/AS1123
* http://www.sensorsmag.com/networking-communications/energy-harvesting/using-a-small-solar-cell-and-a-supercapacitor-a-wireless-sen-7310
* http://www.limpkin.fr/index.php?post/2011/12/07/Indoor-solar-energy-harvesting%3A-a-platform-to-%28finally%29-get-some-numbers