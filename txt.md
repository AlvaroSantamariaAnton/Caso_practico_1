
1. **Polinomio de Newton** y **Polinomio de Lagrange**:  
   - Los errores (SSE) son muy pequeños, en el orden de \(10^{-12}\) o incluso \(10^{-14}\).  
   - De hecho, ambos polinomios (Newton y Lagrange) son dos representaciones distintas del **mismo** polinomio de interpolación (de grado \(n-1\) si hay \(n\) puntos), por lo que sus errores finitos en los puntos originales se deben a efectos de redondeo numérico. En teoría, la interpolación polinómica en esos \(n\) puntos pasa exactamente por todos ellos, de modo que el error en los *puntos de entrenamiento* es cero (o prácticamente cero dentro de la precisión de máquina).

2. **Spline cúbico**:  
   - Presenta errores de magnitud del orden \(10^{-32}\) o \(0.0\) (dentro de la precisión numérica), lo cual también indica que se ajusta prácticamente al 100 % en los puntos de la tabla. Recordemos que un **spline cúbico** es otra técnica de interpolación, por lo que, en dichos \(n\) puntos, debería pasar exactamente por cada dato.  
   - La ventaja de un spline cúbico sobre un polinomio de grado elevado (Newton/Lagrange de grado 10) suele estar en la **estabilidad numérica** y en la menor tendencia a las “oscilaciones” entre puntos.

3. **Regresión no lineal (modelo exponencial)**:  
   - Aquí no estamos forzando el paso exacto por cada punto, sino que buscamos los parámetros \((a,b,c,d)\) que minimizan el error global (SSE). Los errores varían entre aproximadamente **10.8** y **28.2**, bastante más grandes que los métodos de interpolación (que prácticamente tienen SSE = 0 al usar los mismos puntos).  
   - Sin embargo, este modelo exponencial podría ser preferible si el interés es **extrapolar** fuera del rango de \(P\) cubierto por los datos o imponer cierta forma funcional más acorde con un modelo físico (si así lo dictan las leyes o ecuaciones). Con la interpolación polinómica, la extrapolación puede ser muy inestable.

---

### Conclusiones principales

- **Si el objetivo es solo “pasar por los datos”** (es decir, interpolar exactamente en los puntos conocidos), los tres métodos de interpolación (Newton, Lagrange y Spline cúbico) te darán esencialmente un error cero sobre esos puntos.  
- **Si además se busca suavidad y estabilidad numérica**, el **spline cúbico** suele ser preferible a un polinomio de alto grado (p. ej. Newton/Lagrange en grado 10), especialmente si se requieren predicciones “entre” puntos (interpolación interna).  
- **Si lo que interesa es un modelo simple para extrapolar** (o una curva con sentido físico), puede preferirse la **regresión exponencial** u otro modelo no lineal, a pesar de que el error exacto en los puntos de entrenamiento sea mayor.
