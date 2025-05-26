# Experiment: Gendergerechte Embeddings

![](/image.png)

## KI-gerechtes Gendern von Begriffen?

Wenn #Google bald keine Suchmaschine ist, sondern ein #KI-#Chatbot, ändert das nicht nur die SEO-Strategie, sondern auch unsere Sprache. 

Nehmen wir die Idee der gendergerechten Sprache - neben der Gerechtigkeit möchte ich auch, dass unsere Stellenanzeigen bei der @viadee weiterhin von Google gefunden werden. Wie schreibe ich dann am besten "Gesucht: Senior IT-Beraterin Data & AI"?

Ich habe mich daher zu einem kleinen Experiment entschlossen. Wie ähnlich ist aus KI-Sicht der "IT-Berater" zur "IT-Beraterin", "IT-Berater:in", "IT-Berater*in"? 🤔 Es müsste eine rechnerisch optimale Formulierung geben, und zwar die, in der sich die feminine und die maskuline Formulierung am wenigsten voneinander unterscheiden, denn wir möchten möglichst von allen qualifizierten Menschen gefunden werden.

Das lässt sich mit dem Google Embedding-Modell (`gemini-embedding-001`), ein wenig Python-Code und der üblichen Cosinus-Ähnlichkeit sehr einfach messen, bspw. in einer @qdrant-Vektordatenbank.

Die semantischen Distanzen sind im Ergebnis wie folgt:

• IT-Berater 🆚 IT-Berater:in: 0.0386

• IT-Berater 🆚 IT-Berater*in: 0.0392

• IT-Berater 🆚 IT-Beratende: 0.0482

• IT-Berater 🆚 IT-Beraterin: 0.0503

Danach kommen mit einigem Abstand meine stereotypen Kontrollbegriffe "Bademeisterin" und "Hufschmiedin" und ich stelle fest, dass mein Beruf dem eines Bademeisters ähnlicher ist als dem eines Hufschmieds. Nun gut.

Zwischenfazit: Die *IT-Berater:in* wäre also die beste Wahl, um möglichst viele Menschen in Suchanfragen diskriminierungsfrei zu erreichen. Für die beliebten Modelle von OpenAI (hier `text-embedding-3-small`) gilt das übrigens auch.

Allerdings ist der Doppelpunkt auch ein übliches Trennzeichen und kein Wortbestandteil. Für die KI-Sicht der Stellenanzeige ist "Gesucht: IT-Berater in (.. Köln)" auch eine mögliche Fortsetzung des Textes. Dann hätten wir hier nur zwei Männerrollen verglichen, und es fehlt nur zufällig die Stadt. 

Vielleicht funktioniert der Begriff zwar am besten, aber nur aus den 'falschen' Gründen und nicht, weil das Google-Modell angemessen viele deutsche Texte in gendergerechter Sprache als Trainingsvorlage hatte? Ich würde trotzdem pragmatisch zu diesem Begriff raten und wir verwenden ihn glücklicherweise auch schon in unseren Stellenanzeigen... oder seine englischsprachigen Varianten.

Diese Begriffe lesen sich auch gut. "IT-Consultant" ist im Vector-Space aber semantisch doppelt so weit entfernt vom IT-Berater wie die IT-Beraterin. Das Experiment lässt mich in jedem Fall mit dem Wunsch nach mehr europäischer Sprachkompetenz in den KI-Modellen zurück.

Der Link zum Git-Repository mit dem Experiment folgt in den Kommentaren.

▶️ https://github.com/fkoehne/gendergerechte-embeddings

## Experiment nachvollziehen

Wir nehmen eine Python-Entwicklungsumgebung sowie deren Konfiguration mit OpenAI und Google Vertex an.

Als konkretes Setup bleibt dann nur noch der Start der Qdrant-DB übrig. 

Danach können die beiden Notebooks in diesem Repository mit [OpenAI-Embeddings](gendergerecht.ipynb) und [Google Gemini-Embeddings](gendergerecht-gemini.ipynb) ausgeführt werden, um das Experiment nachzuvollziehen.

```bash
podman run -p 6333:6333 qdrant/qdrant
```
# Bild-Quelle

KI-generiert per `Stable Diffusion 3.5 Ultra`
> A friendly robot (orange) putting one finger to her/his face, thinking about which of two doors to open. The left door is a WC marked with a male shape, the right one with a female shape.