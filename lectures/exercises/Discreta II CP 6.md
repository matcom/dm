# Discreta II

## Clase Practica #6

1. Demuestre que en un grafo la cantidad de vértices de grado impar es par.
2. Demuestre que para cualquier número de personas, no es posible que todas conozcan una cantidad distinta de personas.
3. Demuestre que si $G$ y $H$ son isomorfos por un isomorfismo $f$, entonces el $deg(v)$ vértice de G es igual al $deg(f(v)$ vértice de H. 
    1. Demuestre que si dos grafos son isomorfos, entonces, tienen la misma cantidad de aristas.

4. Demuestre que las siguientes definiciones son equivalentes:
    1. $G$ es un grafo acíclico y conexo
    2. $G$ es acíclico y $|E| = n-1$
    3. $G$ es conexo y $|E| = n-1$
    4. $G$ es conexo pero si se suprime una arista cualquiera, deja de serlo
    5. $G$ no tiene ciclos, pero si se añade una lista entre vértices no adyacentes, entonces se crea exactamente uno
    6. Todo par de vértices de G está conectado por exactamente un camino simple.

5. Demuestre que si $C$ es un clique e $I$ es un conjunto independiente, la cardinalidad de la intersección de $C$ e $I$ es $<= 1$.
6. Demuestre que $G$ es bipartito si y sólo si en $G$ no existen ciclos de longitud impar.
7. Demuestre que $G$ existe una cadena cerrada de Euler si y sólo si todos sus vértices tienen grado par.
8. Demuestre que $G$ tiene una cadena de Euler no cerrada si y sólo si tiene exactamente dos vertices de grado impar.
9. Demuestre que si para todo par de vértices no adyacentes $v,w$ se cumple que $deg(v)+deg(w) >= n-1$, entonces $G$ es conexo.
10. Demuestre que si $\Delta$(G) + $\delta(g)$ $<= n-1$, entonces $\Delta(G) <= 4$.
11. Demuestre que la cantidad de componentes conexas de $G$ es mayor igual que $n - m$.
12. Demuestre que en todo grafo con al menos 6 vértices, entonces $\alpha >= 3$ o $\omega >= 3$
13. Demuestre que $\sum_{i \in V(G)} {deg(i)\choose2} >= {n \choose 2}$
14. Demuestre que G es conexo o su complemento lo G.
15. Demuestre que si $v$ es punto de articulación de un grafo G conexo, entonces al quitar $v$, la cantidad de componentes conexas es a lo
sumo $deg(v) - 1$.
16. Demuestre que si $\delta(G) <=3$ existe un ciclo de longitud par.
17. Demuestre que si $n >= 9$, entonces $\alpha(G) >=4$ o $\omega(G) >=3$.
18. Demuestre que si $m >= \frac{(n-1)*(n-2)}{2} +1$, entonces G es conexo.
19. Demuestre que todo arbol con vértices de grado $k$ tiene al menos $k$ vértices de grado 1.
20. Demuestre que si G es un grafo sin vértices aislados que no tiene subgrafo inducido con exactamente 2 aristas, entonces G es un
grafo completo.
21. Demuestre que todo grafo $G$ contiene un subgrafo bipartito $G'$ tal que $|E(G')| >= \frac{|E(G)|}{2}$

## Glosario

1. Una cadena es un camino que no repite aristas.
2. Una cadena cerrada es una cadena que comienza y termina en el mismo vértice.
3. Una cadena de Euler es una cadena que contiene a todas las aristas del grafo.
4. Una cadena cerrada de Euler es una cadena de Euler cerrada (Wao!).
5. $\Delta$(G) es el mayor grado entre todos los vértices de G.
6. $\delta$(G) es el menor grado entre todos los vértices de G.
7. La distancia entre dos vértices es la longitud de su camino simple más corto.
8. El diámetro de un grafo es la mayor distancia entre todas las existentes.
9. $n$ cantidad de vértices.
10. $m$ cantidad de aristas.
11. Un punto de articulación es un vértice tal que si se elimina, aumenta el número de componentes conexas de G.
