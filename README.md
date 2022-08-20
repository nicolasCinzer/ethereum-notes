# Ethereum Notes

Un readme que me va a acompañar en aprendizaje sobre Ethereum.

## Que es Ethereum?

Es una plataforma para ejecutar `Smart Contracts` a traves de una maquina virtual llamada `EVM` (`Ethereum Virtual Machine`) que aplica los cambios en el sistema.

Ethereum a diferencia de Bitcoin, es una maquina virtual all porpouse.

- `Open Blockchain`, es decir, es abierta a todos, publica, neutral, descentralizadas, global e inmutable.

- Utiliza una criptomoneda `Ether - ETH` para gestionar los costos de transacción dentro del ecosistema


## Componentes Principales

Componentes Principales:

    Red P2P: Esta red hace referencia a un mecanismo de transferencia de igual a igual o persona a persona, sobre la cual no existe ningún ente central y de lo contrario se maneja la información de manera descentralizada y segura.

    Algoritmo de consenso(Nakamoto): Ethereum al igual que bitcoin poseen un mecanismo de consenso basado en una prueba de trabajo o proof of work(PoW), presentada en sus inicios por Satoshi Nakamoto el creador de bitcoin. De esta manera Satoshi logro pactar un acuerdo o un consenso entre los nodos, para decidir cual nodo es el encargado de generar un nuevo bloque y actualizar la blockchain, ya que no existe un ente central.

    Ether: Es la moneda propia de Ethereum, esta corre sobre la primera capa de la blockchain de Ethereum haciendola su moneda principal. El verdadero objetivo de esta moneda es servir como herramienta para poder construir la red de aplicaciones descentralizadas que corren dentro de Ethereum.

    Nota: Ether no es lo mismo que Ethereum, Ether es la moneda, y Ethereum es la red.

    Ethereum Virtual Machine: La maquina virtual de Ethereum es la principal encargada de leer y ejecutar la logica de los contratos inteligentes o Smart Contracts escritos en el lenguaje Solidity, para que la red blockchain pueda incluir e interpretar esta lógica. Cada uno de los nodos en su interior poseen esta maquina virtual.

    Algoritmo criptográfico de seguridad (Ethash): Es el algoritmo encargado de cifrar la información manejada en la blockchain de Ethereum. Los mineros utilizan este algoritmo para poder crear nuevos bloques.

    Clientes (Geth, Parity): Estos clientes son paquetes que instalas en tu computador para poder correr un nodo dentro de este y poder conectarte a la red blockchain de Ethereum

Conceptos relevantes:

    Clientes/Nodos: Los clientes son los encargados de empaquetar el sistema sobre el cual se puede ejecutar un nodo en la red BlockChain. Cuando instalas en tu computador este cliente, automáticamente te conviertes en un nodo participante en la red de Ethereum.

    Wallets: Las wallets o billeteras son aplicaciones que nos permiten administrar nuestras cuentas de Ethereum o de cualquier otra red, para poder interactuar con otras personas que también sean parte de esta red. Además de poder controlar nuestros fondos y activos.

    Smart Contracts: Son los programas que nos permiten comunicarnos con la blockchain a partir de ciertas condiciones especificadas dentro de el contrato inteligente. Estos contratos se ejecutan dentro de la EVM para ser analizados y posteriormente implementados en la blockchain.

    Web3: Es una nueva web descentralizada sobre la cual no necesariamente va a existir un ente central, si no que de lo contrario, al ser una red descentralizada o P2P vamos a hacer nosotros mismos los usuarios los encargados tomar decisiones autónomas sin necesidad de recurrir o de pedir información a un ente central.
## ETH y GAS

### Una nota importante es que el gas NO es ether.

Esta concepción tradicional nos lleva a creer que, por ejemplo, si $ETH tiene un precio mayor, entonces los costos de la red también. Sin embargo, son dos conceptos que NO están directamente vinculados.
.
Entonces, ¿cómo funciona?

El gas es sólo eso: gas, y se mide en unidades de gas. Sin embargo, se paga en $ETH.
.
Piensa en esto como si tú fueras en automóvil de tu casa a tu trabajo. La cantidad de trabajo no cambia porque la ruta es la misma sin importar la cantidad de veces que la recorras. Es decir el mismo recorrido siempre consume la misma gasolina, pero, ¿qué pasa si la gasolina escasea? El precio por unidad de gas sube. En el contexto de Ethereum, lo que escasea es el blockspace, es decir, hay una cantidad finita de gas que puede aceptar un bloque (sumando el gas de todas las transacciones de dicho bloque)
.
¿Qué son las unidades de gas?

Las unidades de gas son una representación de esfuerzo computacional.
.
Cuando compilamos código de Solidity a ejecutable de la EVM, el listado de códigos de operación implicará un coste en gas que está definido por una tabla de operadores:
.
https://github.com/crytic/evm-opcodes
.
Es decir, de la misma forma que tu automóvil. Una llamada a una función de un contrato inteligente va a costar siempre la misma cantidad de gas. Lo que cambia es lo demandado que está ese gas en ese momento. Por ejemplo:
.
Si tenemos una transacción que ejecuta a la función claim en un contrato, y la función cuesta 50,000 unidades de gas, y el mercado está saturado, por lo que está pagando 200 Gwei por unidad de gas, entonces tu costo total es de:
```
Costo en Gas = 55000 gas units
Precio por unidad de gas = 200 GWEI (200000000000)
Costo en ETH = 200 GWEI * 55000 gas units = 1.1*10^16 = 0.01 Ethers
```
Sin embargo, sin en la misma transacción, la red no está congestionada, y el gasPrice anda alrededor de 50 GWEI por unidad de gas, entonces:
```
Costo en Gas = 55000 gas units
Precio por unidad de gas = 50 GWEI (50000000000)
Costo en ETH = 50 GWEI * 55000 gas units = 2.75*10^15 = 0.00275 Ethers
```
¿Cómo se calcula el costo?

    El costo de una transacción en unidades de gas está dado de la siguiente forma:

    Gas Cost =  21,000 + Suma de Gas por OPCODE

    Es decir, siempre se pagan 21,000 unidades de gas de base m’as la operación que realices, y al final, el gasPrice (precio por unidad de gas), lo decides tú en base a las condiciones del mercado

Ejemplo que demuestra la NO correlación entre el precio de Ether y el gas

    Esta es una transacción durante DeFi summer 2020, con un precio. degas en 248 GWEI (congestionadísimo), y Ether a $429.
    https://etherscan.io/tx/0x480e02b8941e3ab014df7b8006458da1a6a5322cb73582b58725ae9bf28c811f
    Precio en USD al día de la transacción es de $2.23
    .
    Esta es una transacción en 2021 con Ether a $2323 pero con la red mucho más descongestionada a 8 GWEI por unidad de gas:
    https://etherscan.io/tx/0xa832a8c495a9be14b26a9f9c8cf5510d3f6aa005fef8c4f477d0452d768528c0
    Precio en USD al día de la transacción es de $0.39
    .
    Ambas transacciones consumieron 21,000 unidades de gas, bajo distinta demanda.
