# Introducción a la Teoría de Grafos

*Narra la leyenda…*

![](gt-bridges-art.svg)

## Definiciones generales

> **Grafo** (no dirigdo): Par ordenado $G=(V,E)$ donde $V$ son los vértices, y $E$ son las aristas, un conjunto de pares de vértices $\{ u,v \}$ donde,  $u \in V, v \in V$.

En general, no queremos ni aristas repetidas ni aristas de un vértice a sí mismo (excepto cuando sí).

> **Grafo** (dirigido): Es un grafo donde los elementos de $E$  son pares ordenados.

En general nos concentraremos en los grafos no dirigidos.

Dos grafos pueden ser diferentes superficialmente aunque en la práctica sean prácticamente iguales, por ejemplo, si en un grafo cambiamos todos los nombres de los vértices. 

> Dos grafos $G_1$ y $G_2$ son **isomorfos** si y solo si existe una función biyectiva $f: V_1 \to V_2$ tal que si $u,v$  in $E_1$ entonces $f(u), f(v) \in E_2$ .

Todos los grafos isomorfos entre sí forman una **clase isomorfa**. En general cuando nos referimos a un grafo específico, nos referimos a la clase isomorfa de dicho grafo.

El complemento de un grafo $\hat{G}$ es el *único grafo* que contiene los mismos vértices y todas las aristas que no están en $G$.

Si $u,v$ in $E(G)$ entonces decimos que $u$ y $v$ son vecinos. 
Al conjunto de vecinos de $v$  lo denotamos por $N(v)$. 
A la cantidad de vecinos de $v$ se llama **grado** y se denota por $d(v)$.

> Una secuencia de vértices vecinos consecutivos donde no se repite niguna arista es un **camino**.

Si conectamos el nodo final de un camino al nodo inicial, tenemos un ciclo.
Un camino es **simple** si no se repite ningún vértice.

> **Teorema:** Si entre un par de vértices $u,v$ hay un camino, entonces hay un camino simple.

**DEMOSTRAR EN CLASE**

Si en un grafo, hay un camino entre todos los vértices, le llamamos **conexo**. En caso contrario, el grafo tiene una cantidad $>1$ de **componentes conexas**. Asociado a las componentes conexas tenemos dos conceptos importantes, respectivamente el **vértice (o arista) de corte**.

> Un vértice o arista se denomina **de corte** si su eliminación produce que aumenten la cantidad de componentes conexas.

- ¿Cuántas componentes conexas nuevas pueden aparecer en cada caso?

## Grafos notables

### Árboles

> Un árbol es un grafo conexo y acíclico. Un bosque es un grafo sin ciclos (no necesariamente conexo).

Los árboles son interesantes, además de por las aplicaciones computacionales, porque muchos teoremas en grafos generales son más fáciles de probar si consideramos árboles.

### Grafos bipartitos

Un grafo es $k$-partito si los vértices se pueden particionar en $k$ subconjuntos tal que ninguna arista quede entre vértices de un mismo conjunto.

El caso más interesante es el **grafo bipartito**. Estos grafos surgen naturalmente en uno de los problemas más importantes en ciencia de la computación, los *problemas de emparejamiento*, que estudiaremos más adelante.

### Otros

Hay grafos (o tipos de grafos) tan interesantes que tienen nombres específicos:
- $K_n$ es el **grafo completo** de $n$ nodos, o sea, donde todas las aristas están presentes.
- $K_{n,m}$ es el **grafo bipartito completo** de respectivamente $n$  y $m$ vértices en cada partición, donde todas las aristas posibles existen.
- $C_n$ es el **grafo cíclico** de $n$ nodos, donde todos los vértices tienen exactamente dos vecinos, y hay un solo ciclo en el grafo.
- $P_n$ es es grafo camino de $n$ nodos, donde todos los nodos excepto dos tienen exactamente dos vecinos, y hay un solo camino simple en el grafo.

## Subgrafos

