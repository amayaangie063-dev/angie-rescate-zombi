# 🧟 ANGIE: RESCATE ZOMBI

Un juego 3D hecho con **Three.js** sobre Angie, que debe atravesar un mundo devastado por zombis para rescatar a su pareja **Juan** y a sus gatos **Donna** (blanca con manchas naranjas y negras) y **Zanahorio** (naranja con rayas).
- **Modelo 3D de Angie**: Modelo **Michelle.glb** (Mixamo) cargado vía **GLTFLoader**, con su propio cuerpo, ropa y pelo esculpidos y texturizados (nada de esferas ni cilindros "pegados" encima), esqueleto completo de 65 huesos y **MeshToonMaterial** (cel-shading anime) aplicado sobre su textura original. El esqueleto procedural del juego se sincroniza hueso a hueso con el GLB cada frame (incluye golpes, patadas, disparo y las poses del modo foto), y el arma cuelga naturalmente de la mano. El golpe cuerpo a cuerpo tiene una curva de aceleración con impulso real y deja una **estela blanca (swoosh)** en el arma. Si Michelle.glb no llega a cargar, el juego recurre a **Xbot.glb** como respaldo, con busto/nalgas/pelo/ropa procedurales y una **cara anime propia** (ojos grandes con brillo, parpadeo periódico, rubor y boquita) añadidos encima. Los zombis y Juan siguen estilo bloques Minecraft para contrastar. **Ajustes recientes**: la piel de Angie es **blanca** (los tonos morenos de la textura difusa de Michelle se recolorean en tiempo real, preservando sombreado y sin tocar el uniforme); los **brazos ya no van rígidos** (los codos se flexionan naturalmente al caminar, correr y relajarse); el **arma se agarra con la mano** real del modelo (antes quedaba a la altura del codo); la **patada** ya no levanta el pie como si pateara un balón, ahora es una patada de empuje tipo front-kick (carga la rodilla al pecho, extiende la pierna empujando de frente a la altura de la cintura y se retrae, con el impacto a los zombis sincronizado con el pie, mayor alcance de 4.2 u y un empuje más fuerte que sale disparado: los caminantes vuelan 3 u, los corredores 3,6 u y la abominación apenas se mueve 1,2 u); y al **correr** el torso se inclina hacia delante, el talón golpea el trasero al final de cada zancada y los brazos bombean de forma más humana. **Pulso de naturalidad**: la zancada ya no va atada al reloj — la **fase de marcha avanza con la distancia recorrida** (los pies se "plantan" en el suelo al acelerar y frenar, sin foot-skating) y hay un **blend suave reposo ⇄ caminar ⇄ correr** (la amplitud, la frecuencia, el rebote y los brazos se mezclan progresivamente con la velocidad suavizada en vez de saltar de golpe); el **salto tiene peso** (mantener Espacio salta alto, soltarlo corta el impulso para saltos cortos, hay coyote time y buffer de salto, y al caer las rodillas y el torso ceden con una flexión de impacto); el **cuerpo lidera los giros** (el torso adelanta la curva, la cabeza contra-rota para mantener la mirada y la pelvis se inclina con banking al girar rápido); **agacharse es de verdad** (la pelvis baja y las rodillas, los muslos y el torso se flexionan — copiados hueso a hueso al GLB — en vez de aplastar el modelo con scale.y); Angie **reacciona al daño con un flinch** breve (torso y cabeza atrás, brazos al pecho); los **pasos suenan en el apoyo real del pie** (cada π radianes de zancada = un paso, sincronizado con el ciclo de piernas, no con un temporizador); la **física de senos/nalgas/pelo/falda usa el dt real del frame** (independiente del framerate); el **arma tiene micro-sway** al caminar y respirar; y en **reposo el pecho respira** (expansión sutil que también se propaga al GLB). Los **zombis** también recibieron el mismo pulso: la zancada ya no es rígida (las rodillas se doblan al levantar el pie, los corredores golpean el talón, hay contoneo de cadera y rebote, y los brazos extendidos tienen una ligera flexión de codo con vaivén más vivo, conservando la joroba de cada tipo); y su **ataque** ya no es un mordisco de relleno: al acercarse preparan el **zarpazo al frente** (echan el brazo atrás y se detienen a atacar, luego lanzan el brazo extendido de un tirón con una embestida corta que conecta el daño al terminar la preparación, y vuelven a su vaivén normal).*
- **📸 Modo foto** (tecla **P** en el juego): el mundo se congela y Angie posa en **7 poses** (Q/E: de pie sensual, de perfil con pecho fuera, de rodillas con brazos al cielo, arqueada con manos al pecho, de puntillas con brazos arriba, de espaldas mirando atrás y **🦵 patada de empuje**, que repite en cámara lenta la patada con una pausa en el impacto y coloca un zombi delante para ver cómo conecta el pie; todas con respiración y balanceo), con **cámara orbital** (←→ o arrastra el ratón, ↑↓ altura), **6 filtros de color** ([ ]: normal, cálido sepia, blanco y negro, rosa romántico, violeta neón y noche azul), visor con esquinas de encuadre, flash y sonido de obturador. El arma se oculta en las fotos y el HUD se restaura al salir (P o Esc).*

