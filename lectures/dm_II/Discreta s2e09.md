# Árboles

> **Definición**: Un árbol $T$ es un grafo no dirigido, conexo y acíclico.

## Propiedades

> **Teorema 9.1:** Un grafo $T$ es un árbol si y solo si entre todo par de vértices $u,v$ existe un único camino que los conecta.

**Demostración:** 
$\Rightarrow$ 
Por la definición de árbol, $T$ es conexo, por que existe al menos un camino. Demostremos que es único.
Supongamos que entre $u,v$ existen dos caminos $P,Q$ distintos. Entonces hay un vértice $x$ y un vértice $y$ tales que:
$$
\begin{eqnarray}
P & = & u \rightarrow^* x \rightarrow (p_i) \rightarrow y \rightarrow^* v \\
Q & = & u \rightarrow^* x \rightarrow (q_i) \rightarrow y \rightarrow^* v
\end{eqnarray}
$$
Donde, $u \rightarrow*x$ es idéntico en ambos caminos, y $y$ es el primer vértices después $x$ que aparece en ambos caminos.
Por tanto, hay dos caminos simples disjuntos de $x$ a $y$, lo que implica un ciclo, contradiciendo la definición de árbol.
$\Leftarrow$ Trivial $\blacksquare$ 

> **Teorema 9.2:** Si $T$ es un árbol de orden $n$ entonces tiene exactamente $n-1$ aristas.

**Idea de demostración:** Inducción en $n$, teniendo en cuenta en que toda arista en un árbol es puente. $\blacksquare$

> **Teorema 9.3:** Las siguientes proposiciones son equivalentes:
> - $T$  es un árbol
> - $T$ es conexo y tiene $n-1$ aristas.
> - T es acíclico y tiene $n-1$ aristas.

**Idea de demostración**:
- $(i) \Rightarrow (ii)$ Trivial.
- $(ii) \Rightarrow (iii)$ Demostrar el lema si $G$ es conexo, $|E| ≥ n-1$.
- $(iii) \Rightarrow (i)$  Ver que cada componente conexa de $T$ es un árbol, luego tiene $n_i-1$ aristas. Despejar la cantidad de componentes conexas. $\blacksquare$

> **Teorema 9.4**: Todo árbol no trivial ($n>=2$) contiene al menos dos hojas.

**Idea de demostración:** Sumar los grados asumiendo que $n-1$ vértices tienen grado $≥2$. $\blacksquare$

## Árboles abarcadores

Un árbol abarcador es un subgrafo abarcador que es un árbol.

> **Teorema 9.5:** Todo grafo conexo tiene un árbol abarcador.

**Idea de demostración:** El subgrafo abarcador conexo de menor tamaño tiene que ser un árbol. $\blacksquare$

Definamos la *distancia* de $u$ a $v$, como la longitud del camino más corto de $u$ a $v$. 
$$\delta(u,v) = min_{p:u \rightarrow v}\{ |p| \}$$
Decimos que un subgrafo abarcador $H$ de un grafo $G$ conserva las distancias desde cierto vértice $v$ si $\delta_H(v,u) = \delta_G(v,u)$.

> **Teorema 9.6:** En todo grafo conexo, para todo vértice $v$, existe un árbol abarcador que conserva las distancias desde $v$.

