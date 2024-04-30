# Coloración

## Coloración de vértices

> **Definición 11.1**: Una coloración (válida) de vértices en un grafo $G$ es una asignación de colores (etiquetas en general) a los vértices de $G$ tal que si $uv \in E(G)$ entonces $u$ y $v$ tienen colores diferentes.

Si la coloración usa $k$ colores diferentes, se llama una $k$-coloración.
Un grafo $G$ es $k$-coloreable si existe una $k$-coloración válida.
Una $k$-coloración particiona los vértices en $k$ conjuntos disjuntos, o $k$ clases de equivalencia.

El problema de decisión $D_{color}(G,k)$ consiste en determinar si $G$ es $k$-coloreable. Veamos dos casos particulares.

Un grafo $G$ es $1$-coloreable si y solo si $E(G) = \emptyset$.

> **Teorema 11.2:** Un grafo $G$ no trivial es $2$-coloreable si y solo si $G$ es bipartito.

Luego, para $k \in [1,2]$ el problema $D_{color}(G,k)$ es decidible en tiempo polinomial para todo $G$. Más adelante veremos que para ciertas familias de grafos especiales, también se puede decidir para $k > 2$. Sin embargo, en general, este problema es NP-Completo para $k > 2$.

> **Definición:** El número cromático $\chi(G)$ es el menor $k$ tal que $G$ es $k$-coloreable. Se dice que $G$ es $k$-cromático si $\chi(G) = k$.

Dado que el problema de decisión $D_{color}(G,k)$ es NP-Completo, es evidente que determinar $\chi(G)$ debe ser un problema difícil, y de hecho es NP-Duro. Pero podemos establecer algunos límites inferiores y superiores.

Notemos que si $H$ es un subgrafo de $G$, entonces $\chi(H) \leq \chi(G)$. Diremos entonces que $G$ es $k$-crítico si $\chi(H) < \chi(G) = k$ para todo subgrafo propio $H$.

> **Lema 11.3:** Si $G$ es $k$-cromático, entonces tiene un subgrafo $k$-crítico.

**Demostración:** Vamos a hacer un descenso. Si $G$ no es $k$-crítico, entonces tiene un subgrafo propio $H$ tal que $\chi(H) = \chi(G)$. Sea $H^*$ el subgrafo propio de menor orden tal que $\chi(H') = \chi(G) = k$. $H’$ tiene que ser $k$-crítico, pues de lo contrario tendría un subgrafo propio de menor orden $k$-cromático. 

> **Lema 11.4:** Si $G$ es $k$-crítico, entonces es conexo. 

**Demostración:** Si $G$ no es conexo, entonces $\chi(G) = max\{ \chi(G_{i}) \}$ para alguna de las componentes conexas $G_i$, por lo tanto $G$ no sería $k$-crítico.

> **Lema 11.5:** Si $G$ es $k$-crítico, entonces $\chi(G-u)=\chi(G-e)=k-1$ para todo vértice $u$ y arista $e$.

**Demostración:** Por definición de $k$-criticalidad, $\chi(G-u) \leq k-1$, $\chi(G-e) \leq k-1$. Supongamos que hay una arista $e=uv$ tal que $G-e$ es $(k-2)$-coloreable. Entonces el vértice $u$ se puede colorear con el color $k-1$ y por tanto $G$ no sería $k$-cromático. De igual forma con un vértice $u$ arbitrario.

> **Lema 11.6:** Si $G$ es $k$-crítico con grado mínimo $\delta$, entonces $\delta \geq k-1$.

**Demostración:** Asumamos que $\delta \leq k-2$ y sea $v$ un vértice de grado mínimo. Por condición de $k$-criticalidad, $\chi(G-v) = k-1$, pero en cualquier $k-1$-coloración de $G-v$ a lo sumo se necesitan $k-2$ colores para los vecinos de $v$. Por lo tanto, con $k-1$ colores se puede colorear $G$, lo que contradice que $\chi(G)=k$.

Demostremos entonces la primera cota para $\chi(G)$ para un grafo general.

> **Teorema 11.7:** En todo grafo $G$ con grado máximo $\Delta$ se cumple que $\chi(G) \leq \Delta+1$.

**Demostración:** Si $G$ es $k$-cromático, entonces tiene un subgrafo $k$-crítico $H$, donde se cumple que $\delta(H) \geq k-1$, pero entonces $\Delta(G) \geq \Delta(H) \geq \delta(H) \geq k-1$.

Además, podemos enunciar sin demostración la siguiente cota más ajustada.

> **Teorema 11.8 (Brooks):** $\chi(G) \leq \Delta(G)$ siempre y cuando $G$ no sea un grafo completo o un ciclo impar.

Finalmente, tenemos una cota inferior clara. Si $\omega(G)$ es el tamaño del mayor clique de $G$, está claro que $\chi(G) \geq \omega(G)$. Queda la pregunta de cuán ajustada es esta cota. ¿Son todos los grafos con número cromático grande, grafos que contienen un clique relativamente grande? Pues, sorprendentemente, no.

> **Teorema 11.9:** Para todo valor $k$ existe un grafo $G$ con $\chi(G)=k$ tal que $G$ no contiene ningún subgrafo isomorfo a $K_3$.

**Demostración:** Vamos a hacerlo por inducción en $k$. Para $k\in[1,2,3]$ tenemos $K_1$, $K_{2}$ y $C_{5}$. Asumamos $k>3$ y sea $G_{k-1}$ el grafo correspondiente a $k-1$ con $\chi(G_{{k-1}})=k-1$. Vamos a construir $G_{k}$ de la siguiente forma:
Por cada vértice $v_{i} \in V(G_{k-1})$ añadimos un vértice $u_{i}$ conectado a todos los vecinos de $v_{i}$. Luego añadimos un vértice $v$ más conectado a todos los $u_{i}$.
Notemos que en $G_{k}$ no puede haber triángulos, porque de haberlos, serían dos vértices de $G_{k-1}$ con un vértice $u_i$ de los nuevos (ya que en $G_{k-1}$ no había triángulos). Entonces podría construir un triángulo con $v_i$ también.
Notemos además que $\chi(G_{k}) \leq k$ porque puedo colorear cada $u_{i}$ con el mismo color que $v_{i}$ y me queda un color nuevo para $v$.
Asumamos entonces que $\chi(G_{k}) = k-1$. Entonces, hay al menos un color (supongamos sin pérdida de generalidad que es $k-1$) tal que ningún $u_i$ lo tiene. Pero como $\chi(G_{k-1}) = k-1$ entonces alguno de los $v_i$ tiene que tener ese color. Pero ese $v_i$ podemos colorearlo como $u_i$, ya que todos sus vecinos están bien coloreados. Luego, tendría una $k-2$-coloración para $G_{k-1}$.

## Coloración de aristas

Todas las definiciones aplican también para las aristas, solo que ahora no puede haber un vértice con dos aristas del mismo color.

Le llamamos *índice cromático* $\chi'(G)$  al menor $k$ tal que $G$ es $k$-arista-coloreable.

Dejaremos enunciado sin demostración el teorema fundamental de coloración de aristas:

> **Teorema 11.10:** En todo grafo se cumple que $\Delta \leq \chi'(G) \leq \Delta+1$.

De hecho, a medida que aumenta el orden del grafo, es mucho más probable que sea $\chi(G) = \Delta$, pero determinar si un grafo está en alguna de las dos categorías es un problema NP-Completo.