> **El problema:** cada vez que Angie encuentra a Juan, los gatos se asustan y se escapan... y Juan sale corriendo detrás de ellos. Angie tiene que cruzar un mundo entero de zombis para alcanzarlos de nuevo.

## 🎬 Intro y tutorial

- Al pulsar **JUGAR** se reproduce una **cinemática de introducción** (título, recorrido por las ruinas y narración) creada con el motor de fotogramas clave **HyperFrames**. Puedes saltarla con el botón **SALTAR INTRO**.
- La primera vez que juegues, el **tutorial interactivo** del nivel 1 te enseña los controles paso a paso (moverse, girar, esprintar, saltar, atacar, patada y recoger). Puedes repetirlo desde el menú con el botón **🎓 TUTORIAL**.

## ▶️ Cómo jugar

Abre **`index.html`** en tu navegador (Chrome, Edge o Firefox). Eso es todo.

- El juego funciona **sin internet**: Three.js ya viene incluido en `three.min.js`.
- Si prefieres un servidor local: `python -m http.server` o cualquier servidor estático.

## 🎮 Controles

| Tecla | Acción |
|---|---|
| `W` / `↑` | Correr hacia adelante |
| `A` / `←` `D` / `→` | Girar a izquierda / derecha |
| `Shift` | Esprintar (gasta resistencia) |
| `Enter` / `Clic` | **Atacar** (golpe) o **disparar** con la pistola |
| `1` `2` `3` `4` | Cambiar de arma (bate / machete / pala / pistola) |
| `E` | Recargar la pistola |
| `Ctrl` | **Agacharse** (modo sigilo: te detectan mucho menos) |
| `Espacio` | Saltar |
| `F` | Patada de emergencia (empuja y aturde zombis) |
| `G` | Lanzar **ovillo de lana** que distrae zombis (mejora de tienda) |
| `M` | Silenciar / activar sonido |
| `Esc` | Pausa (con inventario de armas y mejoras) |
| `R` | Reiniciar nivel |

## ⚔️ Combate

