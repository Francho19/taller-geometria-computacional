# Envolvente convexa con Jarvis March

**Estudiante:** Frank Jose Miranda Beleño  
**Código:** 0192526

Este README presenta el cálculo de orientación, la forma de contar las evaluaciones del algoritmo Jarvis March y el análisis de su complejidad.

## 2. Determinante y orientación

Dados los puntos A = (1, 2), B = (5, 3) y C = (3, 6), usamos:

**D = (Bx - Ax)(Cy - Ay) - (By - Ay)(Cx - Ax)**

**D = (5 - 1)(6 - 2) - (3 - 2)(3 - 1) = 16 - 2 = 14**

Como el resultado es positivo, A, B y C giran en sentido antihorario. Un valor negativo representa un giro horario, y un determinante igual a cero indica que los puntos son colineales.

Jarvis March utiliza esta prueba para encontrar el siguiente vértice de la envolvente. Desde el punto actual compara un candidato con los demás y lo actualiza según la orientación. El recorrido termina al regresar al punto inicial.

## 3. Conteo de evaluaciones

Se cuenta una evaluación cada vez que el programa calcula el determinante para comparar puntos durante la búsqueda del siguiente vértice. La selección del punto extremo inicial no se incluye. Los conjuntos se generaron con la semilla **917**, con puntos enteros entre 0 y 999 y sin repetir pares de coordenadas.

| Puntos de entrada (n) | Vértices de la envolvente (h) | Evaluaciones de orientación |
|---:|---:|---:|
| 10 | 6 | 51 |
| 50 | 11 | 538 |
| 100 | 11 | 1089 |

Los conteos dependen de los puntos generados y de cómo se implemente el ciclo. Con la misma semilla, el mismo generador y la misma lógica se obtienen los mismos resultados.

Para instrumentar el programa, inicialice un contador en cero antes de construir la envolvente, súmele uno justo antes de cada evaluación de orientación y muestre su valor al terminar.

## 4. Complejidad temporal

Si el ciclo externo se repite **h** veces y el ciclo interno revisa hasta **n** puntos, entonces:

**T(n, h) = c · n · h**

donde *c* es el tiempo constante de una evaluación. La complejidad es **O(nh)**.

Cuando **h = n**, se obtiene:

**T(n, n) = c · n² = O(n²)**

Este es el caso en que todos los puntos forman parte de la envolvente.

## 5. Comparación de costos

Se comparan los modelos **A = n · h** y **B = n · log₂(n)**. El menor valor representa menos operaciones estimadas.

| Caso (n, h) | A = n · h | B = n · log₂(n) | Menor costo |
|---|---:|---:|:---:|
| (100, 5) | 500 | 664,39 | A |
| (100, 50) | 5.000 | 664,39 | B |
| (1000, 900) | 900.000 | 9.965,78 | B |

Para *n* = 100, log₂(100) ≈ 6,6439; para *n* = 1000, log₂(1000) ≈ 9,9658. Cuando **h = 5**, el modelo **nh** da un costo menor. En los otros casos, **n log₂(n)** es menor. Jarvis March resulta conveniente cuando la envolvente tiene pocos vértices, pero el costo crece cuando *h* se acerca a *n*.

## Anexo: conjuntos de puntos

Los puntos aparecen en el orden de generación. Se usó la semilla 917.

<details>
<summary>Conjunto de 10 puntos</summary>

(971, 899), (453, 788), (315, 548), (438, 540), (505, 953)  
(219, 945), (506, 998), (142, 71), (248, 55), (923, 93)  

</details>

<details>
<summary>Conjunto de 50 puntos</summary>

(168, 682), (972, 598), (63, 875), (593, 458), (691, 405)  
(972, 950), (817, 624), (614, 294), (365, 392), (596, 776)  
(885, 800), (35, 113), (447, 400), (481, 517), (282, 328)  
(196, 99), (16, 424), (276, 352), (353, 732), (596, 631)  
(479, 976), (279, 647), (343, 940), (588, 991), (855, 877)  
(976, 358), (718, 10), (928, 921), (917, 77), (472, 196)  
(609, 805), (209, 122), (490, 864), (472, 562), (303, 261)  
(481, 186), (155, 215), (24, 280), (552, 50), (332, 230)  
(674, 326), (861, 980), (562, 73), (861, 262), (874, 496)  
(655, 119), (229, 447), (75, 194), (548, 256), (675, 252)  

</details>

<details>
<summary>Conjunto de 100 puntos</summary>

(895, 329), (703, 532), (496, 354), (529, 24), (552, 402)  
(753, 244), (177, 587), (384, 779), (629, 719), (985, 680)  
(559, 914), (507, 220), (880, 501), (842, 107), (710, 991)  
(31, 295), (59, 713), (930, 935), (667, 300), (287, 665)  
(510, 605), (692, 559), (966, 508), (691, 42), (886, 780)  
(865, 207), (113, 594), (597, 493), (151, 314), (415, 497)  
(146, 848), (639, 245), (195, 664), (58, 4), (871, 316)  
(477, 827), (369, 925), (675, 560), (744, 357), (823, 111)  
(710, 313), (989, 822), (318, 329), (512, 412), (230, 901)  
(11, 274), (545, 805), (634, 502), (506, 233), (408, 398)  
(961, 767), (765, 780), (307, 459), (688, 707), (942, 690)  
(324, 344), (261, 463), (657, 199), (981, 934), (53, 303)  
(617, 609), (709, 136), (271, 474), (761, 16), (962, 115)  
(799, 280), (830, 955), (642, 283), (536, 114), (937, 581)  
(620, 168), (561, 278), (244, 655), (189, 977), (966, 26)  
(80, 191), (114, 601), (112, 147), (90, 455), (0, 720)  
(105, 319), (152, 546), (821, 706), (469, 568), (879, 449)  
(103, 664), (900, 976), (324, 329), (97, 342), (362, 141)  
(55, 25), (487, 568), (838, 450), (489, 120), (524, 613)  
(446, 650), (509, 284), (637, 79), (163, 627), (365, 634)  

</details>

