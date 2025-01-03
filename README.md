# Cartopy (et une histoire de "Terre plate")

## Une histoire de "Terre plate"

Courant décembre 2024, 3 "platistes" américains ont été conviés à une expédition en Antarctique, baptisée ["The Final Experiment"](https://www.the-final-experiment.com/). L'objectif des accompagnateurs "globistes" était de montrer à ces "platistes" que le Soleil ne se couchait jamais en ce lieu autour du solstice de décembre. Antérieurement, ces 3 messieurs niaient en effet ce simple fait, voire l'existence même d'un pôle sud.

Pour garder une trace de cette expérience, des "timelapses" ont été réalisés ([1](https://www.youtube.com/watch?v=n9_cU3EDWG4) et [2](https://www.youtube.com/watch?v=xR3wPw2MoG0)). Dans [une vidéo](https://www.youtube.com/watch?v=dEc86p1vgLM), SciManDan évoque les réactions d'autres "platistes" américains au sujet de cette expédition, qu'ils considèrent factice malgré la présence sur les lieux de leurs 3 acolytes.

Vous pourriez dire "je m'en bats les reins de tout ce cirque" et je ne vous donnerais pas tort. Mais cette histoire me donne juste l'occasion de présenter un outil intéressant en Python qui s'appelle **cartopy**.

## Cartopy

Cartopy est un package Python conçu pour le traitement de données géospatiales afin de produire des cartes et d’autres analyses de données géospatiales :

https://scitools.org.uk/cartopy/docs/latest/#

On y retrouve notamment un grand nombre de projections cartographiques :

https://scitools.org.uk/cartopy/docs/v0.15/crs/projections.html

Une collection bien fournie d'exemples donne l'étendue des possibilités :

https://scitools.org.uk/cartopy/docs/latest/gallery/index.html

Essayons d'utiliser ce package pour localiser le point d'observation pour les "timelapses" précédemment évoqués, sur une carte [Day and Night World Map](https://www.timeanddate.com/worldclock/sunearth.html) disponible sur le site [timeanddate.com](https://www.timeanddate.com/).

Selon les informations données sous les vidéos, ce point est située à la longitude 82°48'21" ouest et la latitude 79°44'24" sud. La date d'observation est le 15 décembre 2024. La carte "Day and Night World Map" peut être récupérée à cette date, à 5h28 UTC, de sorte qu'il soit minuit (heure solaire) au point considéré. On vérifiera ainsi qu'il fait bien jour à minuit en ce point, sur différentes projections cartographiques.

On suivra ces étapes :
- Installation du package
```
pip install cartopy
```
- Données d'entrée
```
# 15 décembre 2024 à 5h28
date_choisie = '2024-12-16 05:28'
# longitude 82°48'21" ouest, latitude 79°44'24" sud
longitude = -(82+48/60+21/3600)
latitude = -(79+44/60+24/3600)
```
- Récupération d'une image sur le site timeanddate.com
```
On construit le lien menant directement à l'image (https://www.timeanddate.com/scripts/sunmap.php?iso=20241216T0528),
puis on lance une requête pour la télécharger. De façon aléatoire, le fichier image peut avoir le format JPG ou PNG,
mais ce n'est pas gênant pour la suite.
```
- Fichier image récupéré
```
20241216T0528.jpg ou 20241216T0528.png
```
- Visualisation de l'image
- Exploitation de l'image avec cartopy
- Ajout des lignes de côte
- Lieu du tournage (projection cylindrique équidistante)
- Lieu du tournage (projection orthographique centrée sur le pôle sud)
- Lieu du tournage (projection azimutale équidistante centrée sur le pôle sud)
- Projection orthographique centrée sur 80°W 45°S
- Projection azimutale équidistante centrée sur le pôle sud
- Cartes "jour et nuit" de cartopy
```
On peut se passer de l'image fournie par timeanddate
```

## Le notebook

Voici le [notebook](cartopy.ipynb) permettant de suivre et d'exécuter les étapes décrites.

## Quelques illustrations obtenues avec l'exécution du notebook

![image](https://github.com/user-attachments/assets/57bb8c34-b520-4dd6-85c5-f8e606e403ce)

![image](https://github.com/user-attachments/assets/5dee885b-40c5-4f23-b69b-484647c5bc04)

![image](https://github.com/user-attachments/assets/2209e72e-8253-41b5-95c5-a6fe83fb7afb)

![image](https://github.com/user-attachments/assets/05129a65-24c2-4803-8ffa-0bb29313a36e)

![image](https://github.com/user-attachments/assets/1dfeb5e6-e0a8-4b24-988e-42ccb2ceca2f)