- **4 armas**: Bate (equilibrado), Machete (rápido), Pala (lento pero demoledor) y **Pistola** (a distancia, con cargador de 12 balas y munición limitada).
- Las **cajas de armas** aparecen en cada nivel; también puedes encontrar machetes, palas y pistolas. Las **cajas de munición** recargan tus reservas de balas.
- Los zombis tienen **vida**: golpéalos hasta que caigan... y sueltan **botín** 🪙 (monedas, botiquines y cafés).
- **🧟 Zombis realistas y aterradores**: ropa rota (jirones colgando del dobladillo, mangas y pantalones rasgados mostrando piel), heridas abiertas con carne viva y hueso al aire, sangre seca y fresca por todo el cuerpo, cicatrices y sangre bajo los ojos, mandíbula torcida con dientes, y **ojos rojos que brillan y pulsan en la oscuridad** (halo de luz aditivo). Cada zombi deja un **charco de sangre** en el suelo del que se levantó; la **Abominación** muestra costillas al aire y el **Corredor** va empapado en sangre. Los charcos se limpian al morir o cambiar de nivel.*
- Las abominaciones son tanques: sueltan doble botín.
- **Jefe final (nivel 5)**: *El Devorador*, un mega-zombi con barra de vida en pantalla que lanza piedras, entra en furia al 50% de vida y debe caer antes de llegar a casa. Cuando se enfurece, Juan acelera su cocina: pica más rápido, lanza sushi cada ~4 s con muchos más especiales y grita *"¡No le hagas daño a mi Angie!"* (+1000 pts y botín).
- **🍣 Cocina de sushi de Juan (nivel 5)**: Juan monta su puesto en el refugio y te lanza sushi por el aire con un globo de diálogo y frases aleatorias (*"¡Ahí va, Angie!"*, *"¡Del chef con cariño!"*, *"¡Fuerza, Angie!"*…). El nigiri te cura (+25 vida), el **SUSHI ESPECIAL dorado** da +50% de daño 12 s, y el **MOCHI de postre** 🍡 da +150 puntos. A veces lanza sushi a Donna y Zanahorio: comen, ronronean y te devuelven vida y puntos.
- **🍽️ Misión secundaria (nivel 5)**: atrapa **5 sushis de Juan** antes de llegar a la meta y desbloquearás el **final alternativo del banquete de sushi familiar**, con diálogos propios, título especial (*¡BANQUETE DE SUSHI FAMILIAR!*), cita nueva y una fila ✅ en las estadísticas finales. Un contador 🍣 en el HUD (arriba, verde) muestra tu progreso 0/5, con aviso de progreso en el toast de cada sushi atrapado (*Misión 1/5, 2/5…*) y una animación de rebote en el contador al avanzar (el de mochis también). **Segunda misión**: atrapa **3 mochis de postre** 🍡 (contador rosa bajo el primero) para que Donna y Zanahorio tengan su postre en el banquete. **Al recoger el 3er mochi despierta el jefe sorpresa del postre**: el **🍡 Mochi Gigante** (400 de vida, barra rosa en pantalla), un mochi gigante con fresa que salta hacia ti y aplasta al aterrizar, escupe bolas de mochi y rebota al ser golpeado. Derrótalo (+500 pts y botín) para *asegurar el postre*: Juan añade la escena extra con los mochis de fresa de los gatos y las filas *Mochis para los gatos 3/3 ✅* y *Mochi Gigante: ¡Derrotado!* en las estadísticas.
- **🍽️ Mesa del banquete (3D en la cutscene final)**: cuando desbloqueas el final alternativo, aparece una mesa completa en la escena — tablero de madera con mantel a rayas, 9 platos con todos los sushis de Juan (nigiris, makis dorados y mochis), tazón de arroz, tazas de té, palillos y platitos rosas con mochi para los gatos. Angie y Juan se sientan a la mesa (con sillas), Donna y Zanahorio se sientan en sus platitos con las patitas dobladas, y la cámara hace un recorrido alrededor mientras la familia come y los gatos mueven la cola.
- **🏅 Medalla de misiones (HUD)**: al completar las DOS misiones (5 sushis + derrotar al Mochi Gigante), aparece una medalla 🏅 dorada junto al contador que brilla y pulsa durante todo el nivel, con el aviso *"🏅 ¡MEDALLA DE MISIONES COMPLETAS! ¡El banquete perfecto te espera!"* (solo una vez).

## 🛒 Tienda de los Gatitos

Gasta tus puntos para comprar regalitos para Donna y Zanahorio... que te devuelven con amor (y ventajas):

| Regalo | Efecto | Precio |
|---|---|---|
| 🐟 Lata de atún de Donna | +20 de vida máxima | 250 |
| 🪶 Pluma de Zanahorio | +30 de resistencia máxima | 350 |
| 👟 Zapatillas Pata Veloz | Esprintar gasta 25% menos | 400 |
| 🧶 Ovillo de lana mágico | Pulsa G para distraer zombis | 450 |
| 📻 Radio de Juan | Alerta visual de zombis cercanos | 500 |
| 🧴 Champú antipulgas | Los zombis se mueven 15% más lento | 600 |

Accede a la tienda desde el **menú principal** o desde la pantalla de **nivel superado**.

## 🗺️ Los 5 niveles (dificultad creciente)

1. **Las Ruinas del Barrio** (día) — Caminantes lentos te enseñan lo básico.
2. **El Parque Abandonado** (atardecer) — Aparecen los primeros corredores.
3. **El Bosque Siniestro** (noche) 🌙 — Niebla densa y oscura, **linterna de Angie** (cono de luz con sombras dramáticas), cielo estrellado, grillos, corredores y abominaciones. **Los zombis solo se ven cuando la linterna los alcanza** (~30 m): fuera del cono desaparecen en la negrura, y solo sus ojos rojos brillantes delatan que algo acecha. **La linterna gasta batería 🔋**: se drena ~1.6 %/s, parpadea y tiembla por debajo del 25 % y se apaga del todo al llegar a 0 — busca las **10 pilas** repartidas por el bosque para recargarla al 100 %. El HUD muestra la barra de batería (verde → amarilla → roja parpadeante) solo en este nivel. **El bosque susurra 🌲**: sonidos ambientales de pasos arrastrados, crujidos de ramas, susurros y un búho lejano que **se intensifican según la cercanía de los zombis** — tranquilos con el bosque vacío (un sonido cada 4-9 s) y frenéticos con la horda encima (cada 0.5-1.4 s, con susurros y pasos apresurados). **Cuando un zombi se acerca (< 14 m) la linterna empieza a parpadear y el cono de luz se agita** — cada vez más rápido y con apagones espasmódicos cuanto más cerca está, hasta el límite del pánico.*
4. **La Autopista del Caos** (amanecer) — Coches chocados, pilares y mucha horda.
5. **El Centro Devastado** (mediodía) — La horda completa te espera... y **El Devorador**, el jefe final, bloquea el camino a casa.

