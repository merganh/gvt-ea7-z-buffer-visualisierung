# EA 7: Z-Buffer Visualisierung

Einsendeaufgabe 7, Modul Graphical Visualisation Technologies, TH Lübeck, Wintersemester 2026/27.

Eine einseitige WebGL-Anwendung, die den Tiefenpuffer (Z-Buffer) einer Szene als
Graustufenbild zeigt. Die Szene besteht aus Torus, Zylinder, Kugel, Würfel, Kegel
und Quader, die einander durchdringen und auf einer Bodenfläche weit in die Tiefe
gestaffelt sind. Der Fragment-Shader liest den Tiefenwert aus `gl_FragCoord.z`,
rechnet ihn in den linearen Abstand zur Kamera zurück und normiert ihn zwischen
Near- und Far-Clipping-Plane: nahe Fragmente sind dunkel, ferne hell.

## Live-Demo

Öffentlich erreichbar unter:
<https://merganh.github.io/gvt-ea7-z-buffer-visualisierung/>

## Lokal ausführen

Kein Build-Schritt. Die Seite lässt sich über einen lokalen Server öffnen:

```bash
python3 -m http.server 8000
# dann im Browser: http://localhost:8000
```

## Deployment via GitHub Pages

Im Repo liegt ein Workflow unter `.github/workflows/pages.yml`, der die Seite bei
jedem Push auf `main` automatisch nach GitHub Pages deployt. Einmalig im Repo
unter **Settings → Pages → Build and deployment → Source** `GitHub Actions`
wählen.

## Aufbau

- `index.html`: gesamte Anwendung in einer Datei (HTML, CSS, JavaScript und die beiden Shader inline)
- WebGL 1 mit GLSL ES 1.00, ohne Framework und ohne Matrizenbibliothek
- Geometrie aus parametrischen Formen (Kugel, Torus, Zylinder, Kegel), dazu Quader und Bodenfläche, gezeichnet mit Index-Arrays
- Near = 3, Far = 25, Öffnungswinkel 45°

Es werden keine externen Bibliotheken, Schriften oder Bilder verwendet.
Quelle zur Skalierung der Tiefe: Nathan Reed, *Visualizing Depth Precision*,
NVIDIA Technical Blog, <https://developer.nvidia.com/blog/visualizing-depth-precision/>.

## Bedienung

- **W / S**: Kamera in der XY-Ebene nach oben bzw. unten verschieben
- **A / D**: Kamera in der XY-Ebene nach links bzw. rechts verschieben
- **Pfeil links / rechts**: Szene um die Y-Achse drehen
- **Pfeil hoch / runter**: Szene um die X-Achse drehen
- **R**: Startansicht wiederherstellen

Gedrückthalten wiederholt den Schritt. Jede Taste hat zusätzlich einen Button auf der Seite.

## Quelltext-Markierung

Die für die Aufgabe geschriebenen Stellen sind mit
`// START EA7_ZBUFFER` und
`// END EA7_ZBUFFER` markiert.
