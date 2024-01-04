# Caracterización de las canciones más escuchadas en Spotify en 2023
![image](https://github.com/karlarochaes/spotify-2023-hipotesis/assets/88100992/7eeb8062-6a33-47cc-9c51-7acbca704bfb)

---

## Tabla de contenidos
- [Introducción](#introducción)
- [Herramientas](#herramientas)
- [Procesamiento](#procesamiento)
- [Validación de hipótesis](#validación-de-hipótesis)
- [Resultados](#resultados)
- [Visualización](#visualización)
- [Conclusiones y recomendaciones](#conclusiones-y-recomendaciones)

## Introducción
Una discográfica tiene el objetivo de lanzar un nuevo artista en el escenario global, por lo que desea entender qué factores hacen que una canción sea exitosa en la actualidad. Para ello, la discográfica planteó cinco hipótesis sobre qué hace que una canción sea más escuchada. Estas hipótesis fueron confirmadas o refutadas a partir del análisis de un conjunto de datos con las 947 canciones más escuchadas en Spotify en 2023.

## Herramientas
- SQL (Google BigQuery)
- Python ([Google Colab](https://colab.research.google.com/drive/1Vq0BOw6nHnrbLTKc5unCCr2E8173U8DU?usp=sharing))
- Power BI

## Procesamiento
### Limpieza
Se eliminaron de la base de datos cuatro canciones duplicadas y dos canciones con datos erróneos. Se eliminaron los caracteres especiales en el nombre de la canción y el nombre del artista. Asimismo, se descartaron las variables por un alto porcentaje de valores nulos o por su irrelevancia para este análisis en particular.

### Creación de nuevas variables
- `playlists_total`: suma de las apariciones en las playlists de Spotify, Apple y Deezer.
- `cantidad`: total de canciones por artista.
  
Para cada característica de la canción, se crearon dos nuevas variables
- `quartile`: cuartil asignado dependiendo del rango de la característica técnica de la canción. Puede tener los valores 1, 2, 3 o 4.
- `category`: categoría de la canción de acuerdo con el cuartil asignado. A los cuartiles 1, 2 y 3 se les asignó el grupo Bajo, mientras que al cuartil 4 se le asignó el grupo Alto. 
  
## Validación de hipótesis
Las hipótesis planteadas fueron:

1. Las canciones con un mayor BPM (Beats Por Minuto) tienen más éxito en términos de cantidad de streams en Spotify. 
2. Las canciones más populares en el ranking de Spotify también tienen un comportamiento similar en otras plataformas como Deezer.
3. La presencia de una canción en un mayor número de playlists se relaciona con un mayor número de streams.
4. Los artistas con un mayor número de canciones en Spotify tienen más streams totales.
5. Las características de la música influyen en el éxito en términos de cantidad de streams en Spotify.

Cada una de las hipótesis se exploró mediante el cálculo del coeficiente de correlación entre la variable `streams` y otras variables y mediante la observación de la relación de las variables en gráficos de dispersión. Además, para la hipótesis 5 se utilizaron pruebas de significancia estadística (Test de Wilcoxon).

## Resultados
Para cada una de las hipótesis, se encontraron los siguientes puntos:
1. El valor de correlación entre `streams` y `bpm` fue cercano a cero, por lo que estas variables no están relacionadas.

![image](https://github.com/karlarochaes/spotify-2023-hipotesis/assets/88100992/d5b040a7-5b9f-4e2d-b09b-3909a78e36d3)

2. Se encontró una correlación positiva entre la posición de una canción en los rankings de Spotify (`in_spotify_charts`) y la posición en el ranking en otras plataformas como Apple (`in_apple_charts`) y Deezer (`in_deezer_charts`).

![image](https://github.com/karlarochaes/spotify-2023-hipotesis/assets/88100992/798f437e-6a1e-4e02-9e85-f3d91d71e1af)

![image](https://github.com/karlarochaes/spotify-2023-hipotesis/assets/88100992/1e89264b-5dd7-4487-bd20-36cbc9830345)
   
3. El número de apariciones de una canción en las playlists se correlacionó positivamente con la cantidad de `streams`.
   
![image](https://github.com/karlarochaes/spotify-2023-hipotesis/assets/88100992/c933da66-966c-4d3a-8d3e-e5b9e84f735c)

4. Varios artistas con diferente cantidad de canciones acumularon la misma cantidad de `streams`, por lo que la cantidad de canciones en la plataforma no determina el éxito musical.

![image](https://github.com/karlarochaes/spotify-2023-hipotesis/assets/88100992/11d1984c-158c-463d-b57e-460a6f2504c4)

5. Sólo las características de danceability y speechiness tuvieron una diferencia significativa en el promedio de cantidad de streams por grupo (alto y bajo).

![image](https://github.com/karlarochaes/spotify-2023-hipotesis/assets/88100992/d081a4e4-9bc0-4402-b82d-51320ee4434e)

## Visualización
Los resultados más relevantes del análisis se presentaron en un dashboard en Power BI, el cual está disponible para descargar desde este repositorio.

![image](https://github.com/karlarochaes/spotify-2023-hipotesis/assets/88100992/646f13df-ddac-4acb-8f62-5bef77ea2481)

## Conclusiones y recomendaciones
- El nuevo artista podría elaborar canciones considerando qué tan adecuada es la pieza para bailar y la cantidad de palabras que tiene.
- Es clave que las canciones del nuevo artista aparezcan en diversas playlists, ya que esto contribuirá a que sea más escuchado.
- Es mejor enfocarse en pocas canciones de gran impacto. Esto permitirá optimizar los recursos de producción.
- Más allá de las características técnicas, otros factores podrían relacionarse con el éxito musical de una canción, por ejemplo: estrategias de marketing, género musical, aspectos demográficos de los consumidores, entre otras. Es recomendable explorar también estas variables en función de las características del nuevo artista.
