# Transacción

## Advertencia previa
En este apartado, se bajará a un nivel bastante técnico sobre el como funcionan las transacciones en la cadena. Previo a ello, el lector no experimentado tendrá que ir leyendo otras entradas que se van a ir referenciando a lo largo del artículo. Si la lectura del contenido de este curso es más bien generalista, quizás la lectura de este artículo pueda saltarse para ir directamente a ejemplos prácticos y a la parte de investigación.

Hemos considerado adecuado comenzar por las transacciones, porque en parte es la base. Más adelante se cubrirán los nodos, carteras y otros elementos relevantes. Pero por ahora, estos conceptos se tomarán de forma generalista, para cubrir la teoría explicada.

## ¿Qué es una transacción?

Una transacción de bitcoin es solo un conjunto de datos que desbloquea y bloquea lotes de bitcoins.
Para ser más precisos, una transacción selecciona lotes existentes de bitcoins (inputs) y los desbloquea (o descifra); a continuación crea nuevos lotes de bitcoins (outputs) y los bloquea (cifra) de una nueva forma (por ejemplo con la clave pública del destinatario)

Una transacción puede agrupar múltiples inputs y generar múltiples outpus. Además, una transacción al ser parte de una cadena, implica que los inputs de una operación serán los outputs de otra operación futura.

Atendiendo a las palabras del creador de Bitcoin:

> Una moneda digital contiene la clave pública de su propietario. Para transferirla, el propietario firma la moneda junto con la clave pública del siguiente propietario. Cualquiera puede comprobar las firmas para verificar el cambio de titularidad.

## Estructura

