Video Overview del Proyecto:

https://www.youtube.com/watch?v=A_VGgLGJwRw

__________________________________________________________________________________

Descripción del Proyecto:

Desarrollar una interfaz de usuario en realidad virtual que permita al usuario visualizar y gestionar un inventario limitado, 
en este caso utilizando el Meta All-in-One SDK y el Meta XR Interaction SDK.

Dada la limitación de tiempo, decidí enfocarme en desarrollar una solución básica pero funcional (aunque mejorable) en el menor tiempo posible
mostrando mi conocimiento en diseño VR controlando rotaciones escala y velocidades en la interacion con los diferentes objetos,
por lo que opté por diseñar una experiencia que simula un pequeño juego de feria en lugar de utilizar una pistola de manera convencional desde la mano del jugador.
__________________________________________________________________________________

Características Básicas:

Utilizando el URP(dado que es un proyecto en VR ahorraremos en recursos) crear el escenario con los objetos y las interfaces indicados en el documento.

Al señalar con el rayo y hacer clic con el grip(el lateral del mando) sobre cualquiera de estos objetos, el objeto seleccionado se acerca al controlador (equivalente a la mano)y el código detecta el tag del objeto con el que choca el collider. 
Si el objeto tiene uno de los siguientes tags: LifePot, Pistol o Ammo, se debe eliminar y usar su tag como string para sobreescribir el TMP del primer slot disponible en inventario.

__________________________________________________________________________________

Inventario y Funcionalidad:



Se creó un campo en el Inspector para arrastrar el objeto (Unity Canvas) que contiene el ScrollView, 
el cual alberga los diferentes slots.
Al hacer clic sobre un objeto, este se añadirá a un slot si hay disponibilidad.

Los objetos en el inventario pueden realizar las interacciones: "Usar" y "Borrar".
__________________________________________________________________________________

Botón de borrar.

Al hacer clic en el botón de eliminar:
El objeto será removido del slot y ahora se sobreescribe ese string antes mencionado por "basura", indicando que está vacío e indisponible para un nuevo objeto.
__________________________________________________________________________________

Botón de Usar.

La funcionalidad del botón de "Usar" dependerá del tag del objeto en el slot correspondiente:
__________________________________________________________________________________

LifePot (Poción de Vida):

Al usar este objeto, se comprobará la escala del objeto referenciado en el Inspector.
Si su escala es menor a 1.1, se aumentará su escala en el eje X en 0.25 unidades con un límite de 1.
__________________________________________________________________________________

Pistol (Pistola):

Al usar el arma, se alternara la activación del mesh render referenciado en el Inspector, esto "usa" la pistola, que no disparara hasta que utilicemos el ammo para recargarla.

Se debe verificar si el arma tiene munición a través de una variable booleana expuesta en el editor llamada loaded.

Si loaded es true, se comprobará la escala de un objeto (barra de vida) referenciado en el Inspector. Si su escala en el eje X es mayor que 0.2 y menor que 1.1(para evitar problemas de redondeo), su escala decrecerá en 0.25 unidades.

Si la escala llega a 0, no se debe decrecer más, incluso si el arma sigue siendo usada.


Después de utilizar el arma, la variable loaded debe cambiar a false automáticamente.
__________________________________________________________________________________

Ammo (Munición):

Al usar la munición, se recargará el arma, y la variable loaded volverá a ser true.

__________________________________________________________________________________


Este planteamiento quizás no sea el mejor o no es la estructura más clara, si se esperaba otro tipo de solucion al problema
me gustaria recibir feedback para poder tenerlo en cuenta en el futuro y seguir mejorando.

__________________________________________________________________________________
¡Gracias por vuestro tiempo! 