## ⚙️ Mecánicas

- **Vida y resistencia**: evita los mordiscos; esprintar gasta energía.
- **Sigilo**: agáchate para pasar de largo a los zombis; esprintar te delata más.
- **Botiquines** ❤️, **cafés** ☕, **monedas** 🪙 y **cajas de munición** 🔫.
- **Fotos** 📸 de Donna y Zanahorio escondidas en cada nivel (5-7 por nivel, +1000 pts cada una): la puerta del refugio solo se abre cuando las reúnes todas.
- **Zombis**: caminantes, corredores, abominaciones (mucho daño) y zombis tumbados que se levantan al acercarte.
- **Progreso guardado**: niveles desbloqueados, mejoras de tienda y armas (localStorage).
- **🏆 Logros** (botón en el menú): completa hazañas y desbloquéalas para siempre (se guardan en localStorage). Incluye *Misión del banquete* (5 sushis), *Sin un rasguño* (derrota a El Devorador sin recibir daño de él) y *Atrapada al vuelo* (atrapar un sushi en pleno vuelo).
- **Mini-mapa** en pantalla: tu posición, la meta, los zombis, el jefe final y las cajas de armas.
- **Pausa con inventario**: consulta y equipa tus armas, y revisa las mejoras compradas en la tienda.
- **Sonido 100% sintetizado** (WebAudio): gruñidos, golpes, maullidos, pasos, ambiente y música.
- **Cutscenes con diálogos** en español y final feliz: *¡Familia reunida!*
- **🎬 Cinemáticas de juego real**: *vuelo de entrada* con HyperFrames al empezar cada nivel (la cámara sobrevuela el escenario mientras se muestra la tarjeta del nivel), *cinemática de derrota* (Angie cae en cámara lenta con destello rojo y fundido a negro antes de la pantalla de derrota), *confeti* 🎊 en la pantalla final y **créditos finales animados** en español (botón 🎬 VER CRÉDITOS) con los nombres de Angie, Juan, Donna y Zanahorio, las mecánicas, Three.js y *"¡Gracias por jugar!"*.
- **💬 Subtítulos elegantes en las cutscenes**: tipografía grande (21 px) con serifa Georgia, panel dorado cinematográfico y nombre del personaje destacado. Botón **SUBTÍTULOS** en el menú para apagarlos/encenderlos (se guarda en localStorage): al apagarlos, el texto se oculta y solo queda un indicador ▶ para continuar, en diálogos y narraciones.
- **🕹️ Pantalla de "última vez" estilo consola**: al cargar el juego aparece una pantalla retro de arranque (texto verde monoespaciado, scanlines y cursor parpadeante) con las líneas de sistema OK, tu **nivel alcanzado** (X/5, con *¡COMPLETADO!* si lo terminaste), **puntuación récord** y **tiempo jugado**. Se guarda cada sesión en localStorage y se cierra con cualquier tecla o clic.
- **🎊 Confeti y gatos en los créditos**: el confeti de celebración también cae durante los créditos finales, y dos gatos de créditos (🐈 y 🐱) cruzan la parte inferior de la pantalla caminando con un pequeño rebote mientras rueda el texto — Donna y Zanahorio despiden al jugador.

## 📁 Archivos

- `index.html` — todo el juego (HTML, CSS, UI y código Three.js)
- `three.min.js` — motor Three.js r128 (local, sin internet)
- `GLTFLoader.js` — cargador de modelos GLB (local, sin internet)
- `michelle.glb` — modelo 3D de Angie (Mixamo)
- `michelle_b64.js` — copia de `michelle.glb` embebida en base64: Chrome/Edge bloquean la descarga de `.glb` cuando abres `index.html` con doble clic (protocolo `file://`), así que este archivo garantiza que Angie siempre se vea como Michelle aunque no uses servidor local.
- `xbot.glb` — respaldo (maniquí) si Michelle no carga
- `README.md` — este archivo

## 💡 Notas

- Hecho con Three.js r128, sin dependencias externas ni assets descargados.
- Escritorio y teclado recomendado (el ataque usa el ratón).
- Guarda tu progreso con `localStorage` — si limpias el navegador, empiezas de nuevo.

¡Buena suerte, Angie! Donna y Zanahorio dependen de ti. 🐱🐱
