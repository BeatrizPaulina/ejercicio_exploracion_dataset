# 🐱🐶 Oxford-IIIT Pet · Minidataset didáctico

Este conjunto de datos es una **versión reducida y reorganizada del Oxford-IIIT Pet Dataset**, preparada exclusivamente con fines didácticos para el taller **«Del dataset a U-Net: segmentación de imágenes con Deep Learning»**.

El dataset original fue desarrollado por **Omkar M. Parkhi, Andrea Vedaldi, Andrew Zisserman y C. V. Jawahar** y contiene imágenes de perros y gatos correspondientes a **37 categorías**, con aproximadamente 200 imágenes por categoría.

Las imágenes presentan variaciones de escala, pose e iluminación y cuentan con anotaciones relacionadas con la raza, la región de la cabeza (*bounding box*) y la segmentación a nivel de píxel.

Para facilitar las primeras actividades de exploración, esta versión contiene únicamente **una pequeña selección de imágenes del dataset original**, organizada en una estructura simplificada.

> [!IMPORTANT]
> Este minidataset **no representa el conjunto completo de Oxford-IIIT Pet**.
>
> Su propósito es permitir que los participantes exploren la organización de un dataset, identifiquen sus componentes y comprendan cómo se relacionan las imágenes con sus anotaciones.
>
> No está diseñado para entrenar o evaluar modelos de segmentación de manera representativa.

---

## 📁 Estructura del minidataset

Los archivos se encuentran organizados en directorios separados por categoría o clase.

Dentro de cada directorio se almacenan conjuntamente:

- Una **imagen fotográfica** en formato `.jpg`.
- Su correspondiente **máscara de segmentación** en formato `.png`.
- Un archivo de **anotaciones** en formato `.xml`.

Además, en la raíz del minidataset se encuentra el archivo `anotaciones.json`, que contiene los metadatos de las imágenes.

La estructura general es:

```text
minidataset/
├── anotaciones.json
├── clase_01/
│   ├── imagen_01.jpg
│   ├── imagen_01.png
│   └── imagen_01.xml
├── clase_02/
│   ├── imagen_02.jpg
│   ├── imagen_02.png
│   └── imagen_02.xml
└── ...
```

> [!NOTE]
> Los nombres de los directorios y archivos anteriores son ilustrativos.
>
> Lo importante es reconocer que cada categoría tiene su propio directorio y
> que los archivos correspondientes a una misma muestra comparten el **mismo
> nombre base**, pero tienen extensiones diferentes.

---

## 🧩 Componentes del minidataset

| Componente | Formato | Descripción |
|---|---|---|
| **Imagen** | `.jpg` | Fotografía original del animal. Constituye la entrada para un modelo de segmentación. |
| **Máscara** | `.png` | Anotación espacial que identifica las regiones de la imagen a nivel de píxel. |
| **Anotación individual** | `.xml` | Contiene atributos de la imagen, como sus dimensiones, clase y *bounding box* de la cabeza del animal. |
| **Metadatos del dataset** | `.json` | Archivo `anotaciones.json` con información descriptiva de las imágenes del minidataset. |

### 🖼️ Imágenes y máscaras

Cada fotografía tiene una máscara asociada que utiliza el mismo nombre base.

Por ejemplo:

```text
Sphynx_19.jpg
Sphynx_19.png
```

En este caso:

- `Sphynx_19.jpg` corresponde a la **imagen fotográfica**.
- `Sphynx_19.png` corresponde a su **máscara de segmentación**.

En el dataset original, las máscaras utilizan una representación denominada **trimap**, con tres valores de anotación:

| Valor | Significado |
|:---:|---|
| `1` | Primer plano (*foreground*). |
| `2` | Fondo (*background*). |
| `3` | Región no clasificada (*not classified*). |

> [!NOTE]
> Estos valores corresponden a la convención del dataset original.
> Durante la exploración del minidataset se podrá comprobar qué valores
> están presentes en las máscaras proporcionadas.