> Dado un grafo $G_1$, un subgrafo $G_2$ es un grafo donde $V_2 \subseteq V_1$ y $E_2 \subseteq E_1$.

Existen dos tipos de subgrafos interesantes:
- **Subgrafo abarcador:** Si $V_2 = V_1$ 
- **Subgrafo inducido**: Si $E_2$ contiene todas las aristas posibles, o sea, $$E_2 = \left\{ uv \in E_1 \,|\, u, v \in V_2 \right\}$$
Si un subgrafo inducido es completo, se denomina **clique**.
Si un subgrafo inducido no tiene ninguna arista, se denomina **conjunto independiente.**

En un grafo $G$ y su complemento se cumple respectivamente que todo clique en $G$ es un conjunto independiente en $\hat{G}$. Por tanto, el clique de tamaño máximo de un grafo cualquiera es equivalente al conjunto independiente de tamaño máximo de su complemento.

## Ejemplo de demostración formal

Con estos conceptos podemos demostrar nuestro primer teorema formalmente, para tener una idea de cómo atacar las demostraciones de grafos.

> **Teorema**: En todo grafo, la suma de los grados de los vértices es igual al doble de la cantidad de aristas: 
> $$\sum_{v \in V} d(v) = 2 | E |$$

Una manera intuitiva de ver que esto es cierto es notar que cada arista añade 2 a la suma de grados, 1 por cada vértice. 

¿Cómo formalizamos esta idea?

Vamos a hacer inducción en la cantidad de vértices. Para ello tenemos que ver cómo un grafo de $n$ vértices se convierte en un grafo de $n+1$. Pero es difícil ver cómo de un grafo con $n$ vértices llego a cualquier posible grafo con $n+1$ vértices. Por lo tanto, lo que vamos a hacer es lo contrario.

Asume que tengo un grafo cualquiera $G$ de $n$ vértices. Escoge un vértice cualquiera $v$ y elimínalo con todas sus aristas. Sea $G’$ el grafo resultante.

$$G’ = (V(G) - \{v\}, E(G) - \{uv \in E(G) \,|\, u \neq v\})$$
Como $G'$ tiene menos de $n$ vértices, se cumple la hipótesis:

$$
\sum_{u \neq v} d'(u) = 2|E(G)| - 2|\{uv \in E(G) \,|\, u \neq v\}|
$$
Pero lo que tengo a la izquierda es simplemente $d(v)$, la cantidad de vértices vecinos de $v$:
$$
\sum_{u \neq v} d'(u) = 2|E(G)| - 2d(v)
$$
Sumando $2d(v)$ a ambos lados:
$$
\left(\sum_{u \neq v} d'(u)\right) + 2d(v) = 2|E(G)|
$$

Ahora vamos a abrir la sumatoria en dos conjuntos de vértices, los adyacentes a $v$ y el resto.
$$
\left(\sum_{u \notin N(v)} d'(u) + \sum_{u \in N(v)} d'(u)\right) + 2d(v) = 2|E(G)|
$$
Ahora nos toca comparar $d’$ con $d$. Por la forma en que obtuvimos $G’$, podemos decir que $d’$ se define como:
$$
d'(u) = \left\{ \matrix{d(u) & u \notin N(v)\\ d(u) - 1 & u \in N(v)} \right.
$$
Reescribiendo:
$$
\left(\sum_{u \notin N(v)} d(u) \right) + \left( \sum_{u \in N(v)} d(u) - 1\right) + 2d(v) = 2|E(G)|
$$
Sacando el $1$ de la sumatoria y mezclando los primeros dos términos:
$$
\left(\sum_{u \neq v} d(u) \right) - |N(v)| + 2d(v) = 2|E(G)|
$$
Pero $|N(v)|=d(v)$ por definición.
$$
\left(\sum_{u \neq v} d(u) \right) - d(v) + 2d(v) = 2|E(G)|
$$
Y como $v$ es el único vértice que falta en la sumatoria, ya lo que queda es agrupar:
$$
\sum_{u \in V} d(u) = 2|E(G)| \,\,\ \blacksquare
$$
