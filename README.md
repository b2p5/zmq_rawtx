
# Ejemplo de utilización la biblioteca ZeroMQ con rawtx 

1. **Crear un contexto zmq**: El programa comienza creando un nuevo contexto ZeroMQ. Este contexto se utiliza para crear sockets ZeroMQ.

2. **Crear un socket de tipo SUB**: El programa crea un socket SUB utilizando el contexto ZeroMQ. Si hay un error al crear el socket, el programa imprime el error y lo devuelve.

3. **Conectar al nodo Bitcoin**: El socket SUB se conecta a un nodo de Bitcoin que se ejecuta en localhost en el puerto 28332. Si hay un error al conectar, el programa imprime el error y lo devuelve. 
En el archivo ***bitcoin.conf*** se ha de incluir el comando: 
zmqpubrawtx=tcp://127.0.0.1:28332

4. **Suscribirse a eventos relacionados con la mempool**: El socket SUB se suscribe a los eventos "hashblock", que representan las notificionrs sobre todas las transacciones.

5. **Recibir y procesar mensajes**: El programa entra en un bucle donde recibe y procesa continuamente mensajes. El primer mensaje que recibe es el canal de suscripción, que descarta. El segundo mensaje que recibe es el hash del bloque de 32 bytes, la cual se pasa a string. La tercera parte es un numero de secuencia. Si hay un error al recibir cualquiera de los mensajes, el programa imprime el error y continúa con la siguiente iteración del bucle o devuelve el error.

6. **Pausa**: El programa hace una pausa de 2 segundos para evitar el consumo excesivo de recursos.



*Resultado del script:*

Tx: "010000000152e2938421cc63263eab6813776fc393bd3aae08e41905d07fbbc3df1237a8e9050000006b483045022100c4ef977ad6aba2e3b2584ca732118408c5ca206fd63d9edf029b93ea206834f702200ec422ac4eb4cf69cae476820fe228cbe23a0653f7c3ec2889fad13690c2f9cf0121025b357ffef2343cf3e9f694932f84e036f35796a6fcb1d718ea54f6c35ae01c80ffffffff02bed10b0000000000160014909c2d212efdfa86557e8ee3938485510b64f64427eced0200000000160014740e4c9126112dc07979639c6c888c8f5a52e77f00000000"

Topic: "rawtx"

Sequence number: 94d40200 -> "��\u{2}\0"


