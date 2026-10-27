# Changelog

[English](#english) | [Español](#español)

---

## English

### 0.5.2 (includes 0.4.0, 0.5.0 and 0.5.1, which were not released on their own)
- **Repository renamed to Huriz-Sim-Car-Oversteer** (the LMU is gone from the name). Old links keep working, and versions
  already installed still find updates there.
- **Lighter overlay**: the Dash Studio overlay image is only drawn and saved when it changes (car stopped, in the pits or
  in the menus it does nothing), so it uses less CPU and stops creating and deleting files all the time.
- **Clean diagnostics every session**: `diagnostico.txt`, `errores.log` and the effect search logs start empty every time
  SimHub starts, so they never fill up over several days and always show the current session.
- **Active Pedals note**: the Simucube ActivePedal card now says the pedal needs some pressure to feel the vibration
  (at rest it sits on its end stop and nothing moves).
- **New-version window**: when there is a newer release, a small window offers Download, Later or "Don't remind me about
  this version". It shows once per SimHub start, 30 seconds after loading, and never while a game is running. The banner in the tab stays.
- **Support the project**: a coloured strip at the top of the tab and a "Support the project" button next to Diagnostics
  open a PayPal.Me link. The strip closes with the X and does not come back; the plugin stays free.

### 0.5.0 (not released on its own: included in 0.5.2)
- **New name: Huriz - Sim Car Oversteer**, because it is no longer only for Le Mans Ultimate. Updating renames the effects in
  SimHub and the Dash Studio overlay automatically; your settings and setups are kept.
- **iRacing (beta)**: the plugin detects the game by itself. iRacing does not give the slip of each tyre, so the rear slip
  is calculated from the car speed and its yaw rate (the rest of the effect works the same). There is no wheelspin
  filter in iRacing yet. Tested in the game.
- **Slip Max 10° by default** (was 12°): full vibration now arrives right at the limit of a slide you can still save. The
  bar goes from 3° to 18°, green between 8° and 14°. Your saved setups keep their value; only Default and **Reset to
  defaults** change.
- **Reference marks**: the green dot in the centre is replaced by a thin green line (0°); the slide line stays green up to 80% of Slip Start
  and then turns towards yellow at Slip Start and red at Slip Max.
- **Diagnostics for new games**: while a game is running the plugin saves a small text file with the telemetry numbers it gets
  (`diagnostico.txt`), and a button in the tab opens its folder, so it can be tuned with real data. Errors the plugin used
  to ignore silently are now written to `errores.log` in the same folder.
- **One file per game**: the SimHub properties each game is read from are in a small JSON file per game inside the plugin.
  Advanced users can override or add one by dropping a `.json` file into `PluginsData\Common\HurizOversteer.Games` in SimHub.

### 0.4.0 (not released on its own: included in 0.5.2)
- **Active Pedals (Simucube, beta)**: the same slide vibration on the Simucube ActivePedal. The installer creates the effect in
  SimHub (Devices > Simucube Active Pedals), on the throttle, like on the haptic pedals. Its own drop-down with on/off
  switch, frequency (50–75 Hz by default, up to 100 Hz), high priority and live graph. Beta: testing in progress.
- **Installer**: groups for Bass shakers and Pedals (haptic pedals and Simucube ActivePedal, in beta). Each one says "detected"
  or "not detected" and comes ticked when detected, but you can tick it anyway (for example, pedals added to SimHub
  later). The pedal effects go into the **Default profile** of each device.
- **New car drawing** in the live view and the Dash Studio overlay, based on a top view of a GT car: real silhouette,
  windows, vents, mirrors, headlights and a wide rear wing, with relief shading. The slide degrees sit on the roof.
- **Front wheels turn with your steering**, on the car and on its grey shadow, so you see where the wheels point
  compared with how the car is really going.
- **Colours by zone**, in a smooth gradient: green at 80% of your Slip Start, yellow at Slip Start and red at Slip Max.
  The rear wheels, the car outline, the degrees and the percentage use them.
- **Reference marks**: a green dot in the centre, yellow at Slip Start and red at Slip Max. The slide is drawn on the
  degree line itself: blue at the centre, green at 80% of Slip Start, yellow at Slip Start and red at Slip Max.

### 0.3.5
- **New version notice:** when SimHub starts, the plugin checks on GitHub (at most once a day) whether there is a newer
  version. If there is, a blue strip appears at the top of the plugin tab with a **Download** button and a
  **Don't remind me about this version** button. It only asks for the latest version number and sends no data.
  Without internet it simply does nothing. The **Check for updates** button, next to the version, checks right away.
- **Fix:** after a slide, the effect faded out but never reached exactly 0: it kept tiny values on **both** the bass
  shaker and the haptic pedal outputs. On bass shakers it was silent, but haptic pedals (for example Simagic) kept
  vibrating until you paused the game. Now it goes straight to 0 once it drops below 0.5%.
- **Anticipation** *(Pro)* now follows your **Slip Start**: the heads-up can start at 80% of it (2.4° with 3°, 4° with 5°).
  Before, it could start from 2.5° whatever your Slip Start was, too early with high values.
- **Loaded profile** now sits on the right of the header, in line with the language and Guide buttons. With a narrow
  window it moves to its own line instead of overlapping anything.
- No end date: this version keeps working with no time limit.

### 0.3.4
- **High priority** switch in Bass shakers and Haptic pedals, synced with the "High priority" option of the effect in SimHub:
  while it vibrates, it takes precedence over your other SimHub effects so it feels clearer. On by default.
- The installer says clearly that the haptic pedal effect has only been tested with **Simagic** pedals.
- **Uninstalling now really removes your profiles:** it also deletes the copies of the plugin settings that SimHub keeps
  in its own backup folder. Before, SimHub restored your setups after reinstalling.

### 0.3.3
- **Everything in one place**: the settings stay open and Dash Studio overlay, Bass shakers and Haptic pedals are
  **drop-downs** you open and close. Closed, they show a summary, and the plugin remembers which ones you left open.
- **On/off switch** in the header of each drop-down. For bass shakers and haptic pedals it turns the effect on or off
  **directly in SimHub** (ShakeIt and Devices), so you see it there at once.
- **Bass shakers** and **Haptic pedals**: minimum and maximum frequency with **one bar with two handles**. The plugin writes
  them directly into the effect in SimHub (Frequency and High frequency), without forcing frequencies. Haptic pedals up to
  50 Hz. Volume and strength are still set in SimHub.
- **Live graph** in Bass shakers and Haptic pedals, like the one in ShakeIt: the vibration the plugin sends over the last
  8 seconds, from 0 to 100%, with the maximum, current and minimum Hz on the right. With the switch off, it stays flat.
- **Colour zones** under Slip Start, Slip Max and the frequency bars (green recommended, yellow with care, red not recommended)
  and a tick at the default value. The bars no longer reach values that make no sense. Bigger bars, easier to grab.
- **Live view and Dash Studio overlay:** the RL / RR numbers are replaced by a single percentage at the bottom centre: 0% at Slip Start,
  100% at Slip Max.
- The tab only shows the **Bass shakers** and **Haptic pedals** drop-downs when their effect is in SimHub.
- The bass shaker effect is created in **Mono** instead of four corners: a single signal for the rear axle. Send it to the shakers you want with the channel map of your sound output in ShakeIt. Existing ones are changed too.
- The installer groups the effects as **Shaker / haptic effects** and updates the ones you already have.
- **Fix:** the haptic pedal effect could stay silent because its formulas were not set to JavaScript. The installer and
  the plugin now set them to JavaScript.
- **Uninstalling removes everything**: the effects in ShakeIt and on the haptic pedals, the plugin settings and setups,
  and the backups made by the installer. Your other effects are not touched.

### 0.3.2
- **Bass shakers and haptic pedals, on equal terms:** the plugin, the installer and the guide now treat both the same way.
  The installer option is now **Haptic pedal effect** (for example Simagic) and works with any haptic pedals set up in SimHub.
- **New Image group** in the settings (Simple and Pro): **Road** and, in Pro, the slide and steering directions.
  They only change the drawing of the live view and the overlay, never the vibration.
- The overlay **Background** option is now called **Overlay background** and stays in the Dash Studio overlay card, because it only affects the overlay.
- Guide: one body shaker is enough, and haptic pedals only go up to 50 Hz.

### 0.3.1
- **New name: Huriz - LMU Oversteer** (formerly *LMU - Rear Slip Pro*). Updating keeps your settings, setups,
  effects, SimHub menu position and overlay layouts; the old plugin is removed.
- **New installer window** to choose what to install: the plugin (always), the bass shaker effect, the
  **Simagic haptic effect** and the Dash Studio overlay.
- **Simagic haptic pedals:** the installer detects them ("detected" in green, "not detected" in red) and can
  create the effect on the throttle pedal (45 Hz base, 50 Hz high, high priority). You can change it later in SimHub.
- The installer shows the version and follows the language of Windows (English or Spanish).
- New **drifting car icon** in the SimHub menu and in the installer.
- The **Use these settings** button is now **Save settings**.
- Uninstalling asks you to close SimHub and removes the plugin completely.
- Fixed accents in the Spanish texts of the installer.
- **Fix:** **Save settings** now also saves the changes into the loaded profile (before, they were lost when that profile was loaded again). The setup name box comes filled in with the loaded profile, so **Save** overwrites it directly.

### 0.3.0
- **Dash Studio overlay**: shows the live view over the game from the Overlays tab, combinable with any other overlay.
- New **Dash Studio overlay** card in the plugin tab (image on/off, dark or transparent background).

### 0.2.2
- **Live view with two cars**: where the wheels point and how the car is really going, with the extra degrees it slides.
- Curved road, ABS / TC markers on the axles, **Expand** button.
- Road on/off in Simple and Pro; slide and steering direction switches in Pro.

### 0.2.1
- Clearer message about the date this version works until.

### 0.2.0
- New dark settings tab with **Simple / Pro** modes, live view, progression curve and throttle limit.
- English and Spanish interface, **Guide** button, fixed order in the setups list. Slip Max default is now 12°.

### 0.1.0
- First version: rear-slip effect for ShakeIt Bass Shakers, Simple / Pro settings and setups per car.

---

## Español

### 0.5.2 (incluye la 0.4.0, la 0.5.0 y la 0.5.1, que no se publicaron solas)
- **Repositorio renombrado a Huriz-Sim-Car-Oversteer** (ya no lleva LMU en el nombre). Los enlaces antiguos siguen
  funcionando y las versiones ya instaladas siguen encontrando actualizaciones ahí.
- **Overlay más ligero**: la imagen del overlay de Dash Studio solo se dibuja y se guarda cuando cambia (con el coche parado,
  en boxes o en los menús no hace nada), así que gasta menos CPU y deja de crear y borrar ficheros sin parar.
- **Diagnóstico limpio en cada sesión**: `diagnostico.txt`, `errores.log` y los registros de búsqueda de efectos empiezan
  vacíos cada vez que arranca SimHub, así que no se llenan con los días y siempre muestran la sesión actual.
- **Aviso en Active Pedals**: la tarjeta del Simucube ActivePedal ahora dice que el pedal necesita algo de presión para
  notar la vibración (en reposo está en su tope y no hay nada que mover).
- **Ventana de versión nueva**: cuando hay una release más nueva, una ventana pequeña ofrece Descargar, Más tarde o "No
  avisar de esta versión". Sale una vez por arranque de SimHub, 30 segundos después de cargar, y nunca con un juego en marcha. El aviso de la pestaña sigue.
- **Apoyar el proyecto**: una franja de color arriba de la pestaña y un botón "Apoyar el proyecto" junto a Diagnóstico
  abren un enlace de PayPal.Me. La franja se cierra con la X y no vuelve a salir; el plugin sigue siendo gratis.

### 0.5.0 (no se publicó sola: va incluida en la 0.5.2)
- **Nuevo nombre: Huriz - Sim Car Oversteer**, porque ya no es solo para Le Mans Ultimate. Al actualizar se renombran solos
  los efectos de SimHub y el overlay de Dash Studio; tus ajustes y setups se conservan.
- **iRacing (beta)**: el plugin detecta el juego solo. iRacing no da el deslizamiento de cada neumático, así que el derrape
  de la zaga se calcula con la velocidad del coche y su giro (yaw); el resto del efecto funciona igual. Todavía no hay
  filtro de wheelspin en iRacing. Probado en el juego.
- **Slip Max 10° por defecto** (antes 12°): la vibración a tope llega justo en el límite de un derrape que aún se salva.
  La barra va de 3° a 18°, en verde entre 8° y 14°. Tus setups guardados conservan su valor; solo cambian Default y
  **Restablecer valores**.
- **Marcas de referencia**: el punto verde del centro se sustituye por una línea verde fina (0°); la línea del derrape es verde
  hasta el 80% de Slip Start y de ahí cambia hacia amarillo en Slip Start y rojo en Slip Max.
- **Diagnóstico para juegos nuevos**: mientras hay un juego en marcha el plugin guarda un pequeño archivo de texto con los números de telemetría
  que recibe (`diagnostico.txt`), y un botón de la pestaña abre su carpeta, para poder ajustarlo con datos reales. Los errores
  que antes se ignoraban sin dejar rastro se anotan ahora en `errores.log`, en la misma carpeta.
- **Un fichero por juego**: las propiedades de SimHub de las que se lee cada juego están en un pequeño JSON por juego dentro del
  plugin. Un usuario avanzado puede sustituir o añadir uno dejando un `.json` en `PluginsData\Common\HurizOversteer.Games` de SimHub.

### 0.4.0 (no se publicó sola: va incluida en la 0.5.2)
- **Active Pedals (Simucube, beta)**: la misma vibración del derrape en los Simucube ActivePedal. El instalador crea el efecto en
  SimHub (Dispositivos > Simucube Active Pedals), en el acelerador, igual que en los pedales hápticos. Desplegable propio
  con interruptor, frecuencia (50–75 Hz por defecto, hasta 100 Hz), prioridad alta y gráfica en vivo. Beta: en pruebas.
- **Instalador**: grupos para Bass shakers y Pedales (hápticos y Simucube ActivePedal, en beta). Cada uno indica
  "detectado" o "no detectado" y sale marcado si se detecta, pero se puede marcar igualmente (por ejemplo, pedales que
  añadirás a SimHub más tarde). Los efectos de los pedales se crean en el **Default profile** de cada dispositivo.
- **Coche nuevo** en la vista en vivo y en el overlay de Dash Studio, basado en una vista cenital de un GT: silueta real,
  cristales, tomas, retrovisores, faros y alerón ancho, con relieve. Los grados del derrape van sobre el techo.
- **Las ruedas delanteras giran con el volante**, en el coche y en su sombra gris, para ver hacia dónde apuntan las
  ruedas frente a cómo va de verdad el coche.
- **Colores por zonas**, en degradado continuo: verde en el 80% de tu Slip Start, amarillo en Slip Start y rojo en Slip Max.
  Los usan las ruedas traseras, el contorno del coche, los grados y el porcentaje.
- **Marcas de referencia**: punto verde en el centro, amarillo en Slip Start y rojo en Slip Max. El derrape se pinta
  sobre la propia línea de grados: azul en el centro, verde en el 80% de Slip Start, amarillo en Slip Start y rojo en Slip Max.

### 0.3.5
- **Aviso de versión nueva:** al arrancar SimHub, el plugin mira en GitHub (como mucho una vez al día) si hay una versión
  más nueva. Si la hay, aparece una franja azul arriba en la pestaña del plugin con un botón **Descargar** y otro
  **No avisar de esta versión**. Solo pide el número de la última versión y no envía ningún dato. Sin internet,
  simplemente no hace nada. El botón **Buscar actualizaciones**, junto a la versión, lo comprueba al momento.
- **Corrección:** después de un derrape, el efecto se iba apagando pero nunca llegaba a 0 exacto: quedaban restos diminutos
  **tanto** en la salida de bass shakers como en la de pedales hápticos. En los bass shakers no se oía, pero los pedales
  hápticos (por ejemplo Simagic) seguían vibrando hasta pausar el juego. Ahora pasa directamente a 0 cuando baja del 0,5%.
- **Anticipación** *(Pro)* sigue ahora a tu **Slip Start**: el aviso puede empezar al 80% de ese valor (2,4° con 3°, 4° con 5°).
  Antes podía empezar desde 2,5° fuera cual fuera tu Slip Start, demasiado pronto con valores altos.
- **Perfil cargado** va ahora a la derecha de la cabecera, en línea con los botones de idioma y Guía. Con la ventana
  estrecha baja a su propia línea en vez de solaparse con nada.
- Sin fecha de fin: esta versión funciona sin límite de tiempo.

### 0.3.4
- Interruptor **Prioridad alta** en Bass shakers y Pedales hápticos, sincronizado con la opción "High priority" del efecto en
  SimHub: mientras vibra, tiene preferencia sobre los demás efectos de SimHub y se nota más claro. Activado por defecto.
- El instalador indica claramente que el efecto para pedales hápticos solo está probado con pedales **Simagic**.
- **Al desinstalar ahora sí se borran tus perfiles:** también se borran las copias de los ajustes del plugin que SimHub guarda
  en su propia carpeta de copias de seguridad. Antes, SimHub recuperaba tus setups al reinstalar.

### 0.3.3
- **Todo en un solo sitio**: la configuración queda siempre abierta y Overlay de Dash Studio, Bass shakers y Pedales hápticos
  son **desplegables** que abres y cierras. Cerrados muestran un resumen, y el plugin recuerda cuáles dejaste abiertos.
- **Interruptor on/off** en la cabecera de cada desplegable. En bass shakers y pedales hápticos activa o desactiva el efecto
  **directamente en SimHub** (ShakeIt y Dispositivos), así que lo ves allí al momento.
- **Bass shakers** y **Pedales hápticos**: frecuencia mínima y máxima con **una barra de dos tiradores**. El plugin las escribe
  directamente en el efecto de SimHub (Frequency y High frequency), sin forzar frecuencias. Pedales hápticos hasta 50 Hz.
  El volumen y la fuerza se siguen ajustando en SimHub.
- **Gráfica en vivo** en Bass shakers y Pedales hápticos, como la de ShakeIt: la vibración que manda el plugin en los
  últimos 8 segundos, de 0 a 100%, con los Hz máximo, actual y mínimo a la derecha. Con el interruptor apagado se queda plana.
- **Zonas de color** bajo Slip Start, Slip Max y las barras de frecuencia (verde recomendado, amarillo con cuidado, rojo no
  recomendable) y una raya en el valor por defecto. Las barras ya no llegan a valores sin sentido. Barras más grandes, más fáciles de mover.
- **Vista en vivo y overlay de Dash Studio:** los números TI / TD se sustituyen por un solo porcentaje abajo en el centro: 0% en Slip Start,
  100% en Slip Max.
- La pestaña solo muestra los desplegables de **Bass shakers** y **Pedales hápticos** si su efecto está en SimHub.
- El efecto de bass shakers se crea en **Mono** en vez de cuatro esquinas: una sola señal para el tren trasero. Mándala a los shakers que quieras con el mapa de canales de tu salida de sonido en ShakeIt. Los que ya existen también se cambian.
- El instalador agrupa los efectos como **Efectos para shakers / hápticos** y pone al día los que ya tienes.
- **Corrección:** el efecto de los pedales hápticos podía no vibrar porque sus fórmulas no estaban en JavaScript.
  El instalador y el plugin las ponen ahora en JavaScript.
- **Al desinstalar se borra todo**: los efectos de ShakeIt y de los pedales hápticos, los ajustes y setups del plugin
  y las copias de seguridad del instalador. Tus otros efectos no se tocan.

### 0.3.2
- **Bass shakers y pedales hápticos, al mismo nivel:** el plugin, el instalador y la guía tratan los dos por igual.
  La opción del instalador pasa a ser **Efecto para pedales hápticos** (por ejemplo Simagic) y sirve para cualquier pedal háptico configurado en SimHub.
- **Nuevo grupo Imagen** en los ajustes (Simple y Pro): **Carretera** y, en Pro, los sentidos del derrape y del volante.
  Solo cambian el dibujo de la vista en vivo y del overlay, nunca la vibración.
- La opción **Fondo** del overlay pasa a llamarse **Fondo del overlay** y se queda en la tarjeta del overlay de Dash Studio, porque solo afecta al overlay.
- Guía: basta con un body shaker, y los pedales hápticos solo llegan hasta 50 Hz.

### 0.3.1
- **Nombre nuevo: Huriz - LMU Oversteer** (antes *LMU - Rear Slip Pro*). Al actualizar se conservan tus ajustes,
  setups, efectos, posición en el menú de SimHub y diseños de overlays; el plugin viejo se quita.
- **Nueva ventana en el instalador** para elegir qué instalar: el plugin (siempre), el efecto para bass shakers,
  el **efecto háptico de Simagic** y el overlay de Dash Studio.
- **Pedales hápticos Simagic:** el instalador los detecta ("detectado" en verde, "no detectado" en rojo) y puede
  crear el efecto en el pedal del acelerador (45 Hz base, 50 Hz alta, prioridad alta). Puedes cambiarlo después en SimHub.
- El instalador muestra la versión y sigue el idioma de Windows (inglés o español).
- Nuevo **icono de coche derrapando** en el menú de SimHub y en el instalador.
- El botón **Usar esta configuración** pasa a llamarse **Guardar configuración**.
- Al desinstalar pide cerrar SimHub y quita el plugin del todo.
- Arreglados los acentos de los textos en español del instalador.
- **Corrección:** **Guardar configuración** guarda también los cambios en el perfil cargado (antes se perdían al volver a cargar ese perfil). El nombre del setup aparece ya relleno con el perfil cargado, así **Guardar** lo sobrescribe directamente.

### 0.3.0
- **Overlay para Dash Studio**: muestra la vista en vivo sobre el juego desde la pestaña Overlays y se combina con cualquier otro overlay.
- Nueva tarjeta **Overlay de Dash Studio** en la pestaña del plugin (imagen sí/no, fondo oscuro o transparente).

### 0.2.2
- **Vista en vivo con dos coches**: hacia dónde apuntan las ruedas y cómo va realmente el coche, con los grados que se va de más.
- Carretera curva, marcas de ABS / TC en los ejes, botón **Ampliar**.
- Carretera sí/no en Simple y Pro; conmutadores de sentido del derrape y del volante en Pro.

### 0.2.1
- Mensaje más claro sobre la fecha hasta la que funciona esta versión.

### 0.2.0
- Nueva pestaña de ajustes oscura con modos **Simple / Pro**, vista en vivo, curva de progresión y límite de gas.
- Interfaz en español e inglés, botón de **Guía**, lista de setups con orden fijo. Slip Max por defecto pasa a 12°.

### 0.1.0
- Primera versión: efecto de derrape trasero para ShakeIt Bass Shakers, ajustes Simple / Pro y setups por coche.
