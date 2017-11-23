# Adaptive Media - Multiplex megjelenés

Ez a reklám típus videó tartalom megjelenítésére szolgál.

## Használata

A "parallax" könyvtáron belül található "parallax_code.html" tartalmát kell felvenni HTML-ként az adengine-be.

## A desktop és mobil megjelenéshez szükséges fájlok

"AdaptiveMediaParallax.min.js"
4 darab kép
### Előnézeti kép tulajdonságai:
#### Méret: 1160x773px, max 500Kbyte,

### Videó fájlok tulajdonságai:
#### Képarány:16:9
#### Méret: max 10Mbyte
#### -Első videó: MP4, amelyben H.264 a videó és MP3 a hang enkódolása. 
#### -Második videó: Webm, Vorbis enkódolású

##### Mozilla leírása a böngésző DeviceMotion események támogatottságról: https://developer.mozilla.org/en-US/docs/Web/API/DeviceMotionEvent

Ezeket a fájlokat fel kell venni az adengine-be és bekötni a "parallax_code.html" fájlon belül látható módon a megfelelő helyekre.

## "parallax_code.html" fájl felépítése és használata

Az alábbi konfigurációs objektumban lehet beállítani kattintási kódot, előnézeti képet, statisztikai események URL kéréseit.

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
                    imageUrl: 'https://bbcdn.go.cz.bbelements.com/creatives/....../...../.../mobilParallax_banner_02.jpg',
                },
                backgroundLayers: [
                    {
                        imageUrl: 'https://bbcdn.go.cz.bbelements.com/creatives/....../...../.../gate_background_pix_.jpg',
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


