# Circuitos Eléctricos — Modelado con EDOs y Simulación Numérica

Proyecto final de la asignatura **Matemáticas IV** (2do año, Ingeniería en Inteligencia Artificial, UNSTA). Se desarrolla un análisis completo de los circuitos **RC**, **RL** y **RLC** en serie: modelado físico mediante las Leyes de Kirchhoff, deducción y resolución analítica de sus ecuaciones diferenciales ordinarias (EDO), y simulación numérica con el **método de Euler** en Python.

> 📄 Informe completo: [`PROYECTO_FINAL_-_GRUPO_1_-_Mat_IV.pdf`](docs/PROYECTO_FINAL_-_GRUPO_1_-_Mat_IV.pdf)
> 
> 📓 Simulaciones: [`SIMULACIONES_Grupo_1_Mat_IV.ipynb`](SIMULACIONES_Grupo_1_Mat_IV.ipynb)
> 
> 📋 Consigna: [`circuito.pdf`](docs/circuito.pdf)

## Equipo

- Barrios, Julieta Luján
- Pannuto, José Leandro
- Urday, Nazareno

**Docentes a cargo:** Lic. María Isabel Gianinni — Lic. Monge Silva, Matías Nicolás

## Descripción del proyecto

Los circuitos formados por resistencias (R), capacitores (C) e inductores (L) son la base de sistemas electrónicos en telecomunicaciones, procesamiento de señales y control. Su comportamiento dinámico se describe rigurosamente mediante EDOs derivadas de las Leyes de Kirchhoff.

El trabajo aborda tres circuitos en serie, cada uno con su propio tipo de EDO:

| Circuito | Tipo de EDO | Variable de interés | Constante de tiempo |
|---|---|---|---|
| RC | Lineal de 1er orden | Tensión en el capacitor v_C(t) | τ = RC |
| RL | Lineal de 1er orden | Corriente i(t) | τ = L/R |
| RLC | Lineal de 2do orden | Corriente i(t) | ω₀ = 1/√LC, ζ = R/2·√(C/L) |

Para cada circuito se realizó: obtención de la EDO a partir de la LKV, resolución analítica por factor integrante (1er orden) o ecuación característica (2do orden), ejemplo numérico con condición inicial, interpretación física, y validación mediante simulación con Euler.

## Contenido del informe

1. **Marco teórico** — conceptos físicos (corriente, voltaje, componentes) y matemáticos (EDOs de 1er y 2do orden, factor integrante, ecuación característica).
2. **Circuito RC** — EDO: `RC·dv_C/dt + v_C = V₀` → solución: `v_C(t) = V₀(1 − e^{−t/RC})`.
3. **Circuito RL** — EDO: `L·di/dt + Ri = V₀` → solución: `i(t) = (V₀/R)(1 − e^{−(R/L)t})`.
4. **Circuito RLC** — EDO de 2do orden; análisis del discriminante Δ = R²/L² − 4/LC para clasificar el régimen de amortiguación.
5. **Simulaciones** — implementación del método de Euler en Python para los tres circuitos, comparación con la solución analítica.
6. **Conclusiones**.

## Tipos de amortiguación (circuito RLC)

| Condición | Régimen | Comportamiento |
|---|---|---|
| Δ < 0 (ζ < 1) | Subamortiguado | Oscilaciones con amplitud decreciente |
| Δ = 0 (ζ = 1) | Críticamente amortiguado | Retorno más rápido al equilibrio sin oscilar |
| Δ > 0 (ζ > 1) | Sobreamortiguado | Retorno lento y suave, sin oscilaciones |

## Simulaciones (método de Euler)

Las simulaciones se implementaron en Python (Google Colab) usando el método de Euler explícito, que aproxima la solución de una EDO con la regla iterativa `x_{k+1} = x_k + f(t_k, x_k)·Δt`. Los tres circuitos fueron simulados y comparados con sus soluciones analíticas:

- **RC y RL:** convergencia prácticamente exacta entre la curva numérica y la analítica para pasos temporales pequeños.
- **RLC críticamente amortiguado:** diferencia de forma durante el transitorio, aunque ambas curvas convergen al mismo valor final.
- **RLC subamortiguado:** coincidencia en oscilaciones, sobrepaso inicial y convergencia al estado estable.
- **RLC sobreamortiguado:** curvas prácticamente superpuestas.


## Tecnologías

- Python (NumPy, Matplotlib)
- Google Colab
- Método de Euler (integración numérica de EDOs)
