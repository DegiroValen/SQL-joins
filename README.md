# SQL-joins

 ##Introduccion

 Vamos a mostrar un poco de como se usan joins y un par de comandos basicos
El contexto es que tome 5 datasets de https://ourworldindata.org/ los cuales dan datos de un topcio de muchos paises, busco unificarlo en una tabla mediante el join


 ### Art 1. ¿Que es el cross join y es necesario usarlo en estos casos?
 El cross join no es mas que el producto cartesiano, donde los elementos son cada registro.
 El producto cartesiano de dos conjuntos son todas las combinaciones posibles de sus elementos. Por ejemplo: El producto cartesiano de {1,2} con {3,4} es {(1,3),(1,4),(2,3),(2,4)}
 Claramente en este caso no es necesario usarlo. Esto pues cada registro(registro son las filas de una tabla) contiene un año y pais a los cuales se asocia su respectivo dato, y el producto cartesiano asignaria ese dato a todos los pares

### Art 2. ¿Que es el inner join y es necesario usarlo?
El inner join es un cross join pero con condiciones que son necesarias para que se ejecute el producto cartesiano
En este caso lo uso para unir las dos tablas que considere mas importante, densidad de la poblacion con natalidad. Notese que esta condicion soluciona el problema dicho antes, ya que ahora el dato se asigna solo a su año y pais
Tambien surge la duda de porque elimine los que no tenian datos en ambos, y no permiti que se quede los datos presentes solo en uno y colocar null en donde falta(como veremos mas adelante). Mi respuesta es que es una mera cuestion practica, dado que eran los datasets mas importanes, y que el conjunto de densidad de poblacion tenia fechas no mu utiles, considere esta opcion mas conveniente

### Art 3. ¿Que es el left y right join y es necesario usarlos?
El left join funciona igual que el inner join, pero los registros de la izquierda que no se hayan emparejado con nadie entonces lo hacen con un registro de nulls
Esto lo uso para todo el resto de emparejamientos, ya que algunos(donde mas se nota es el registro de fumadores) tienen pocos elementos y entonces se perderia mucha informacion

El right join es similar, la difrencia es que el registro siempre presente es el de la derecha. No lo uso porque solo dificultaria la lectura

### Art 4. ¿Que es el full outer join y es necesario usarlo?
El full outer join es la union de los registros del right join y left join
Si bien es es plausible en principio, los registros extras serian datos muy aisaldos, que dificultarian mas de lo que aportan

