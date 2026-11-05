# Inventario Forestal Nacional (IDEAM)

**Trabajo Final de Semestre Académico: Programación 1**

Software de consola en Python que apoya la ejecución del Inventario Forestal Nacional (IFN) del IDEAM, permitiendo registrar y consultar inspecciones de conglomerados.

---

## Integrantes

- Adrian David Santos Buitrago
- Freddy Stiven Rueda Hernandez
- Breyner Cermeño Castellanos

**Asignatura:** Programación 1
**Docente:** Ing. Carlos Carrascal

---

## 1. Planteamiento del caso

El IDEAM (Instituto de Hidrología, Meteorología y Estudios Ambientales) es la entidad oficial de investigación sobre el estado de los recursos naturales en Colombia. Uno de sus proyectos es el **Inventario Forestal Nacional (IFN)**, que comprende:

- Muestreo de ecosistemas boscosos y monitoreo del estado de los bosques.
- Registro de especies nuevas, amenazadas o en peligro de extinción.
- Labores de reforestación en zonas donde se pierden especies.
- Actualización normativa para el uso de especies maderables o para la producción de alimentos y medicamentos.

### Organización territorial y brigadas

El territorio colombiano se divide en **conglomerados**, que son asignados a **brigadas** de levantamiento de información conformadas por científicos, profesionales de distintas ramas y coinvestigadores locales.

### Proceso de recolección y procesamiento de muestras

1. Conformación de las brigadas e identificación de los conglomerados asignados.
2. Desplazamiento hasta el centroide del conglomerado, verificación de geolocalización y ubicación de las subparcelas.
3. Conteo de árboles según su diámetro: **fustales, latizales y brinzales**.
4. Toma de muestras: registro de nombre común, uso (medicinal, alimenticio o maderable) y asignación de código de identificación.
5. Envío al laboratorio de clasificación taxonómica para determinar el nombre científico.
6. Una vez clasificadas, las muestras permiten determinar a nivel municipal y departamental las especies presentes, sus usos y su distribución geográfica, además de indicadores como la densidad de cobertura vegetal.

> Para el primer pilotaje, el inventario incluye únicamente el muestreo de especies vegetales, sin considerar el muestreo de suelos.

---

## 2. Problema

Desarrollar un software que brinde soporte a la ejecución del Inventario Forestal Nacional. El sistema debe cumplir con los siguientes requisitos:

- Permitir la consulta de cualquier inspección, presentando los datos del conglomerado, de la brigada y los datos de conteo y muestreo.
- Desarrollarse en **arquitectura de tres (3) capas**.
- Implementar **persistencia de datos en archivos de texto plano**.
- Ofrecer interacción con el usuario mediante **consola**.

---

## 3. Solución implementada

### Funcionalidades

- **Registrar nueva inspección:** ID de inspección, datos del conglomerado, datos de la brigada, conteo de fustales, latizales y brinzales, y una o varias muestras (código, nombre común, uso y nombre científico, o "pendiente" si va a laboratorio).
- **Consultar inspección:** búsqueda por ID, mostrando los datos del conglomerado, la brigada, el conteo de árboles y las muestras recolectadas.
- **Validación:** los conteos de árboles deben ser numéricos.

### Arquitectura de tres capas

| Capa | Clase | Responsabilidad |
|---|---|---|
| Presentación | `CapaPresentacion` | Menú de consola, entrada y salida de datos con el usuario. |
| Negocio | `CapaNegocio` | Lógica del programa: armar el registro (`agregarInspeccion`) y buscarlo (`buscarInspeccion`). |
| Datos | `CapaDatos` | Lectura y escritura en el archivo de texto plano (`guardarRegistro`, `leerTodosLosRegistros`). |

### Persistencia

Los datos se guardan en el archivo `inspecciones.txt`, una inspección por línea, con los campos separados por `|` y las muestras separadas por `-`:

```text
idInspeccion|datosConglomerado|datosBrigada|conteoFustales|conteoLatizales|conteoBrinzales|codigoId:nombreComun:tipoUso:nombreCientifico-codigoId:nombreComun:tipoUso:nombreCientifico
```

---

## 4. Cómo ejecutar

Requisitos: Python 3.

```bash
python Parcial_3P.py
```

También se puede ejecutar la celda del cuaderno `Parcial_3P.ipynb` en Google Colab o Jupyter.

El menú principal ofrece:

```text
--- INVENTARIO FORESTAL NACIONAL (IDEAM) ---
1. Registrar nueva inspección
2. Consultar inspección
3. Salir
```

---

## 5. Entregables del trabajo

- **Pertinencia:** uso únicamente de las técnicas de Programación Estructurada vistas en clase.
- **Diseño de la estructura:** diagrama de flujo del algoritmo, con sección explicativa del funcionamiento.
- **Prueba de diseño:** verificación del diseño con cada conjunto de datos de prueba.
- **Implementación:** codificación del programa en Python.
- **Prueba de funcionalidad:** capturas de pantalla con evidencia paso a paso del funcionamiento.
- **Exposición del resultado final:** material de exposición y video de máximo 10 minutos.

### Composición de la nota

| Componente | Porcentaje |
|---|---|
| Diseño del algoritmo | 50% |
| Prueba de diseño | 10% |
| Implementación | 20% |
| Prueba de funcionalidad | 10% |
| Exposición del resultado | 10% |

---

## 6. Fuentes consultadas

- [La importancia del Inventario Forestal en Colombia, Planeta Caracol (Cadena Caracol, 2023)](https://caracol.com.co/2023/03/04/la-importancia-del-inventario-forestal-en-colombia/)
- [Inventario Forestal Nacional, IDEAM](http://www.ideam.gov.co/web/ecosistemas/inventario-forestal-nacional)
- Canal de YouTube del IDEAM: Primera expedición forestal, objetivo y misión del IFN, y entrevistas a integrantes de brigadas del IFN (Pacífico).