**Demostración:** Lo haremos por construcción.
Definamos los conjuntos $D_i = \{ u \in V \,|,\ d_G(v,u) = i \}$ para todo $i \in [1,k]$ donde $k$ es la máxima distancia en $G$. Definamos $D_0 = \{ v \}$. Evidentemente $\{ D_i \}$ es una partición de los vértices de $G$, pues $G$ es conexo, así que todo vértice pertenece a uno y solo uno de los conjuntos $D_i$.
Para cada vértice $u$ en cada conjunto $D_i, i>0$ existe al menos una arista $e$ que lo conecta con un vértice en $D_{i-1}$ pues por definición, existe un camino $p=v \rightarrow^* w \rightarrow u$ de longitud $i$ entre $v$ y $u$, por lo que existe un camino $p=v\rightarrow^* w$ entre $v$ y $w$ de longitud $i-1$ (que puede ser $0$ y por eso definimos $D_0$. Si hay más de una arista, sea $e_u$ la primera arista que cumple esta condición para el vértice $u$.
Sea $T$ el subgrafo abarcador donde $E(T) = \{ e_u \}$ es el conjunto de todas las aristas por cada vértice $u \in D_i, i > 0$. Evidentemente $|E(T)| = n-1$ pues existe una arista por cada vértice $u \in V - \{v\}$. Además, $T$ es conexo (¿por qué?). Luego, $T$ es un árbol.
Además, $T$ conserva la distancia por inducción en $i$. $\blacksquare$

# Emparejamiento

Un conjunto de aristas $e_{(i)} = \{ u_i, v_i \}$ y $xy$ en un grafo $G$ se dicen *mutuamente independientes* si $\bigcap_i \{u_i, v_i\} = \emptyset$, o sea si no comparten vértices.

> **Definición**: En un grafo $G$, un subcojunto $M \subseteq E$ de *aristas mutuamente independientes* es un **emparejamiento**.

Un emparejamiento es *maximal* si no se puede adicionar ninguna arista a $M$ que sea independiente con todas las además. Un emparejamiento es *máximo* si tiene la mayor cardinalidad entre todos los emparejamientos posibles.
## Emparejamientos máximos

Dado un emparejamiento $M$, todos los vértices en los que incide cualquier arista $e \in M$ se denominan *vértices $M$-emparejados*. El resto son vértices no $M$-emparejados.

Dado un emparejamiento $M$, un camino que alterna entre aristas de $M$ y $M^C$ se llama camino *$M$-alternante*. Si los vértices de ambos extremos son no $M$-emparejados, entonces se llama un **camino $M$-incremento**.

> **Teorema 9.7 (Berge):** Un emparejamiento $M$ es máximo si y solo si no existe ningún camino $M$-incremento.

**Demostración:** 
$\Leftarrow$ Si existe un camino $M$-incremento, se puede construir un emparejamiento de cardinalidad $|M|+1$.
$\Rightarrow$ Supongamos que $M$ no es máximo, demostremos que existe un camino $M$-incremento.
Sea $M^*$ un emparejamiento máximo, entonces $|M^*| > |M|$. Sea $H$ el subgrafo abarcador definido por $E(H) = M^* \,\Delta\, M = M^*-M \cup M - M^*$, o sea, las aristas que están en $M^*$ o en $M$ pero no en ambos.
Cada vértice en $H$ tiene grado $d_H(v) \leq 2$. Notemos que en este grafo están todas las componentes conexas son caminos o ciclos. Además, en cada camino o ciclo, las aristas en $E(H)$ alternan entre $M$ y $M^*$ (¿ por qué?). Luego, como todo ciclo tiene longitud par, y en $E(H)$ hay más aristas de $M^*$ que de $M$, tiene que existir una componente conexa $P$ que es un camino que empieza y termina con aristas de $M^* - M$.
Sean $u$ y $v$ los vértices extremos respectivos de dicho camino. Notemos que $u$ y $v$ no pueden ser $M$-emparejados. Supongamos que $u$ es $M$-emparejado, entonces hay una arista $e \in M, e \notin E(H)$ incidente en $u$, pero $e \notin M^*$ porque ya hay una arista incidente en $u$ en $M^*$, por tanto $e \in M - M^*$ lo que contradice que $e \notin E(H)$. Por el mismo motivo $v$ no es $M$-emparejado tampoco. Así que $P$ es un camino $M$-incremento. $\blacksquare$

## Emparejamiento en Grafos Bipartitos

> **Definición:** Sea $G = (X \cup Y, E)$ un grafo bipartito con $|X| \leq |Y|$, se dice que $X$ está (parcialmente) emparejado a $Y$ por $M$, si existe un emparejamiento $M$ que cubra todos los vértices de $X$. Si cubre todos los vértices de $Y$, diremos que $M$ es un emparejamiento perfecto.

De ahora en adelante usaremos la notación $N(X)$ para referirnos a la unión de las vecindades de todo vértice $x \in X$.
$$
N(X) = \bigcup_{x \in X} N(x)
$$

> **Teorema 9.8 (Hall):** En un grafo bipartito $G=(X \cup Y, E)$ existe un emparejamiento de $X$ a $Y$ si y solo si $|N(S)| \geq |S|$**Teorema para todo $S \subseteq X$ no vacío.

**Demostración:**
$\Rightarrow$
Sea $M$ el emparejamiento, sea $S \subseteq X$ un subconjunto cualquiera, por definición todo vértice $x \in S$ está $M$-emparejado. Sea $M(S)$ el conjunto de vértices $y \in Y$ correspondientemente emparejados a $S$. Por definición de emparejamiento, $|M(S)| = |S|$. Además, para todo vértice $y \in M(S) \Rightarrow y \in N(S)$ dado que está emparejado. Entonces $M(S) \subseteq N(S)$, luego $|N(S)| \geq |M(S)| = |S|$.
$\Leftarrow$
Supongamos que $|N(S)| \geq |S|$ pero $X$ no puede ser emparejado completamente. Sea $M$ el emparejamiento máximo, entonces $\exists v \in V$ tal que $v$ no está $M$-emparejado. 
Sea $Z$ el conjunto de vértices en $G$ que son alcanzables desde $v$ por caminos $M$-alternantes. Como $M$ es un emparejamiento máximo, el único vértice no emparejado en $Z$ es $v$ (¿por qué?).
Definamos $S = Z \cap X$ y $T = Z \cap Y$. Notemos que, por construcción, todos los vértices en $S$ deben estar $M$-emparejados con algún vértice de $T$, excepto $v$. Por lo tanto, $|T| = |S| - 1$, y $T \subseteq N(S)$.
Supongamos que hay un vértice $w \in N(S)$ tal que $w \notin T$. Esto significa que $w$ no está unido a $v$ por un camino $M$-alternante, pero entonces tendríamos un camino $M$-incremento, lo cuál es imposible porque $M$ es un emparejamiento máximo. Por tanto, $N(S) \subseteq T$, por lor que $N(S) = S$, y entonces $|N(S)| = |S| - 1 < |S|$, lo que contradice la hipótesis inicial. $\blacksquare$

Finalmente, vamos a demostrar un corolario interesante del teorema de Hall.

> **Teorema 9.9 (Teorema de los matrimonios):** Todo grafo bipartito regular de grado $r \geq 1$ tiene un emparejamiento perfecto.

**Demostración:**
Si $G$ es bipartito y regular con $r \geq 1$, entonces $r|X|$ = $r|Y|$ y por tanto $|X| = |Y|$.
Sea $S \subseteq X$ un subconjunto no vacío cualquiera de $X$. Sea $E_1$ las aristas incidentes en $S$ y $E_2$ las aristas incidentes en $N(S)$. Por definición de $N(S)$ tenemos que $E_1 \subseteq E_2$.
Entonces, si $|E_1| = r|S|$ y $|E_2| = r|N(S)|$ tenemos que $r|N(S)| ≥ r|S|$ por lo que $|N(S)| \geq |S|$. $\blacksquare$
