# Changelog

**Latest version / Última versión: [v0.6.7](../../releases/latest)**

[English](#english) | [Español](#español)

---

## English

### 0.6.7
- **Update with one click.** When there is a new version, press **Update** (in the notice or in the plugin tab): it downloads it from
  GitHub, installs it by itself when you close SimHub (Windows asks for permission once) and opens SimHub again, with the same options you chose last time.
  If something fails, `install-error.log` opens. Works from this version on.
- **New device: Simsonn VAM / VAM Pro (beta).** Same as the Simagic and Simnet haptic pedals: its own card in the tab (on/off, 20-50 Hz,
  high priority, live graph and SimHub profiles) and its own option in the installer, which detects it and adds the effect to all its profiles,
  on the throttle pedal. Not tested with a real VAM yet: feedback welcome.
- **Fixed: effect groups.** The installer now puts the effect in profiles that contain effect groups. In ShakeIt (and in the pedal devices) a profile can have a *group* of
  effects (for example a "braking" group). The installer counted the effect lists wrongly when a profile had a group and, instead of installing,
  stopped with "unexpected structure" without changing anything. Now it only looks at the list of each profile, puts the effect in all of them and leaves
  your groups untouched (it still makes a backup first).
- **If something goes wrong while setting up the effect, the installer says so and opens `install-error.log`** (full screen in Notepad, with what that install did) so you can
  send it. Before, a failed step was silent.
- **New tool: `Huriz-SimHub-Check.exe`** (in the release, next to the installer). One click, it installs nothing: it checks SimHub, tries the
  installer steps on a **copy** of your SimHub settings and opens a report in Notepad to send if something does not work.

### 0.6.4 (includes the 0.6.x test versions, which were not released on their own)
- **New games: rFactor 2, Automobilista 2 (beta) and RaceRoom (beta).** rFactor 2 works like Le Mans Ultimate. Automobilista 2
  and RaceRoom use the same method as iRacing. **iRacing is no longer beta.** (In Automobilista 2 turn on the shared memory option.)
- **iRacing, Automobilista 2 and RaceRoom learn your car by themselves.** These games do not say how much each tyre slides, so the
  plugin needs to calculate the distance from the centre of gravity to the rear axle. It learns it while you drive between
  15 and 30 km/h with the wheel turned, saves it for each car and stops when the car has its samples (10 by default, up to 50).
  The faster the car goes while a reading is taken, the shorter the distance comes out, so every reading is **corrected for its
  speed** (the same table for every car and game). In our tests the learned distance was within about 3 % of the real one.
- **New Samples tab** (next to General): a table with your cars for each game (distance, averages, samples, done), a click on
  the car name searches its wheelbase and weight distribution, the pencil lets you type the value or calculate it from
  wheelbase × front weight, and there are reset, delete, refresh, open-file, export and import buttons. Learning settings: 10 to 50 samples per car.
- **Learning marks in the live view and the overlay**: little dots that fill with each sample and a speed bar that shows when you
  are in the right speed range.
- **Profiles**: the **Bass shakers**, **haptic pedals** and **Simucube ActivePedal** cards show a table with every SimHub profile
  (high priority, frequency, active, reset). The loaded profile is in green and a click on a name loads it in SimHub (if SimHub changes profile
  by itself, the plugin follows). What you change in SimHub shows up in the table and the other way round. The switch at the top of the card is the one of
  the loaded profile, and the live graph shows that profile. A **new button** copies the effect into the profiles that do not have it.
- **The installer puts the effect in every profile**, not only the default one (it never creates a profile), and it keeps a
  log, `install.log`, with what each step did, to find problems faster.
- **New device: Simnet Haptic Pedals (beta)**, with the same options as the Simagic pedals. Haptic pedals now go down to 20 Hz (was 25).
- **A more reliable slide in iRacing, Automobilista 2 and RaceRoom**: the slide is measured at the rear axle with the learned distance, and when the
  whole car and the axle go to opposite sides it counts as no slide (it fixed the live view drawn to the wrong side at low speed).
- **Speed Start uses the speed of the rear axle in every direction** (all games): the effect no longer cuts out in the middle of a spin with the car sideways.
- **Overlay**: with the plugin off, an expired version or no game running, the overlay shows nothing instead of freezing on the last picture.
- **Diagnostics**: the files are now `diagnostics.txt` and `errors.log` (in English). The diagnostics switch is still off by default.

### 0.5.3
- **Power oversteer always vibrates (LMU and iRacing)**: the wheelspin filter is gone. It muted the effect with more than
  30 % throttle when the rear wheels spun, even if the rear was stepping out (a drift under power). Now, if the rear slides,
  it vibrates, with or without throttle.
- **iRacing: more accurate slip angle (testing)**: the plugin now measures the slide in two places (the whole car and the
  rear axle) and uses the smaller one. It no longer vibrates in normal fast corners (the tyre working, not sliding) nor
  when you are almost stopped turning the wheel, and the live view is no longer drawn crossed. When the rear really steps
  out, both rise and it vibrates as before.
- **iRacing: wheelspin estimate (testing)**: iRacing does not give the speed of each wheel, so the plugin estimates the
  wheelspin from the engine revs, the gear and the car speed. It is only shown in the diagnostics file (revs, gear and the
  estimate); it does not change the effect.
- **Diagnostics switch**: next to **Open the diagnostics** there is a switch to turn the diagnostics file on or off. It is
  **off by default** (off, it writes nothing); turn it on only when you need to send a diagnostics file. The file is now
  more complete (4 readings per second, throttle, target and more).
- **Minimum speed 15 km/h** (it was about 22 km/h): below that the effect stays off. It applies to everyone, also to
  saved settings. It can be changed with the new **Speed Start** slider (Simple and Pro) (0–60 km/h; red below the value, green above).
- **Throttle limit (Pro) in colour**: green where the effect works and red above the value, where it switches off
  (at 100% it is all green).
- **Running game in the header**: next to the loaded profile, a blue box shows the game SimHub is running
  (e.g. "Game: iRacing"). It changes on its own and hides with no game.
- **Brand in the device names**: the drop-downs and the installer say **Simagic Haptic Pedals** and **Simucube
  ActivePedal**, so each device is easy to find as more are added.
- **Tab**: the diagnostics and support buttons are in a box under the setups; the support strip at the top comes back
  with each installation and closes with the X.
- **Installer**: the pedals (Simagic haptics and Simucube ActivePedal) share one group, with a short note about each one.

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
  open a PayPal.Me link. The strip closes with the X and stays closed until you install again; the plugin stays free.

### 0.5.0 (not released on its own: included in 0.5.2)
- **New name: Huriz - Sim Car Oversteer**, because it is no longer only for Le Mans Ultimate. Updating renames the effects in
  SimHub and the Dash Studio overlay automatically; your settings and setups are kept.
- **iRacing (beta)**: the plugin detects the game by itself. iRacing does not give the slip of each tyre, so the rear slip
  is calculated from the car speed and its yaw rate (the rest of the effect works the same). Still in testing.
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

### 0.6.7
- **Actualizar con un clic.** Cuando haya una versión nueva, pulsa **Actualizar** (en el aviso o en la pestaña del plugin): se descarga de
  GitHub, se instala sola al cerrar SimHub (Windows pide permiso una vez) y SimHub se vuelve a abrir, con las mismas opciones que elegiste la última vez.
  Si algo falla, se abre `install-error.log`. Funciona a partir de esta versión.
- **Dispositivo nuevo: Simsonn VAM / VAM Pro (beta).** Igual que los pedales hápticos Simagic y Simnet: su tarjeta en la pestaña
  (interruptor, 20-50 Hz, prioridad alta, gráfica en vivo y perfiles de SimHub) y su opción en el instalador, que lo detecta y pone el efecto en todos
  sus perfiles, en el pedal del acelerador. Aún sin probar con un VAM de verdad: se agradecen opiniones.
- **Corregido: grupos de efectos.** El instalador ya pone el efecto en perfiles que tienen grupos de efectos. En ShakeIt (y en los dispositivos de pedales) un perfil puede llevar un
  *grupo* de efectos (por ejemplo un grupo de «frenada»). El instalador contaba mal las listas de efectos cuando un perfil tenía un grupo y, en vez de
  instalar, se paraba con «estructura inesperada» sin cambiar nada. Ahora mira solo la lista de cada perfil, pone el efecto en todos y no toca tus
  grupos (sigue haciendo copia de seguridad antes).
- **Si algo falla al poner el efecto, el instalador lo dice y abre `install-error.log`** (en grande en el Bloc de notas, con lo que hizo esa instalación) para que
  lo envíes. Antes, un paso que fallaba no avisaba.
- **Herramienta nueva: `Huriz-SimHub-Check.exe`** (en la release, junto al instalador). Un clic y no instala nada: revisa SimHub, prueba
  los pasos del instalador sobre una **copia** de tus ajustes de SimHub y abre un informe en el Bloc de notas para enviarlo si algo no va.

### 0.6.4 (incluye las versiones de prueba 0.6.x, que no salieron por separado)
- **Juegos nuevos: rFactor 2, Automobilista 2 (beta) y RaceRoom (beta).** rFactor 2 funciona como Le Mans Ultimate. Automobilista 2
  y RaceRoom usan el mismo método que iRacing. **iRacing deja de ser beta.** (En Automobilista 2 hay que activar la opción de memoria compartida.)
- **iRacing, Automobilista 2 y RaceRoom aprenden tu coche solos.** Estos juegos no dicen cuánto desliza cada neumático, así que el
  plugin necesita calcular la distancia del centro de gravedad al eje trasero. La aprende mientras conduces entre
  15 y 30 km/h con el volante girado, la guarda para cada coche y termina cuando el coche tiene sus muestras (10 por defecto, hasta 50).
  Cuanto más rápido va el coche al tomar una lectura, más corta sale la distancia, así que cada lectura se **corrige según su
  velocidad** (la misma tabla para todos los coches y juegos). En nuestras pruebas la distancia aprendida quedó a menos de un 3 % de la real.
- **Pestaña Muestras nueva** (junto a General): una tabla con tus coches para cada juego (distancia, medias, muestras, hecho), un clic en
  el nombre del coche busca su distancia entre ejes y su reparto de peso, el lápiz deja escribir el valor o calcularlo con
  distancia entre ejes × peso delantero, y hay botones de reiniciar, borrar, actualizar, abrir el fichero, exportar e importar. Ajustes del aprendizaje: de 10 a 50 muestras por coche.
- **Marcas de aprendizaje en la vista en vivo y el overlay**: puntitos que se llenan con cada muestra y una barra de velocidad que dice cuándo
  estás en el rango de velocidad bueno.
- **Perfiles**: las tarjetas de **Bass shakers**, **pedales hápticos** y **Simucube ActivePedal** enseñan una tabla con todos los perfiles de SimHub
  (prioridad alta, frecuencia, activo, reinicio). El perfil cargado va en verde y un clic en el nombre lo carga en SimHub (si SimHub cambia de perfil
  solo, el plugin lo sigue). Lo que cambias en SimHub sale en la tabla y al revés. El interruptor de arriba de la tarjeta es el del
  perfil cargado y la gráfica en vivo enseña ese perfil. Un **botón nuevo** copia el efecto en los perfiles que no lo tienen.
- **El instalador pone el efecto en todos los perfiles**, no solo en el de por defecto (nunca crea un perfil), y guarda un
  registro, `install.log`, con lo que hizo cada paso, para encontrar los problemas antes.
- **Dispositivo nuevo: Simnet Haptic Pedals (beta)**, con las mismas opciones que los pedales Simagic. Los pedales hápticos bajan ahora hasta 20 Hz (antes 25).
- **El derrape es más fiable en iRacing, Automobilista 2 y RaceRoom**: se mide en el eje trasero con la distancia aprendida, y cuando el
  coche entero y el eje van hacia lados contrarios cuenta como sin derrape (arregló la vista en vivo dibujada al lado contrario a baja velocidad).
- **Speed Start usa la velocidad del eje trasero en cualquier dirección** (todos los juegos): el efecto ya no se corta en mitad de un trompo con el coche de lado.
- **Overlay**: con el plugin apagado, una versión caducada o sin juego en marcha, el overlay no enseña nada en vez de quedarse congelado con la última imagen.
- **Diagnóstico**: los ficheros pasan a llamarse `diagnostics.txt` y `errors.log` (en inglés). El interruptor del diagnóstico sigue apagado por defecto.

### 0.5.3
- **El sobreviraje con gas siempre vibra (LMU e iRacing)**: se quita el filtro de wheelspin. Silenciaba el efecto con más
  del 30 % de gas cuando patinaban las traseras, aunque el culo se estuviera yendo de lado (un drift acelerando). Ahora, si
  la zaga desliza, vibra, con gas o sin él.
- **iRacing: ángulo de deslizamiento más fiel (en pruebas)**: el plugin mide ahora el deslizamiento en dos sitios (el coche
  entero y el eje trasero) y usa el menor. Ya no vibra en curvas rápidas normales (el neumático trabajando, sin deslizar) ni
  casi parado girando el volante, y la vista en vivo ya no sale cruzada. Cuando el culo se va de verdad, suben los dos y
  vibra como antes.
- **iRacing: estimación del patinazo (en pruebas)**: iRacing no da la velocidad de cada rueda, así que el plugin estima el
  patinazo con las revoluciones del motor, la marcha y la velocidad del coche. Solo se muestra en el fichero de diagnóstico
  (revoluciones, marcha y la estimación); no cambia el efecto.
- **Interruptor del diagnóstico**: al lado de **Abrir el diagnóstico** hay un interruptor para encender o apagar el fichero de
  diagnóstico. Viene **apagado por defecto** (apagado no escribe nada); actívalo solo cuando tengas que mandar un
  diagnóstico. El fichero es más completo (4 lecturas por segundo, gas, objetivo y más).
- **Velocidad mínima de 15 km/h** (antes unos 22 km/h): por debajo el efecto va apagado. Vale para todos, también para
  ajustes guardados. Se cambia con la barra nueva **Speed Start** (Simple y Pro) (0–60 km/h; rojo por debajo del valor, verde por
  encima).
- **Límite de gas (Pro) en colores**: verde donde funciona el efecto y rojo por encima del valor, donde se apaga (al 100 %
  todo verde).
- **Juego en marcha en la cabecera**: al lado del perfil cargado, un recuadro azul muestra el juego que tiene SimHub en
  marcha (por ejemplo «Juego: iRacing»). Cambia solo y se oculta sin juego.
- **Marca en el nombre de los dispositivos**: los desplegables y el instalador dicen **Simagic Haptic Pedals** y
  **Simucube ActivePedal**, para que cada dispositivo se encuentre fácil cuando haya más.
- **Pestaña**: los botones de diagnóstico y apoyo van en un recuadro bajo los setups; la franja de apoyo de arriba vuelve a
  salir con cada instalación y se cierra con la X.
- **Instalador**: los pedales (hápticos Simagic y Simucube ActivePedal) comparten un grupo, con una nota breve de cada uno.

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
  abren un enlace de PayPal.Me. La franja se cierra con la X y no vuelve a salir hasta que se instale otra vez; el plugin sigue siendo gratis.

### 0.5.0 (no se publicó sola: va incluida en la 0.5.2)
- **Nuevo nombre: Huriz - Sim Car Oversteer**, porque ya no es solo para Le Mans Ultimate. Al actualizar se renombran solos
  los efectos de SimHub y el overlay de Dash Studio; tus ajustes y setups se conservan.
- **iRacing (beta)**: el plugin detecta el juego solo. iRacing no da el deslizamiento de cada neumático, así que el derrape
  de la zaga se calcula con la velocidad del coche y su giro (yaw); el resto del efecto funciona igual. En pruebas.
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
