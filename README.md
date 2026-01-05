# IA Avanzada FSM
### Cambios en el proyecto

- He descargado various paquetes desde Unity Store; un monstruo con animaciones, unas texturas de pared y suelo, un PlayerController en Primera Persona. Modifiqué el controller de las animaciones para encajar con el proyecto.
- He añadido un plano y he creado unas paredes con cubos. A las paredes y suelo les puse unas texturas. Al suelo le puse el componente **NavMesh Surface** con el **Agent Type** a "Humanoid" e hice un **Bake**. Tanto el suelo como las paredes tienen colliders.
- Añadí unos checkpoints para que el monstruo pueda seguirlos. Pusé cubos por el escenario y luego les quité el mesh. Puse el Tag a "checkpoint". 
- Al monster le asigné el "AI" script y pusé la capsula del **FirstPersonController** como el **Player** del script. También le asigné un **NavMesh Agent** con el **Agent Type** a "Humanoid", dejé casí todos los parámetros por defecto.
- Le añadí un **AudioSource** al monstruo con un sonido de rugido.
- Modifiqué el script de "State.cs", incluyendo otro estado "ROAR" (rugir), en el enum y luego creando la clase "Roar" al final del archivo, herredando de la clase "State".
- En la clase "Roar" puse una referencia al AudioSource, un timer del rugido y su duración.
- He creado los métodos construct, Enter, Update, y Exit. En el construct añadí "agent.isStopped" para que dejara de seguir "navegando" por el navmesh mientras hace el rugido y muestra la animación.
- En el método "Enter" activé la animación y el sonido del rugido, en el "Update" compruebo el tiempo pasado y cuanto tiene que durar, y en el "Exit" reseteo el trigger de la animación y cambio "agent.isStopped" a false para que pueda seguir moviendose por el escenario.
- El estado "Roar" se activa en las clases "Patrol" y "Idle" si el monstruo ve al jugador, luego en el "Roar" cuando haya acabado la animación y sonido, transiciona a "Pursue". Patrol/Idle -> Roar -> Pursue -> Attack 

[Vínculo al repositorio en Github](https://github.com/jnomada/IAFiniteStateMachines)