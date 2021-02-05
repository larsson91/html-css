## Labb 1

Hur bekant är du med html och css?

Om du aldrig har sysslat med html och/eller css rekommenderas det att du gör några uppgifter på Codecademy för att bli bekant med grunderna.

HTML: https://www.codecademy.com/courses/learn-html

CSS: https://www.codecademy.com/learn/learn-css

## Labb 2

1. Skapa en ny fil. Ge den namnet index.html
2. Fyll filen med följande html kod:

```html
<!DOCTYPE html>
<html>
<head>
  <title>My awesome site!</title>
  <style>
    /* You style here */
  </style>
</head>
<body>

</body>
</html>
```

3. Lägg till en rubrik och en paragraf text.
4. Lägg till styling så att paragrafen får större font än rubriken.
5. Selecta du på klass namn, id, element eller skrev du inline style? Varför valde du det du valde?
6. Bryt ut CSS:en till en egen fil som du importerar i din html fil.
7. När är det lämpligt att ha CSS i en egen fil och när är det lämpligt att inkludera den direkt i din html sida? Tips: CSS blockar rendering

## Labb 3

0. Kom ihåg: Disponera din tid väl. Om du anser att du inte får ut något av denna lab så bör du fortsätta till nästa lab
1. I denna mapp ser du en undermapp som heter lab-3.
2. Öppna upp index.html och style.css i din favorit editor (ex. VS Code, Sublime, Atom, Vim, Visual Studio)
3. Ändra index.html och style.css så att resultatet liknar bilden my-page.png så mycket som möjligt.

## Lab 4 - Critical Rendering Path

Kräver Chrome v.72 och Python (eller annat enkelt sätt att serva filer med en webbserver) installerat.

1. Öppna nu upp mappen lab-4 i din editor.
2. Starta en enkel http server som servar dina filer, förslagsvis simple server med Python: `python -m SimpleHTTPServer` med Python 2 och `python -m http.server` med Python 3.
3. Gå till http://localhost:8000 (Eller var server filerna från) i din webbläsare (du kan välja vilken du vill men följande anvisningar kommer vara för Chrome)
4. Öppna dev tools (genom ex. högerklicka på sidan och sedan välja "inspect" eller cmd+alt+i på mac, ctrl+alt+i i Windows)
5. Byt flik till "Network"
6. Se till att checkboxen ”Disable Cache” är i klickad
7. Byt flik till "Performance"
8. Gå till Performance settings (Kugghjulet), välj att begränsa hastigheten till Slow 3G
9. Se till att “screenshots” är i klickad. Klicka sedan på “Start profiling and reload page”
10. Hur lång tid tar det innan man kan se första renderingen på sidan? Det är linjen som hör till FCP man kan använda för det.
11. Hur kan du förbättra tiden för den första renderingen utan att ta bort externa filer? (Går att förbättra väldigt mycket)

## Labb 5 - Web components

1. Se till att du har den senaste versionen av Chrome, Opera, Firefox eller Safari installerat
2. Föreställ er att vi ska bygga vidare på MVC-projektet som listade alla medlemmar i ett projekt. Det vi vill visa är namn och bild på personen och vi vill att det ska länka till personens sida på intranätet. Html-koden skulle kunna se ut på följande vis:
```html
  <div class="image-wrapper">
    <img class="portrait" src="./mycard-the-joker.jpg">
    <a class="title" href="https://en.wikipedia.org/wiki/Joker_(character)">Joker</a>
  </div>
```

