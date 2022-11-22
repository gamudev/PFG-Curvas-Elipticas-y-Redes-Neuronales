<div align="justify">

# Criptografía de Curvas Elípticas y Redes Neuronales

*Proyecto final presentado para optar al grado de Ingeniería del Software.*  
Alumno: [Javier García Muñoz](mailto:javier.garciamu@alumnos.upm.es)  
Director: [Ángel González Prieto](mailto:angel_gonzalez@ucm.es)  
Codirector: [Raúl Lara Cabrera](mailto:raul.lara@upm.es)  
[Escuela Técnica Superior de Ingeniería de Sistemas Informáticos](https://www.upm.es/)  
[Universidad Politécnica de Madrid](https://www.etsisi.upm.es/)

## Abstract en español

El objetivo de este proyecto es analizar el comportamiento y la eficacia de la criptografía de curvas elípticas sobre cuerpos finitos. Para ello, hemos presentado los fundamentos matemáticos necesarios para el estudio de conjuntos de elementos, como son los grupos, anillos y cuerpos. Estas colecciones, junto al Problema del Logartimo Discreto, sirven de base para estudiar el comportamiento y las propiedades de la criptografía de curvas elípticas. Por último, se realiza una investigación sobre el aprendizaje automático, concretamente en el campo de las redes neuronales artificiales. La unión de ambas partes, nos lleva finalmente a un caso práctico en el que ponemos a prueba los conocimientos adquiridos y la eficacia de las redes neuronales frente a dos algoritmos de cifrado: el cifrado César y el cifrado ElGamal sobre curvas elípticas.  

**Palabras clave:** *Criptografía, cuerpos finitos, curvas elípticas, redes neuronales.*

## Abstract en inglés

The aim of this project is to analyse the performance of elliptic curve cryptography on finite fields against machine learning of neural networks. To this end, we have focused on the study of the mathematical foundations necessary to be able to understand the properties of different sets of elements, such as groups, rings and fields. These collections, together with the Discrete Logarithm Problem, serve as a basis for understanding the behaviour and characteristics of elliptic curve cryptography. Finally, an introduction to the world of machine learning, in particular to the field of artificial neural networks, was given. Both theoretical parts come together in a practical case in which we test the knowledge acquired and analyse how this branch of artificial intelligence responds to two encryption algorithms: the Caesar cipher and the ElGamal cipher on elliptic curves.

**Key words:** *Cryptography, finite fields, elliptic curves, neural
networks.*

## Introducción


Durante siglos el ser humano se ha visto en la necesidad de realizar
comunicaciones secretas para preservar la privacidad de la información
transmitida, con el objetivo de que solo las personas autorizadas
pudieran leer dicha información. Podemos encontrar multitud de ejemplos
en la historia, desde el cifrador del César utilizado por los romanos,
hasta la máquina Enigma, utilizada por las fuerzas armadas alemanas
durante la Segunda Guerra Mundial. Con la llegada de la Era Digital y el
uso masivo de las comunicaciones digitales, ha aumentado el peligro de
que esas comunicaciones sean interceptadas, y para garantizar la
seguridad, se han desarrollado numerosos algoritmos, protocolos y
sistemas que protegen la información.


La criptografía es la técnica utilizada para el cifrado de dicha
información para dotar de seguridad a las comunicaciones. La palabra
criptografía proviene del griego, donde *Kryptos* significa oculto y
*graphia* significa escritura, y su definición es *arte de escribir con
clave secreta o de un modo enigmático*. Hay dos tipos fundamentales de
criptosistemas en función del tipo de cifrado: **simétricos** que son
aquellos que emplean la misma clave para cifrar y descifrar, y
**asimétricos** que emplean diferentes claves (pública y privada).

Uno de los problemas matemáticos en los que se basan algunos sistemas
criptográficos es el del logaritmo discreto. Su complejidad se debe a
que dados dos enteros *a* y *m* módulo *n*, calcular *a*<sup>*m*</sup>
es computacionalmente sencillo, pero conociendo *x* = *a*<sup>*m*</sup>,
es muy difícil calcular el exponente *m*. En algunos casos no hay ningún
algoritmo eficaz conocido para resolver el problema en general y la
complejidad en el caso promedio resulta tan difícil como en el peor de
los casos.

A lo largo del capítulo <a href="#chap:1" data-reference-type="ref"
data-reference="chap:1">[chap:1]</a>, se estudiarán las bases
matemáticas necesarias para la correcta comprensión del trabajo. Este
capítulo está dividido en tres partes: grupos, anillos y cuerpos.

Los **grupos** son estructuras algebraicas formadas por un conjunto de
elementos y una operación definida sobre dicho conjunto, que es cerrada,
asociativa, con un elemento neutro y con inverso para todos los
elementos que lo forman. A su vez, un grupo estará formado por
subconjuntos que cumplen las mismas propiedades, conocidos como
subgrupos. En este apartado, es fundamental la comprensión del Teorema
de Lagrange, que relaciona el orden o tamaño de grupos finitos y sus
subgrupos, de manera que el orden de los subgrupos es divisor del orden
del grupo. Además a lo largo de esta sección veremos algunos tipos de
grupos, grupos cocientes, homomorfismos de grupos y los teoremas de
isomorfía.

Los **anillos** además de cumplir las propiedades de un grupo, tienen
definidas dos operaciones sobre el conjunto de sus elementos, la de
producto y la de suma. A lo largo de esta sección, también trataremos
algunos tipos de anillos (como el anillo de polinomios), los dominios de
integridad, que son anillos conmutativos que carecen de elementos
divisores de cero, o los ideales de un anillo, que son conjuntos que
operados por otros elementos del anillo, derivan de nuevo en un elemento
del ideal.

Los **cuerpos** se diferencian de los anillos en que cumplen la
propiedad de tener inversos para ambas operaciones (excepto para el
elemento neutro de la suma). Esto significa que todos los elementos
menos los neutros, tienen inverso para la multiplicación. Dentro de esta
sección, se incluyen las extensiones de cuerpos, que son conjuntos más
grandes que los cuerpos donde además se pueden resolver ecuaciones
polinómicas. Por último, trataremos los cuerpos finitos y primos, los
cuales son esenciales en el desarrollo de este trabajo, ya que serán
utilizados para la criptografía de curvas elípticas.

Durante las últimas décadas, las curvas elípticas ha aumentado su
importancia tanto en la teoría de números como en campos como la
criptografía, hasta llegar a ser parte de algunos estándares
industriales. Este tipo de criptografía utiliza diferentes algoritmos
para cifrar o descifrar información a partir del problema del logaritmo
discreto, llegando a garantizar una seguridad equivalente a métodos
antiguos (como RSA), pero con la ventaja de trabajar con claves mucho
menores que en otros casos. Esto implica una mejora de rendimiento
significativa, y a su vez, el aumento de su uso en diferentes ámbitos,
como por ejemplo, tarjetas inteligentes o en la tecnología blockchain.

A lo largo del capítulo <a href="#chap:2" data-reference-type="ref"
data-reference="chap:2">[chap:2]</a>, se desarrollan conceptos acerca de
las **curvas elípticas**, sus propiedades y su uso en criptografía. Se
profundiza en la explicación sobre el problema del logaritmo discreto y
se pueden ver diferentes algoritmos de cifrado y su funcionamiento. La
intención de este trabajo es probar la seguridad del problema del
logaritmo discreto en curvas elípticas. Las curvas elípticas conforman
un campo de las matemáticas relativamente nuevo. Hasta el año 1985, no
se escucha hablar de estas curvas y su popularidad aumenta porque se
empiezan a implementar sistemas criptográficos más difíciles de romper,
cuyas claves son más pequeñas que con otros criptosistemas de clave
pública convencionales.

Durante el capítulo <a href="#chap:3" data-reference-type="ref"
data-reference="chap:3">[chap:3]</a> el tema principal es el
**aprendizaje automático** (machine learning). Este campo trabaja con
algoritmos que tratan de identificar patrones en conjuntos de datos, y a
partir de estos patrones, se crean modelos de datos para hacer
predicciones. El aprendizaje automático es utilizado en una gran
cantidad de aplicaciones, como reconocimiento del lenguaje escrito,
diagnósticos médicos, juegos, robótica o motores de búsqueda. Dentro del
aprendizaje automático encontramos dos tipos según si es el aprendizaje
es supervisado o no supervisado.

Concretamente, este capítulo expone las **redes neuronales
artificiales**. Estos algoritmos aprenden a través de un elemento de
retroalimentación, igual que los seres humanos siempre que tratamos de
aprender algo, lo hacemos tal y como nos han dicho que es la manera
correcta, por lo tanto, ajustamos nuestra conducta según los
conocimientos adquiridos. La retroalimentación en una red neuronal es
conocida como propagación hacia atrás y compara la salida de la red con
lo que resultado esperado. Para entrenar una red de esta manera, se
necesita un gran conjunto de ejemplos a partir de los cuáles, la red
pueda aprender.

El objetivo de este proyecto es comprobar la seguridad de la
criptografía de curvas elípticas a partir del aprendizaje automático.
Esto se prueba en el capítulo
<a href="#chap:4" data-reference-type="ref"
data-reference="chap:4">[chap:4]</a>. Al ser la primera vez que trabajo
con redes neuronales y debido a la complejidad que presenta la
criptografía de curvas elípticas, en este capítulo también se incluye
una prueba inicial frente al Cifrado César. Este consiste en desplazar
todas las letras el mismo número de posiciones, y este cifrado es mucho
más sencillo para que una red neuronal artificial aprenda a resolverlo.
Finalmente, nuestra red neuronal contra la criptografía curvas elípticas
se basa en el criptosistema de ElGamal, recibirá como parámetro de
entrada la clave pública del cifrado y tratará de devolver la clave
privada.

Tras realizar la diseño y el desarrollo de los modelos para ambas redes
neuronales, los resultados obtenidos han sido disparejos para cada caso.
Para el cifrado César, la red es capaz de encontrar un patrón para
resolver el algoritmo y se ve claramente el aumento de la precisión y la
disminución del error. Bien es cierto que este algoritmo es muy sencillo
y no representa ningún problema para el aprendizaje. Por otro lado, en
el caso de la criptografía de curvas elípticas, la red neuronal no es
capaz de mejorar la precisión, por lo tanto, no distingue el ruido y no
encuentra un patrón para alcanzar el resultado deseado.

# Fundamentos matemáticos de la criptografía

## Teoría de grupos

El estudio de algunos conceptos matemáticos es necesario para una
correcta comprensión del texto y de los puntos clave de esta memoria. La
criptografía es definida como el estudio de los algoritmos, protocolos y
sistemas, para los que se necesita una base matemática. A lo largo de
este capítulo, se estudiarán ciertos tipos de estructuras algebraicas y
los conjuntos de elementos, operaciones y propiedades que las forman,
como paso previo a la criptografía de curvas elípticas. En primer lugar
vamos a conocer la teoría de grupos, que será la estructura más básica
de la memoria y clave para entender los anillos y cuerpos. El contenido
de esta sección se ha desarrollado en base a los capítulos 4 y 5 del
libro *Números, grupos y anillos* de Eugenio Hernández y José Dorronsoro
. Además se recomienda una lectura previa del capítulo 3 sobre
congruencias, que serán utilizadas a lo largo del capítulo.

### Definición de Grupo

Un grupo es un conjunto no vacío de elementos *G* donde se encuentra
definida la operación binaria · (adición o multiplicación) como una
función *G* × *G* → *G* y se satisfacen las siguientes propiedades:

-   La operación binaria · es **cerrada** dentro del conjunto de
    elementos *G*. El resultado de la operación entre dos elementos del
    grupo G, será otro elemento del grupo.

-   La operación binaria · es **asociativa** entre los elementos del
    grupo. Dados tres elementos del grupo *G*, se verifica que el orden
    de ejecución de las operaciones entre ellos, no afecta al resultado
    final.
    *g*<sub>1</sub> ⋅ (*g*<sub>2</sub>⋅*g*<sub>3</sub>) = (*g*<sub>1</sub>⋅*g*<sub>2</sub>) ⋅ *g*<sub>3</sub>

-   Existe un elemento *e* que es **neutro**, de manera que la operación
    de cualquier elemento del grupo *G* con el neutro, equivale al
    elemento original. En caso de que la operación binaria sea la suma,
    también se conoce como **elemento cero** o **elemento nulo**.
    *g* ⋅ *e* = *g*

-   Todo elemento *g* del grupo *G* tiene un elemento **inverso**
    *g*<sup>−1</sup>. La operación binaria entre el elemento y su
    inverso, siempre equivale al elemento neutro.
    *g* ⋅ *g*<sup>−1</sup> = *e*

Otra forma para definir al grupo *G* con la operación binaria · es (*G*,
·).

El conjunto de los números reales tiene estructura de grupo con la
operación suma (ℝ, +). Su elemento neutro es el 0 y el inverso de *g* es
 − *g*, ya que *g* + (−*g*) = 0.

El conjunto de los números racionales no es grupo con la operación
producto (ℚ,×), debido a que el elemento 0 no tiene inverso.

#### Grupo conmutativo o abeliano

Todos los grupos *G* cumplen las anteriores propiedades, pero algunos se
caracterizan por tener otras. Aquellos en los que se cumpla la propiedad
conmutativa, es decir, si el resultado de la operación entre dos
elementos cualquiera, es el mismo, sea cual sea el orden de los
elementos, es conocido como grupo **conmutativo** o **abeliano**.
*g*<sub>1</sub> ⋅ *g*<sub>2</sub> = *g*<sub>2</sub> ⋅ *g*<sub>1</sub>

El conjunto de los números enteros (ℤ) junto con la operación de suma,
forman un grupo abeliano, ya que se cumplen todas las propiedades
anteriores.

#### Orden de un grupo

Se conoce como **orden de *G*** al número de elementos que forman un
grupo *G*, es decir, el orden es su cardinalidad, lo denotaremos como
\|*G*\| y diremos que es un grupo finito. Si el orden del grupo *G* es
1, entonces el grupo se denomina grupo trivial.

Hay que diferenciar entre el orden de un grupo y el orden de un
elemento. Posteriormente trataremos esto en profundidad, ya que es
necesario para entender el Teorema de Lagrange
(<a href="#thm:Lagrange" data-reference-type="ref"
data-reference="thm:Lagrange">[thm:Lagrange]</a>).

El orden del grupo formado por las clases de equivalencia módulo 2
(ℤ<sub>2</sub>) es 2, ya que está formado por \[0\] y \[1\].

### Ejemplos de grupos

Los siguientes ejemplos nos ayudarán a entender y profundizar en la
estructura de un grupo.

#### Grupo de congruencias

Se recomienda la lectura del capítulo 3 del libro *Números, grupos y
anillos* de Eugenio Hernández y José Dorronsoro , para una introducción
completa a la teoría de congruencias.

Una congruencia equivale a que dos elementos *a* y *b* tengan el mismo
resto al dividirlos por otro número m, conocido como módulo.
*a* ≡ *b*(*m*) ↔ *a* − *b* = *k**ṁ*

La relación de congruencia definida en el conjunto ℤ de los números
enteros es una relación de equivalencia, conocida como el conjunto de
las clases de congruencias módulo m.
ℤ<sub>*m*</sub> = \[0\], \[1\], \[2\], ..., \[*m*−1\]

En la teoría de congruencias citada anteriormente, se demostró que las
operaciones de suma y multiplicación están bien definidas en
ℤ<sub>*m*</sub> y son cerradas en el conjunto. Con la operación de suma,
(ℤ<sub>*m*</sub>,+) es un grupo abeliano, pero con la multiplicación,
no. Esto se debe a que al menos el elemento \[0\] no tiene elemento
inverso y no se cumple la propiedad (4). En caso de trabajar con otros
tamaños de modulo, nos encontramos con más elementos que no tienen
inverso, como por ejemplo \[2\],\[3\],\[4\] para ℤ<sub>6</sub>.

Para todo número entero positivo primo p,
(ℤ<sub>*p*</sub><sup>\*</sup>, ×) es un grupo abeliano con *p* − 1
elementos.

Para demostrar que la operación de adición es cerrada en el conjunto
ℤ<sub>*m*</sub><sup>\*</sup>, no puede darse el caso \[a\]×\[b\]=\[0\].
Si suponemos que se da ese caso, se deduce que *a* × *b* = *k* × *p*
para algún elemento *k* de ℤ; entonces *p* divide a *a* × *b*, o lo que
es lo mismo *p*\|*a* o *p*\|*b*. Esto implica que \[a\] o \[b\] equivale
a \[0\], contradiciendo que \[a\],\[b\] pertenecen al conjunto
ℤ<sub>*m*</sub><sup>\*</sup>.

#### Grupo simétrico *S*<sub>*n*</sub>

El grupo simétrico *S*<sub>*n*</sub> sobre un conjunto *C* es el formado
por las aplicaciones biyectivas del conjunto en sí mismo. Cuando el
conjunto es finito, se denomina grupo de permutaciones de *n* elementos,
es decir, las permutaciones son las diferentes formas de ordenar al
conjunto. A partir del conjunto formado por *n* números naturales
*C* = 0, 1, 2, ..., *n*, obtenemos el conjunto de todas sus biyecciones
*S*<sub>*n*</sub>.

La operación del grupo ∘ es la composición de funciones, que tiene que
ser cerrada. Para ello, necesitamos comprobar que para las aplicaciones
biyectivas *f*, *g* sobre *C*, *f* ∘ *g* es biyectiva también. A partir
de dos elementos del conjunto, tenemos que
*g* ∘ *f*(*x*) = *g* ∘ *f*(*y*), esto equivale a
*g*(*f*(*x*)) = *g*(*f*(*y*)) y como ambas funciones son inyectivas, se
demuestra que *x* = *y* y que *g* ∘ *f* es inyectiva. Para demostrar que
es sobreyectiva, basta con tomar *g*(*y*) = *z* y como *f* es
sobreyectica *f*(*x*) = *y*, *g*(*f*(*x*)) = *z*. Ha quedado demostrado
que la composición de aplicaciones es cerrada en *C* y se demuestra
fácilmente que es asociativa. Por último, hay que encontrar el elemento
neutro y que todos tienen un inverso. La aplicación identidad de *C* es
*I*<sub>*C*</sub>, que es nuestro elemento neutro y para para cualquier
*f* tenemos *f*<sup>−1</sup>, donde
*f*(*f*<sup>−1</sup>(*x*)) = *f*(*f*<sup>−1</sup>(*y*)), y
también,*f*<sup>−1</sup>(*x*) = *f*<sup>−1</sup>(*f*(*y*)) = *y*, por lo
que *f*<sup>−1</sup> es biyectiva. Como esta definición implica que
*f*<sup>−1</sup> ∘ *f*(*x*) = *f*(*x*) ∘ *f*<sup>−1</sup>, para
cualquier elemento *x* de *C*, podemos asegurar que *S*<sub>*n*</sub> es
un grupo.

Los elementos de *S*<sub>*n*</sub> se escriben de la siguiente manera:

$$\begin{pmatrix}
		1 & 2 & \cdots & n\\\\
		\alpha(1) & \alpha(2) & \cdots & \alpha(n)\\\\
	\end{pmatrix}$$

*S*<sub>*n*</sub> no es un grupo abeliano porque no es conmutativo, ya
que *f* ∘ *g* no es lo mismo que *g* ∘ *f*.

A partir de dos permutaciones *f*, *g* ∈ *S*<sub>3</sub> :

$$f = 
		\begin{pmatrix}
			1 & 2 & 3\\\\
			2 & 1 & 3\\\\
		\end{pmatrix}
		, \hspace{0.2cm} g =
		\begin{pmatrix}
			1 & 2 & 3\\\\
			3 & 2 & 1\\\\
		\end{pmatrix}$$

Y la operación cambiando el orden:

$$f \circ g = 
		\begin{pmatrix}
			1 & 2 & 3\\\\
			2 & 1 & 3\\\\
		\end{pmatrix}
		\circ
		\begin{pmatrix}
			1 & 2 & 3\\\\
			3 & 2 & 1\\\\
		\end{pmatrix}	
		=
		\begin{pmatrix}
			1 & 2 & 3\\\\
			3 & 1 & 2\\\\
		\end{pmatrix}$$

$$g \circ f = 
		\begin{pmatrix}
			1 & 2 & 3\\\\
			3 & 2 & 1\\\\
		\end{pmatrix}
		\circ
		\begin{pmatrix}
			1 & 2 & 3\\\\
			2 & 1 & 3\\\\
		\end{pmatrix}
		=
		\begin{pmatrix}
			1 & 2 & 3\\\\
			2 & 3 & 1\\\\
		\end{pmatrix}$$

De esta manera confirmamos que el grupo *D*<sub>3</sub> no es
conmutativo.

#### Grupo diédrico *D*<sub>*n*</sub>

Otro ejemplo de grupo es el diédrico o diedral *D*<sub>*n*</sub>, que se
obtiene a partir de la simetría de un polígono regular de *n* lados. Su
operación es la composición de los movimientos en el plano y se llaman
simetrías (rotaciones y reflexiones).

Para entender mejor las simetrías nos vamos a apoyar en la figura del
triángulo equilátero, también conocido como el grupo diedral
*D*<sub>3</sub>. La figura
<a href="#fig:simetrias" data-reference-type="ref"
data-reference="fig:simetrias">1.1</a> muestra las simetrías de un
triángulo equilátero. *I* sería la identidad, *A* (120º) y
*A*<sup>2</sup> (240º) las rotaciones en contra del sentido de las
agujas de un reloj y *B*<sub>0</sub>, *B*<sub>1</sub>, y *B*<sub>2</sub>
son las reflexiones.

<figure>
<img src="Figures/MAT1.jpg" id="fig:simetrias"
alt="Rotaciones de un triángulo equilatero" />
<figcaption aria-hidden="true">Rotaciones de un triángulo
equilatero</figcaption>
</figure>

$\newline$ Por lo que acabamos de ver,
*S*<sub>3</sub> = {*I*, *A*, *A*<sup>2</sup>, *B*<sub>0</sub>, *B*<sub>1</sub>, *B*<sub>2</sub>}
y podemos encontrar los resultados de sus operaciones en la tabla de
Cayley <a href="#fig:tablaCayley" data-reference-type="ref"
data-reference="fig:tablaCayley">1.2</a>.

<figure>
<img src="Figures/MAT3.jpg" id="fig:tablaCayley"
alt="Tabla de Cayley" />
<figcaption aria-hidden="true">Tabla de Cayley</figcaption>
</figure>

### Subgrupos

Dentro del conjunto de elementos que forman un grupo *G*, podemos
encontrar subconjuntos. Se dice que un subconjunto *H* es subgrupo de
(*G*, ·) y se escribe (*H*, ·) ≤ (*G*, ·) cuando *H* es un grupo junto
con la operación binaria · definida en *G* y cumple las siguientes
propiedades:

-   La operación binaria es **cerrada** en el subgrupo *H*.
    ∀ *h*<sub>1</sub>, *h*<sub>2</sub> ∈ *H* → *h*<sub>1</sub> ⋅ *h*<sub>2</sub> ∈ *H*

-   El elemento **neutro** del grupo *G* forma parte del subgrupo *H*.
    *e* ∈ *G* → *e* ∈ *H*

-   El **inverso** de cualquier elemento del subgrupo *H* también
    pertenece al grupo.
    ∀ *h*<sup>−1</sup> ∈ *H* → *h*<sup>−1</sup> ∈ *G*

Como la operación binaria · ya es asociativa en *G*, lo será también en
*H*, y por lo tanto, no es necesario comprobarlo.

<span id="ex:subgrupos" label="ex:subgrupos"></span> El grupo de los
números enteros ℤ y la operación suma es un subgrupo de los números
racionales ℚ, que a su vez es subgrupo de los números reales ℝ.

Otra manera de representar que un conjunto es subgrupo de otro aplicada
al ejemplo <a href="#ex:subgrupos" data-reference-type="ref"
data-reference="ex:subgrupos">[ex:subgrupos]</a>:
(ℤ,+) ≤ (ℚ,+) ≤ (ℝ,+)

El conjunto de los múltiplos enteros del número natural n, es decir nℤ =
*n**x* : *x* ∈ ℤ, se tiene que (nℤ,+) es subgrupo de (ℤ,+).

No es necesario demostrar las tres condiciones anteriores para verificar
que *H* es un subgrupo de (*G*, ·) si para *h*, *g* ∈ *H* se cumple que:
*h* ⋅ *g*<sup>−1</sup> ∈ *H*

Suponiendo que *H* es un subgrupo de *G*. Dados los elementos
*x*, *y*, *y*<sup>−1</sup> ∈ *H*, por lo tanto
*x* ⋅ *y*<sup>−1</sup> ∈ *H*. A partir de la segunda propiedad,
*x* ⋅ *x*<sup>−1</sup> = *e* ∈ *H*, que nos lleva a
*e* ⋅ *x*<sup>−1</sup> = *x*<sup>−1</sup> ∈ *H*. Finalmente,
*x* ⋅ *y* = *x* ⋅ (*y*<sup>−1</sup>)<sup>−1</sup> ∈ *H*. Con esto,
quedan probadas las tres propiedades y *H* es un subgrupo de *G*.

Todos los grupos tienen al menos dos subgrupos, que son conocidos como
**subgrupos impropios**, el del elemento neutro y el de todos los
elementos del grupo. Al resto de subgrupos se les denomina **subgrupos
propios**.

Es posible obtener subgrupos mediante cualquier subconjunto *S* de *G*.
⟨*S*⟩ será el subgrupo más pequeño de (*G*, ·) que contiene a *S*.

⟨*S*⟩ = *x*<sub>1</sub><sup>*α*1</sup>, *x*<sub>2</sub><sup>*α*2</sup>, ..., *x*<sub>*n*</sub><sup>*α**n*</sup> : *x*<sub>1</sub>, *x*<sub>2</sub>, ..., *x*<sub>*n*</sub> ∈ *S*, *α*<sub>1</sub>, *α*<sub>2</sub>, ..., *α*<sub>*n*</sub> ∈ ℤ

Sea el grupo (ℤ<sub>6</sub>, ·) y el subconjunto \[2\], el grupo
generado por dicho subconjunto es ⟨\[2\]⟩ = \[0\], \[2\], \[4\].

#### Subgrupo cíclico

Un grupo (*G*, ·) se dice que es cíclico si al menos un elemento *x* del
grupo *G*, puede llegar a generar el grupo *G* completo, es decir, ⟨*s*⟩
= *G*. En este caso, el elemento *x* es conocido como generador de *G*.

El grupo (ℤ<sub>4</sub>,+) es cíclico y los elementos \[1\] y \[3\] son
generadores ya que con ellos se pueden obtener el grupo completo:

\[1\], \[1\] + \[1\] = \[2\] $\hspace{0.8cm}$ \[1\] + \[1\] + \[1\] =
\[3\] $\hspace{0.8cm}$ \[1\] + \[1\] + \[1\] + \[1\] = \[0\]

\[3\], \[3\] + \[3\] = \[2\] $\hspace{0.8cm}$ \[3\] + \[3\] + \[3\] =
\[1\] $\hspace{0.8cm}$ \[3\] + \[3\] + \[3\] + \[3\] = \[0\]

El orden de un elemento generador *x* es el número de elementos que
posee el subgrupo *H* formado por dicho elemento, siempre que sea
finito. Se representa \|⟨*S*⟩\|.

El orden del elemento \[1\] del grupo (ℤ<sub>6</sub>,+) es 6.

Para un grupo finito (*G*, ·) y su elemento *x*, podemos encontrar un
entero positivo *n*, de manera que *x*<sup>*n*</sup> = *e* y el subgrupo
generado por *x* sea
⟨*x*⟩ = {*x*, *x*<sup>2</sup>, ..., *x*<sup>*n* − 1</sup>, *x*<sup>*n*</sup> = *e*}.

Como el grupo *G* es finito, el conjunto de las potencias de *x* debe
tener repeticiones, es decir, existen enteros *i*,*j* tal que
*x*<sup>*i*</sup> = *x*<sup>*j*</sup>. De aquí se deduce que:

*e* = *x*<sup>*i*</sup> ⋅ *x*<sup>−*i*</sup> = *x*<sup>*j*</sup> ⋅ *x*<sup>−*i*</sup> = *x*<sup>*j* − *i*</sup>

Podemos suponer que *j* $\textgreater$ *i* y tomar *n* = *j* − *i* y el
subconjunto generado por:
⟨*x*⟩ = {*x*, *x*<sup>2</sup>, ..., *x*<sup>*k*</sup>, ..., *x*<sup>−1</sup>, *x*<sup>−2</sup>, ..., *x*<sup>−*k*</sup>, ...}

Si *k* $\textgreater$ *n*, tenemos *k* = *c**n* + *r* donde
*c*, *r* ∈ ℕ. Entonces
*x*<sup>*k*</sup> = *x*<sup>*c**n*</sup> ⋅ *x*<sup>*r*</sup> = *x*<sup>*r*</sup>.
Esto nos dice que los elementos *x*<sup>*k*</sup> (k $\textgreater$ n)
se pueden eliminar en ⟨*x*⟩ porque están repetidos. Los elementos de la
forma *x*<sup>−*i*</sup> también aparecen repetidos ya que
 − *i* = *c**n* + *r* para *c*, *r* ∈ ℤ.

Cuando (*G*, ·) es un grupo finito y *x* ∈ *G*, tomando *n* como el
menor entero positivo que cumple *x*<sup>*n*</sup> = *e*, encontramos
todos los elementos
*x*, *x*<sup>2</sup>, ..., *x*<sup>*n* − 1</sup>, *x*<sup>*n*</sup> = *e*
distintos.

A partir de la explicación anterior, podemos demostrar que el orden de
*x* coincide con el menor entero positivo *k* tal que
*x*<sup>*k*</sup> = *e*.

<span id="ex:orden" label="ex:orden"></span> A partir del grupo
(ℤ<sub>4</sub>,+):

orden de \[0\] = 1     orden de \[1\] = 4     orden de \[2\] = 2    
orden de \[3\] = 4

Cuando un elemento *x* del grupo finito *G* de orden *k* finito y *m*
entero positivo, cumple que *x*<sup>*m*</sup> = *e*, su orden *k* divide
a *m*.

Si *x*<sup>*m*</sup> = *e*, escribimos *m* = *c**k* + *r* donde
*r* = *x*<sup>*m*</sup> = *x*<sup>*c**k*</sup> ⋅ *x*<sup>*r*</sup> = (*x*<sup>*k*</sup>)<sup>*c*</sup> ⋅ *x*<sup>*r*</sup> = (*e*)<sup>*e*</sup> ⋅ *x*<sup>*r*</sup> = *x*<sup>*r*</sup>.
Como 0 ≤ *r* ≤ *k* y *k* es el menor entero que cumple
*x*<sup>*k*</sup> = *e*, se deduce que *r* = 0 y *m* = *c**k*, lo que
prueba que *k* divide a *m*.

### Teorema de Lagrange

En el ejemplo <a href="#ex:orden" data-reference-type="ref"
data-reference="ex:orden">[ex:orden]</a> hemos visto que el orden de los
elementos de (ℤ<sub>4</sub>,+) es 1, 2 y 4 y el del grupo es 4, por lo
que todos los órdenes son divisores del orden del propio grupo. Se puede
comprobar que en otros sucede lo mismo, como en
(ℤ<sub>6</sub><sup>\*</sup>,+), cuyo orden es 5 y los de sus generadores
son 1 y 5. Esta observación puede ser cierta para cualquier grupo
finito.

Sea *G* un grupo finito y *x* un elemento del grupo, el orden de *x* es
divisor del orden de *G*. Desde esta afirmación, se infiere que el
número de elementos de un subgrupo *H* de *G*, divide al número de
elementos de *G*.

Sea *k* el orden de *x* y *n* el número de elementos de *G*, por lo que
pudimos ver en el apartado de subgrupos cíclicos, sabemos que

⟨*x*⟩ = *x*, *x*<sup>2</sup>, ..., *x*<sup>*n* − 1</sup>, *x*<sup>*n*</sup> = *e*

y que las potencias de *x* en el conjunto ⟨*x*⟩ no se repiten. Si
partimos el grupo *G* tantas veces como sea necesario hasta obtener
subconjuntos m que posean el mismo número de elementos, es decir, el
orden de *G*. Si operamos cada subconjunto *m* con ⟨*x*⟩, obtenemos
subconjuntos de tamaño igual al orden de ⟨*x*⟩. Entonces tenemos que
\|⟨*x*⟩\|*m* = \|*G*\| = *n*, por lo que demostramos que el orden del
grupo es divisible por el del elemento.

La demostración anterior está ligada con el concepto de partición de un
conjunto, que a su vez, está relacionado con relaciones de equivalencia.
Por otro lado, esencialmente no está ligada a subgrupos de la forma de
⟨*x*⟩, sino que cualquier subgrupo *H* de *G* lo cumple. A partir de
esto, podemos llegar a la afirmación **“el número de elementos de un
subgrupo *H* de *G* divide al número de elementos de *G*”**. Esta
afirmación es conocida como el Teorema de Lagrange
(<a href="#thm:Lagrange" data-reference-type="ref"
data-reference="thm:Lagrange">[thm:Lagrange]</a>) y lo demostraremos más
adelante.

Para entender mejor el teorema, primero vamos a conocer la clases por la
izquierda y por la derecha. Si *H* es un subgrupo de *G*, se definen
como:
*g**H* = {*g**h* : *h* ∈ *H*} como clase por la izquierda
*H**g* = {*h**g* : *h* ∈ *H*} como clase por la derecha

Para el grupo (ℤ,+) y su subconjunto de los múltiplos de 5 (5ℤ), tenemos
5ℤ = {2 + 5*z* : *z* ∈ ℤ} = 7 + 5ℤ.

Dos elementos *x*, *y* ∈ *G* se relacionan con *H* de manera que
*x* ≡ *y*(*H*), si *x*<sup>−1</sup>*y* ∈ *H*. Esto es conocido como una
relación de equivalencia y la clase de equivalencia del elemento *x* de
*G*, coincide con la clase *x**H*. Además, el número de elementos de
*x**H*, coincide con el de *H*.

La relación de equivalencia que define al subgrupo 5ℤ es *n* ≡ *m*(5ℤ),
siempre que  − *m* + *n* ∈ 5ℤ.

<span id="thm:Lagrange" label="thm:Lagrange"></span> Si *G* es un grupo
finito y *H* un subgrupo de *G*, el número de elementos de *H* divide al
número de elementos de *G*.

Las clases de equivalencia de esta relación establecen una partición de
*G*, que coinciden con *x**H*:
*G* = (*x*<sub>1</sub>*H*) ∪ (*x*<sub>2</sub>*H*) ∪ ... ∪ (*x*<sub>*n*</sub>*H*)

Cada conjunto *x*<sub>*i*</sub>*H* tiene \|*H*\| elementos, por lo
tanto:
\|*G*\| = \|*x*<sub>1</sub>*H*\| + \|*x*<sub>2</sub>*H*\| + ... + \|*x*<sub>*m*</sub>*H*\| = *m*\|*H*\|

El número entero *m* tal que \|*G*\| = *m*\|*H*\|, se denomina índice de
*H* y se denota como \[*G*:*H*\]. Los *x**H* que hemos visto
anteriormente, son las clases de equivalencia por la izquierda módulo
*H* que tiene el conjunto. De igual manera, pueden definirse *H**x* como
las clases por la derecha.

Antes de avanzar a otro apartado, es importante conocer que un grupo *G*
con orden primo *p*, siempre va a ser un grupo cíclico. Por el Teorema
de Lagrange (<a href="#thm:Lagrange" data-reference-type="ref"
data-reference="thm:Lagrange">[thm:Lagrange]</a>), el orden de los
elementos del grupo tiene que dividir a *p*. Los únicos divisores
posibles de un primo, son el 1 y el propio *p*. Como \|⟨*x*⟩\|  \> 1, se
tiene que \|⟨*x*⟩\| = *p* y *x* es generador de *G*. Por lo tanto, se
trata de un grupo cíclico ya que tiene elemento generador.

#### Subgrupo normal

Un subgrupo *H* de un grupo *G* se dice normal y lo escribiremos como
*H* ⊲ *G*, cuando se cumpla:

$$(xH)(yH) = (xy)H  \hspace{0.3cm} \forall x,y \in G$$

En (ℤ,+) el subgrupo 5ℤ es normal ya que para todo *m*,*n* enteros:

(*m*+5ℤ) + (*n*+5ℤ) = (*m*+*n*)5ℤ = {*m* + 5*z*<sub>1</sub> + *n* + 5*z*<sub>2</sub> : *z*<sub>1</sub>, *z*<sub>2</sub> ∈ ℤ} = {*m* + *n* + 5*z* : *z* ∈ ℤ} = *m* + *n* + 5ℤ.

Otra manera de saber si un subgrupo es normal en *G* es si se cumple
*x**N* = *N**x* para todo *x* ∈ *G*, es decir, las coclases a ambos
lados, coinciden. Si *G* es un grupo finito y *H* es un subgrupo de *G*,
el orden de *H* divide al orden de *G*, es decir,
 $\dfrac{\|H\|}{\|G\|}$.

Al dividir *G* en clases de equivalencia
*x*<sub>1</sub>*H*, *x*<sub>2</sub>*H*, ..., *x*<sub>*k*</sub>*H*, se
obtendrá un número finito *k*, de modo que el orden de *G*, es la suma
de los órdenes de cada clase de equivalencia, pero todas las clases de
equivalencia tienen orden \|*H*\|, por lo tanto, \|*G*\| = *k*\|*H*\|.

En general, no todo subgrupo es normal, pero todos los subgrupos de un
grupo abeliano, son normales.

### Grupo cociente

En el Teorema de Lagrange
(<a href="#thm:Lagrange" data-reference-type="ref"
data-reference="thm:Lagrange">[thm:Lagrange]</a>) hemos conocido las
clases de equivalencia para ver su demostración. El grupo cociente
*G*/*H* es el conjunto de clases de equivalencia que se obtienen al
definir en *G* la relación de equivalencia modulo *H*.
*x* ≡ *y*(*H*) si y sólo si *x*<sup>−1</sup>*y* ∈ *H*
Una vez definido el conjunto cociente, habría que asegurar que cumple
las condiciones de estructura de grupo con la operación binaria definida
en *G*, pero esto no sucede con cualquier subgrupo, solamente con los
normales.

Sea *G* un grupo y *H* un subgrupo normal de *G*, la operación
(*x**H*)(*y**H*) = (*x**y*)*H*

define en el conjunto cociente *G*/*H* la estructura de grupo. Recibe el
nombre de **grupo cociente de *G* sobre *H***.

La operación de clases de equivalencia tiene que ser verificada para
asegurar que está bien definida en *G*/*H*, es decir, si *x*′, *y*′,
*x*′*y*′ son representantes de *x**H*, *y**H*, (*x**y*)*H*,
respectivamente. Como *x*′ ∈ *x**H*, *y*′ ∈ *y**H*,
*x*′*y*′ ∈ (*x**H*)(*y**H*) ya que *H* es un subgrupo normal de *G*. La
asociatividad de la operación es una consecuencia de la asociatividad de
*G*, puesto que:
((*x**H*)(*y**H*)(*z**H*)) = ((*x**y*)*H*)(*z**H*) = (*x**y*)*z**H* = (*x**H*)((*y**H*)(*z**H*))
El elemento neutro es *H* = *e**H*, puesto que:
$$(xH)(eH) = (xe)H = xH \hspace{0.4cm} \text{y} \hspace{0.4cm} (eH)(xH) = (ex)H = xH$$
Por último, para *x**H* ∈ *G*/*H*, tenemos que su inverso
*x*<sup>−1</sup> ∈ *G*/*H*, puesto que:
$$(xH)(x^{-1}H) = (xx^{-1})H = eH = H \hspace{0.4cm} y \hspace{0.4cm} (x^{-1}H)(xH) = (x^-1x)H = eH = H$$

*G*/*N* está formado por el conjunto de las coclases tal que:
*G*/*N* = (*N**g* \| *g*∈*G*)
De modo que si *N* es subgrupo normal de *G*, *G*/*N* con la operación
de multiplicación de subconjuntos de *G*, tiene estructura de grupo con
las siguientes propiedades:

-   ∀*x*, *y* ∈ *G*, (*N**x*) ⋅ (*N**y*) = *N* ⋅ *x* ⋅ *y*

-   *N* es el elemento neutro de *G*/*N*.

-   $(Nx)-1 = N \cdot x-1 \hspace{0.2cm} \forall x \in G$.

Los grupos cocientes serán muy útiles debido a que conseguiremos
conjuntos mucho más pequeños que tengan estructura de grupo.

### Homorfismos de grupos

La teoría de grupos contiene tres teoremas de isomorfía
(<a href="#thm:iso1" data-reference-type="ref"
data-reference="thm:iso1">[thm:iso1]</a>,
<a href="#thm:iso2" data-reference-type="ref"
data-reference="thm:iso2">[thm:iso2]</a>,
<a href="#thm:iso3" data-reference-type="ref"
data-reference="thm:iso3">[thm:iso3]</a>) que relacionan a los grupos
con sus grupos cocientes y sirven para construir isomorfismos. Durante
esta sección introduciremos los homomorfismos y estudiaremos algunas
propiedades previas a los teoremas.

Un homomorfismo es una aplicación que conserva las operaciones de los
grupos entre los que está definida.
*f* : *G*<sub>1</sub> → *G*<sub>2</sub>

Sean (*G*<sub>1</sub>, ⋅) y (*G*<sub>2</sub>, ∘) dos grupos y *f* una
aplicación de *G*<sub>1</sub> en *G*<sub>2</sub>, *f* es un
**homomorfismo** si para todo *x*, *y* ∈ *G*<sub>1</sub>:
*f*(*x*⋅*y*) = *f*(*x*) ∘ *f*(*y*)

Si *G* es un grupo abeliano y a un elemento de *G*,
*f*(*a*) = *a*<sup>2</sup> define un homomorfismo de *A* en *A*:
*f*(*a**b*) = (*a**b*)<sup>2</sup> = *a**b**a**b* = *a*<sup>2</sup>*b*<sup>2</sup> = *f*(*a*)*f*(*b*)

Si *f* es una aplicación biyectiva, es decir, si todos los elementos del
conjunto de salida tienen una imagen distinta en el conjunto de llegada,
diremos que *f* es un **isomorfismo**.

Los isomorfismos nos sirven para definir igualdades entre grupos de
diferentes elementos, tendrán el mismo comportamiento y para su estudio
podemos tratarlos como equivalentes. También se pueden definir entre
homomorfismos, pero como la aplicación no es biyectiva, no son tan
fuertes.

Dado un homomorfismo *f* entre los grupos *G*<sub>1</sub> y
*G*<sub>2</sub>, se define el núcleo mediante:
*k**e**r*(*f*) = *x* ∈ *G*<sub>1</sub> : *f*(*x*) = *e*<sub>2</sub>

Es decir, el núcleo está formado por los elementos *x* de
*G*<sub>1</sub> que tiene como imagen el elemento neutro de
*G*<sub>2</sub>. El núcleo del homomorfismo juega un papel importante en
el desarrollo de los teoremas de isomorfía que estudiaremos a
continuación.

### Teoremas de isomorfía

Una de las técnicas fundamentales en la teoría de grupos, es la relación
existente entre subgrupos normales y homomorfismos. Esta relación está
recogida en el primer teorema de isomorfía, que es uno de los resultados
principales de esta sección.

<span id="thm:iso1" label="thm:iso1"></span> Un homomorfismo
suprayectivo *f* : *G*<sub>1</sub> → *G*<sub>2</sub> y su núcleo es
ker(f), cumple que:

-   El grupo cociente de *G*<sub>1</sub>/*k**e**r*(*f*) es isomorfo al
    otro grupo *G*<sub>2</sub>.

-   Entre los subgrupos de *G*<sub>1</sub> y *G*<sub>2</sub> que
    contienen a ker(f), existe una correspondencia biyectiva.

<span id="thm:iso2" label="thm:iso2"></span> Sea *G* un grupo, *H* y *K*
subgrupos normales de *G* y *H* subgrupo de *K*. Se cumple que *K*/*H*
es un subgrupo normal de *G*/*H* y:
$$G/H \textbf{\LARGE /} K/H \approx G/K$$

<span id="thm:iso3" label="thm:iso3"></span> Sea *G* un grupo y *H* y
*K* subgrupos de *G* con *K* normal en *G*. Entonces *H**K* es un
subgrupo de *G*, *K* es normal en *H**K* y *H* ∩ *K* es normal en *H*.
Además:
$$HK \textbf{\LARGE /} K = H \textbf{\LARGE /} (H \cap K)$$

## Teoría de anillos

Anteriormente hemos analizado el conjunto de elementos conocido como
grupo y sus diferentes propiedades. A lo largo de esta sección, nos
centraremos en conocer un nuevo conjunto que se conoce como anillo y
cumple ciertas características similares a los grupos. Para consultar
información más extensa y todas demostraciones de los teoremas que se
exponen a lo largo de esta sección, mediante la lectura del capítulo 6
del libro *Un curso de álgebra* .

### Definición de anillo

Un anillo es un conjunto (*R*, +,⋅) no vacío con dos operaciones
binarias:
*r* + *s* (adición)   *r* ⋅ *s* (multiplicación)
que satisface las siguientes propiedades:

-   (*R*, +) es un grupo abeliano. Al elemento neutro de (*R*, +), que
    sabemos que es único, se le denominará elemento cero (o cero) y se
    denotará por 0.

-   La operación binaria · (conocida como producto) es interna y
    asociativa en *R*
    $$(r \cdot s)\cdot t = r \cdot (s \cdot t) \hspace{0.2cm} \forall \\, r,s,t \\, \in R$$

-   Se verifica la propiedad distributiva de · respecto de +, para
    *r*, *s*, *t* ∈ *R*:
    (*r*+*s*) ⋅ *t* = *r* · *t* + *s* ⋅ *t*,   *r* ⋅ (*s*+*t*) = *r* ⋅ *s* + *r* ⋅ *t*

El conjunto de los números enteros con las operaciones adición y
multiplicación (ℤ, +,⋅) es un anillo.

El conjunto de los números enteros módulo 6 con las operaciones adición
y multiplicación (ℤ<sub>6</sub>, +,⋅) también es un anillo.

Al igual que ocurría con los grupos, hay conjuntos más pequeños dentro
de los anillos que cumplen unas condiciones para considerarlos
**subanillos**. Decimos que *S* es un subanillo de *R* si contiene a1
elemento neutro de la multiplicación, es decir, es unitario y la
multiplicación y resta de cualquier par de elementos de *S*, también
pertenece a *S*.
∀*s*, *t* ∈ *S* ↔ *s* − *t*, *s* ⋅ *t* ∈ *S*

El conjuntos de los números enteros ℤ es un subanillo del conjunto de
los racionales ℚ.

### Tipos de anillos

#### Anillo con identidad

Un anillo *R* se conoce como **anillo con identidad** cuando tiene un
elemento 1 tal que 1 ⋅ *r* = *r* ⋅ 1 = *r* para todos elementos del
anillo, es decir, algunos anillos tienen un elemento neutro para la
multiplicación. Todos los anillos sobre los que trabajaremos a partir de
ahora son anillos con identidad.

#### Anillo conmutativo

Al igual que ocurría con los grupos abelianos, que eran aquellos que
cumplían la propiedad conmutativa, ocurre lo mismo en los **anillos
conmutativos**. Un anillo *R* en el que:
$$rs = sr \hspace{0.1cm} \forall \text{ r,s} \in R$$

Los números racionales, reales, y complejos forman anillos conmutativos
con las operaciones habituales.

#### Anillo de polinomios

Un anillo bastante común es el **anillo de polinomios** *R*\[*x*\], que
está construido sobre un anillo *R* y se forma a partir de polinomios
*p*:
*p* = ∑<sub>*n* ≥ 0</sub>*a*<sub>*n*</sub>*x*<sup>*n*</sup> = *a*<sub>0</sub> + *a*<sub>1</sub>*x* + ... + *a*<sub>*m*</sub>*x*<sup>*m*</sup>
Se conoce como grado del polinomio al valor de m, sus coeficientes son
*a*<sub>0</sub>, *a*<sub>1</sub>, ..., *a*<sub>*m*</sub> y su
coeficiente director es *a*<sub>*m*</sub>. En caso de que el coeficiente
director sea 1, el polinomio es mónico.

El conjunto de todos los polinomios con coeficientes en *R* se define
como *R*\[*x*\] y las operaciones entre los polinomios
*p*(*x*) = ∑<sub>*n* ≥ 0</sub>*a*<sub>*n*</sub>*x*<sup>*n*</sup>,
*q*(*x*) = ∑<sub>*n* ≥ 0</sub>*b*<sub>*n*</sub>*x*<sup>*n*</sup> son:

-   Suma:
    *p*(*x*) + *q*(*x*) = ∑<sub>*n* ≥ 0</sub>(*a*<sub>*n*</sub>+*b*<sub>*n*</sub>)*x*<sup>*n*</sup>

-   Producto:
    *p*(*x*) ⋅ *q*(*x*) = ∑<sub>*n* ≥ 0</sub>(∑<sub>*i* + *j* = *n*</sub>)*a*<sub>*i*</sub> ⋅ *b*<sub>*j*</sub>)*x*<sup>*n*</sup>

Diremos que los anteriores polinomios son iguales si y sólo si
*a*<sub>*n*</sub> = *b*<sub>*n*</sub>.

El anillo ℤ\[*x*\] está formado por los polinomios de coeficientes
enteros como:
$$2 - x + 4x^5 \hspace{1.2cm} -15 + x^8 - 2x^{21} + 7x^{33}$$

#### Dominios de integridad

Un anillo conmutativo no cero *R* es un **dominio de integridad** cuando
∀*r*, *s* ∈ *R*, *r**s* = 0 implica que *r* = 0 ó *s* = 0, lo que
significa que en el anillo no existe ningún elemento que sea divisor de
0.

El conjunto de los números enteros ℤ es un dominio de integridad.

Si *R* un anillo, se dice que *u* ∈ *R* es una unidad, si existe
*u*′ ∈ *R*, tal que *u* ⋅ *u*′ = *u*′ ⋅ *u* = 1, es decir, un elemento
es una unidad si tiene un elemento inverso para la operación producto.
Cuando todos los elementos tienen inverso respecto al producto, *R* es
un **cuerpo**. En la siguiente sección estudiaremos en profundidad los
cuerpos.

### Ideales y teoremas de isomorfía

De alguna manera, es posible relacionar el concepto de los subgrupos
normales en la teoría de grupos al de los ideales en la teoría de
anillos. Si *R* es un anillo, un subgrupo *I* de *R* será ideal si el
producto de un cualquier elemento de *I* con uno de *R*, es también un
elemento de *I*. Es decir:

*r* ∈ *R*, *i* ∈ *I* → *x**r*, *r**x* ∈ *I*

0 y *R* son ideales de cualquier anillo y se conocen como ideales
triviales.

El conjunto de los múltiplos de ℤ (*n*ℤ) es un ideal.

En anillos conmutativos, los ideales no son más que un conjunto de
múltiplos (*r*) de un elemento del anillo *R*:
(*r*) = *R**r* = {*s**r*\|*s* ∈ *R*}

A partir de un ideal I de R, se obtiene el grupo abeliano *R*/*I* que es
un anillo con la multiplicación:
(*r*+*I*)(*s*+*I*) = *r**s* + *I*

Si *r*, *r*′, *s*, *s*′ ∈ *R* son tales que
*r* + *I* = *r*′ + *I**y**s* + *I* = *s*′ + *I*, veamos que
*r**s* + *I* − *r*′*s*′ + *I*. Sabemos que *r* − *r*′*y**s* − *s*′ están
en *I*. Así:
*r**s* − *r*′*s*′ = *r**s* − *r*′*s* + *r*′*s* − *r*′*s*′ = (*r*−*r*′)*s* + *r*′(*s*−*s*′) ∈ *I*

El grupo abeliano *R*/*I* es conocido como anillo cociente y tiene
estructura de dominio de integridad. En próximos apartados utilizaremos
el anillo cociente *Z*<sub>*n*</sub> = ℤ/*n*ℤ, es decir, el conjunto
formado por el anillo ℤ y su ideal *n*ℤ (múltiplos de un entero positivo
*n*). Es muy interesante porque forma un cuerpo siempre que *n* sea un
número primo, pero sobre esto profundizaremos más adelante.

#### Ideales principales

Sea *R* un anillo conmutativo y el ideal *I* de *R*\[*x*\], existe un
polinomio mónico que pertenece al cuerpo, tal que *I* = (*p*), es decir,
un ideal principal es un ideal generado por un único elemento.

El conjunto de todos los múltiplos de 3 es el ideal principal generado
por 3, debido a que un entero *n* es múltiplo de 3 cuando hay un número
entero *k* tal que *n* = *k* ⋅ 3.

Cuando todos los ideales de un anillo son principales, el anillo *R* es
conocido como un **dominio de ideales principales (DIP)** y todos sus
elementos se pueden factorizar como producto de los elementos primos del
anillo. En estos dominios existe siempre el concepto de máximo común
divisor y el mínimo común múltiplo, hecho que no ocurre en los dominios
de integridad en general.

El anillo ℤ de los números enteros.

#### Ideales primos

Diremos que un ideal *I* ⊂ *A* es un ideal primo cuando *I* no sea lo
mismo que *R* y se verifica la siguiente condición: el producto de dos
elementos del anillo pertenece al ideal si y sólo si alguno de los
elementos pertenece al ideal, es decir, si x, y
 ∈ *A*, *x**y* ∈ *I* → *x* ∈ *I* y  ∈ *I*.

Sea *I* ⊂ *R* un ideal. Las propiedades siguientes son equivalentes:

-   I es un ideal primo (demostración
    <a href="#dm:ideal_primo_1" data-reference-type="ref"
    data-reference="dm:ideal_primo_1">[dm:ideal_primo_1]</a>).

-   El anillo cociente *R*/*I* es un dominio de integridad (demostración
    <a href="#dm:ideal_primo_2" data-reference-type="ref"
    data-reference="dm:ideal_primo_2">[dm:ideal_primo_2]</a>).

<span id="dm:ideal_primo_1" label="dm:ideal_primo_1"></span> *R*/*I* es
un dominio de integridad donde *I* es el ideal primo de *R*:

Tomamos *a*, *b* ∈ *R* tal que *a* ⋅ *b* ∈ *I*, entonces
\[*a*+*I*\] ⋅ \[*b*+*I*\] = \[*a*⋅*b*+*I*\] = *I* (sabiendo que *I* es
el elemento neutro del anillo *R*/*I*). Como *R*/*I* es dominio de
integridad, se cumple que \[*a*+*I*\] = *I*, o bien, \[*b*+*I*\] = *I*.
Por lo tanto, también se cumple que *a* ∈ *I* o bien *b* ∈ *I*. Esto nos
lleva a que *I* es un ideal primo.

<span id="dm:ideal_primo_2" label="dm:ideal_primo_2"></span> *I* es un
ideal primo de *R* → *R*/*I* es dominio de integridad:

Sea \[*a*+*I*\] ⋅ \[*b*+*I*\] = *I* para un par de elementos
\[*a*+*I*\], \[*b*+*I*\] de *R*/*I*, tenemos que
*I* = \[*a*+*I*\] ⋅ \[*b*+*I*\] = \[*a*⋅*b*+*I*\] → *a* ⋅ *b* ∈ *I*.
Como *I* es primo, tendremos que *a* ∈ *I*, o bien ,*b* ∈ *I*, y por
tanto, \[*a*+*I*\] = *I*, o bien, \[*b*+*I*\] = *I*. Esto implica que
*R*/*I* es dominio de integridad.

Dado un anillo *R* formado por el conjunto de los números enteros ℤ, los
ideales primos de *R* son los ideales de la forma ℤ*p*, donde *p* es un
número primo.

#### Ideales maximales

Diremos que un ideal *I* ⊂ *R* es un ideal maximal si *I* = *R* y el
único ideal de *R* que contiene a *I* es el propio *R*. Es importante
saber que todo ideal maximal es primo y que todo ideal propio *I* de
*R*, está contenido en algún ideal maximal.

Sea *I* ⊂ *R* un ideal. Las propiedades siguientes son equivalentes:

-   *I* es un ideal maximal.

-   El anillo cociente *R*/*I* es un cuerpo.

En ℤ todo ideal primo es maximal. Más generalmente, todo ideal primo de
un Dominio Ideal Principal (DIP) es maximal.

El conjunto *P* = {0, 2, 4, 6, 8, 10} es un ideal primo y maximal en
ℤ<sub>12</sub>.

#### Homomorfismo de anillos

Durante la teoría de grupos hemos comprendido que es un homomorfismo de
grupos y el **homomorfismo de anillos** es prácticamente lo mismo.
Concretamente, es una función entre objetos matemáticos con la misma
estructura algebraica que mantienen las operaciones definidas. En este
caso, un homomorfismo entre anillos preserva las operaciones de adición
y multiplicación en el anillo. Dados dos anillos *R* y *S*, tendremos un
homomorfismo de anillos si se cumple que *f* : *R* → *S*,
*f*(*x**y*) = *f*(*x*)*f*(*y*) y *f*(1) = 1.

Dentro de los diferentes tipos de homomofismos, cuando la función *f* es
biyectiva (todos los elementos del conjunto de salida tienen una imagen
distinta en el conjunto de llegada, y a cada elemento del conjunto de
llegada le corresponde un elemento del conjunto de salida) se dice que
*f* es un **isomorfismo de anillos**.

Es posible trabajar con el homomorfismo de un anillo *R* y su ideal *I*,
a partir de la aplicación *f* : *R* → *R*/*I**y**f*(*r*) = *r* + *I*.

El homomorfismo de anillos *f* : *R* → *S*, donde *f*(*R*) es un
subanillo de *S* y *k**e**r*(*f*) es un ideal de *R* y existe la
aplicación $\overline{f} = R/ker(f) \rightarrow f(R)$ dada por
$\overline{f}(x + ker(f)) = f(x)$ es un isomorfismo de anillos.

Como *f* es un homomorfismo de grupos, sabemos que:
*K* = *k**e**r*(*f*) = {*x* ∈ *R*\|*f*(*x*) = 0}
es un subgrupo normal de *R* y la aplicación $\overline{f}$ está bien
definida y es un isomorfismo de grupos. También, *f*(*R*) es un subgrupo
de *S*. Como *f*(*x**y*) = *f*(*x*)*f*(*y*) y *f*(1) = 1, está claro que
*f*(*R*) es un subanillo de *S*. Veamos que *K* es un ideal de *R*. Si
*r* ∈ *R* y *k* ∈ *K*, tendremos que:
*f*(*r**k*) = *f*(*r*)*f*(*k*) = 0 = *f*(*k*)*f*(*r*) = *f*(*k**r*)
Con lo que deducimos que *r**k*, *k**r* ∈ *K*. Finalmente:
$$\overline{f}((x + K)(y + K)) = \overline{f}(xy + K) = f(xy) = f(x)f(y) = \overline{f}(x + K)\overline{f}(y + K), \overline{f}(1 + K) = 1$$
y el teorema queda probado.

El elementos del homomorfismo de anillos que tiene como imagen el
elemento neutro de la suma, juegan un papel fundamental en la teoría de
anillos. Para cualquier homomorfismo *f* : *R* → *S* definimos el núcleo
de un homomorfismo de anillos como el conjunto:
*k**e**r*(*f*) = {*r* ∈ *R* : *f*(*r*) = 0}
El núcleo de un homomorfismo es importante porque siempre es un ideal.

Un importante homomorfismo de anillos es el homomorfismo de evaluación.
Si
*p*(*x*) = *a*<sub>0</sub> + *a*<sub>1</sub>*x* + ... + *a*<sub>*m*</sub>*x*<sup>*m*</sup> ∈ *R*\[*x*\]
y *a* ∈ *R*, definimos:
*p*(*a*) = *a*<sub>0</sub> + *a*<sub>1</sub>*a* + ... + *a*<sub>*m*</sub>*a*<sup>*m*</sup> ∈ *R*

La aplicación *e*<sub>*a*</sub> : *R*\[*x*\] → *R* dada por
*e*<sub>*a*</sub>(*p*) = *p*(*a*) es un homomorfismo de anillos si *R*
es un anillo conmutativo y *a*∈ *R*. Gracias a esto, podemos decir que
*a* será una raíz de *p* en *R* siempre que se cumpla *p*(*a*) = 0.

Observamos que *e*<sub>*a*</sub>(1) = 1. Para dos polinomios *p*(*a*) y
*q*(*a*), por definición tenemos que
(*p*+*q*)(*a*) = *p*(*a*) + *q*(*a*), y además,
*p**q*(*a*) = *p*(*a*)*q*(*a*). Esto es inmediato.

En los anillos de polinomios también nos encontramos con un algoritmo
para realizar la división, al igual que para el conjunto de los números
enteros.

<span id="thm:div" label="thm:div"></span> Dados *f*, *g* ∈ *R*\[*x*\]
no cero, suponiendo que el coeficiente director de *g* es una unidad del
anillo *R*, existen dos polinomios únicos *d*, *r* ∈ *R*\[*x*\] tal que
*f* = *d**g* + *r*.

Gracias al anterior teorema
(<a href="#thm:div" data-reference-type="ref"
data-reference="thm:div">[thm:div]</a>), podemos definir el máximo común
divisor de dos polinomios. Además, dos polinomios son coprimos cuando su
máximo común divisor es un polinomio constante. El objetivo final de
todo esto, es conseguir polinomios irreducibles, es decir, lograr
expresar un polinomio en varios de menor grado, ya que los irreducibles
se comportan como los elementos primos, cuyo máximo común divisor con
cualquier otro elemento es 1.

## Teoría de cuerpos

El cuerpo es la última entidad matemática que vamos a estudiar a lo
largo de este trabajo. Como hemos podido ver durante la teoría de
anillos, un cuerpo es un anillo conmutativo con identidad donde todos
los elementos tienen un inverso en el producto. A lo largo de esta
sección vamos a profundizar en los teoremas más importantes hasta llegar
a los cuerpos finitos que usaremos en la criptografía de curvas
elípticas. La información sobre cuerpos descrita en este apartado, se ha
desarrollado en base al contenido del capítulo 6 del libro *Un curso de
algebra* .

### Definición de cuerpo

Un cuerpo es un sistema algebraico en el que las dos operaciones que lo
forman (+ y · conocidas como adición y multiplicación respectivamente)
se pueden realizar y se cumple que la multiplicación es asociativa,
conmutativa y distributiva respecto de la adición. Además, posee inverso
y elemento neutro para ambas operaciones, lo que permite efectuar las
operaciones de sustracción y división (excepto la división por cero).
Esto lo diferencia de un anillo conmutativo en el cual no existe el
elemento inverso de la multiplicación, y por lo tanto, no hay división.

Un cuerpo es un conjunto no vacío (*K*, +,⋅) que cumple las siguientes
propiedades:

-   (*K*, +) es un grupo abeliano.

-   (*K*<sup>\*</sup>, ⋅) es un grupo abeliano, donde *K*<sup>\*</sup> =
    *K* − {0}.

-   La operación suma será distributiva respecto al producto, es decir,
    para *r*, *s*, *t* ∈ *R*:
    (*r*+*s*) · *t* = *r* · *t* + *s* · *t*
    *r* · (*s*+*t*) = *r* · *s* + *r* · *t*

Por lo tanto, un cuerpo siempre tendrá como mínimo dos elementos, el
neutro para la suma y el neutro para el producto. Además de las
anteriores propiedades, es necesario saber que todo cuerpo es tanto
dominio de integridad y como anillo.

(ℚ, +,⋅) es un cuerpo, donde ℚ es el conjunto de los números racionales.

(ℝ, +,⋅) es un cuerpo, donde ℝ es el conjunto de los números reales.

Al igual que los anillos, los cuerpos también tienen elementos
inversibles *r**s* = *s**r* = 1 conocidos como unidades.

Las unidades de *K*\[*x*\] son los polinomios constantes no cero. El
conjunto de las unidades de un cuerpo *K* es *K*<sup>*x*</sup>.

También en los cuerpos, encontramos conjuntos más pequeños que cumplen
ciertas propiedades y son conocidos como subcuerpos. Si *K* es un cuerpo
y *S* un subanillo *S* de *K*, *S* será un subcuerpo cuando todos sus
elementos tienen inverso (excepto el cero).

ℚ es un subcuerpo de ℂ.

### Ideales y homomorfismos de cuerpos

El homomorfismo de cuerpos se produce cuando dos cuerpos *K* y *S* son
un homomorfismo de grupos con la aplicación *f* : *K* → *S* tal que
*f*(*x**y*) = *f*(*x*)*f*(*y*) y *f*(1) = 1. Si además *f* es biyectiva,
es un isomorfismo de cuerpos.

Como todo cuerpo es un anillo, podríamos preguntarnos por la forma que
tengan sus ideales. Para empezar, como todo cuerpo es anillo
conmutativo, todo ideal por la izquierda es ideal y todo ideal por la
derecha es también ideal. Así pues, sólo tenemos que estudiar los
ideales del cuerpo.

Si *I* es ideal del cuerpo *K*, entonces todo elemento no nulo *a* ∈ *K*
ha de tener inverso, *a*<sup>−1</sup>  ∈ *K*, luego a es una unidad de
*K* (esto es, *a* ∈ *U*(*K*)), y se tendrá que *I* ∩ *U*(*K*) ≠ ⌀, es
decir, *I* = *R*. De esta manera, los únicos ideales de un cuerpo son el
propio cuerpo y el ideal nulo.

### Extensiones de cuerpos

Un cuerpo *E* es una extensión de cuerpos de *K* si *K* es un subcuerpo
de *E*. Se conoce al cuerpo *K* como cuerpo base y la extensión se
presenta mediante *E*/*K*, donde *E* es un espacio vectorial sobre *K*.

ℂ es una extensión de ℚ y de ℝ.

Una extensión *E*/*K* es finita si la dimensión de *E* como *K*-espacio
vectorial es finita. Como todo espacio vectorial tiene base, podemos
calcularlo mediante:
\|*E*:*K*\| = *d**i**m*<sub>*K*</sub>(*E*)
y es conocido como el **grado de la extensión**. Por lo tanto, *E*/*K*
será finita siempre que tenga un subconjunto finito
*a*<sub>1</sub>, ..., *a*<sub>*n*</sub>

Sea *E*/*K* una extensión y *K* ⊆ *L* ⊆ *E* es un subcuerpo intermedio.
*E*/*K* es finita siempre que *E*/*L* y *L*/*K* sean finitas. Por lo
tanto:
\|*E*:*K*\| = \|*E*:*L*\|\|*L*:*K*\|

#### Elemento algebraico

Un elemento *a* de la extensión *E*/*K* es **algebraico** sobre *K*
cuando existe un polinomio *p*(*x*) ≠ 0 ∈ *K*\[*x*\] tal que
*p*(*a*) = 0. Cuando todos los elementos de *E* son algebraicos sobre
*K*, diremos que *E*/*K* es una **extensión algebraica**.

Una extensión *E*/*K* es algebraica, siempre que es finita.

Sea *a* ∈ *E* y supongamos que \|*E*:*K*\| = *n*. Queremos probar que
*a* es raíz de algún polinomio no cero de *K*\[*x*\]. Podemos suponer
que *a* ≠ 0. Si existen enteros *i* \> *j* ≥ 0 tales que
*a*<sup>*i*</sup> = *a*<sup>*j*</sup>, entonces *a* es raíz del
polinomio *x*<sup>*i* − *j*</sup> − 1 ∈ *K*\[*x*\]. En caso contrario,
el conjunto {1, *a*, *a*<sup>2</sup>, ..., *a*<sup>*n*</sup>} tiene
*n* + 1 elementos, y por tanto, es *K*-ligado. Por tanto, existen
*k*<sub>0</sub>, ..., *k*<sub>*n*</sub> ∈ *K* no todos cero, tales que
*k*<sub>0</sub> + *k*<sub>1</sub>*a* + ... + *k*<sub>*n*</sub>*a*<sup>*n*</sup> = 0.
Entonces, el siguiente polinomio no cero se anula en *a*:
*f*(*x*) = *k*<sub>0</sub> + *k*<sub>1</sub>*x* + ... + *k*<sub>*n*</sub>*x*<sup>*n*</sup> ∈ *K*\[*x*\]

Sea *E*/*K* una extensión y supongamos que *a* ∈ *E* es algebraico sobre
*K*:

-   Existe un único polinomio mónico *p* ∈ *K*\[*x*\] irreducible en
    *K*\[*x*\] tal que *p*(*a*) = 0.

-   Si *q* ∈ *K*\[*x*\], *q*(*a*) = 0 si y sólo si *p* divide a *q*.

-   *K*(*a*) = {*f*(*a*)\|*f* ∈ *K*\[*x*\]}

-   Si *δ*(*p*) = *n*, entonces {1, *a*, ..., *a*<sup>*n* − 1</sup>} es
    una *K*-base de *K*(*a*). Por tanto, \|*K*(*a*):*K*\| = *δ*(*p*)

El polinomio *p*(*x*) es conocido como **polinomio mínimo o
irreducible** de a sobre K.

Un cuerpo *K* es **algebraicamente cerrado** cuando no existen
extensiones algebraicas propias de *K*, es decir, para la extensión
*E*/*K* se tiene que *E* = *K*. Además, se conoce como clausura
algebraica de *K* cuando se verifica que:

-   *E* es algebraicamente cerrado.

-   *E*/*K* es una extensión algebraica.

Todos los cuerpos tienen una clausura algebraica que es única salvo para
*K*-isomorfismos.

#### Cuerpo de escisión

La clausura algebraica de un cuerpo *K* tiene como consecuencia que para
cada polinomio *f*(*x*) ∈ *K*\[*x*\] exista una determinada extensión de
*K* en la que dicho polinomio, tiene todas sus raíces. El cuerpo
generado por dichas raíces, es conocido como **cuerpo de escisión** de
*f*(*x*) sobre *K* es único salvo *K*-isomorfismos.

Sean *K* un cuerpo y *f* ∈ *K*\[*x*\] no constante, entonces existe un
cuerpo de escisión de *f* sobre *K*.

### Cuerpos primos

El cuerpo primo *F* de *K* es la intersección de los subcuerpos de *K*.
Todo cuerpo *F* contiene un cuerpo primo que es, o bien ℚ, o bien
ℤ<sub>*p*</sub> = ℤ/*p*ℤ para algún primo *p*.

Sea *K* un cuerpo, llamamos característica de *K* al menor número
natural *n* tal que la un número sumado *n* veces, es igual a 0. En caso
de que no exista dicho número, *c**a**r**K* = 0. Siempre la
característica de *K* será igual a 0 ó a un número primo. Se llama
subcuerpo primo de *K* a la intersección de los subcuerpos de *K*. Sea
*K* un cuerpo y *F* su cuerpo primo. Cuando *F* sea isomorfo a ℚ,
diremos que la característica de *K* es 0. En cambio, cuando sea
isomorfo a *Z*<sub>*p*</sub>, diremos que la característica de *K* es
*p*. Por lo tanto, un cuerpo *K* de característica *p*, se tiene que:
*p**k* = *k* + ... + *k* = *k*(1+...+1) = *k*(*p*1) = 0

El cuerpo ℚ de los racionales es un cuerpo primo.

Sea *K* un cuerpo y sea *F* su cuerpo primo. Entonces *F* es isomorfo a
ℚ ó *F* es isomorfo a ℤ<sub>*p*</sub> para cierto primo *p*. En el
primer caso *n*1 ≠ 0 para todo 0 ≠ *n* ∈ ℤ. En el segundo, *n*1 = 0 si y
sólo si *p* divide a *n*.

### Cuerpos finitos

Un **cuerpo finito** es un cuerpo definido sobre un conjunto finito de
elemento. Tiene un amplio uso en teoría de números, geometría algebraica
o criptografía y también son conocidos como **cuerpos de Galois**. Los
cuerpos finitos están formados por un número de elementos
*q* = *p*<sup>*n*</sup> (donde *p* es un número primo y *n* un entero
positivo). La cardinalidad de un cuerpo finito se define de una única
manera, por lo que todos los cuerpos finitos que comparten cardinalidad,
son isomorfos entre sí.

El conjunto ℤ<sub>7</sub> formado por los enteros módulo 7 es un cuerpo
finito.

Si *K* es un cuerpo finito, entonces \|*K*\| = *p*<sup>*n*</sup> para
algún primo *p* y algún entero positivo *n*. Recíprocamente, dado un
primo *p* y un entero positivo *n*, existe un único cuerpo de
*p*<sup>*n*</sup> elementos que denominamos como
𝔽<sub>*p*<sup>*n*</sup></sub>, excepto en caso de isomorfismo.

Un cuerpo primo de *K* es *F* ≅ ℤ<sub>*p*</sub> para algún primo *p*.
Como *K* es finito, necesariamente *K* es un *F*-espacio vectorial de
dimensión finita. Sea {*a*<sub>1</sub>, ..., *a*<sub>*n*</sub>} una
*F*-base de *K*. Como cada elemento de *K* se escribe de forma única
como una *F*-combinación lineal de los elementos de la base, concluimos
que \|*K*\| = *p*<sup>*n*</sup>, donde
*n* = *d**i**m*<sub>*F*</sub>(*K*). Recíprocamente, supongamos que *p*
es un primo y *n* un entero positivo. Sea *F* = ℤ<sub>*p*</sub> y sea
*E* un cuerpo de escisión de
*f* = *x*<sup>*p*<sup>*n*</sup></sup> − *x* ∈ *F*\[*x*\]. Sea *U* el
conjunto de raíces de *f* en *E*. Notemos que *f*′ =  − 1. Entonces
(*f*,*f*′) = 1 y \|*U*\| = *p*<sup>*n*</sup>. Si *a*, *b* ∈ *U*,
entonces *a* − *b* ∈ *U*. También, si *b* ≠ 0, tenemos que
*a*/*b* ∈ *U*. Por lo tanto, *U* es un subcuerpo de *E*. Como
*E* = *F*(*U*), necesariamente *E* = *U* y \|*E*\| = *p*<sup>*n*</sup>.
Finalmente, supongamos que *L* es otro cuerpo de *p*<sup>*n*</sup>
elementos,y sea *D* su cuerpo primo. Por el primer párrafo de esta
demostración, si *D* ≅ ℤ<sub>*p*</sub> es el cuerpo primo de *L*,
entonces \|*L*\| es una potencia de *q*. Por tanto, deducimos que
*D* ≅ *F*. Por consiguiente, *L*<sup>*x*</sup> es un grupo cíclico de
*p*<sup>*n*</sup> − 1 elementos. De esta manera, si
*l* ∈ *L*<sup>*x*</sup>, tenemos que
*l*<sup>*p*<sup>*n*</sup> − 1</sup> = 1, que implica que
*l*<sup>*p*<sup>*n*</sup></sup> = *l*. Así *L* es cuerpo de escisión de
*x*<sup>*p*<sup>*n*</sup></sup> − *x* sobre *D*. Por todo ello, podemos
deducir que existe un isomorfismo de cuerpos entre *D* y *F* y otro
entre *E* y *L*. Queda demostrado que existe el cuerpo de
*p*<sup>*n*</sup> elementos y si existen otros de la misma cardinalidad,
serán isomorfos.

**Construcción de cuerpos finitos**

Una forma de obtener los cuerpos finitos es mediante la característica
*p* de *K*, que es el orden del elemento neutro del grupo multiplicativo
en el grupo aditivo, y siempre es un número primo o su potencia. Es
decir, hay cuerpos de 2, 3, 4, 5, ... elementos, pero no los hay de
6, 10, 12, 14, ... elementos.

La característica del cuerpo 𝔽<sub>8</sub> es 2.

Por lo tanto, un cuerpo finito tiene *p*<sup>*n*</sup> elementos.
Además, excepto en isomorfismos, sólo existe un cuerpo de orden
*p*<sup>*n*</sup>. Para su construcción, partimos de un polinomio
irreducible *p*(*x*) ∈ ℤ<sub>*p*</sub>\[*x*\] de grado *n*. Esto se debe
a que el conjunto de polinomios de grado menor que *n*, con la suma
habitual de polinomios y el producto con módulo un polinomio irreducible
*p*(*x*) de grado *n*, tiene estructura de cuerpo.

El cuerpo *K* construido se denomina cuerpo cociente
ℤ<sub>*p*</sub>\[*x*\]/*p*(*x*). Como el polinomio *p*(*x*) es
irreducible, produce la existencia completa de los elementos inversos.
Si no fuera irreducible, ciertos polinomios no serían inversibles y se
trataría del anillo cociente ℤ<sub>*p*</sub>\[*x*\]/*p*(*x*).

En el grupo (*K*, +), todos los polinomios (excepto el nulo) tienen
orden *p*, ya que los coeficientes están en ℤ<sub>*p*</sub>. Además, el
orden de todos los elementos es *p* (excepto el 0). En cuanto al grupo
(*K*<sup>\*</sup>, ·) es un grupo conmutativo de orden
*p*<sup>*n*</sup> − 1 y resulta ser cíclico. Esto quiere decir que tiene
generadores. Cuando el polinomio *x* es generador, es decir, si
*K* = ⟨*x*⟩, entonces el polinomio *p*(*x*), es un polinomio irreducible
primitivo.

En el cuerpo 𝔽<sub>8</sub> el polinomio
*x*<sup>3</sup> + *x*<sup>2</sup> + 1 es irreducible primitivo.

# Criptografía de Curvas Elípticas

Durante las últimas décadas el uso de curvas elípticas ha aumentado su
importancia tanto en la teoría de números como en campos relacionados
directamente con la criptografía. Gracias a esta repercusión y todo lo
que aportan, han llegado a ser parte de algunos estándares industriales.

Este tipo de criptografía utiliza diferentes algoritmos para cifrar o
descifrar información a partir del problema del logaritmo discreto. Su
rendimiento actual es capaz de garantizar una seguridad equivalente a
métodos antiguos (como RSA), pero con la ventaja de trabajar con claves
mucho menores que en otros casos. Esto implica una mejora significativa
del rendimiento, sobretodo en para dispositivos o ámbitos donde
minimizar el gasto de memoria es fundamental, como por ejemplo en
tarjetas inteligentes o en la tecnología blockchain.

A lo largo de este capítulo, vamos a introducir la teoría de curvas
elípticas, su uso en criptografía y diferentes algoritmos que trabajan
ellas. Si desea profundizar en este tema, puede consultar el libro
*Criptografía con curvas elípticas* . o la lectura del temario completo
sobre la criptografía de curvas elípticas de Criptored . Criptored es
una Red Temática Iberoamericana de Criptografía y Seguridad, que
colaboró con la Universidad Politécnica de Madrid a través del Dr. Jorge
Ramió hasta su jubilación en 2021.

## Curvas elípticas

Las curvas elípticas conforman un campo de las matemáticas relativamente
nuevo. Hasta el año 1985 no se escucha hablar de ellas y su popularidad
aumenta porque se empiezan a implementar sistemas criptográficos más
difíciles de romper, cuyas claves son más pequeñas que con otros
criptosistemas de clave pública convencionales.

Para la correcta comprensión de este tema, se van a explicar diferentes
conceptos claves en las siguientes secciones.

### Curva algebraica

Una curva algebraica está formada por el conjunto de puntos
(*x*<sub>1</sub>, *y*<sub>1</sub>) que satisfacen que
*p*(*x*<sub>1</sub>,*y*<sub>1</sub>) = 0. Una curva plana definida sobre
un cuerpo *K* puede expresarse en el plano afín como
*A*<sup>2</sup>(*K*) mediante la función *f*(*x*,*y*) = 0. El conjunto
de puntos (*x*,*y*) de *K*<sup>2</sup> son las coordenadas afines o no
homogéneas de un punto cualquiera de la curva. Por otro lado, la misma
curva puede representarse en el plano proyectivo sobre el cuerpo *K*
como *P*<sup>2</sup>(*K*), mediante la ecuación *f*(*x*,*y*,*z*) = 0. El
conjunto de puntos (*x*,*y*,*z*) ∈ *K*<sup>3</sup> − {0, 0, 0} son las
coordenadas proyectivas y homogéneas de un punto de la curva.

Las coordenadas proyectivas están formadas por las relaciones de
equivalencia ∼ tal que dos puntos
(*x*<sub>1</sub>,*y*<sub>1</sub>,*z*<sub>1</sub>) y
(*x*<sub>2</sub>,*y*<sub>2</sub>,*z*<sub>2</sub>) son equivalentes si
existe un valor *λ* ≠ 0 con el que
(*x*<sub>1</sub>,*y*<sub>1</sub>,*z*<sub>1</sub>) = (*λ**x*<sub>2</sub>,*λ**y*<sub>2</sub>,*λ**z*<sub>2</sub>).
Cada clase de equivalencia es un punto proyectivo y se denotan como
(*x*:*y*:*z*). + Existe solamente un punto de la forma
(*x*/*z*,*y*/*z*,1). De modo que a partir de *z* = 0, es posible
identificar puntos proyectivos con puntos afines.

En función del grado de los coeficientes de la curva, puede ser
denominadas con un nombre particular. Las de grado 1 son conocidas
como**lineales**, las de grado 2 como **cónicas** y las de grado 3,
**cúbicas**. También, se diferencia las curvas según otra
características de sus puntos. Un punto es singular en el caso de que
las derivadas parciales se anulen en dicho punto, es decir, el punto
puede ser definido por varias tangentes. Si son dos tangentes distintas,
se trata de un nodo (figura
<a href="#fig:nodo" data-reference-type="ref"
data-reference="fig:nodo">1.1</a>), pero si es una tangente doble, se
conoce como cúspide (figura
<a href="#fig:cuspide" data-reference-type="ref"
data-reference="fig:cuspide">1.2</a>).

Los puntos de la curva que se definen con una única tangente, son
denominados lisos. Si todos los puntos de una curva son lisos, se
tratará de una curva no singular, pero con un solo punto que no sea
liso, se tratará de una curva singular.

<figure>
<img src="Figures/ECC3.jpg" id="fig:nodo"
alt="Curva y^2 = x^3 + 5x^2 sobre \mathbb R con un nodo en (0,0)." />
<figcaption aria-hidden="true">Curva <span
class="math inline"><em>y</em><sup>2</sup> = <em>x</em><sup>3</sup> + 5<em>x</em><sup>2</sup></span>
sobre <span class="math inline">ℝ</span> con un nodo en
(0,0).</figcaption>
</figure>

<figure>
<img src="Figures/ECC2.jpg" id="fig:cuspide"
alt="Curva y^2 = 0.25x^3 sobre \mathbb R con una cúspide en (0,0)." />
<figcaption aria-hidden="true">Curva <span
class="math inline"><em>y</em><sup>2</sup> = 0.25<em>x</em><sup>3</sup></span>
sobre <span class="math inline">ℝ</span> con una cúspide en
(0,0).</figcaption>
</figure>

Sea *K* un cuerpo, decimos que *p* = (*x*,*y*) es un punto racional de
la curva si *f*(*p*) = 0 y *p* ∈ *K*<sup>2</sup>.

### Definición de curva elíptica

Una **curva elíptica** es una curva plana no singular de grado 3 junto
con un punto racional prefijado, que denominaremos punto base. Se
denomina orden o cardinalidad de una curva al número de elementos de esa
curva.

#### Ecuación de Weierstrass

Una curva elíptica sobre un cuerpo *K* es una curva algebraica que se
representa a partir de la ecuación general de Weierstrass:
$$y^2 + a_1xy + a_3y = x^3 + a_2x^2 + a_4x + a_6 \hspace{0.6cm} a_i \in K$$

Cuando la característica del cuerpo es distinta de 2 y 3, es denominada
ecuación reducida de Weierstrass y se representa:
$$y^2 = x^3 + ax + b \hspace{0.5cm} a,b \in K$$

En la figura <a href="#fig:curvaeliptica" data-reference-type="ref"
data-reference="fig:curvaeliptica">1.3</a> podemos ver una curva
elíptica representada con la ecuación reducida de Weierstrass.

Los elementos que tomamos para los valores de *a*, *b* pueden pertenecer
a diferentes conjuntos, pero siempre con la estructura de cuerpo. Por
ejemplo, los números reales ℝ, los números complejos ℂ, los números
racionales ℚ, uno de los campos finitos
*F*<sub>*p*</sub>(=ℤ<sub>*p*</sub>) para un primo *p*, o uno de los
campos finitos *F*<sub>*q*</sub>, donde *q* = *p**k* con *k* ≥ 1. En uno
de los siguientes apartados, vamos a profundizar en cuerpos finitos, que
serán en los que se va a apoyar este trabajo.

Para obtener los valores *a*, *b* ∈ *K* y que la curva no tenga
singularidades, se tiene que cumplir que:
4*a*<sup>3</sup> + 27*b*<sup>2</sup> ≠ 0 (*m**o**d* *p*)

<figure>
<img src="Figures/ECC1a.jpg" id="fig:curvaeliptica"
alt="Curva elíptica y^2 = x^3 - 10x + 15 definida sobre \mathbb R." />
<figcaption aria-hidden="true">Curva elíptica <span
class="math inline"><em>y</em><sup>2</sup> = <em>x</em><sup>3</sup> − 10<em>x</em> + 15</span>
definida sobre <span class="math inline">ℝ</span>.</figcaption>
</figure>

La ecuación homogénea de Weierstrass define una curva proyectiva plana
con el punto especial denominado **punto en el infinito**,
*O* = \[0:1:0\], que no tiene correspondencia en el plano afín.

### Estructura de grupo

El conjunto de puntos *G* que forman la curva (soluciones de la ecuación
y punto en el infinito *O*) junto con la operación aditiva +, forman un
grupo abeliano. Una vez más es importante destacar que el problema del
logaritmo discreto sobre un conjunto de puntos de un grupo abeliano
finito (PLDCE) presenta un nivel de seguridad igual o superior al de los
cuerpos finitos (PLD), con la ventaja extra de un menor tamaño de claves
en la criptografía de curvas elípticas.

Si *E*/*K* es una curva elíptica sobre un cuerpo *K*, denotaremos por
*E*(*K*) el conjunto de puntos *P* = (*x*,*y*) ∈ *K* × *K* que
satisfacen la ecuación de la curva junto con el punto del infinito de la
curva *O*. Sobre ese conjunto de puntos se define una operación interna
a partir del método de la cuerda y la tangente (figura
<a href="#fig:sumapuntos" data-reference-type="ref"
data-reference="fig:sumapuntos">1.4</a>), que consiste en trazar una
recta *r* por los dos puntos *P* y *Q* y se calcula el tercer punto
intersección *R* de la recta *r* con la curva. Lo llamamos suma elíptica
y le proporciona al conjunto la estructura de grupo abeliano, cuyo
elemento neutro es el punto del infinito de la curva.

<figure>
<img src="Figures/ECC4.jpg" id="fig:sumapuntos"
alt="Ejemplo de suma de puntos R = P + Q" />
<figcaption aria-hidden="true">Ejemplo de suma de puntos <span
class="math inline"><em>R</em> = <em>P</em> + <em>Q</em></span></figcaption>
</figure>

Con lo que acabamos de ver, para todo punto *P* de la curva, podemos
definir la operación suma de puntos de la siguiente manera:

1.  *P* + *O* = *O* + *P* = *P*, es decir, *O* es el elemento neutro de
    la suma.

2.  Existe
     − *P* = (*x*<sub>*P*</sub>−*y*<sub>*P*</sub>−*a*<sub>1</sub>*x*<sub>*P*</sub>−*a*<sub>3</sub>),
    de manera que *P* + (−*P*) = *O*.

3.  Dados dos puntos *P* ≠ *Q*, se define
    *R* = *P* + *Q* = (*x*<sub>*R*</sub>,*y*<sub>*R*</sub>) de manera
    que:
    *x*<sub>*R*</sub> = *λ*<sup>2</sup> + *a*<sub>1</sub>*λ* − *a*<sub>2</sub> − *x*<sub>*P*</sub> − *x*<sub>*Q*</sub>,
    *y*<sub>*R*</sub> = *λ*(*x*<sub>*P*</sub>−*x*<sub>*R*</sub>) − *y*<sub>*P*</sub> − *a*<sub>1</sub>*x*<sub>*R*</sub> − *a*<sub>3</sub>,
    $$\lambda = \dfrac{y_Q - y_P}{x_Q - x_P }$$

4.  La duplicación de un punto *P* es el punto *R* = *P* + *P* = 2*P* de
    manera que:
    *x*<sub>*R*</sub> = *λ*<sup>2</sup> + *a*<sub>1</sub>*λ* − *a*<sub>2</sub> − *x*<sub>*P*</sub> − *x*<sub>*Q*</sub>,
    *y*<sub>*R*</sub> = *λ*(*x*<sub>*P*</sub>−*x*<sub>*R*</sub>) − *y*<sub>*P*</sub> − *a*<sub>1</sub>*x*<sub>*R*</sub> − *a*<sub>3</sub>,
    $$\lambda = \dfrac{3x^2_P +2a_2x_P + a_4 -a_1y_P}{2y_P +a_1x_P + a_3}$$

Como hemos visto en el primer punto, al sumar dos puntos que tengan el
mismo valor de en la primera coordenada, la recta que pasa por ambos
conjuntos no corta a la curva en ningún otro punto. Esto se debe a que
la recta corta a la curva en el punto del infinito.

Finalmente, vamos a asegurar que la operación suma descrita
anteriormente cumple las propiedades de grupo y tiene estructura de
grupo abeliano:

1.  Asociatividad: (*P*+*Q*) = *R* = *P* + (*Q*+*R*) para todo
    *P*, *Q*, *R* ∈ *E*(*K*).

2.  Existencia de elemento neutro: *O* : *P* + *O* para todo punto
    *P* ∈ *E*(*K*).

3.  Existencia de elemento inverso: *P* + *P*′ = *O* donde
    *P*′ =  − *P*.

4.  Conmutatividad: *P* + *Q* = *Q* + *P* para todo *P*, *Q* ∈ *E*(*K*).

De manera adicional, existe otra operación en los cálculos con puntos de
una curva. Consiste en el producto de un punto *P* por un entero
positivo *k*, que es el equivalente de sumar el punto *P* una cantidad
de *k* veces consigo mismo.
*k**P* = *P* + ...<sup>(*k*)</sup>... + *P*
Esta operación, que es el equivalente aditivo de la exponenciación en
grupos abelianos multiplicativos, es la base de la criptografía con
curvas elípticas. Además, en criptografía se trabajará con grupos
finitos grandes, cuyos elementos tengan una buena representación. Así,
en lugar de definir las curvas elípticas sobre cuerpos de característica
0, serán definidas sobre cuerpos finitos.

### Curvas elípticas sobre cuerpos finitos

Como hemos visto anteriormente, el orden de un cuerpo finito 𝔽 es el
número de elementos de dicho cuerpo. Es posible demostrar que la
existencia de un cuerpo finito de orden *q*, denominado 𝔽<sub>*q*</sub>,
está relacionada con el valor de *q* = *p*<sup>*m*</sup>, donde *p* es
la característica del cuerpo que siempre es un número primo y *m* es
cualquier entero positivo. Además, existe un único cuerpo, salvo
isomorfismos, con cardinal *p*<sup>*m*</sup>. Normalmente en
criptosistemas de curvas elípticas se utilizan dos tipos de cuerpos
finitos: el cuerpo finito primo 𝔽<sub>*q*</sub> y el cuerpo finito
binario 𝔽<sub>2<sup>*m*</sup></sub>.

**Ejemplos:**
𝔽<sub>7</sub> = {0, 1, 2, 3, 4, 5, 6}
𝔽<sub>2<sup>3</sup></sub> = {0, 1, *x*, *x* + 1, *x*<sup>2</sup>, *x*<sup>2</sup> + 1, *x*<sup>2</sup> + *x*, *x*<sup>2</sup> + *x* + 1}

En la figura <a href="#fig:sumafinitos" data-reference-type="ref"
data-reference="fig:sumafinitos">1.5</a> se puede ver la representación
de los puntos con coordenadas afines y la suma de puntos en una curva
sobre un cuerpo finito.

<figure>
<img src="Figures/ECC5.jpg" id="fig:sumafinitos"
alt="Ejemplo de suma de puntos R = P + Q en un cuerpo finito" />
<figcaption aria-hidden="true">Ejemplo de suma de puntos <span
class="math inline"><em>R</em> = <em>P</em> + <em>Q</em></span> en un
cuerpo finito</figcaption>
</figure>

## Uso en criptografía

En esta sección, analizaremos algunos de los criptosistemas que utilizan
curvas elípticas. En su mayoría trataremos aquellos que se basan en el
problema del logaritmo discreto, por lo que se incluye una explicación
más profunda sobre PLD.

La criptografía de curvas elípticas proporciona una seguridad
equivalente a los sistemas clásicos utilizando menos bits. Se estima que
una clave tamaño de 4096 bits para RSA (algoritmo asimétrico)
proporciona el mismo nivel de seguridad que 313 bits en un sistema
criptografíco de curva elíptica.

<figure>
<img src="Figures/ECC7.jpg" id="fig:tabla_bits"
alt="Comparación entre RSA y ECC" />
<figcaption aria-hidden="true">Comparación entre RSA y ECC</figcaption>
</figure>

En la tabla <a href="#fig:tabla_bits" data-reference-type="ref"
data-reference="fig:tabla_bits">1.6</a> se puede ver la comparación de
las longitudes de las claves entre RSA y ECC., mientras que en la figura
<a href="#fig:grafico_bits" data-reference-type="ref"
data-reference="fig:grafico_bits">1.7</a>, se puede ver la comparación
de rendimiento entre RSA y ECC. Con claves mucho menores, las curvas
elípticas son capaces de conseguir el mismo nivel de seguridad.

<figure>
<img src="Figures/ECC6.jpg" id="fig:grafico_bits"
alt="Comparación entre RSA y ECC" />
<figcaption aria-hidden="true">Comparación entre RSA y ECC</figcaption>
</figure>

Estos datos demuestran que el uso de curvas elípticas ofrece mejor
rendimiento que otras propuestas, por lo que consideramos que sus
ventajas provocarán un incremento de uso en un futuro próximo.

La información descrita a lo largo de esta sección ha sido obtenida a
partir de libros como *Elliptic curves: number theory and cryptography*
o *Criptografía con curvas elípticas* .

### Introducción

El auge de las comunicaciones digitales durante los últimos años ha
provocado el aumento de manera considerable de problemas de relacionados
con el ámbito de la seguridad. La información enviada a través de la red
puede llegar a tener un alto valor, por lo su intercepción supone un
alto nivel riesgo. La seguridad de dicha información debe garantizarse
para un uso adecuado de la comunicación.

La criptografía es la parte de la criptología que se encarga del estudio
de diferentes métodos (algoritmos, protocolos y sistemas) que tratan de
garantizar la confidencialidad y la integridad de la información. La
criptografía utiliza diferentes técnicas matemáticas que sirven como
herramientas para garantizar objetivos.

Hay dos tipos básicos de cifrado. El cifrado simétrico es aquel en el
que la clave de cifrado y la clave de descifrado son las mismas (o una
puede deducirse fácilmente una de la otra), y el cifrado de clave
pública o asimétrico, en el que tanto emisor como receptor tienen una
clave pública los emisores la usen para cifrar la información y una
privada para que solamente ellos pueden descifrarla.

### El Problema del Logaritmo Discreto

La criptofrafía de curvas elípticas está basada en el Problema del
Logaritmo Discreto. El hecho de que el problema no se pueda resolver en
un tiempo razonable si se utiliza aritmética modular, conlleva a su
amplio uso en criptografía. El logaritmo discreto de *y* en base *g*
donde *g*, *y* son elementos de un grupo cíclico finito *G*, es la
solución *x* de la ecuación *g*<sup>*x*</sup> = *y*, o lo que es lo
mismo:
*x* = *l**o**g*<sub>*g*</sub>(*y*) → *g*<sup>*x*</sup> = *y*

El valor de *x* es difícil de averiguar cuando trabajamos con números
primos de gran tamaño. El cálculo de su inversa es una tarea muy
sencilla en términos computacionales, pero el cálculo del logaritmo
discreto es complejo cuando se trabaja con ciertos grupos. El problema
real es que no se puede resolver en un tiempo razonable si se utiliza
aritmética modular.

Como se acaba de mencionar, la dificultad a la hora de resolver el
problema, varía según el grupo en el que se trabaja. Por ejemplo, cuando
trabajamos con el conjunto de los números enteros ℤ con la operación
suma o el conjunto de los números reales sin el cero (ℝ − {0}) con la
multiplicación, es demasiado fácil de romper.

Existen diferentes tipos de algoritmos que se encargan de la computación
para resolver el problema del logaritmo discreto, como elevar sucesivas
potencias hasta encontrar la deseada o la factorización de enteros.
Estos algoritmos funcionan más rápido que el algoritmo anterior, pero
ninguno corre en un tiempo polinómico. Algunos de los algoritmos
funcionan para cualquier grupo, mientras otros sólo trabajan para grupos
concretos. Como el objetivo de este trabajo no es el estudio de estos
algoritmos, para obtener más información se recomienda leer el capítulo
6 del libro *Cryptography: Theory and Practice* .

La criptografía clásica trabaja con el conjunto de enteros módulo *n*
(ℤ<sub>*n*</sub><sup>\*</sup>, ⋅), donde la operación aumenta
considerablemente su dificultad. El problema con este último grupo es
que no está demostrado que sea o no resoluble en un tiempo polinómico.
En el apartado anterior
<a href="#sec:CurvasElipticas" data-reference-type="ref"
data-reference="sec:CurvasElipticas">1.1</a>, hemos estudiado las curvas
elípticas, que a partir de los puntos de un grupo *G* que forman dicha
curva, obtenemos un conjunto finito donde se cree que es más difícil de
resolver el Problema del Logaritmo Discreto. Este caso, se conoce como
Problema del Logaritmo Discreto en Curvas Elípticas (PLDCE). Para un
análisis más profundo de este tema, se recomienda la lectura del
capítulo *The elliptic curve discrete logarithm problem* del libro
*Guide to Elliptic Curve Cryptography* .

Sea 𝔽<sub>2131</sub><sup>\*</sup> un grupo multiplicativo del conjunto
de enteros módulo 2131, se tiene que
𝔽<sub>2131</sub><sup>\*</sup> ≡ ⟨37⟩. Como 1217 ≡ 37<sup>5</sup> (mód
2131), el logaritmo discreto de 1217 en base 37 es 5.

Hemos podido comprobar que la exponenciación es una función trampa, ya
que aumenta la complejidad. Por este motivo, algunos criptosistemas
basan su seguridad en el PLD. Durante los siguientes apartados se
estudian varios algoritmos cuya seguridad reside en la extrema
dificultad de calcular logaritmos discretos en un cuerpo finito. Como la
idea fundamental del trabajo es estudiar la criptografía del curvas
elípticas, todos los algoritmos trabajarán con curvas elípticas
establecidas por los interlocutores sobre un cuerpo finito. La
información descrita ha sido obtenida en el capítulo 6 (*Elliptic Curve
Cryptography*) del libro *Elliptic curves: number theory and
cryptography*

### Algoritmo de Diffie-Hellman

El protocolo criptográfico Diffie-Hellman (figura
<a href="#fig:Diffie-Hellman" data-reference-type="ref"
data-reference="fig:Diffie-Hellman">1.8</a>) consiste en utilizar una
clave compartida entre dos interlocutores sin permitir que alguien que
acceda a las comunicaciones, pueda llegar a obtenerla. Para ello, cada
uno tiene una clave pública propia y otra secreta.

Los interlocutores utilizan una fórmula matemática que incluye
exponenciación y necesita dos números públicos y un número secreto. Los
resultados tras la operación, se intercambian de forma pública. Revertir
esta función es tan difícil como calcular un logaritmo discreto. Como
hemos visto en la introducción, esta operación es muchísimo más costosa
que la exponenciación usada para transformar los números inicialmente.

Por último, cada interlocutor utiliza una fórmula matemática que combina
los resultados de la primera operación con su número secreto y ambos
obtienen resultado final, que será la clave compartida. La descripción
paso a paso del protocolo criptográfico de Diffie-Hellman entre los
interlocutores *A* y *B* sería:

1.  *A* y *B* acuerdan trabajar con la curva elíptica *E* sobre un campo
    finito 𝔽<sub>*q*</sub> y el punto *P* ∈ *E*(𝔽<sub>*q*</sub>), cuyo
    subgrupo generado tiene un orden grande. Normalmente la curva
    elíptica y el punto son elegidos para que el orden sea un número
    primo de gran tamaño.

2.  *A* elige un número entero secreto *a*, calcula
    *P*<sub>*a*</sub> = *a**P* y envía *P*<sub>*a*</sub> a *B*.

3.  *B* elige un número entero secreto *b*, calcula
    *P*<sub>*b*</sub> = *b**P* y envía *P*<sub>*b*</sub> a *A*.

4.  *A* computa *a**P*<sub>*b*</sub> = *a**b**P*.

5.  *B* computa *b**P*<sub>*a*</sub> = *b**a**P*.

6.  *A* y *B* utilizan un método acordado para extraer una clave del
    resultado de *a**b**P*. Por ejemplo, podrían usar los últimos bits
    de la coordenada *x* de *a**b**P* o utilizar una función hash en la
    coordenada.

<figure>
<img src="Figures/Diffie-Hellman.jpg" id="fig:Diffie-Hellman"
alt="Intercambio de claves Diffie-Hellman" />
<figcaption aria-hidden="true">Intercambio de claves
Diffie-Hellman</figcaption>
</figure>

Por lo tanto, la única información pública es la curva *E*, el campo
finito 𝔽<sub>*q*</sub> y los puntos *P*, *P*<sub>*a*</sub> y
*P*<sub>*b*</sub>. La única manera de calcular *a**b**P* sería mediante
el Problema del Logaritmo Discreto.

### Algoritmo de Massey-Omura

Este criptosistema (figura
<a href="#fig:Massey-Omura" data-reference-type="ref"
data-reference="fig:Massey-Omura">1.9</a>) utiliza la conmutatividad de
ciertas funciones para conseguir que dos personas intercambien un
mensaje de forma segura, sin llegar a compartir ninguna clave
públicamente. El procedimiento entre *A* y *B* sería el siguiente:

1.  *A* y *B* eligen una curva elíptica *E* sobre un campo finito
    𝔽<sub>*q*</sub> de manera que el Problema del Logaritmo Discreto es
    difícil de resolver en *E*(𝔽<sub>*q*</sub>).

2.  *A* representa su mensaje como un punto *M* ∈ *E*(𝔽<sub>*q*</sub>).
    Elige un número entero como su clave *m*<sub>*A*</sub> que cumpla
    *M**C**D*(*m*<sub>*A*</sub>,*E*(𝔽<sub>*q*</sub>)) = 1. Por último,
    calcula *M*<sub>1</sub> = *m*<sub>*A*</sub>*M* y se lo envía a *B*.

3.  *B* elige un número entero como su clave *m*<sub>*B*</sub> que
    cumpla *M**C**D*(*m*<sub>*B*</sub>,*E*(𝔽<sub>*q*</sub>)) = 1. Por
    último, calcula *M*<sub>2</sub> = *m*<sub>*B*</sub>*M* y se lo envía
    a *A*.

4.  *A* calcula
    *m*<sub>*A*</sub><sup>−1</sup> ∈ ℤ<sub>*E*(𝔽<sub>*q*</sub>)</sub>.
    Calcula
    *M*<sub>3</sub> = *m*<sub>*A*</sub><sup>−1</sup>*M*<sub>2</sub> y
    envía *M*<sub>3</sub> a *B*.

5.  *B* calcula
    *m*<sub>*B*</sub><sup>−1</sup> ∈ ℤ<sub>*E*(𝔽<sub>*q*</sub>)</sub>.
    Calcula
    *M*<sub>4</sub> = *m*<sub>*B*</sub><sup>−1</sup>*M*<sub>3</sub> y
    obtiene el mensaje inicial, porque *M*<sub>4</sub> equivale al *M*
    inicial del paso 2.

La fórmula completa del proceso es:
*M*4 = *m*<sub>*B*</sub><sup>−1</sup>*m*<sub>*A*</sub><sup>−1</sup>*m*<sub>*B*</sub>*m*<sub>*A*</sub>*M* = *M*

Donde *m*<sub>*A*</sub><sup>−1</sup> y *m*<sub>*B*</sub><sup>−1</sup>
representan al inverso de *m*<sub>*A*</sub> y *m*<sub>*B*</sub> mod *N*,
respectivamente.

<figure>
<img src="Figures/Massey-Omura.jpg" id="fig:Massey-Omura"
alt="Criptosistema de Massey-Omura" />
<figcaption aria-hidden="true">Criptosistema de
Massey-Omura</figcaption>
</figure>

### Algoritmo de ElGamal para Clave Pública

El procedimiento de cifrado/descifrado ElGamal (figura
<a href="#fig:ElGamal" data-reference-type="ref"
data-reference="fig:ElGamal">1.10</a>) es un algoritmo de criptografía
asimétrica basado en la idea de Diffie-Hellman y que funciona de una
forma parecida, pero con algunas mejoras.

El algoritmo consiste en que el receptor elige una curva elíptica *E*
sobre un campo finito *F*<sub>*q*</sub> de manera que el problema del
logaritmo discreto sea difícil de resolver para *E*(*F*<sub>*q*</sub>).
También elige un punto *P* en la curva elíptica *E*, cuyo orden es un
número primo grande. Además, elige un número entero secreto *s* y
calcula *B* = *s**P*. La curva elíptica *E*, el campo finito
𝔽<sub>*q*</sub> y los puntos *P* y *B* son la clave pública para el
emisor y cualquiera puede conocer estos datos. La clave privada es el
entero *s* que solamente conoce el receptor del mensaje.

Para enviar un mensaje al receptor anterior, hay que seguir los
siguientes pasos:

1.  Descargar su clave pública (curva elíptica *E*, el campo finito
    𝔽<sub>*q*</sub> y los puntos *P* y *B*).

2.  Expresar nuestro mensaje como un punto *M* ∈ *E*(𝔽<sub>*q*</sub>).

3.  Elegir un entero aleatorio secreto *k* y calcular
    *M*<sub>1</sub> = *k**P*.

4.  Calcular *M*<sub>2</sub> = *M* + *k**B*.

5.  Enviar *M*<sub>1</sub>, *M*<sub>2</sub> al receptor.

El receptor obtendrá el mensaje inicial, después de descifrar mediante
la siguiente operación:
*M* = *M*2 − *s**M*1

<figure>
<img src="Figures/ElGamal.jpg" id="fig:ElGamal"
alt="Algoritmo de ElGamal para Clave Pública" />
<figcaption aria-hidden="true">Algoritmo de ElGamal para Clave
Pública</figcaption>
</figure>

### Algoritmo de ElGamal para Firma Digital

La firma clásica se puede integrar de modo muy sencillo a cualquier
documento gracias a la digitalización, pero tiene la desventaja de que
cualquiera puede utilizar esa firma. Por lo tanto, es necesario tomar
medidas para asociar la firma al documento de tal manera que no se pueda
volver a utilizar. Además, debe ser posible verificar que la firma es
válida y demostrar que pertenece a esa persona. La solución a estos
problemas, se resuelve mediante el algoritmo de ElGamal para la firma
digital (figura <a href="#fig:ElGamal-Firma" data-reference-type="ref"
data-reference="fig:ElGamal-Firma">1.11</a>). Inicialmente el algoritmo
se desarrolló para el grupo multiplicativo de un campo finito y se
aplica a cualquier grupo finito. En este caso, lo vamos a presentar para
curvas elípticas.

Para firmar un documento con este algoritmo, primero se necesita
establecer una clave pública y elegir la curva elíptica *E* sobre un
campo finito 𝔽<sub>*q*</sub> donde se va a trabajar, de manera que el
Problema del Logaritmo Discreto sea difícil de resolver. Además hay que
elegir un punto de *A* ∈ *E*(𝔽<sub>*q*</sub>), cuyo orden sea un número
primo grande *N*. Por último, a partir de un número entero privado *a*,
calcular *B* = *a**A* y elegir la función
*f* : *E*(𝔽<sub>*q*</sub>) → ℤ, necesaria para operar.

Por lo tanto, La información pública es ***E*, 𝔽<sub>*q*</sub>, *f*, *A*
y *B***, a es la clave privada y *N* no necesita hacerse público, porque
ni afecta a la seguridad, ni sirve para firmar.

Los pasos para firmar un documento son los siguientes:

1.  Representar el documento como un entero *m*. En caso de que *m* sea
    más grande orden del punto *A*, habría que utilizar una curva más
    grande o usar una función hash.

2.  Elegir un número entero aleatorio *k* con mcd(*k*,*N*) = 1 y calcula
    *R* = *k**A*.

3.  Calcular *s* ≡ *k* − 1(*m*−*a**f*(*R*))(*m**o**d**N*).

Después de estos pasos, el mensaje firmado estaría formado por
*m*, *R*, *s* donde *m*, *s* son números enteros y *R* ∈
*E*(*F*<sub>*q*</sub>). Para poder verificar que el documento está
firmado, se tienen que realizar los siguientes pasos:

1.  Descargar la información pública del firmante.

2.  Calcular *V*<sub>1</sub> = *f*(*R*)*B* + *s**R* y
    *V*<sub>2</sub> = *m**A*.

3.  Si *V*<sub>1</sub> = *V*<sub>2</sub>, la firma es válida y el
    documento está firmado por la persona adecuada.

<figure>
<img src="Figures/ElGamal-Firma.jpg" id="fig:ElGamal-Firma"
alt="Algoritmo de ElGamal para Firma DIgital" />
<figcaption aria-hidden="true">Algoritmo de ElGamal para Firma
DIgital</figcaption>
</figure>

### Algoritmo de Firma Digital

La firma digital es básicamente un conjunto de datos asociados a un
mensaje que permiten asegurar la identidad del firmante y la integridad
del mensaje, igual que hemos podido ver en el apartado anterior. La
firma digital debe depender tanto del mensaje como del autor. Si esto no
fuese así, el receptor podría modificar el mensaje y mantener la firma,
produciendo así un fraude. Los criptosistemas de clave pública pueden
ser fácilmente utilizados para generar firmas digitales. El Algoritmo de
Firma Digital (DSA por sus siglas en inglés) es una variante del esquema
de firmas de ElGamal, con algunas modificaciones.

Para firmar un documento *m*, que es un número entero (normalmente se
firma el hash del documento), se elige una curva elíptica sobre un campo
finito 𝔽<sub>*q*</sub> tal que *E*(𝔽<sub>*q*</sub>) = *f**r*, donde *r*
es un número primo grande y *f* es un número entero pequeño,
generalmente 1, 2 o 4 (*f* debería ser pequeño para mantener el
algoritmo eficiente). Además, se elige un punto *G* en *E*(𝔽*q*) de
orden *r*. Finalmente, se escoge un entero secreto *a* y hay que
calcular *Q* = *a**G*.

La información pública es **𝔽<sub>*q*</sub>, *E*, *r*, *G*, *Q*** y para
firmar el mensaje *m*, se siguen los siguientes pasos:

1.  Elegir un número entero aleatorio *k* con 1 ≤ *k* \< *r* y calcula
    *R* = *k**G* = (*x*,*y*).

2.  Calcular *s* = *k*<sup>−1</sup>(*m*+*a**x*)(mod *r*).

El documento firmado es (*m*,*R*,*s*). Para verificar la firma, se hace
lo siguiente:

1.  Calcular *u*<sub>1</sub> = *s*<sup>−1</sup>*m*(*m**o**d**r*) y
    *u*<sub>2</sub> = *s*<sup>−1</sup>*x*(*m**o**d**r*).

2.  Calcular *V* = *u*<sub>1</sub>*G* + *u*<sub>2</sub>*Q*.

3.  En caso de que *V* = *R*, la firma es válida y el documento está
    firmado por la persona adecuada.
    
# Redes Neuronales

## Introducción

La computación cada día es más potente y el ser humano continua
trabajando en el desafío de automatizar tareas relativamente simples
para las personas, como reconocer una letra o diferenciar un animal.
Gracias a nuestro aprendizaje, somos capaces de lograr un mejor
desempeño en tareas más complejas, como maximizar recursos o alcanzar un
objetivo común. Algunas de estas actividades pueden ser agrupadas en
patrones similares o ser resueltas mediante soluciones informáticas.

El desarrollo de las redes neuronales artificiales comenzó hace
aproximadamente 50 años, motivado por el deseo de intentar comprender el
cerebro e imitar algunas de sus fortalezas. Las ideas iniciales sobre el
aprendizaje en máquinas estuvieron en un segundo plano debido al gran
progreso de la computación digital. Además, la ideas generadas sobre los
primeros modelos de redes neuronales fueron negativas y llevaron a
numerosas dudas. Un renovado reciente interés en el campo ha surgido
gracias a nuevas arquitecturas y técnicas de entrenamiento, ordenadores
de alto rendimiento y hardware mucho más específico para realizar
simulaciones de redes neuronales en condiciones mucho más óptimas. A su
vez, el progreso en la computación tradicional ha hecho que el estudio
de este campo sea más sencillo y se han encontrado nuevas limitaciones,
que han motivado a tomar otras direcciones en la investigación.

Las redes neuronales son interesantes en diferentes áreas por muchas
razones. En electrónica se usan en aplicaciones de procesamiento de
señales y teoría de control, en computación para la mejora de
rendimiento de hardware, o en robótica, diferentes áreas como
inteligencia artificial o el reconocimiento de patrones, las utilizan
como herramienta para modelar problemas.

Una red neuronal artificial es un sistema de procesamiento de
información que comparte características con las redes neuronales
biológicas. Concretamente, son modelos matemáticos que cumplen que:

-   La información se procesa en elementos simples llamados neuronas.

-   Las neuronas se encuentran conectadas entre sí y se envían señales
    de datos.

-   Cada conexión tiene un peso o valor que multiplica la señal que
    llega a la neurona.

-   Cada neurona utiliza una función de activación para determinar la
    señal de salida.

La red neuronal está caracterizada por su patrón de conexiones entre las
neuronas, que se conoce como arquitectura. El método que se usa para
determinar los pesos de las conexiones es llamado entrenamiento o
aprendizaje.

Se recomienda la lectura de *Fundamentals of neural networks:
architectures, algorithms, and applications* y *Pattern Recognition and
Machine Learning* para obtener información más profunda y completa sobre
de las redes neuronales.

### Aprendizaje automático

El aprendizaje automático forma parte de una rama de la inteligencia
artificial y es un proceso mediante el cual se usan modelos matemáticos
de datos con el objetivo de que las computadoras aprendan sin
instrucciones directas. El aprendizaje automático trabaja con algoritmos
que tratan de identificar patrones en conjuntos de datos, y a partir de
los patrones, se crean modelos de datos para hacer predicciones. Los
resultados del aprendizaje son más precisos con la experiencia y
conjuntos de datos más amplios, es decir, las computadoras aprenden de
manera similar a los humanos, ya que mejoran con la práctica.

El aprendizaje automático es una opción ideal en casos donde los datos o
la tarea a realizar se cambian constantemente, ya que la codificación de
una solución para estos problemas, sería prácticamente imposible de
construir manualmente o tendría un alto coste en caso de ser posible. Es
utilizado en una gran cantidad de aplicaciones, como por ejemplo en
diagnósticos médicos, robótica o motores de búsqueda.

Dentro del aprendizaje automático encontramos dos tipos según si es el
aprendizaje es supervisado o no. En la figura
<a href="#fig:clas_aprendizaje" data-reference-type="ref"
data-reference="fig:clas_aprendizaje">1.1</a> podemos observar ambos
conjuntos y otros subtipos dentro de cada una. A lo largo de este
capítulo estudiaremos los más importantes.

<figure>
<img src="Figures/RN3.jpg" id="fig:clas_aprendizaje"
alt="Clasificación aprendizaje automático" />
<figcaption aria-hidden="true">Clasificación aprendizaje
automático</figcaption>
</figure>

### Redes neuronales biológicas

La semejanza entra la estructura de las redes neuronales artificiales y
biológicas es bastante clara. Un neurona biológica (figura
<a href="#fig:neurona_biologica" data-reference-type="ref"
data-reference="fig:neurona_biologica">1.2</a>) tiene tres tipos de
componentes que son interesantes para entender la artificial (figura
<a href="#fig:neurona_artifical" data-reference-type="ref"
data-reference="fig:neurona_artifical">1.4</a>): dentritas, soma y axón.

-   Las **dentritas** reciben señales desde otras neuronas. Las señales
    son impulsos eléctricos, transmitidos a través de una brecha
    sináptica, es decir, mediante procesos químicos. El transmisor
    químico modifica la señal entrante de manera similar a los pesos en
    la neurona artificial.

-   El **soma** es el cuerpo de la neurona y suma los impulsos
    recibidos. Cuando recibe la cantidad suficiente, se produce el
    incendio celular que transmite la señal a otras células. Esta forma
    de transmitir puede ser tratada como binaria, ya que o la neurona
    manda la señal o no.

-   El **axón** es la conexión entre las neuronas, por donde cada una
    envía sus impulsos.

<figure>
<img src="Figures/RN5.jpg" id="fig:neurona_biologica"
alt="Neurona biológica" />
<figcaption aria-hidden="true">Neurona biológica</figcaption>
</figure>

## Funcionamiento

Una red neuronal artificial puede tener entre un par de neuronas hasta
millones que se encuentran separadas en diferentes capas. En la figura
<a href="#fig:red_neuronal" data-reference-type="ref"
data-reference="fig:red_neuronal">1.3</a> se representa una red neuronal
de varias capas.

Cada capa está conectada con la anterior y con la siguiente. Las
neuronas también son conocidas como unidades y sus conexiones se
representan con un número llamado peso, el cuál puede ser positivo o
negativo, y su valor está relacionado con la influencia que tenga la
neurona previa. Cuanto mayor es el peso, más influencia tiene una
neurona sobre otra. Como hemos podido ver antes, esto es lo que hacen
las neuronas biológicas, que disparan impulsos a través de sus
conexiones.

<figure>
<img src="Figures/RN1.jpg" id="fig:red_neuronal"
alt="Estructura de una red neuronal " />
<figcaption aria-hidden="true">Estructura de una red neuronal
</figcaption>
</figure>

La figura <a href="#fig:neurona_artifical" data-reference-type="ref"
data-reference="fig:neurona_artifical">1.4</a> es una neurona con tres
entradas (*x*<sub>1</sub>,*x*<sub>2</sub>,*x*<sub>3</sub>), los pesos de
cada entrada (*w*<sub>1*j*</sub>,*w*<sub>2*j*</sub>,*w*<sub>3*j*</sub>),
el bias (*b*<sub>*j*</sub>), el cálculo final de entrada con los valores
anteriores (*z*<sub>*j*</sub>), la función de activación
(*f*(*z*<sub>*j*</sub>)) y el resultado de salida de la nuerona
(*y*<sub>*j*</sub>).

<figure>
<img src="Figures/RN4.jpg" id="fig:neurona_artifical"
alt="Neurona artificial y parámetros" />
<figcaption aria-hidden="true">Neurona artificial y
parámetros</figcaption>
</figure>

Así considerando su estructura podemos hablar de redes monocapa,
compuestas por una única capa de neuronas, o redes multicapa (figura
<a href="#fig:red_neuronal" data-reference-type="ref"
data-reference="fig:red_neuronal">1.3</a>), donde las neuronas se
organizan en diferentes capas. Normalmente, las neuronas de una misma
capa, se comportan de la misma manera.

Varios factores clave a la hora de determinar el comportamiento de una
neurona, son la función de activación y el patrón de ponderación de
conexiones con el resto de neuronas, pero esto lo trataremos un poco más
adelante. Por lo general, las neuronas de la misma capa, comparten ambas
cosas.

### Capas

En general las neuronas se suelen agrupar en unidades estructurales que
denominaremos capas. El conjunto de una o más capas constituye la red
neuronal. Se distinguen tres tipos de capas: de entrada, salida y
ocultas (figura <a href="#fig:capas_neurona" data-reference-type="ref"
data-reference="fig:capas_neurona">1.5</a>).

-   La **capa de entrada** está compuesta por neuronas que reciben datos
    o señales procedentes del entorno.

-   La **capa oculta** no tiene una conexión directa con el entorno, es
    decir, no se conecta directamente ni a órganos sensores ni a
    efectores. Este tipo de capa oculta proporciona grados de libertad a
    la red neuronal gracias a los cuales es capaz de representar
    determinadas características del entorno que trata de modelar.

-   La **capa de salida** se compone de neuronas que proporcionan la
    respuesta de la red neuronal.

<figure>
<img src="Figures/RN2.jpg" id="fig:capas_neurona"
alt="Capas de una red neuronal" />
<figcaption aria-hidden="true">Capas de una red neuronal</figcaption>
</figure>

Los patrones de información alimentan a la red a través de las entradas,
las cuales disparan valores en la capa oculta y estas llegan
eventualmente a las neuronas de salida. Esto es denominado red de
alimentación hacia adelante. No necesariamente una neuorana se activa
siempre. Esta activación depende de los valores de las entradas y de si
alcanza un valor umbral. Esto es algo similar a las neuronas humanas y
es la señal que se conoce como estímulo nervioso.

La disposición de las neuronas en capas y los patrones de conexión se
denomina arquitectura de red.

### Arquitectura de red

La **red monocapa** tiene una única capa de pesos de conexión. Las
neuronas reciben señales de entrada y generan la respuesta de la red.
Las unidades de entradas están directamente conectadas a las unidades de
salida.

La **red de Hopfield** es una red monocapa. Aunque también se puede
mostrar como una red bicapa, donde la primera capa es de sensores y la
segunda es la encarga de realizar el procesamiento. En la versión
bicapa, la manera de conectar las neuronas es mediante la unión de la
primeras con las de la segunda linealmente, es decircada neurona con su
respectiva.

La **red multicapa** es aquella con una o más capas ocultas entre las
unidades de entrada y salida. Normalmente hay una capa de pesos entre
dos capas adyacentes (entrada, oculta y salida). Las redes multicapa
pueden resolver problemas más complejos que las monocapa, pero el
entrenamiento es más complejo y conlleva una cantidad superior de
tiempo. En algunas ocasiones los entrenamientos más grandes pueden
llevar al éxito que una red de una capa no puede alcanzar porque su
entrenamiento sea incompleto.

La **red competitiva** se diferencia de otras redes neuronales porque
las neuronas compiten para representar los patrones, es decir, cuando
ejecutamos un patrón en una red competitiva, se activa únicamente la
neurona que representa mejor dicho patrón. Eso la diferencia del resto
de redes, donde las neuronas colaboran entre ellas para la
representación de los patrones. Las redes competitivas son usualmente
bicapas. La función de la primera capa es hacer de sensor y por ella
entran los patrones a la red. Por lo tanto, debe tener el mismo tamaño
que la longitud del patrón. La segunda capa tiene tantas neuronas como
categorías deseemos. Sin embargo, algunas redes competitivas, crean
neuronas dinámicamente, con el objetivo de ajustar el número de
categorías automáticamente.

### Forward Step. Función de activación

El funcionamiento básico de un neurona equivale a sumar la señal de
entrada ponderada y aplicar la **función de activación** que define la
salida. Esta salida determina si la neurona se va a activar o no.
Normalmente, se trabaja con el mismo tipo de función para todas las
neuronas de una capa, aunque no es obligatorio. En redes multicapa, la
función suele ser no lineal. Dentro de las diferentes funciones con las
que podemos trabajar, destacamos las siguientes:

La función **de paso binario** (figura
<a href="#fig:binario" data-reference-type="ref"
data-reference="fig:binario">1.6</a>) es utilizada por redes monocapa
para convertir una entrada de valor continuo, en una señal de salida
binaria (0 ó 1) o bipolar (1 ó -1).
$$f(x) = max(0,x) = \left\\{ \begin{array}{lcc}
	0 &   si  & x \< 0 \\\\
	1 &  si &  x \geq 0 \\\\
\end{array}
\right.$$

<figure>
<img src="Figures/RN_pasobinario.jpg" id="fig:binario"
alt="Función de paso binario" />
<figcaption aria-hidden="true">Función de paso binario</figcaption>
</figure>

La función **lineal** (figura
<a href="#fig:lineal" data-reference-type="ref"
data-reference="fig:lineal">1.7</a>) es la más básica de esta lista y
normalmente se utiliza en el nodo de salida, cuando el objetivo es
obtener un valor real. Su mayor inconveniente es que no puede manejar la
complejidad de los datos.
*f*(*x*) = *x*

<figure>
<img src="Figures/RN_lineal.jpg" id="fig:lineal" alt="Función lineal" />
<figcaption aria-hidden="true">Función lineal</figcaption>
</figure>

La función **sigmoide o logística** (figura
<a href="#fig:sigmoide" data-reference-type="ref"
data-reference="fig:sigmoide">1.8</a>) convierte los valores
introducidos a una escala (0,1), de modo que los valores más altos
tienden a 1 y los más bajos a 0. Es útil para cálculos probabilísticos,
aunque su optimización es más compleja porque no está centrada en cero.
$$f(x) = \dfrac{1}{1 + e^{-x}}$$

<figure>
<img src="Figures/RN_sigmoidal.jpg" id="fig:sigmoide"
alt="Función sigmoide" />
<figcaption aria-hidden="true">Función sigmoide</figcaption>
</figure>

La función **tangente hiperbólica** (figura
<a href="#fig:tangente" data-reference-type="ref"
data-reference="fig:tangente">1.9</a>) transforma los valores
introducidos a una escala (-1,1), de modo que los valores altos tienden
a 1 y los más bajos a -1. A diferencia que la función sigmoide, las
salidas pueden ser valores negativas, por lo que se entrena más
fácilmente, ya que se puede centrar a cero. Computacionalmente es pesada
y su convergencia es mucho más lenta.
$$f(x) = \dfrac{2}{1 + e^{-2x}} -1$$

<figure>
<img src="Figures/RN_tanh.jpg" id="fig:tangente"
alt="Función tangente hiperbólica" />
<figcaption aria-hidden="true">Función tangente hiperbólica</figcaption>
</figure>

La función **ReLU**(*Rectified Linear Unit*) (figura
<a href="#fig:ReLU" data-reference-type="ref"
data-reference="fig:ReLU">1.10</a>) anula los valores negativos y deja
los positivos tal y como entran. Es una función extremadamente rápida de
calcular y tiene gran efectividad frente a varios dominios de
aplicación. Además, ayuda a minorizar el problema de la saturación de
gradiente (véase <a href="#sssec:gradiente" data-reference-type="ref"
data-reference="sssec:gradiente">1.2.5.1</a>) cuando los valores de la
combinación lineal de entrada son mayores que cero. Esta función logra
que la propagación hacia atrás sea efectiva incluso en redes profundas.
Es importante tener en cuenta que algunas neuronas pueden llegar a
colapsar durante el entrenamiento, debido a su derivada para ciertos
valores.
$$f(x) = max(0,x) = \left\\{ \begin{array}{lcc}
	0 &   si  & x \< 0 \\\\
	x &  si &  x \geq 0 \\\\
\end{array}
\right.$$

<figure>
<img src="Figures/RN_relu.jpg" id="fig:ReLU" alt="Función ReLU" />
<figcaption aria-hidden="true">Función ReLU</figcaption>
</figure>

La función **Leaky ReLU** (figura
<a href="#fig:Leaky" data-reference-type="ref"
data-reference="fig:Leaky">1.11</a>) multiplica valores de entrada
negativos por un coeficiente rectificativo y deja los positivos tal y
como entran. Soluciona el problema de colapso de las neuronas que hemos
visto en la función ReLU.
$$f(x) = \left\\{ \begin{array}{lcc}
	0 &   si  & x \< 0 \\\\
	a\cdot x &  si &  x \geq 0 \\\\
\end{array}
\right.$$

<figure>
<img src="Figures/RN_leakyrelu.jpg" id="fig:Leaky"
alt="Función Leaky ReLU" />
<figcaption aria-hidden="true">Función Leaky ReLU</figcaption>
</figure>

La función **Softmax** (figura
<a href="#fig:Softmax" data-reference-type="ref"
data-reference="fig:Softmax">1.12</a>) no es realmente una función de
activación, ya que no recibe un único elemento como entrada. Se encarga
de calcular la exponencial de cada elemento y la divide entre la suma de
las exponenciales del vector. El resultado es un vector con las
probabilidades de cada elemento que suman en total 1. La función Softmax
debe usarse en aquellos casos donde las clases son excluyentes, en otro
caso, se recomiendo usar la función sigmoide.
$$f(x) = \dfrac{e^{x_j}}{\sum\_{k=1}^{K}e^{x_k}}$$

<figure>
<img src="Figures/RN_softmax.jpg" id="fig:Softmax"
alt="Función Softmax" />
<figcaption aria-hidden="true">Función Softmax</figcaption>
</figure>

El crecimiento de las capas utilizadas en las redes neuronales y sus
capacidades provoca el uso y la creación de nuevas arquitecturas,
modelos de neuronas y formas de optimización. En los próximos apartados,
exploraremos algunas de las estrategias para enfrentar estos desafíos,
así como nuevas arquitecturas y su aplicación a problemas más complejos.

### Entrenamiento

Durante muchos años, el perceptrón fue el algoritmo utilizado en todos
los estudios de redes neuronales, pero solamente era capaz de resolver
problemas lineales y era incapaz de resolver problemas más complejos.
Con la publicación del libro *Perceptrons* donde se mostraban sus
limitaciones, tuvo lugar un parón en la financiación y el estudio de la
inteligencia artificial. Más de 15 años después, se publicó el artículo
*Learning representations by back-propagating errors* sobre un algoritmo
que autoajustaba los parámetros de la red neuronal, conocido como
backpropagation.

Las redes neuronales aprenden a través de un elemento de
retroalimentación, igual que el ser humano usa la retroalimentación todo
el tiempo. Siempre que tratamos de aprender algo, lo hacemos tal y como
nos han dicho que es la manera correcta. Esto quiere decir que ajustamos
nuestra conducta a los conocimientos adquiridos. La retroalimentación en
una red neuronal es conocida como **propagación hacia atrás** y su
principal objetivo es el de comparar la salida de la red con el
resultado esperado. Para entrenar una red de esta manera, se necesita un
gran conjunto de ejemplos a partir de los cuáles la red pueda avanzar en
el aprendizaje. Todo este entrenamiento tiene que trabajar sobre datos
en binario, para que las neuronas hagan su trabajo y se aproximen lo
máximo posible al resultado esperado.

Las redes neuronales se clasifican según la disposición de las neuronas
en cada capa, los diferentes patrones para la conexión y los algoritmos
o métodos que se utilizan para entrenar y lograr el aprendizaje. Es
importante tener en cuenta que las redes neuronales no siempre se
entrenan, como en el caso de las redes de pesos fijos, que no utilizan
ningún tipo de entrenamiento. El método de ajustar los valores de los
**pesos** es otra característica distintiva y se utiliza tanto en el
aprendizaje supervisado y como en el no supervisado.

Los modelos de **aprendizaje supervisado** son aquellos en los que se
especifica el conjunto de datos con la relación de entrada y su salida
deseada, para llegar al objetivo del aprendizaje. Según el tipo de
salida, hay una subcategoría que diferencia entre **modelos de
clasificación** cuando la salida es un valor categórico (por ejemplo, un
conjunto finito de clases), y **modelos de regresión** cuando la salida
es un valor de un espacio continuo. Las redes neuronales de
entrenamiento supervisado son las más populares, el hecho de conocer la
salida beneficia al entrenamiento como si tuviera la supervisión de un
maestro. En estos casos, el peso de una neurona en la etapa (*m*+1) se
calcula con la siguiente fórmula:
*w*<sub>*i**j*</sub><sup>*m* + 1</sup> = *w*<sub>*i**j*</sub><sup>*m*</sup> +  ▵ *w*<sub>*i**j*</sub><sup>*m*</sup>

Por otro lado, los modelos de **aprendizaje no supervisado** no cuentan
con datos que definan qué información es satisfactoria o no, su objetivo
no es ajustar los pares de entrada y salida, sino trabajar en el aumento
del conocimiento estructurado de los datos disponibles, es decir,
clasificar los datos en grupos en función de sus atributos. Algunos
ejemplos son la Regla de Aprendizaje de Hebb y el aprendizaje
competitivo.

Los modelos de **peso fijo** se utilizan para tratar de resolver
problemas de optimización con restricciones. Los pesos son establecidos
para representar las restricciones y la cantidad a maximizar o
minimizar. Normalmente, una solución casi óptima es satisfactoria.
Ejemplos de este modelos son la máquina de Boltzmann (sin aprendizaje) y
la red de Hopfield.

### Función de pérdida

El propósito de entrenar un modelo es predecir un resultado lo más
cercano posible a la respuesta correcta, es decir, minimizar al máximo
el error. Este error se mide a partir de la función de pérdida y para
obtener sus mínimos, se necesita encontrar los valores óptimos del
gradiente.

Una función de pérdida *J*(*x*) mide el nivel de insatisfacción de las
predicciones de nuestro modelo respecto a la respuesta correcta. Existen
varias funciones de pérdida como el error cuadrático medio o la entropía
cruzada. La selección de uno de ellos depende de varios factores como el
algoritmo seleccionado o el nivel de confianza deseado, pero
principalmente depende del objetivo del modelo.

Una **función de pérdida** es la que evalúa la desviación entre las
predicciones realizadas por la red neuronal y los valores reales de las
observaciones utilizadas durante el aprendizaje. La eficiencia de la red
neuronal depende del resultado de esta función. El objetivo principal de
una red neuronal es reducir al mínimo la desviación entre ambos valores
y se consigue ajustando los pesos de las neuronas.

El **error de aprendizaje** se calcula obteniendo la diferencia entre el
valor real que hay que predecir y el valor retornado por la neurona
artificial. Este es el error que buscaremos minimizar durante los
aprendizajes.
*E**r**r**o**r* = *P**r**e**d**i**c**c**i**o**n* *r**e**a**l* − *P**r**e**d**i**c**c**i**o**n* *r**e**a**l**i**z**a**d**a*

El **error cuadrático medio** es una función de error global del
aprendizaje. Es decir, que esta función nos permitirá conocer de manera
global el porcentaje de error cometido por nuestra neurona.

Esto se conoce como optimización y es la base de los algoritmos usados
en redes neuronales. Al igual que con la función de pérdida, existen
varios métodos de optimización que impactan en el rendimiento de nuestro
modelo y el tiempo que toma entrenarlo.

#### Descenso de gradiente

El descenso de gradiente (figura
<a href="#fig:RN_gradiente2" data-reference-type="ref"
data-reference="fig:RN_gradiente2">1.13</a>) es un algoritmo que se
utiliza en las redes neuronales para modificar ciertos parámetros y
reducir el error, es decir, mejorar el rendimiento y por lo tanto,
lograr el aprendizaje. Para lograr el mayor aprendizaje, necesitamos
conocer los mínimos locales de la función de coste, es decir, aquellos
puntos donde el coste sea menor. Nos apoyaremos en la derivada, que será
igual a cero en esos puntos y nos ayuda a conocer la pendiente de la
función en cada punto. El descenso de gradiente es un algoritmo que
estima numéricamente dónde una función genera sus valores más bajos. Por
lo tanto, evalúa la pendiente en cada punto en busca de los mínimos
(figura <a href="#fig:RN_gradiente" data-reference-type="ref"
data-reference="fig:RN_gradiente">1.14</a>).

<figure>
<img src="Figures/RN_gradiente2.jpg" id="fig:RN_gradiente2"
alt="Descenso del gradiente" />
<figcaption aria-hidden="true">Descenso del gradiente</figcaption>
</figure>

El gradiente es la generalización vectorial de la derivada, es un vector
de tantas dimensiones como la función y cada dimensión contiene la
derivada parcial en dicha dimensión:
$$\nabla f = \left( \dfrac{\partial f}{\partial x_1},\dfrac{\partial f}{\partial x_2},...,\dfrac{\partial f}{\partial x_n} \right)$$

La fórmula para recalcular los parámetros tiene el siguiente formato:
*θ̂* = *θ* − *α*∇*J*(*θ*)
Donde *θ* es el valor anterior del parámetro *θ̂* el nuevo, *α* la tasa
de aprendizaje y ∇*J*(*θ*) el gradiente de la función de coste para el
parámetro *θ*.

<figure>
<img src="Figures/RN_gradiente.jpg" id="fig:RN_gradiente"
alt="Mínimo global y local" />
<figcaption aria-hidden="true">Mínimo global y local</figcaption>
</figure>

Es importante no utilizar una tasa de aprendizaje grande, porque
determina el tamaño del paso que hace el algoritmo por la función y
puede impedir que se encuentren los puntos mínimos. Una estrategia sería
si la función crece mucho, descender la tasa de aprendizaje mucho, y si
crece poco, descender la tasa un poco. En otras palabras, dar el paso en
forma proporcional al gradiente. El ratio de aprendizaje también se
conoce como parámetro de *Tunning*.

A pesar de que avancemos en dirección contraria al gradiente, no se
puede garantizar que lleguemos al punto más mínimo. En algunas ocasiones
llegaremos a mínimos locales. Estos son regiones que parecen mínimos por
la configuración alrededor a ellos, pero no son el mínimo global.

Cuando una red neuronal es profunda, el proceso de backpropagation puede
provocar que gradientes menores a uno se hagan cada vez más pequeños al
pasar por múltiples capas. Si el gradiente se vuelve demasiado pequeño,
puede redondearse a cero (colapso numérico). Este suceso se conoce como
**desvanecimiento de gradiente**. De manera similar, cuando tenemos
muchas capas y los gradientes son mayores que uno, puede comenzar a
crecer rápidamente ocasionando que el cálculo tenga un **overflow**,
conocido como explosión de gradiente. Estos problemas se agravan según
la forma de la derivada de la función de activación de cada una de las
neuronas en las capas ocultas (saturación de gradiente). Por estos
motivos, es fundamental la selección de la función de activación para
evitar problemas con el gradiente.

El concepto de parámetros, función de pérdida y optimización son los
principales componentes en muchos algoritmos usados en el aprendizaje
automático.

#### Parámetros de la red

Para la optimización de la red neuronal, se emplean diferentes métodos
de ajuste de parámetros de la red (pesos de las conexiones y sesgo de
las neuronas), a partir de unos valores o bien aleatorios, o bien
predefinido (inicialización de la red).

Al construir un sistema neuronal, se parte de un cierto modelo de
neurona y de una determinada arquitectura de red, estableciéndose los
pesos iniciales como nulos o aleatorios. En la optimización del
entrenamiento, se ajustan los **pesos**.

El **sesgo o bias** permite indicar cuándo debe reaccionar la neurona,
es decir, es un valor que controla qué tan predispuesta está la neurona
a devolver un 1 o un 0, independientemente de los pesos. Un sesgo alto
hace que la neurona necesite una entrada más alta para generar 1 de
salida, justo al contrario sucede con un sesgo bajo.

Ajustar el sesgo nos ayudará a mejorar el proceso de ajuste de datos y
por consecuencia, modelos más precisos. Adicionalmente, evitará el error
de sobreajuste o la falta de ajuste.

#### Optimización a partir del dataset

Entrenar al modelo con datos sesgados hacia una determinada dirección,
puede empeorar el desempeño, condenando los resultados obtenidos. Es la
diferencia entre la predicción esperada de nuestro modelo y los valores
verdaderos. Aunque al final nuestro objetivo es siempre construir
modelos que puedan predecir datos muy cercanos a los valores verdaderos,
no siempre es tan fácil porque algunos algoritmos son demasiado rígidos
para aprender señales complejas del conjunto de datos. Es necesario
tener esto en cuenta a la hora de preparar el dataset de entrenamiento.

### Pruebas

La información fluye a través de una red neuronal de dos maneras. Cuando
la red se entrena durante el proceso de aprendizaje, o bien, tras el
entrenamiento, cuando se opera con ella para obtener los resultados. Es
decir, una vez entrenado y optimizado el modelo, es el momento de probar
la red neuronal y comprobar los resultados que genera.

## Construir una red neuronal com Keras

Keras es una biblioteca de código abierto escrita en Python, que se basa
principalmente en el trabajo del desarrollador de Google François
Chollet. La primera versión se lanzó en marzo de 2015 con el objetivo de
acelerar la creación de redes neuronales. Keras no funciona como un
framework independiente, sino como una interfaz que permite acceder a
varios frameworks de aprendizaje automático y desarrollarlos de manera
mucho mas sencilla. Entre los frameworks compatibles con Keras, se
incluyen TensorFlow[1], Theano[2] o Microsoft Cognitive Toolkit[3]. Para
más información sobre Keras, véase . También puede acceder a la
documentación de Python en .

[1] <https://www.tensorflow.org/>

[2] <https://theano-pymc.readthedocs.io/en/latest/>

[3] <https://docs.microsoft.com/en-us/cognitive-toolkit/>

# Implementación práctica de una red neuronal

## Introducción

El objetivo inicial de este proyecto es el de construir una red neuronal
para ponerla a prueba y comprobar si es capaz de romper un algoritmo
criptográfico. A lo largo de esta sección vamos a tratar de implementar
dos redes neuronales con un diseño y una meta diferente. La red inicial
tiene el objetivo de romper el algoritmo de cifrado César y el destino
de la segunda es el de probar la inteligencia artificial contra la
criptografía de curvas elípticas que vimos en el capítulo
<a href="#chap:2" data-reference-type="ref"
data-reference="chap:2">[chap:2]</a>.

La necesidad de probar el funcionamiento de las redes neuronales contra
dos algoritmos diferentes de cifrado, se debe a la complejidad que
presenta la criptografía de curvas elípticas. Este nivel de dificultad
debería impedir a la red neuronal aprender hasta encontrar un patrón que
rompa este problema matemático. Ese es el motivo principal por el que en
primer lugar trabajaremos con el cifrado César. Gracias a su sencillez,
la red neuronal no debería encontrar dificultad para encontrar el patrón
y aprender, y por lo tanto, partiremos de una red neuronal inicial que
funcione, y podremos comparar los resultados de ambos casos.

Antes de empezar en profundidad con los casos prácticos, es importante
comentar que el propósito de este trabajo es el estudio de la aplicación
de redes neuronales a la criptografía, y no el desarrollo desde cero de
una red neuronal. Por esta razón, el desarrollo de código se va a apoyar
en una biblioteca de código abierto para redes neuronales, llamada Keras
. Esta biblioteca facilita la implementación de redes neuronales desde
una capa muy simple y sencilla, sin tener que programar las partes más
complejas y profundas del código.

Este desarrollo ha sido realizado en el entorno Colab de Google[1] y se
puede encontrar en mi GitHub personal .

## Red neuronal cifrado César

Esta sección trata sobre la implementación de la red neuronal para
tratar de romper el cifrado César. Tras una breve explicación de este
tipo de cifrado, mostraremos el análisis y diseño de la red y el código
utilizado. La idea es aumentar la complejidad de la red en el avance de
las pruebas, es decir, al comienzo la red es más básica y en las
siguientes pruebas aumentaremos el tamaño de las palabras para ver el
comportamiento y como responde la red en cada caso.

### Descripción

El cifrado César o cifrado por desplazamiento es un tipo de cifrado por
sustitución, en el que cada letra es reemplazada por la que se encuentra
un número fijo de posiciones más adelante en el alfabeto.

La figura <a href="#fig:ROT3" data-reference-type="ref"
data-reference="fig:ROT3">1.1</a> muestra el ROT3, que significa
remplazar la letra por la que se encuentra 3 posiciones delante.

<figure>
<img src="Figures/ROT3.jpg" id="fig:ROT3" alt="Tabla ROT3" />
<figcaption aria-hidden="true">Tabla ROT3</figcaption>
</figure>

El cifrado ROT3 o la rotación de 3 posiciones de la palabra *HOLA* sería
*KROD* (figura <a href="#fig:ROT3_ejemplo" data-reference-type="ref"
data-reference="fig:ROT3_ejemplo">1.2</a>).

<figure>
<img src="Figures/ROT3_ejemplo.jpg" id="fig:ROT3_ejemplo"
alt="Ejemplo en ROT3" />
<figcaption aria-hidden="true">Ejemplo en ROT3</figcaption>
</figure>

Las redes neuronales trabajan mejor directamente con valores numéricos y
para obtener mejores resultados, pasaremos las letras a números (figura
<a href="#fig:abecedario_num" data-reference-type="ref"
data-reference="fig:abecedario_num">1.3</a>).

<figure>
<img src="Figures/abecedario_num.jpg" id="fig:abecedario_num"
alt="Abecedario númerico" />
<figcaption aria-hidden="true">Abecedario númerico</figcaption>
</figure>

Los números ahora se pasan a formato bits, que es cómo trabajan las
redes neuronales, para ello usamos *One-hot* (figura
<a href="#fig:one-hot" data-reference-type="ref"
data-reference="fig:one-hot">1.4</a>), que consiste en una cadena de
bits del tamaño del número de elementos (en este caso 26 por el
abecedario) con un único bit a 1 para cada letra. Por ejemplo, para el
número 1, la cadena solamente activa el último bit y para el número 25,
el primero.

<figure>
<img src="Figures/one-hot.jpg" id="fig:one-hot"
alt="Codificación One-hot" />
<figcaption aria-hidden="true">Codificación One-hot</figcaption>
</figure>

El diseño de la red neuronal será como el de la figura
<a href="#fig:RN_diseño_Cesar" data-reference-type="ref"
data-reference="fig:RN_diseño_Cesar">1.5</a>. Una única letra en la
entrada y salida de la red, dividida en 26 neuronas debido a la
codificación *One-hot*.

<figure>
<img src="Figures/RN_diseño_Cesar.jpg" id="fig:RN_diseño_Cesar"
alt="Diseño para la red neuronal de cifrado César" />
<figcaption aria-hidden="true">Diseño para la red neuronal de cifrado
César</figcaption>
</figure>

Progresivamente vamos a aumentar la complejidad del cifrado.
Inicialmente, queremos ver como la red neuronal se comporta con cadenas
de tres caracteres. Más adelante, probaremos cadenas de mayor tamaño y
habrá que optimizar la red y ajustar los hiperparámetros en busca de un
mejor resultado.

### Implementación del código

Para facilitar la comprensión del trabajo y no cargar el contenido de
este capítulo, se ha incluido el código implementado para el desarrollo
del ejercicio en el apéndice
<a href="#RN_Cesar" data-reference-type="ref"
data-reference="RN_Cesar">[RN_Cesar]</a>. El código está desarrollado en
python y para su ejecución es necesario el uso de ficheros de texto
plano con extensión “.py” (o “.pyw”). Además, para su ejecución es
necesario el uso de un terminal, un editor IDLE o un entorno
interactivo.

### Resultados obtenidos

Una vez terminado el desarrollo de la red y comprobado su
funcionamiento, nos hemos ayudado de la función GridSearchCV[2] para
tratar de encontrar los mejores resultados para diferentes
hiperparámetros de entrada. Un ejemplo de las pruebas realizadas es
siguiente código.

batch_size = \[50, 100, 200, 500\] epochs = \[50, 60, 100, 150, 300\]
optimizer = \[’SGD’, ’RMSprop’, ’Adagrad’, ’Adadelta’, ’Adam’, ’Adamax’,
’Nadam’\] loss = \[’binary_crossentropy’,’categorical_crossentropy’\]
activation = \[’relu’,’sigmoid’,’softmax’\] unit1 = \[50, 80, 120, 200\]
unit2 = \[50, 80, 120, 200\]

Esta función evalúa y selecciona los valores que le proporcionamos en
una lista para cada hiperparámetro mencionado anteriormente y nos
muestra el rendimiento en cada caso, y de esta manera podemos realizar
el modelo con la mejor selección. El modelo modelo finalmente usado es
el siguiente:

def
crearModelo(loss=’poisson’,activation=’relu’,u1=120,u2=80,optimizer=’RMSprop’):
\# Definir modelo model = Sequential() \# Capas model.add(Dense(nn\[4\],
input_dim=(26\*word_size))) model.add(Dense(u1, activation))
model.add(Dense(u2, activation)) model.add(Dense(u1, activation))
model.add(Dense(nn\[4\], activation)) \# Compilar modelo
model.compile(loss=’binary_crossentropy’,
optimizer=optimizer,metrics=\[’accuracy’\]) return model

Durante las pruebas, se ha modificado también algunas características de
la red neuronal, como el tamaño de palabra en cifrado César, para tratar
de aumentar la complejidad, o el uso de ROT3 (visto en la figura
<a href="#fig:ROT3" data-reference-type="ref"
data-reference="fig:ROT3">1.1</a>). Las pruebas se han separado en
función de varios hiperparámetros, como la longitud de la cadena de
caracteres (3, 5 ó 10 letras) o la cantidad de combinaciones del dataset
de entrenamiento (5.000, 10.000 ó 50.000).

En primer lugar, la figura
<a href="#fig:RNCC_prueba1" data-reference-type="ref"
data-reference="fig:RNCC_prueba1">1.6</a> muestra los resultados de la
primera prueba con un entrenamiento de 5.000 combinaciones de entrada.
La que mejor resultados presenta es la red neuronal con 3 caracteres de
entrada/salida. Como es de esperar, al ser más pequeña, las
combinaciones posibles son muchas menos que la de 10 letras.

<figure>
<img src="Figures/Prueba1.jpg" id="fig:RNCC_prueba1"
alt="Pruebas con 5.000 combinaciones de entrada" />
<figcaption aria-hidden="true">Pruebas con 5.000 combinaciones de
entrada</figcaption>
</figure>

En segundo lugar, la figura
<a href="#fig:RNCC_prueba2" data-reference-type="ref"
data-reference="fig:RNCC_prueba2">1.7</a> contiene los resultados de las
prueba con tras el entrenamiento con 10.000 combinaciones de entrada. La
red de tamaño 3 sigue siendo la que mejor resultados presenta y mejora
los resultados de la prueba anterior, pero en los otros 2 casos, se han
empeorado los porcentajes de acierto, a pesar de aumentar el
entrenamiento con más datos de entrada.

<figure>
<img src="Figures/Prueba2.jpg" id="fig:RNCC_prueba2"
alt="Pruebas con 10.000 combinaciones de entrada" />
<figcaption aria-hidden="true">Pruebas con 10.000 combinaciones de
entrada</figcaption>
</figure>

Por último, en la figura
<a href="#fig:RNCC_prueba3" data-reference-type="ref"
data-reference="fig:RNCC_prueba3">1.8</a> muestra los resultados de la
prueba con un entrenamiento de 50.000 combinaciones de entrada. El
modelo de 3 letras prácticamente acierta todas las letras, pero es
cierto que el entrenamiento es completo a nivel de combinaciones.

<figure>
<img src="Figures/Prueba3.jpg" id="fig:RNCC_prueba3"
alt="Pruebas con 50.000 combinaciones de entrada" />
<figcaption aria-hidden="true">Pruebas con 50.000 combinaciones de
entrada</figcaption>
</figure>

En las figuras <a href="#fig:grafico_palabras" data-reference-type="ref"
data-reference="fig:grafico_palabras">1.9</a> y
<a href="#fig:grafico_letras" data-reference-type="ref"
data-reference="fig:grafico_letras">1.10</a>, se muestra como varía el
porcentaje de acierto de palabras y letras respectivamente, con el
aumento de las combinaciones del dataset de entrada.

<figure>
<img src="Figures/grafico_palabras.jpg" id="fig:grafico_palabras"
alt="Evolución del acierto de palabras" />
<figcaption aria-hidden="true">Evolución del acierto de
palabras</figcaption>
</figure>

<figure>
<img src="Figures/grafico_letras.jpg" id="fig:grafico_letras"
alt="Evolución del acierto de letras" />
<figcaption aria-hidden="true">Evolución del acierto de
letras</figcaption>
</figure>

Las cadenas de 3 caracteres tienen un porcentaje alto de acierto, tanto
de letras como de palabras completas. Es normal que esto suceda debido a
la baja complejidad, el número de combinaciones (17.576) y la alta
cantidad de muestras usadas para el entrenamiento. Además de esto, los
hiperparámetros usados para configurar la red, se han elegido en base a
pruebas sobre este caso, es decir, la función GridSearchCV trabajó
contra palabras de 3 caracteres.

Los resultados obtenidos para cadenas de 5 letras son bastante buenos,
casi al nivel del anterior caso. Al contrario sucede con palabras de 10
letras. En este caso, la red se rompe y el porcentaje de aciertos es
casi nulo. Seguramente se deba a la configuración de la red, que como
hemos mencionado no se había optimizado para este caso.

<figure>
<img src="Figures/precision_CC.jpg" id="fig:precision_CC"
alt="Precisión Red Neuronal Cifrado César" />
<figcaption aria-hidden="true">Precisión Red Neuronal Cifrado
César</figcaption>
</figure>

Las figuras <a href="#fig:precision_CC" data-reference-type="ref"
data-reference="fig:precision_CC">1.11</a> y
<a href="#fig:perdida_CC" data-reference-type="ref"
data-reference="fig:perdida_CC">1.12</a> muestran la precisión y pérdida
de nuestro modelo con cadenas de cinco caracteres y un dataset de diez
mil combinaciones. A partir del gráfico de precisión (figura
<a href="#fig:precision_CC" data-reference-type="ref"
data-reference="fig:precision_CC">1.11</a>) podemos ver que el modelo
tiene un rendimiento similar tanto en el entrenamiento como en la
validación, por lo tanto, el modelo no ha sobre-aprendido el conjunto de
datos utilizado. También en ambas gráficas podemos ver el ruido que
tiene el modelo, por un sobreajuste u overfitting, es decir, nuestro
modelo en algunos casos no es capaz de reconocer nuevos datos de
entrada. Esto puede ser debido al tamaño del dataset o al ajuste de
hiperparámetros realizado inicialmente.

<figure>
<img src="Figures/perdida_CC.jpg" id="fig:perdida_CC"
alt="Pérdida Red Neuronal Cifrado César" />
<figcaption aria-hidden="true">Pérdida Red Neuronal Cifrado
César</figcaption>
</figure>

A partir de este punto, se podría tratar de optimizar aún más nuestro
modelo, pero el objetivo principal de este trabajo no era optimizar la
red neuronal contra el cifrado César, sino el de probar el rendimiento
de un modelo contra la criptografía de curvas elípticas, que veremos en
la siguiente sección.

Otra visión de los resultados, es el mostrar un caso real de prueba.
Podemos ver la salida esperada de las cadenas generadas aleatoriamente y
la salida que devuelve la red neuronal. Se utiliza el carácter ’-’
cuando no se devuelve el correcto.

Otra prueba más visual ha sido la de introducir mi nombre en ROT3
(figura <a href="#fig:ROT3" data-reference-type="ref"
data-reference="fig:ROT3">1.1</a>) como se puede ver en la figura
<a href="#fig:prueba_cc_nombre" data-reference-type="ref"
data-reference="fig:prueba_cc_nombre">[fig:prueba_cc_nombre]</a>.

Lo más importante y el objetivo de este apartado era lograr un buen
porcentaje de acierto para nuestra red, para poder confirmar el uso
correcto de las herramientas usadas a lo largo de su desarrollo. Ahora
podemos afrontar el objetivo real del trabajo y tratar de analizar el
comportamiento de la red frente a la criptografía de curvas elípticas.

## Red neuronal curvas elípticas

Esta sección está dedicada a la implentación de una red neuronal que va
a poner a prueba la seguridad de la criptografía de curvas elípticas.
Para ello, al igual que en la sección de la red neuronal contra el
cifrado César (<a href="#sec:cifradocesar" data-reference-type="ref"
data-reference="sec:cifradocesar">1.2</a>), nos ayudaremos en el
desarrollo con la biblioteca Keras .

Antes de comenzar con la descripción de la red neuronal, la
implementación y los resultados, es importante señalar que la
complejidad que presenta este tipo la criptografía de curvas elípticas
es bastante alta, tal y como se puedo ver a lo largo del capítulo
<a href="#chap:2" data-reference-type="ref"
data-reference="chap:2">[chap:2]</a> donde se explica en profundidad su
propiedades y como trabajan los diferentes algoritmos de cifrado con las
curvas elípticas.

### Descripción

Nuestra red neuronal contra la criptografía de curvas elípticas va a
trabajar en concreto contra el criptosistema de cifrado/descifrado
ElGamal. Por recordar brevemente, este criptosistema es un algoritmo
matemático de criptografía asimétrica que se basa en el problema del
logaritmo discreto. El algoritmo trabaja con un par de claves, una
pública para el cifrado del mensaje y otra privada para el descifrado.
Para ver el funcionamiento del algoritmo en profundidad, se puede volver
al apartado donde se explica
(<a href="#sub:ElGamal" data-reference-type="ref"
data-reference="sub:ElGamal">[sub:ElGamal]</a>).

Como el propósito de esta prueba es el de analizar el comportamiento de
este algoritmo de cifrado en curvas elípticas, nuestro diseño se basa en
la propia idea del algoritmo y vamos a tratar que la red a partir la
clave pública del cifrado como entrada, trate de devolver la clave
privada que se usa para el descifrado.

Para la implementación de este diseño vamos a contar con la ayuda de una
librería pública de GitHub que genera los pares de claves públicas y
privadas que necesitamos para entrenar a la red neuronal.

Tanto en el caso de la libería pública, como en el de la implementación
de nuestra red neuronal, se trabaja sobre la curva Curve25519[3], que
está diseñada para su uso con el esquema de intercambio de clave
Diffie-Hellman (<a href="#sub:DH" data-reference-type="ref"
data-reference="sub:DH">[sub:DH]</a>). El criptosistema de ElGamal a su
vez se basa en el intercambio Diffie-Hellman, por lo que la curva es
perfectamente válida para nuestras pruebas.

En el siguiente código se puede ver la función de generar el par de
claves que usaremos como datos de entrada y salida para la red neuronal.
Para más información sobre el código de las funciones de generación de
las claves privadas y públicas ver el anexo
<a href="#gen_keypair_apendix" data-reference-type="ref"
data-reference="gen_keypair_apendix">[gen_keypair_apendix]</a> o en el
repositorio de GitHub .

def gen_keypair(curve: Curve, randfunc: Callable = None) -\> Tuple\[int,
Point\]: randfunc = randfunc or urandom private_key =
gen_private_key(curve, randfunc) public_key =
get_public_key(private_key, curve) return private_key, public_key

Una las complicaciones encontradas para que la implementación de este
diseño es la conversión del par de claves para que la red neuronal no
tenga problema a la hora de trabajar con los valores de entrada. Es
necesario recordar que las redes neuronales artificiales tienen un mejor
rendimiento al trabajar directamente con bits, pero la entrada para este
diseño es la clave pública que es un punto de coordenadas (*X*,*Y*). La
decisión tomada (ver figura
<a href="#fig:RN_curvas_elipticas" data-reference-type="ref"
data-reference="fig:RN_curvas_elipticas">1.13</a>) consta de formar un
número con la concatenación de los valores *X*, *Y* de las coordenadas
en binario. También es necesario tener en cuenta que en algunas
ocasiones el tamaño de las coordenadas varía, por lo que en estos casos
se rellena con ceros por la izquierda hasta obtener el total de dos
números de 256 bits. Por consiguiente, la entrada de la red neuronal en
este caso tendrá de 512 neuronas. En el caso de la salida, la clave
privada es un número entero y estará formado por una salida de 256
neuronas en formato binario.

<figure>
<img src="Figures/RN_curvas_elipticas.jpg" id="fig:RN_curvas_elipticas"
alt="Diseño para la red neuronal de curvas elípticas" />
<figcaption aria-hidden="true">Diseño para la red neuronal de curvas
elípticas</figcaption>
</figure>

### Implementación del código

Para facilitar la comprensión del trabajo y no cargar el contenido de
este capítulo, se ha incluido el código utilizado para el desarrollo del
ejercicio en el apéndice
<a href="#RN_curvaeliptica" data-reference-type="ref"
data-reference="RN_curvaeliptica">[RN_curvaeliptica]</a>. El código está
desarrollado en python y para su ejecución es necesario el uso de
ficheros de texto plano con extensión “.py” (o “.pyw”). Además, para su
ejecución es necesario el uso de un terminal, un editor IDLE o un
entorno interactivo.

### Resultados obtenidos

Antes de comenzar a exponer los resultados obtenidos al poner a prueba
el modelo de la red neuronal contra la criptografía de curvas elípticas,
es necesario recordar que la complejidad que presenta este tipo de
criptografía es significativamente superior a la del cifrado César del
apartado anterior. Esta complejidad es el principal condicionante a la
hora de analizar el aprendizaje de esta red neuronal.

Durante la búsqueda del mejor diseño y la configuración de los
hiperparámetros de la red neuronal, al igual que en el apartado
anterior, se ha utilizado la función GridSearchCV[4].

Tras la elección de los hiperparámetros, se ha entrenado el modelo y se
ha testeado con los resultados de precisión y pérdida que se muestran en
las figuras <a href="#fig:precision_CE" data-reference-type="ref"
data-reference="fig:precision_CE">1.14</a> y
<a href="#fig:perdida_CE" data-reference-type="ref"
data-reference="fig:perdida_CE">1.15</a>, respectivamente. La curva de
aprendizaje en el caso de la precisión (fig.
<a href="#fig:precision_CE" data-reference-type="ref"
data-reference="fig:precision_CE">1.14</a>), no consigue aumentar, por
lo que nuestro modelo no está siendo capaz de distinguir el ruido y
encontrar un patrón que logra el resultado deseado. También podemos ver
que en el caso de la pérdida (fig.
<a href="#fig:perdida_CE" data-reference-type="ref"
data-reference="fig:perdida_CE">1.15</a>), la curva de entrenamiento, ha
empezado a aumentar tras el ciclo 100 y está aumentando el error, al
contrario de lo que debería hacer un modelo que esté aprendiendo
correctamente. Para obtener más información sobre las curvas de
aprendizaje y la mejora del modelo, se recomienda la lectura del libro
*Learning curve models and applications: Literature review and research
directions*

<figure>
<img src="Figures/precision_CE.jpg" id="fig:precision_CE"
alt="Precisión Red Neuronal ECC" />
<figcaption aria-hidden="true">Precisión Red Neuronal ECC</figcaption>
</figure>

Como hemos mencionado anteriormente, la complejidad a la que nos
enfrentamos en este problema es el principal punto a tener en cuenta.
¿Existe función con potencia y base para resolver el Problema del
Logaritmo Discreto? Una solución posible es la fuerza bruta, pero se
trata de una solución demasiado lenta. Una explicación más a fondo
podemos encontrar en el apartado dedicado al Problema del Logartimo
Discreto<a href="#sssec:pld" data-reference-type="ref"
data-reference="sssec:pld">[sssec:pld]</a>, donde ya mencionamos la
complejidad que supone el cálculo de la inversa es muy sencilla en
términos computacionales en comparación con el cálculo del logaritmo
discreto para ciertos grupos y en esta caso concreto, en trabajando con
curvas elípticas. El problema no tiene solución en un tiempo razonable
utilizando aritmética modular, pero en nuestro caso, la idea de probar a
resolver este problema a través de las redes neuronales, era
precisamente por la velocidad y el rendimiento que nos proporciona esta
tecnología, aunque tampoco hemos logrado los resultados deseados.

<figure>
<img src="Figures/perdida_CE.jpg" id="fig:perdida_CE"
alt="Pérdida Red Neuronal ECC" />
<figcaption aria-hidden="true">Pérdida Red Neuronal ECC</figcaption>
</figure>

Como era de esperar, nuestra red no ha sido capaz de romper el cifrado y
devolver la clave privada esperada, y mucho menos, de encontrar patrones
para lograr el aprendizaje. Después de numerosas pruebas y ajuste de los
hiperparámetros, la precisión se mantenía cercana a cero.

La optimización de la red no ha sido posible, a pesar de usar diferentes
niveles de capas o modificar los valores de los hiperparámetros. Tampoco
ha servido la ayuda de la función GridSearchCV. Uno de los motivos que
nos lleva al fracaso del aprendizaje de nuestro modelo puede ser el uso
de keras. Esta biblioteca nos ha facilitado el desarrollo y la
implementación de la red neuronal, pero también limita las pruebas y las
modificaciones de código a niveles más bajos, ya que lo trabajamos muy
superficialmente. Podría ser interesante en un futuro o en otro trabajo
continuar por este camino y desarrollar el modelo sin la ayuda de keras,
pero el tiempo limitado impide hacerlo en este proyecto.

[1] <https://colab.research.google.com>

[2] <https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html>

[3] <a href=" https://hmong.es/wiki/Curve25519/" class="uri">
https://hmong.es/wiki/Curve25519/</a>

[4] <https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html>

# Impacto social, ambiental, ético y legal

Este trabajo se ha realizado con el objetivo de poner a prueba el
rendimiento de diferentes tecnologías, pero sin lograr unos resultados
que puedan tener interés social más allá del propio ámbito educativo. La
posibilidad de encontrar alguna vulnerabilidad en la seguridad de la
criptografía de curvas elípticas era mínima, por lo que el desarrollo de
este trabajo no suponía ningún problema a nivel social. El avance de las
tecnologías es evidente y la seguridad de la información nunca estará
completamente garantizada. De esta manera, el uso de mejores
herramientas para mejorar la seguridad, implica claramente múltiples
beneficios para la sociedad.

Por la naturaleza de este proyecto, no tiene ninguna implicación
ambiental, ya que únicamente se trataba de analizar el comportamiento de
las redes neuronales y la criptografía de curvas elípticas. Aunque uno
de los puntos comentados a lo largo de los apartados, ha sido la mejora
que supone el uso de la criptografía de curvas elípticas frente a la
criptografía tradicional. Este punto puede tener un enfoque ambiental,
ya que esta mejora de rendimiento, puede implicar una mejora ambiental.

A nivel ético y legal, el trabajo estaba enfocado en poner a prueba
tecnologías que se usan ya en nuestra sociedad, pero sin salir del
terreno legal y con el objetivo de ayudar siempre a mejorar la sociedad.

# Trabajo futuro

A lo largo de este proyecto hemos trabajado sobre dos ramas, las
criptografía de curvas elípticas y las redes neuronales. Se podría
seguir ampliando conocimiento en el futuro en ambas direcciones, por
ello, se proponen las siguientes ideas o expansiones:

-   **Cambiar los datos de entrada y salida de la red:** En este
    trabajo, hemos trabajo a través de la clave privada como datos de
    entrada y la clave pública como salida. Otra opción viable podría
    ser repetir el modelo utilizado para la red neuronal contra el
    cifrado César <a href="#sec:cifradocesar" data-reference-type="ref"
    data-reference="sec:cifradocesar">[sec:cifradocesar]</a>, es decir,
    usar palabras cifradas como entrada y descifradas como salida para
    las pruebas con criptografía de curvas elípticas
    <a href="#sec:red_ce" data-reference-type="ref"
    data-reference="sec:red_ce">[sec:red_ce]</a>.

-   **Probar contra otros algoritmos criptográficos:** Nuestra red
    neuronal contra la criptografía curvas elípticas se basa en el
    criptosistema de ElGamal
    (<a href="#sub:ElGamal" data-reference-type="ref"
    data-reference="sub:ElGamal">[sub:ElGamal]</a>). En el futuro, se
    podría implementar la red contra otros algoritmos como
    Diffie-Hellman o DSA.

-   **Crear nuestro propio código de la red neuronal:** La red neuronal
    ha sido implementada gracias a la biblioteca de código abierto
    Keras. Su uso es sencillo y modular, de forma que es muy amigable
    para los usuarios. Podría ser interesante profundizar en la
    implementación del código para obtener mejor rendimiento.

-   **Estudiar otros tipos de ataques contra curvas elípticas**:
    Comprobar la seguridad de la criptografía de curvas elípticas frente
    a otros tipos de ataques, como por ejemplo, ataques mediante
    computación cuántica[1] y compararlo con los resultados de las redes
    neuronales.

[1] <https://www.welivesecurity.com/la-es/2016/06/14/computacion-cuantica-armagedon-criptografico/>

# Conclusiones

A modo de cierre de este trabajo, podemos señalar que se ha tratado de
aprender los fundamentos matemáticos (capítulo
<a href="#chap:1" data-reference-type="ref"
data-reference="chap:1">[chap:1]</a>) necesarios para una correcta
comprensión de la criptografía de curvas elípticas (capítulo
<a href="#chap:2" data-reference-type="ref"
data-reference="chap:2">[chap:2]</a>) y el funcionamiento de una red
neuronal artificial (capítulo
<a href="#chap:3" data-reference-type="ref"
data-reference="chap:3">[chap:3]</a>). Tras una parte teórica, la parte
práctica de este trabajo ha tratado de comprobar la seguridad que
presentan dos diferentes sistemas de cifrado frente al aprendizaje
automático de una red neuronal (capítulo
<a href="#chap:4" data-reference-type="ref"
data-reference="chap:4">[chap:4]</a>). En primer lugar, la red neuronal
ha sido capaz de aprender a resolver el cifrado César de una manera
sencilla. Esto se debe a lo sencillo que es este algoritmo de cifrado y
a la poca complejidad que presenta. En segundo lugar, la alta
complejidad que presenta la criptografía de curvas elípticas ha
dificultado el trabajo de la red neuronal, que no ha conseguido romper
su seguridad.

La potencia de nuestro equipo y lo sencilla que era nuestra red
neuronal, han sido otros factores que frente a la alta complejidad de
este tipo de criptografía, han dado como resultado un sistema no
vulnerable a nuestro estudio.

A pesar de estos resultados, desde el inicio del trabajo se conocía la
dificultad de conseguir resultados positivos, por lo que el objetivo del
trabajo era corroborar esta idea.

</div>