---

## 🏷️ Identificadores y categorías

Se conserva la convención de identificadores utilizada en el dataset original.

| Campo | Descripción | Valores |
|---|---|---|
| `class_id` | Identificador de la categoría o raza. | `1–37` |
| `species_id` | Identificador de la especie. | `1`: gato, `2`: perro |
| `breed_id` | Identificador de la raza dentro de cada especie. | Gatos: `1–25`; perros: `1–12` |

> [!IMPORTANT]
> Los identificadores conservan la convención del dataset original.
>
> Como este minidataset contiene únicamente una selección de muestras, **no
> necesariamente estarán representadas las 37 categorías**.

---

## 📐 Anotaciones XML

Cada muestra cuenta con un archivo `.xml` que almacena información descriptiva de la imagen.

Entre sus atributos se encuentran:

- **Tamaño de la imagen:** dimensiones de la fotografía.
- **Clase:** categoría a la que pertenece el animal.
- **Bounding box:** coordenadas del rectángulo que delimita la cabeza del animal.

### ¿Qué es un *bounding box*?

Un *bounding box* es un rectángulo utilizado para delimitar una región de interés dentro de una imagen.

En este dataset, el *bounding box* corresponde a la **región de la cabeza del animal**.

Es importante distinguirlo de la máscara de segmentación:

- El **bounding box** delimita una región mediante un rectángulo.
- La **máscara** identifica regiones a nivel de píxel.

Por lo tanto, representan **dos tipos diferentes de anotaciones espaciales**.

---

## 📄 Metadatos: `anotaciones.json`

El archivo:

```text
anotaciones.json
```

contiene los metadatos de las imágenes incluidas en el minidataset.

Su propósito es reunir información descriptiva que permita identificar y relacionar las muestras con sus características y anotaciones.

Durante las actividades del taller, este archivo servirá como punto de partida para explorar los metadatos y comprender su relación con los archivos de imágenes y máscaras.

---

## 🔎 Consideraciones para la exploración

Antes de utilizar un dataset, es importante conocer su organización y las convenciones utilizadas para almacenar sus archivos.

Durante la exploración de este minidataset, presta atención a:

1. **Estructura de directorios:** cómo están agrupadas las muestras.
2. **Nombres de archivos:** qué elementos permiten identificar una muestra.
3. **Extensiones:** cómo distinguir fotografías, máscaras y anotaciones.
4. **Correspondencia imagen–máscara:** cómo reconocer los archivos que pertenecen a una misma muestra.
5. **Metadatos:** qué información adicional describe cada imagen.
6. **Identificadores:** cómo se representan las categorías, especies y razas.

> [!TIP]
> No todos los datasets utilizan la misma estructura de directorios o las
> mismas convenciones de nombres.
>
> Antes de comenzar a procesar sus archivos, es importante consultar la
> documentación y comprender cómo se relacionan sus diferentes componentes.

---

## 📚 Dataset original y referencia

**Oxford-IIIT Pet Dataset**

**Autores:**

Omkar M. Parkhi, Andrea Vedaldi, Andrew Zisserman y C. V. Jawahar.

**Publicación:**

Parkhi, O. M., Vedaldi, A., Zisserman, A., & Jawahar, C. V. (2012).

*Cats and Dogs.*

IEEE Conference on Computer Vision and Pattern Recognition (CVPR).

**Página del dataset:**

https://www.robots.ox.ac.uk/~vgg/data/pets/

---

## ⚖️ Condiciones de uso

El Oxford-IIIT Pet Dataset original se distribuye con fines de investigación.

El uso de las imágenes debe respetar las condiciones correspondientes a los sitios web originales de los que fueron obtenidas, de acuerdo con lo indicado por los autores del dataset.

Esta selección reducida y su reorganización se realizaron con **fines exclusivamente didácticos** para las actividades del taller.

La preparación de este minidataset no modifica las condiciones de uso establecidas para las imágenes originales.