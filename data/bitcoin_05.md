# Nodos y mineros

Hemos comentado desde el inicio, que bitcoin se compone de una red de nodos. Es el momento de ver en qué consisten los nodos.

Básicamente, un nodo es cualquier ordenador que envía, recibe o procesa datos conectado a la red de bitcoin; esto es, que ejecuta algún código que le permite tal conexión, generalmente [BitcoinCore](https://bitcoin.org/es/descargar),

Las dos tareas principales del nodo es tener un copia de la blockchain y validar y distribuir las nuevas transacciones y bloques. 

Correr un nodo permite además de proporcionar mayor privacidad y confianza, explotar los datos de la blockchain directamente con `bitcoin-cli`

![addressinfo](/images/bitocoincore1.png)

Para obtener información de otras carteras, hay que editar el .con y poner txindex=1 y luego, ejecutando el cliente desde línea de comandos, hacerlo con la opción -reindex

## Mineros
Son aquellos que toman transacciones de la pool de memoria y las insertan en la blockchain. Un nodo no tiene porqué minar, ni un minero tiene que correr un full nodo.

Minar es una especie de competición. Primero se selecciona un bloque candidato, con sus transacciones, de la memoria; acto seguido se crea la cabecera del [bloque](/data/bloque.md). Luego se toma la cabecera y se calcula el hash SHA256 dos veces, y se espera que el resultado sea menor que el objetivo que está marcado.

El target u objetivo, se ajusta cada 2016 bloques, que son más o menos dos semanas. Se trata de un ajuste dinámico, de forma que si se generan muchos bloques por hora, se incrementa la dificultad. Esto, compensa por ejemplo, los momentos en los que hay muchos mineros y el bloque podría bajar mucho de los 10 minutos. De la misma forma, si hubiese pocos, la dificultad se bajaría par que el bloque no exceda de los 10 minutos.

No es necesario ahondar mucho más en el proceso de minado, salvo que te interese por motivos particulares. Los mineros reciben recompensa por su trabajo en forma de bitcoin, mediante las transacciones [coinbase](/data/coinbasetx.md)

[SIGUIENTE](/data/bloque.md)
