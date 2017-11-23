# Adaptive Media - Parallax megjelenés

Ez a reklám típus videó tartalom megjelenítésére szolgál.

## Használata

A "parallax" könyvtáron belül található "parallax_code.html" tartalmát kell felvenni HTML-ként az adengine-be.

## A desktop és mobil megjelenéshez szükséges fájlok

"AdaptiveMediaParallax.min.js" és 2 darab kép (desktop és mobil megjelenéshez)

* Desktop háttérkép tulajdonságai
    * Méret: 2048x2414px, max 500Kbyte,
    * **pl:** desktop_background.jpg

* Mobil háttérkép tulajdonságai
    * Méret: 3760x1200px, max 500Kbyte,
    * **pl:** mobile_banner.jpg

##### Mozilla leírása a böngésző DeviceMotion események támogatottságról: https://developer.mozilla.org/en-US/docs/Web/API/DeviceMotionEvent

Ezeket a fájlokat fel kell venni az adengine-be és bekötni a "parallax_code.html" fájlon belül látható módon a megfelelő helyekre.

## "parallax_code.html" fájl felépítése és használata

Az alábbi konfigurációs objektumban lehet beállítani kattintási kódot, képekett és a működéshez szükséges beállításokat.

```html
    <script>
        adaptiveMediaParallaxConfig = {
            clickURL: 'http://bmw.hu',
            clickTarget: '_blank',
            isMobile: true,
            media: {
                mobileBackgroundLayer: {
                    speed: 9.5,
                    IOSSpeed: 0.030,
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
```

## parallax konfigurációs paraméterek
* **isMobile**: "true" értéket kell megadni ha mobil megjelenésként vesszük fel. "false" értéket kell megadni, ha desktop megjelenéshez vesszük fel. [true/false]
* **speed**: **Mobil megjelenés** esetén az eszköz mozgásérzékenységét tudjuk állítani. Egy olyan tört számot adhatunk meg, ami összeszorzódik a szenzor mért gyorsulás értékével. [9.5]
* **IOSSpeed**: **Mobil megjelenés** esetén az eszköz mozgásérzékenységét tudjuk állítani. Egy olyan tört számot adhatunk meg, ami összeszorzódik a szenzor mért gyorsulás értékével. [0.030]

