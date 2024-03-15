# UTXO

Hasta ahora hemos visto qué compone una transacción al nivel más bajo posible. Si has leído todo el post anterior, con todas las referencias que tenía y has entendido todo lo siguiente será fácil. Si aún sientes nauseas y mareos es normal, no te preocupes, era muy denso profundizar en todo.

En bitcoin existe una figura, el UTXO, que significa unespent transaction output; seguramente al leer el nombre ya entiendas de que va esto. En el fondo, cada transacción de bitcoin genera outputs que pueden ser consumidos como inputs más adelante; el utxo es simplemente aquellos outputs que no se consumen.

El utxo tiene dos implicaciones fundamentales, permite validar las transacciones y calcular el balance de la cartera.

## Validando una transacción

Cuando un nodo recibe una transacción, lo primero que tiene que comprobar es si los inputs que se quieren gastar no están ya gastados (¿lógico no?).

## Balance de una cartera

Hay que pensar que los bitcoins no están en las carteras, es más correcto pensar en ello como que determinados lotes de bitcoin, están bloqueados por una dirección. De esta forma, todos aquellos "lotes" que estén bloqueados por la misma dirección componen su balance. En este caso son los utxo de una misma cartera, es decir, bloqueados por la misma dirección.

## Bitcoin Core

La consulta sobre balances sería muy lenta si ha de hacerse a través de toda la cadena, de ahí que el core de bitcoin almacene estos datos en una especie de RAM en `~/.bitcoin/chainstate`

## Cambio

Cuando sobra cantidad de una transacción, el típico ejemplo de querer enviar 6btc, pero se tienen dos outputs de 5btc y 2btc. En este caso, el destinatario tendrá un utxo de 6bct como output, bloqueado bajo su clave; y al emisor le retornará 1btc como utxo cerrado bajo su clave. En muchos casos, este retorno se da a una nueva dirección, denominada dirección de cambio. Pero igualmente pertenece al mismo emisor. Lo veremos con más calma más adelante.

**Todas las direcciones de una cartera con sus claves privadas se generan de una misma seed o semilla.**

[SIGUIENTE](/data/bitcoin_05.md)