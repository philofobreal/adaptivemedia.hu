
## FIGYELEM: v.65 chromium hiba miatt ki van kapcsolva ebben a verziószámban a giroszkópos üzemmód. Korábbi és későbbi verziójú chromiumban a továbbiakban is működik a giroszkóp. 
# Adaptive Media - 444.hu Parallax technikai specifikáció

Ez egy multiplatformos interaktív hirdetési típus. A felhasználó egér, oldal scroll, illetve mobil eszközének mozgását követi le a hirdetési anyag.

##### Ügyfeleknek szánt specifikációk: 
###### Desktop skin: https://docs.google.com/document/d/13HqEukS-THeycI-nzEFbLQ1Sv3kizp8tz-vLvnMR3UU/edit?usp=sharing
###### Mobile: https://docs.google.com/document/d/1WDrYZ6UKSMyZRzMHCsVuXmmnbLdCoe6fdAUA9yXvp6k/edit?usp=sharing

## Használata

A "parallax" könyvtáron belül található "parallax_code.html" tartalmát kell felvenni (Insert HTML) HTML-ként az adengine-be. 
Érdemes külön desktop és külön mobil kódot készíteni belőle. A desktop kód fölé behelyezhető html banner. **Fontos, hogy az "isMobile" paraméter desktop-on "false", mobilon "true" értékre legyen állítva!** Az "isMobile" paraméterrel lehet átadni a platform megállapítást az adengine-nek. Így a mobilra szánt kódban az "isMobile: true", a desktop-ra szánt kódban a "isMobile: false" értékmegadás a helyes. 

## A desktop és mobil megjelenéshez szükséges fájlok

"AdaptiveMediaParallax.min.js" és 1 darab desktop és 1 darab mobil háttérkép

* **Desktop háttérkép tulajdonságai**
    * **Méret:** 2048x2414px, max 500Kbyte,
    * **Design tulajdonságok:** A 444.hu háttérszínétől **whitesmoke: #f5f5f5** nagyban nem üthet el a desktop reklám grafikája. A mintán látható mennyiségű rekláminformáció szerepelhet csak a képen.
    * **minta:** desktop_background.jpg
    * **2 db mozgó layer:** 2048 px széles és max 1600px magas, 300KByte méret képenként. A mintákon látható módon a középső homogén színű területre nem szabad grafikát elhelyezni.

* **Mobil háttérkép tulajdonságai**
    * **Méret:** 3760x1200px, max 500Kbyte,
    * **Design tulajdonságok:** A mintában megadott módon lehet felosztani a jobb és bal szélekre elhelyezhető reklám területeket. Nem kell élesen elkülöníteni ezeket a területeket, viszont oldalbetöltődéskor a jobb és bal széleken lévő területek nem fognak látszódni. Csak a mobil eszköz elfordítása után válnak láthatóvá. 
    * **minta:** mobile_banner.jpg

##### Mozilla leírása a böngésző DeviceMotion események támogatottságról: https://developer.mozilla.org/en-US/docs/Web/API/DeviceMotionEvent

Ezeket a fájlokat fel kell venni az adengine-be és bekötni a "parallax_code.html" fájlon belül látható módon a megfelelő helyekre.

## "parallax_code.html" fájl használata

Az alábbi konfigurációs objektumban lehet beállítani kattintási kódot, képeket és a működéshez szükséges paramétereket. Desktop környezetben a desktop banner kódja alá kell bemásolni (Insert HTML) a teljes "parallax_code.html" fájl tartalmát.

```html
    ...
    <script>
        adaptiveMediaParallaxConfig = {
            clickURL: 'http://bmw.hu',
            clickTarget: '_blank',
            isMobile: true,
            media: {
                mobileBackgroundLayer: {
                    speed: 9.5,
                    androidFirefoxSpeed: 0.5,
                    IOSSpeed: 0.60,
                    frequency: 50,
                    pxLimit: 21,
                    imagePosition: '-28%',
                    imageWidth: '122%',
                    iconEffect: 'blinker blink_me',
                    imageUrl: 'https://bbcdn.go.cz.bbelements.com/creatives/....../...../.../mobile_banner.jpg',
                },
                backgroundLayers: [
                    {
                        imageUrl: 'https://bbcdn.go.cz.bbelements.com/creatives/....../...../.../desktop_background.jpg',
                        layerDepth: '0.00',
                        animatedClass: ''
                    },
                    {
                        imageUrl: 'https://bbcdn.go.cz.bbelements.com/creatives/....../...../.../gate_layer_2_.png',
                        layerDepth: '0.15',
                        animatedClass: 'wave1'
                    },
                    {
                        imageUrl: 'https://bbcdn.go.cz.bbelements.com/creatives/....../...../.../gate_layer_3_.png',
                        layerDepth: '0.25',
                        animatedClass: 'wave2'
                    }
                ]
            }
        }
    </script>
    ...
```

## parallax konfigurációs paraméterek
* **layerDepth**: **Desktop megjelenés** esetén az egér mozgását követő rétegek tér érzetének mélységi értékét tudjuk megadni. **[0.00 - 0.99]**

* **isMobile**: **"true"** értéket kell megadni ha mobil megjelenésként vesszük fel. **"false"** értéket kell megadni, ha desktop megjelenéshez vesszük fel. **[true/false]**
* **speed**: **Mobil megjelenés** esetén az eszköz mozgásérzékenységét tudjuk állítani **Nem IOS** környezetekben. Egy olyan tört számot adhatunk meg, ami összeszorzódik a szenzor mért gyorsulás értékével. 
* **androidFirefoxSpeed**: **Mobil megjelenés** esetén az eszköz mozgásérzékenységét tudjuk állítani **android/firefox** környezetekben. Egy olyan tört számot adhatunk meg, ami összeszorzódik a szenzor mért gyorsulás értékével. 
* **IOSSpeed**: **Mobil megjelenés** esetén az eszköz mozgásérzékenységét tudjuk állítani **IOS** környezetekben. Egy olyan tört számot adhatunk meg, ami összeszorzódik a szenzor mért gyorsulás értékével. 
* **frequency**: **Mobil megjelenés** esetén a mozgásérzékelés frissítési gyakoriságát adhatjuk meg Hertz-ben. Ez egy mintavételezési sebesség. Akár tekinthető fps-ként is.
* **pxLimit**: **Mobil megjelenés** esetén a parallax mobil banner kimozdíthatóságának a határa százalékban megadva. A megadott százalékban lehet csak elcsúsztatni a képet jobbra és balra.
* **imagePosition**: **Mobil megjelenés** esetén a parallax mobil banner képét tudjuk pozícionálni.
* **imageWidth**: **Mobil megjelenés** esetén a parallax mobil banner képét tudjuk méretezni.
* **iconEffect**: **Mobil megjelenés** esetén az eszköz elfordítására buzdító piktogram css class megadásának lehetősége. A piktogram villogásának, illetve egyéb más figyelem felkeltő animációs tulajdonáságait itt tudjuk css class-okkal megadni.
