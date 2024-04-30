# Tours

Vamos a estudiar dos tipos de recorridos en grafos que llamaremos *tours* porque de alguna manera involucran “todo” el grafo.

- Ciclos y caminos *Eulerianos*: son aquellos que involucran a **todas las aristas**.
- Ciclos y caminos *Hamiltoneanos* son aquellos que involucran a **todos los vértices**.

A pesar de parecer muy similares, veremos que ambos problemas son cualitativamente diferentes en cuanto a su complejidad.

## Grafos Eulerianos

> **Definición 10.1**: En un (multi)grafo $G=(V,E)$, un **ciclo (camino) euleriano** es un ciclo (camino) que contiene todas las aristas exactamente una vez. $G$ se denomina *grafo euleriano* si contiene un ciclo euleriano.

Notemos que en un ciclo euleriano, si un vértice $v$ aparece $k$ veces, debe tener $d(v) = 2k$. Extendamos esto a una condición necesaria y suficiente.

> **Teorema 10.1 (Euler y Hierholzer)**: Un (multi)grafo conexo $G$ no trivial es euleriano si y solo si todo vértice $v$ tiene grado par.

**Demostración:** 
$\Leftarrow$ Trival.
$\Rightarrow$ Vamos a hacer inducción fuerte en $m = |E|$. Si $m=2$ el único grafo posible es $K_{2,2}$ que evidentemente es euleriano.
Sea $G=(V,E)$ un grafo conexo no trivial con $m = |E| ≥ 3$ y todos los vértices de grado par. Si $n = 2$ entonces $m$ tiene que ser par, y el grafo es euleriano de forma trivial.
Supongamos $n ≥ 3$ entonces existen tres vértices distintos $u,v,w$ tal que $uv \in E, uw \in E$ (¿por qué?).
Sea $H=(V,E')$ el multigrafo donde $E’= E - \{uv, uw\} \cup \{ vw \}$, donde todo vértice sigue teniendo grado par. Hay dos opciones:
Si $H$ es conexo, como $|E’| < |E|$, en $H$ hay un ciclo euleriano. Reemplazando $vw$ por $uv, uw$ se obtiene un nuevo ciclo euleriano.
Si $H$ no es conexo, tiene dos componentes conexas, $H_v$ con los vértices $v$ y $w$, y $H_u$ posiblemente trivial, con el vértice $u$. En $H_v$ hay un ciclo euleriano por hipótesis de inducción fuerte. En ese ciclo, quitamos $vw$ y saltamos por $uv$ hacia $H_u$. Si $H_u$ es no trivial, tiene un ciclo euleriano que podemos recorrer y regresar a $u$, para luego regresar por $uw$ y completar el ciclo euleriano en $H_v$. $\blacksquare$

> **Teorema 10.2:** Un multigrado conexo $G$ tiene un camino euleriano si y solo si exactamente dos vértices $x$ e $y$ tienen grado impar. Además, estos vértices son los extremos del camino.

**Idea de demostración:** Reducción al teorema anterior añadiendo la arista $xy$.

> **Teorema 10.3:** Un multigrafo dirigido $G$ es euleriano si y solo si para todo vértice el grado entrada es igual al grado de salida.

**Idea de demostración:** Similar al 10.1 pero teniendo en cuenta la dirección.

### Notas de Algoritmia

Una vez vistos los teoremas anteriores, queda la pregunta de cómo encontrar un camino de Euler en la práctica. Aunque la demostración es constructiva, es bastante ineficiente, pues requiere encontrar un vértice conveniente que quitar. Una mejor solución es el algoritmo de Fleury, que no vamos a estudiar en detalle, pero podemos ver la idea intuitiva: en principio cualquier arista sirve para construir un camino de Euler, salvo si es un puente. 

## Grafos Hamiltoneanos

Si un grafo euleriano es aquel donde hay ciclos que usan todas las aristas, un grafo hamiltoneano va a ser el concepto equivalente cuando usamos todos los vértices.

> **Definición 10.2:** En un grafo $G$, un ciclo (camino) de Hamilton es un ciclo (camino) simple que contiene todos los vértices. Un grafo es hamiltoneano si tiene un ciclo de Hamilton.

A pesar de la similitud con Euler, en el caso de los grafos hamiltoneanos no se conoce ninguna condición cerrada de necesidad y suficiencia, y de hecho, se sospecha que no debe existir, ya que el problema de determinar si un grafo es de Hamilton es uno de los más conocidos problemas NP-Completos.

Vamos entonces a estudiar algunas condiciones de necesidad o suficiencia. Tres condiciones de necesidad evidentes son:
1. $G$ debe ser conexo,
2. $G$ tiene orden $≥ 3$, y
3. $G$ no tiene vértices de corte (¿por qué?).

Además, si denotamos por $k(G)$ la cantidad de componentes conexas de $G$, tenemos la siguiente condición (que generaliza la condición 3):

> **Teorema 10.4**: Si $G$ es un grafo hamiltoneano, y $S \subset V$ un subconjunto propio de los vértices de $V$, entonces $k(G-S) ≤ |S|$.

**Demostración:** Sea $C$ in ciclo de Hamilton, y $H=(V-S, E(C))$, el grafo definido por las aristas de $C$ quitando los vértices de $S$. Notemos que en $H$ toda componente conexa es un camino (¿por qué?). Además, $k(H) ≤ |S|$, pues es un ciclo (camino) todo vértice tiene grado a lo sumo $2$ y quitarlo crea a lo sumo una componente conexa adicional. (Puede pasar que no cree ninguna si este vértice es extremo de un camino). Pero $H$ es un subgrafo abarcador de $G - S$ por definición, por lo que $k(G-S) ≤ k(H)$. $\blacksquare$

**Nota:** La condición anterior es una condición necesaria pero no suficiente. Un grafo famoso que la cumple pero no es hamiltoneano es el grafo de Petersen (demostrar en CP).

### Teoremas de Dirac

Veamos ahora algunas condiciones suficientes. La idea más intuitiva para garantizar un ciclo de Hamilton es exigir que haya muchas aristas. Por ejemplo, si todo vértice tiene grado $d(v) \geq \frac{n}{2}$, intuitivamente, debemos poder encontrar un ciclo de Hamilton por palomar. Formalizemos esta idea.

> **Teorema 10.5 (Dirac):** Sea $G$ un grafo de orden $n ≥ 3$ con grado mínimo $\delta ≥ \frac{n}{2}$, entonces $G$ es hamiltoneano.

**Demostración:**
Para $n = 3$ tenemos que $\delta ≥ 2$ por lo que $G = K_3$ que es hamiltoneano.
Asumamos que $n \geq 4$.
Vamos a buscar el camino más largo y demostrar que es un ciclo hamiltoneano.
Sea $P = v_{1} \dots v_{k}$ el camino más largo en $G$, entonces todos los vértices adyacentes a $v_1$ están en $P$. Como $d(v) \geq \delta$, hay al menos $\frac{n}{2}+1$ vértices en $P$. 
Notemos que debe existir un $v_{i} \in P$ tal que $v_{k}$ es adyacente a $v_{i-1}$, pues de lo contrario, $d(v_{k}) < \frac{n}{2}$ (¿?). Entonces hay un ciclo $C$ que involucra todos los vértices de $P$.
Ahora notemos que todo vértice de $G$ debe estar en $C$. Si no fuera así, a lo sumo hay $< \frac{n}{2}$ vértices fuera de $C$. Asumamos que $u \notin C$, como $d(u) \geq \frac{n}{2}$, entonces $u$ debe ser adyacente a algún vértice de $C$, y entonces $P$ no sería el camino más largo.
Luego, $C$ es un ciclo de Hamilton.

**Nota:** Esta condición evidentemente no es necesaria, porque todo grafo cíclico $C_n$ es hamiltoneano por definición, y $d(v) < \frac{n}{2}$ si $n \geq 5$.

Extendamos esta condición a grafos bipartitos.

> **Teorema 10.6 (Dirac para grafos bipartitos):** Sea $G=(V_{1} \cup V_{2}, E)$ un grafo bipartito con $|V_{1}|=|V_{2}|=n \geq 2$, y grado mínimo $\delta > \frac{n}{2}$, entonces $G$ es hamiltoneano.

**Demostración:**
Supongamos que es falso. Sea $G$ un grafo maximal no hamiltoniano que cumple las hipótesis del teorema (¿por qué este grafo debe existir?).
Como $K_{n,n}$ es hamiltoneano, $G$ debe tener al menos un par de vértices $u \in V_{1}, v \in V_{2}$ no adyacentes entre sí. Además, como $G$ es maximal, $G + uv$ es hamiltoneano, por lo que $G + uv$ contiene un ciclo que pasa por la arista $uv$. Entonces en $G$ hay un camino de hamilton entre $u$ y $v$:
$$P: u=v_{1} \dots v_{2n} = v$$
donde $v_{2i} \in V_{2}$ y $v_{2i+1} \in V_{1}$ por ser $G$ bipartito.
Notemos entonces que si $v_1v_i \in E(G)$ entonces $v_{i}v_{2n} \notin E(G)$, pues de lo contrario habría un ciclo de Hamilton en $P$ (como en la demostración de Dirac).
Eso implica que por cada vértice adyacente a $v_1$ en $P$ hay un vértice no adyancente a $v_{2n}$ en $P$, por lo que: 
$$d(v_{2}) \leq n - d(v_{1}) < n - \frac{n}{2}$$
Lo cuál es una contradicción con la suposición inicial que $\delta > \frac{n}{2}$. $\blacksquare$
 
### Clausura

Vamos a definir ahora una operación *clausura* sobre grafos $cl(G)$ que consiste en adicionar todas las aristas $uv$ tales que $d(u)+d(v)\geq n$. Hay que demostrar que la operación clausura está bien definida.

Veamos entonces primero el siguiente teorema:

> **Teorema 10.7 (Bondy & Chvatal):** Sea $G$ un grafo con $u$, $v$ dos vértices no adyacentes tales que $d(u)+d(v)\geq n$. Entonces $G$ es hamiltoneano si y solo si $G + uv$ es hamiltoneano. 

**Idea de demostración:** Asumir que $G + uv$ es hamiltoneano, por lo tanto en $G$ hay un camino de Hamilton $P:u \rightarrow v$ entre $u$ y $v$. Notar que debe haber un par de vértices $v_{i-1},v_{i} \in P$ tales que $uv_i \in P$ y $v_{i-1}v \in P$, pues de lo contario la suma de los grados debe ser menor que $n$.

Con este teorema, es fácil demostrar que:

> **Teorema 10.8 (Bondy y Chvatal generalizado:** Un grafo $G$ es hamiltoneano si y solo si $cl(G)$ es hamiltoneano.

### Notas de Algoritmia

Encontrar un ciclo de Hamilton en un grafo es un problema sumamente complejo. Los mejores algoritmos conocidos para casos generales no dejan de ser exponenciales en el peor caso. De hecho, este problema es un conocido problema NP-Completo, por lo que la mayoría de los científicos sospecha que no existe ningún algoritmo eficiente, y por tal motivo, tampoco existe ninguna condición de necesidad y suficiencia simple y cerrada (pues daría un algoritmo eficiente). La demostración de que Hamilton es NP-Completo la veremos en DAA.

