
# Clase: Principios de Alineamiento de Secuencias (Local vs Global)

## Objetivo de la clase
Al final de esta sesión el estudiante será capaz de:
- Comprender los principios básicos del alineamiento de secuencias.
- Diferenciar entre alineamiento **global** y **local**.
- Reconocer los algoritmos clásicos asociados a cada enfoque.
- Aplicar herramientas en línea para realizar alineamientos.
- Interpretar resultados y discutir aplicaciones biológicas.

Duración estimada: **≈3 horas** (1.5 h teoría + 1.5 h práctica/ejercicios)

---

## 1. Introducción 

El **alineamiento de secuencias** es una de las técnicas centrales en bioinformática.  
Permite:
- Comparar secuencias de ADN y o proteínas.
- Identificar regiones de similitud evolutiva o funcional.
- Predecir estructuras y relaciones filogenéticas.

Existen dos enfoques principales:

- **Alineamiento Global**: compara secuencias completas.
- **Alineamiento Local**: compara subsecuencias altamente similares.

---

## 2. Fundamentos teóricos 

### 2.1 Alineamiento Global
- Busca maximizar la similitud a lo largo de toda la secuencia.
- Algoritmo clásico: **Needleman–Wunsch (1970)**.
- Adecuado cuando:
  - Las secuencias son de longitud similar.
  - Se desea comparar genes ortólogos*.
  - Ejemplo: comparar el gen *cox1* de dos especies cercanas.

*Ortólogos: genes que derivan de un ancestro en común y tienen la misma función en diferentes organismos.

**Ejemplo simplificado:**

Algoritmo de Needleman-Wunsch Explicado Sencillamente
📘 ¿Qué es?
Es un método para comparar dos secuencias (como ADN o proteínas) y encontrar la mejor forma de alinearlas, incluso si necesitan espacios vacíos (huecos).


🧩 ¿Cómo funciona? (En 3 pasos)
1. Crear una tabla
Se hace una tabla donde:
Arriba va una secuencia (ej: A G)
Izquierda va la otra (ej: A A G)
La primera fila y columna se llenan con números negativos (-1, -2, -3...) por los "huecos"

2. Llenar la tabla
Para cada casilla:

✅ Si las letras coinciden: Sumar puntos (+1)
❌ Si no coinciden: Restar puntos (-1)
➖ Por huecos: Restar puntos (-1)
Siempre se elige la opción con más puntos

3. Seguir el camino de regreso

Desde la esquina inferior derecha, se sigue el camino de más puntos hacia atrás
Así sabemos dónde poner los huecos

👀 **Ejemplo Súper Sencillo**
Secuencias: "AG" y "AAG"

Tabla resultante:
### Ejemplo de matriz de alineamiento

Secuencias a alinear:  
- Horizontal: `A A G`  
- Vertical: `A G`  

Matriz de puntuación (con penalización por huecos):

|   |   | A | A | G |
|---|---|---|---|---|
|   | 0 | -1 | -2 | -3 |
| A | -1 |  1 |  0 | -1 |
| G | -2 |  0 |  0 |  1 |


Mejor alineación:

text
A - G   (con un hueco)
A A G
---

### 2.2 Alineamiento Local

- Busca subsecuencias con similitud significativa.
- Algoritmo clásico: **Smith–Waterman (1981)**.
- Adecuado cuando:
  - Las secuencias son muy diferentes en longitud.
  - Se buscan **motivos conservados** (p. ej., sitios activos de enzimas).
  - Ejemplo: identificar un dominio funcional en una proteína.

**Ejemplo simplificado:**

```
Secuencia A: ATGCTAGC
Secuencia B:   GCTAG
```
El algoritmo Smith-Waterman es como el "buscador de fragmentos iguales" entre dos secuencias (como ADN o proteínas).

🧩 En esencia:
No compara las secuencias completas, solo busca trozos pequeños que sean idénticos o muy parecidos.

Es como encontrar párrafos copiados entre dos libros, sin importar el resto del contenido.

📌 Pasos muy simples:
Crea una tabla con una secuencia arriba y otra a la izquierda.

Rellena la tabla:
Si las letras coinciden → suma puntos (ej: +2).
Si no coinciden → resta puntos (ej: -1).
Si el puntaje es negativo → pon 0 (¡aquí está la clave!).
El número más alto en la tabla indica el inicio del fragmento igual.
Sigue el camino hacia atrás desde ese número hasta encontrar un 0 → eso te da el fragmento común.

👀 Ejemplo:
Secuencias: "TGCT" y "ACT"
Encuentra: Que "CT" es común.
Alineación:

text
T G C T  
- - C T  

🎯 ¿Para qué sirve?
*Encontrar genes similares en diferentes especies.
*Identificar dominios funcionales en proteínas.
*Detectar plagio en textos (en bioinformática, ¡claro!).

🔍 Smith-Waterman vs Needleman-Wunsch:

