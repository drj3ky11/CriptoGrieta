# Transacción

## Advertencia previa
En este apartado, se bajará a un nivel bastante técnico sobre el como funcionan las transacciones en la cadena. Previo a ello, el lector no experimentado tendrá que ir leyendo otras entradas que se van a ir referenciando a lo largo del artículo. Si la lectura del contenido de este curso es más bien generalista, quizás la lectura de este artículo pueda saltarse para ir directamente a ejemplos prácticos y a la parte de investigación.

Hemos considerado adecuado comenzar por las transacciones, porque en parte es la base. Más adelante se cubrirán los nodos, carteras y otros elementos relevantes. Pero por ahora, estos conceptos se tomarán de forma generalista, para cubrir la teoría explicada.

## ¿Qué es una transacción?

Una transacción de bitcoin es solo un conjunto de datos que desbloquea y bloquea lotes de bitcoins.
Para ser más precisos, una transacción selecciona lotes existentes de bitcoins (inputs) y los desbloquea (o descifra); a continuación crea nuevos lotes de bitcoins (outputs) y los bloquea (cifra) de una nueva forma (por ejemplo con la clave pública del destinatario).

El cifrado de un output contiene la clave pública, esto quiere decir que es necesaria la clave privada asociada a esa pública para descifrar y para firmar.

Una transacción puede agrupar múltiples inputs y generar múltiples outpus. Además, una transacción al ser parte de una cadena, implica que los inputs de una operación serán los outputs de otra operación futura.

Atendiendo a las palabras del creador de Bitcoin:

> Una moneda digital contiene la clave pública de su propietario. Para transferirla, el propietario firma la moneda junto con la clave pública del siguiente propietario. Cualquiera puede comprobar las firmas para verificar el cambio de titularidad.

## Estructura

Veamos un ejemplo de una transacción, tomemos el hash ` b460aefaca8026569b9d432fa20d6fca82514489479c25ce79b52593b5d76633`
Los datos de la transacción, son conjunto de números tal que así:

```
02000000000102078259717fe999ad3c7005d6b1a30c7b59897f78f6e2fe29b8
ad92279cfb5c860000000000fdffffff90e7b7f15bf9befa81ce468ef2c15894
7b65ec69a22859b683e2d10f785cd4a70000000000fdffffff02f82401000000
00001600140738c93dd800e9c492d43eed777fd68b7fd92371a0860100000000
0017a9140796cc225d45ae0b497972994cc0a163cb9a764d8702473044022011
b2440e1d26fd72b243d0f4f1d768e2808ac46eea7a610dc50f7767ca15ba0902
2030f683e07dcf6b2252beca755b0fa6e9b476e012ae4f96bb59ffc63a2e1d0c
a001210376a2954a0c1eb9d47763dfeae74eafd065ed9fa6aab3534c8d91104b
3bd4c57302473044022041a92bc25071e99ed8d25f0e1930c5ec89e858029786
7194a617dd6af37d6e50022064803d49d585a2258fbbe4fc3afc4409674d7833
fbb33b3f183ac379550118b7012103ab7df281310b558f0095acb94ce642fbd3
cf1dfb46c36661bed11024b983d3382d8e0a00
```
Para continuar con esta aproximación a las transacciones, sería bueno tener claro que son los [bit y bytes](https://es.wikipedia.org/wiki/Unidades_de_informaci%C3%B3n) algo de [hexadecimal](https://es.wikipedia.org/wiki/Sistema_hexadecimal) y un poco de (¿por qué no?) [little-endian o big-endian](https://es.wikipedia.org/wiki/Endianness)

Y una forma un poco más amigable de ver la cadena anterior es esta:

```json
{
  "version": "02000000",
  "marker": "00",
  "flag": "01",
  "inputcount": "02",
  "inputs": [
    {
      "txid": "078259717fe999ad3c7005d6b1a30c7b59897f78f6e2fe29b8ad92279cfb5c86",
      "vout": "00000000",
      "scriptsigsize": "00",
      "scriptsig": "",
      "sequence": "fdffffff"
    },
    {
      "txid": "90e7b7f15bf9befa81ce468ef2c158947b65ec69a22859b683e2d10f785cd4a7",
      "vout": "00000000",
      "scriptsigsize": "00",
      "scriptsig": "",
      "sequence": "fdffffff"
    }
  ],
  "outputcount": "02",
  "outputs": [
    {
      "amount": "f824010000000000",
      "scriptpubkeysize": "16",
      "scriptpubkey": "00140738c93dd800e9c492d43eed777fd68b7fd92371"
    },
    {
      "amount": "a086010000000000",
      "scriptpubkeysize": "17",
      "scriptpubkey": "a9140796cc225d45ae0b497972994cc0a163cb9a764d87"
    }
  ],
  "witness": [
    {
      "stackitems": "02",
      "0": {
        "size": "47",
        "item": "3044022011b2440e1d26fd72b243d0f4f1d768e2808ac46eea7a610dc50f7767ca15ba09022030f683e07dcf6b2252beca755b0fa6e9b476e012ae4f96bb59ffc63a2e1d0ca001"
      },
      "1": {
        "size": "21",
        "item": "0376a2954a0c1eb9d47763dfeae74eafd065ed9fa6aab3534c8d91104b3bd4c573"
      }
    },
    {
      "stackitems": "02",
      "0": {
        "size": "47",
        "item": "3044022041a92bc25071e99ed8d25f0e1930c5ec89e8580297867194a617dd6af37d6e50022064803d49d585a2258fbbe4fc3afc4409674d7833fbb33b3f183ac379550118b701"
      },
      "1": {
        "size": "21",
        "item": "03ab7df281310b558f0095acb94ce642fbd3cf1dfb46c36661bed11024b983d338"
      }
    }
  ],
  "locktime": "2d8e0a00"
}
```

