

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
_Ejemplo:_ 
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

*Ortólogos: genes que derivan de un ancestro en común y tiene la misma funcion en diferentes organismos.

**Ejemplo simplificado:**

```
Secuencia A: ATGCTAGC
Secuencia B: ATG--AGC
```

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

---

### 3.2 Ejercicio 1 (Global)
1. Abrir **EMBOSS Needle**.  
2. Introducir dos secuencias de genes ortólogos (ej. *cox1* humano vs *cox1* chimpancé).  
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
   - Valores de e-value.
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

## 4. Discusión y aplicaciones (15 min)

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