Smith-Waterman: Busca similitudes locales (fragmentos, trocitos).

Needleman-Wunsch: Alinea secuencias completas.
---

### 2.3 Diferencias clave

| Característica              | Alineamiento Global             | Alineamiento Local              |
|------------------------------|---------------------------------|---------------------------------|
| **Objetivo**                | Comparar toda la secuencia      | Comparar subsecuencias          |
| **Algoritmo**                | Needleman–Wunsch                | Smith–Waterman                  |
| **Uso típico**                | Genes ortólogos                 | Motivos/dominios conservados    |
| **Aplicación**               | Evolución, duplicaciones        | Función, búsqueda en bases de datos |
| **Sensibilidad**             | Buena en secuencias similares   | Buena en secuencias divergentes |

---

## 3. Ejemplos prácticos (30 min)

### 3.1 Herramientas en línea

- **NCBI BLAST** (local alignment):  
  👉 https://blast.ncbi.nlm.nih.gov/  
  
- **EMBOSS Needle** (global alignment):  
  👉 https://www.ebi.ac.uk/Tools/psa/emboss_needle/
    
- **EMBOSS Water** (local alignment):  
  👉 https://www.ebi.ac.uk/Tools/psa/emboss_water/
###¿cómo descargamos secuenciasde DNA/AA de [NCBI](https://www.ncbi.nlm.nih.gov/)?
---
### 3.1.1 Descarga 10 secuencias de gene ortólogos en formato fasta... :thinking:


### 3.2 Ejercicio 1 (Global)

1. Abrir **EMBOSS Needle**.  
2. Introducir dos secuencias de genes ortólogos (ej. *cox1* humano vs *cox1* chimpancé), **¿Qué otro gen?**.  
3. Observar:
   - Longitud del alineamiento.
   - Porcentaje de identidad.
   - Diferencias de inserción/deleción (gaps).

---

### 3.3 Ejercicio 2 (Local)

1. Abrir **BLASTp** (proteínas).  
2. Introducir una proteína con dominio conocido (ej. *p53* humano).  
3. Analizar los dominios conservados en especies distintas.  
4. Observar:
   - Regiones alineadas.
   - Valores de e-value *(número esperado de alineamientos por azar; mientras más bajo sea el E-value, más significativo es el alineamiento, Un E-value de 0.001 indica que hay una probabilidad muy baja (1 en 1000))*.

   - Porcentaje de identidad local.

---

### 3.4 Ejercicio 3 (Comparativo)
1. Tomar dos secuencias distantes (ej. *hemoglobina alfa* en humano vs *mioglobina* en pez).  
2. Realizar:
   - Un alineamiento global (Needle).
   - Un alineamiento local (Water).  
3. Discusión:
   - ¿Qué diferencias aparecen?  
   - ¿Cuál es más informativo en este caso?

---

## 4. Discusión y aplicaciones (≈15 min)

- **Global**:  
  - Comparación evolutiva de genomas completos.  
  - Estudios filogenómicos.  
- **Local**:  
  - Identificación de **motivos funcionales** en proteínas.  
  - Descubrimiento de dominios conservados.  
  - Herramientas de búsqueda en bases de datos (BLAST).

**Ejemplo real:**  
El uso de BLAST permitió identificar genes de resistencia a antibióticos en bacterias patógenas a partir de secuencias metagenómicas.

---

## 5. Ejercicios complementarios en línea (30 min)

- **Ejercicio A (BLASTn):**  
  Buscar similitudes entre una secuencia de ADN propia (p. ej., de un proyecto de laboratorio) y el genoma de bacterias conocidas.

- **Ejercicio B (BLASTx):**  
  Traducir una secuencia de ADN y compararla contra bases de datos de proteínas.

- **Ejercicio C (Multialineamiento):**  
  Explorar Clustal Omega 👉 https://www.ebi.ac.uk/Tools/msa/clustalo/  
  - Alinear tres secuencias homólogas.
  - Observar regiones conservadas.

---

## 6. Conclusión (5 min)

- El alineamiento global y local son **estrategias complementarias**.  
- La elección depende de la **pregunta biológica** y del **tipo de secuencias**.  
- Ambas herramientas son indispensables en bioinformática moderna.  

---

## 7. Referencias y lecturas recomendadas

- Needleman, S. B., & Wunsch, C. D. (1970). *A general method applicable to the search for similarities in the amino acid sequence of two proteins*. J. Mol. Biol. 48(3):443–453.  
- Smith, T. F., & Waterman, M. S. (1981). *Identification of common molecular subsequences*. J. Mol. Biol. 147(1):195–197.  
- Mount, D. W. (2004). *Bioinformatics: Sequence and Genome Analysis*. Cold Spring Harbor Laboratory Press.  
- NCBI BLAST Documentation 👉 https://blast.ncbi.nlm.nih.gov/Blast.cgi  

---
