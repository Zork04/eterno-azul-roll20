# Eterno Azul - ficha para Roll20

Versión de desarrollo funcional basada en la Guía de inicio de Eterno Azul.

## Archivos

- `sheet.html`: ficha, plantilla de chat y lógica de tiradas.
- `sheet.css`: posicionamiento sobre el fondo y estilo de la plantilla de chat.
- `ea-ficha-pj.jpg`: imagen definitiva de la ficha de PJ corregida en Photoshop (1073 x 1465 px).
- `ea-navio.png`: imagen definitiva de la ficha de navío corregida en Photoshop (1074 x 1465 px).
- `eterno-azul-roll-template-compacta.png`: fondo activo para las tiradas del chat, con marco completo y el logotipo como marca de agua suave (600 x 600 px).
- `eterno-azul-roll-template.png`: variante alta opcional del mismo fondo (600 x 900 px).
- `TradeWinds-Regular.ttf`: fuente de los titulares.

La hoja intenta usar la copia local de Trade Winds y, si el jugador no la tiene instalada, cargar la versión oficial pública indicada en `sheet.css`.

Las Acciones y las Señas usan casillas transparentes superpuestas: al escoger un dado se dibuja una X azul directamente sobre la casilla impresa correspondiente. El lienzo HTML usa exactamente las dimensiones de la base de Photoshop.

## Pestañas

- `PERSONAJE JUGADOR`: ficha rellenable y motor de Desafíos.
- `NAVÍO`: Valores del navío, Clase, Buscadores presentes, Tripulación, Mejoras, Desperfectos, Carga y Armamento.
- `PNJ`: nombre, descripción y una lista libre de apartados repetibles. El botón `+ Add` de Roll20 crea tantos bloques como hagan falta; cada uno tiene un título en negrita y un texto libre debajo. Sirve para reproducir perfiles breves o extensos sin imponer una estructura fija. No incluye tiradas para los enemigos porque la DJ no realiza tiradas.

## Alojamiento provisional de las imágenes

La opción recomendada durante el desarrollo es crear un repositorio público de GitHub, por ejemplo `eterno-azul-roll20`, y subir los tres fondos a una carpeta `images`. No hacen falta GitHub Pages ni una página web.

Después de abrir cada archivo en GitHub, pulsa `Raw` y copia la dirección directa. Tendrá una forma parecida a esta:

`https://raw.githubusercontent.com/TU-USUARIO/eterno-azul-roll20/main/images/ea-ficha-pj.jpg`

Usa la misma estructura para `ea-navio.png` y `eterno-azul-roll-template-compacta.png`, y pega las tres direcciones en sus correspondientes reglas `background-image` de `sheet.css`.

El repositorio tiene que ser público para que las fichas de todos los jugadores puedan cargar los fondos. Evita espacios, acentos y otros caracteres especiales en los nombres de carpetas y archivos.

## Instalación en Roll20

1. La persona propietaria de la partida necesita una suscripción que permita fichas personalizadas.
2. En la configuración de la partida, selecciona `Custom` como ficha de personaje.
3. Copia todo `sheet.html` en la pestaña HTML.
4. Copia todo `sheet.css` en la pestaña CSS.
5. Sube `ea-ficha-pj.jpg`, `ea-navio.png` y `eterno-azul-roll-template-compacta.png` a un alojamiento público estable. Las URL deben abrir directamente las imágenes sin página intermedia.
6. En `sheet.css`, sustituye las tres URL que comienzan por `https://REEMPLAZAR-CON-URL-PUBLICA/` por las URL respectivas.
7. Guarda los cambios y abre una ficha de personaje.

## Funcionamiento de los Desafíos

Al pulsar el nombre de cualquiera de las diez Acciones, Roll20 pregunta en este orden:

1. Si es una Bravata.
2. Qué Seña ha autorizado la DJ; `Ninguna` añade el d6 básico.
3. Qué Aptitud autorizada se aplica.
4. Qué Pertrecho autorizado se aplica.
5. Qué Condición favorable se aprovecha.
6. Si hay apoyo de un aliado.
7. Cuántas Ventajas adicionales concede la DJ.
8. El Riesgo total del Desafío.

La ficha tira la reserva heterogénea y calcula automáticamente:

- 1 éxito por cada resultado de 4 a 7.
- 2 éxitos por cada resultado de 8 a 12.
- Resultado narrativo comparando éxitos y Riesgo.
- Margen de éxito o margen de consecuencia.
- Recordatorio de la consecuencia adicional cuando una Bravata tiene consecuencias.

## Decisiones de diseño

- La Bravata añade `+1d6`; no aumenta automáticamente el Riesgo. La DJ sigue estableciendo el Riesgo conforme a la situación.
- Solo se ofrece una fuente de cada tipo por Desafío, conforme a la guía.
- Una Aptitud puede configurarse como `Sin dado`, `+1 Ventaja` o `+1 dado de Acción` para cubrir las capacidades de los personajes pregenerados.
- Los Vínculos se registran y pueden marcarse como agotados, pero no se suman automáticamente a la reserva: su efecto es un éxito adicional para otro personaje y requiere coordinación entre fichas.
- La ficha registra Bríos, Defensa, Aguante, Heridas, Pertrechos, Equipo de buscador, armas, armaduras y magia. Las Condiciones favorables se consultan como autorización Sí/No porque la hoja impresa no reserva un bloque para anotarlas.

## Comprobación recomendada

Prueba primero un personaje vacío con `Armonizar d6`, sin Seña, sin fuentes de Ventaja y Riesgo 1. La reserva debe contener exactamente `2d6`. Después añade una Seña d10 y una Bravata: la reserva debe ser `1d6 + 1d10 + 1d6`.

La hoja está validada estructuralmente, pero la ejecución final de las consultas y `startRoll` debe probarse dentro del editor real de Roll20.