3. Som du kan tänka dig är ex. klass-namnet för länken (title) inget bra namn då det lätt kan skapa konflikter med resten av sidan.
Man skulle kunna skapa ett mer unikt namn, så som portrait-title, men det är inte heller ett bra namn. I och med att vår sida växer så kommer vi vilja visa upp porträtt och dess namn på olika sätt. Eftersom klass namn är som standard globala får vi försöka komma på ett mer unikt namn. Kanske my-persons--portrait--title. Som du förstår kommer det bli allt svårare och svårare att komma på lämpliga namn. Det finns olika tekniker att komma fram till unika namn, exempelvis: BEM som man kan läsa mer om här: http://getbem.com/introduction/
Ett annat sett att lösa problemet är att använda web components som isolerar CSS:en till just den komponenten. Om vi också vet att vi kommer behöva visa upp samma komponent på flera system (tex. [intranätet](https://intranet.valtech.se/), [Blp](https://blp.valtech.se) och [Sourcing](https://sourcing.valtech.se/)) är web components ett enkelt sätt att kunna återanvända komponenter där man inte använder samma tekniker.
4. Öppna upp mappen lab-5 i din editor.
5. Editera [components.html](lab-5/components.html) skriv om PortraitComponent så att den visar bilden och text, likt i den andra komponenten ovan, och isolera dess CSS.
6. Web components erbjuder fantastiska möjligheter. Ex. kan du nu dela och importera web componenter mellan olika sidor som fungerar helt isolerat. Om du exempelvis behöver en date-picker eller inloggningsformulär eller en sorterings tabell kan du enkelt importera dessa och de kommer fungera utan att skapa globala CSS klasser eller javascript variabler. MEN som du kanske märkte när du gjorde denna övning så finns det vissa problem med web components. Web components är en ny teknik som inte riktigt är mogen än men det kommer. Tanken med denna lab var att ge dig en försmak på vad som komma skall. Det finns redan ett antal projekt som förenklar användandet av Web Components, tex [Polymer](https://www.polymer-project.org/), [Hybrids](https://hybrids.js.org/) och [X-Tag](http://x-tag.github.io/) som du kan kolla närmare på.

7. Nu ska vi använda komponenten i projektet från MVC-labben och det kräver att du kört klart till och med labb 3 i den labbserien, så om du inte gjort det så [fortsätt](https://git.valtech.se/talangprogrammet/Mvc) där du är och kom tillbaks hit när du klarat av labb 3. 
8. Till en början ska vi utöka MVC-projektet lite:  
Se till så att klassen Consultant har följande properties:  
```csharp
    public string Name { get; set; }
    public string LinkUrl { get; set; }
    public string ImageUrl { get; set; }
```
Byt ut till följande lista som Team i ditt projekt du skapat HomeController (ändra i ConsultantService om du hunnit med MVC labb 6):  
```csharp
	new List<Consultant>
        {
            new Consultant() {Name = "Mikael Dahlgren", LinkUrl = "https://intranet.valtech.se/employees/mikael.dahlgren/",  ImageUrl = "https://www.gravatar.com/avatar/dd559e64f11b1ea7e70f07aa24ba1089.jpg?s=480&d=monsterid"},
            new Consultant() {Name = "Martin Wedberg", LinkUrl = "https://intranet.valtech.se/employees/martin.wedberg/",  ImageUrl = "https://www.gravatar.com/avatar/3a5fcf4849ee1cf64c0356f5dd2172a2.jpg?s=120&d=monsterid"},
            new Consultant() {Name = "Theodor Klaar", LinkUrl = "https://intranet.valtech.se/employees/theodor.klaar/",  ImageUrl = "https://www.gravatar.com/avatar/82af00fd2f27f6c8f5ec5f4bdf783c6d.jpg?s=120&d=monsterid"},
            new Consultant() {Name = "Patric Hjort", LinkUrl = "https://intranet.valtech.se/employees/patric.hjort/",  ImageUrl = "https://www.gravatar.com/avatar/f4907989ce7d228635a704aa548508e8.jpg?s=120&d=monsterid"},
            new Consultant() {Name = "Erik Ohlsson", LinkUrl = "https://intranet.valtech.se/employees/erik.ohlsson/",  ImageUrl = "https://www.gravatar.com/avatar/4e74e4203c06b87218bdef369e4df1a0.jpg?s=120&d=monsterid"},
            new Consultant() {Name = "Valeria Helle", LinkUrl = "https://intranet.valtech.se/employees/valeria.helle/",  ImageUrl = "https://www.gravatar.com/avatar/1b1ac29b8ed0f164286e657952330305.jpg?s=120&d=monsterid"},
            new Consultant() {Name = "Erik Difs", LinkUrl = "https://intranet.valtech.se/employees/erik.difs/",  ImageUrl = "https://www.gravatar.com/avatar/0b17fa0558b0ebf8118b4094b9697eb6.jpg?s=120&d=monsterid"},
            new Consultant() {Name = "Caroline Borg", LinkUrl = "https://intranet.valtech.se/employees/caroline.borg/",  ImageUrl = "https://www.gravatar.com/avatar/970f3fa96bb5bef7978bfec23a8bae67.jpg?s=120&d=monsterid"},
            new Consultant() {Name = "Alex Lindström", LinkUrl = "https://intranet.valtech.se/employees/alex.lindstrom/",  ImageUrl = "https://www.gravatar.com/avatar/832318a9115aeaf40967c96d2efd3847.jpg?s=120&d=monsterid"},
        };
```
9. Kopiera över den nyskapade webbkomponenten till filen `Views/Shared/_Layouts.cshtml` i MVC-projektet så att du kan använda den i projektet och använd den för att lista alla medlemmar i home-vyn (`Views/Home/Index.cshtml`).
10. Grattis! Nu har du skapat upp dig själv och dina talangkollegor som helfräsiga webbkomponenter 🎉

## The end

Du var en snabb en 🚀  
Läs gärna igenom följande artiklar (ta det som är intressant för dig) hjälp din granne, fortsätt med en labb du inte är klar med eller lös lite uppgifter på [Exercism](https://exercism.io/my/tracks):

- Grundläggande HTML: http://learn.shayhowe.com/html-css/building-your-first-web-page/
- "Critical Rendering Path" här: https://bitsofco.de/understanding-the-critical-rendering-path
- Hur utvecklare har tenderat till att använda CSS genom åren: https://m.alphasights.com/css-evolution-from-css-sass-bem-css-modules-to-styled-components-d4c1da3a659b#.jwhdxnrvb
- Och här: https://medium.com/yplan-eng/inline-styles-are-so-2016-f100b79dafe1#.59th7hucy
- Web components https://www.smashingmagazine.com/2016/12/styling-web-components-using-a-shared-style-sheet/ https://developer.mozilla.org/en-US/docs/Web/Web_Components

Om du vill lära dig mer om flexbox och grid för CSS finns även https://flexboxfroggy.com/ och http://cssgridgarden.com/.
