# AMAC: Plataforma de empleo

Proyecto final de Desarrollo de Aplicaciones Web (OT2026-WEB), Entrega 2.

AMAC es una bolsa de trabajo para personas adultas mayores en Nuevo León. En la entrega pasada diseñamos el prototipo en Figma y en esta lo pasamos a código: páginas en HTML y CSS hechas a mano, sin Bootstrap, Tailwind ni plantillas.

**Sitio publicado:** https://amac-eight.vercel.app

**Repositorio:** https://github.com/elihuosuna-a11y/amac

## Equipo

| Integrante | Qué hizo |
|---|---|
| Elihu Osuna | Estructura del proyecto, variables de diseño, estilos base, encabezado, menú y pie de página, listado de vacantes y publicación en Vercel |
| Gustavo Treviño | Componentes reutilizables, detalle de vacante, flujo de postulación y Mis solicitudes |
| Omar Villareal | Inicio de sesión, registro de candidato y de empresa, panel de la empresa, Conoce a AMAC y página 404 |

## Páginas

Estas son las seis que pedía la entrega:

| Página | Qué muestra | Requerimientos |
|---|---|---|
| `index.html` | Listado de vacantes con buscador y filtros | RF-001, RF-002, RF-007 |
| `vacante.html` | Detalle de una vacante, con botón para postularse y para llamar | RF-003, RF-004, RF-051 |
| `login.html` | Inicio de sesión | RF-008 |
| `registro-candidato.html` | Registro de candidato en 5 partes | RF-011, RF-012, RF-013 |
| `mis-solicitudes.html` | Solicitudes enviadas y su estatus | RF-005, RF-006 |
| `empresa-vacantes.html` | Panel donde la empresa ve sus vacantes | RF-020, RF-021 |

También hicimos algunas de más:

- `confirmar-postulacion.html` y `postulacion-enviada.html`, para que se pueda recorrer completo el proceso de postularse.
- `registro-empresa.html` (RF-015).
- `conoce-amac.html`, con información de la asociación, contacto, aviso de privacidad y donativos (RF-031 a RF-034).
- `404.html`, que aparece si alguien entra a una dirección que no existe.
- Modo de alto contraste, que se activa solo cuando la persona lo tiene configurado en su computadora o celular.

## Cómo está organizado el código

```
css/
  variables.css     colores, fuentes y espaciados
  base.css          estilos generales y foco del teclado
  layout.css        encabezado, menú, pie y acomodo de cada página
  componentes.css   botones, tarjetas, formularios, etiquetas, tablas
img/
  iconos/
  capturas/
*.html
```

Todos los colores y tamaños viven en `variables.css`, así que si algo cambia en el diseño solo hay que tocarlo en un lugar.

## Colores

Son los mismos que definimos en los estilos de Figma.

| Variable | Color | Uso |
|---|---|---|
| `--color-marino` | `#202945` | Texto, botones principales y pie de página |
| `--color-coral` | `#FF815C` | Línea de los títulos y botón de donativo |
| `--color-texto-secundario` | `#4A5068` | Textos de apoyo |
| `--color-fondo` | `#F6F7F9` | Fondo de las páginas |
| `--color-superficie` | `#FFFFFF` | Tarjetas |
| `--color-superficie-suave` | `#EEF1F6` | Menú activo y etiquetas |
| `--color-superficie-ayuda` | `#FFE4D9` | Botón de ayuda |
| `--color-borde-tarjeta` | `#D5D9E2` | Bordes de tarjetas |
| `--color-borde-campo` | `#6B7288` | Bordes de los campos |
| `--color-azul-claro` | `#CAE4EF` | Estatus "Enviada" |
| `--color-durazno` | `#FDDAAD` | Estatus "En revisión" y "Pausada" |
| `--color-exito-fondo` | `#D3EBD5` | Estatus "Aceptada" y "Activa" |
| `--color-rechazo-fondo` | `#F6D6D6` | Estatus "Rechazada" |
| `--color-peligro` | `#9B1C1C` | Acciones que no se pueden deshacer |

## Tipografía

Usamos las dos fuentes del prototipo, las dos de Google Fonts: **Libre Baskerville** para los títulos y **Work Sans** para todo lo demás.

El texto normal es de 19 px. Los títulos de página miden 30 px en celular y 44 px en computadora. Pusimos todo en `rem` para que, si alguien agranda la letra en su navegador, el sitio crezca con ella.

## Componentes reutilizables

Al hacer las páginas nos dimos cuenta de que muchas piezas se repiten, así que cada una tiene su propia clase en `componentes.css`. En la Entrega 3 la idea es que cada una se convierta en un componente de React.

| Clase | Componente en React | Dónde se usa |
|---|---|---|
| `.boton` | `<Boton />` | En todo el sitio |
| `.boton-ayuda` | `<BotonAyuda />` | Encabezado, para llamar a AMAC (RF-052) |
| `.encabezado` y `.menu` | `<Encabezado />` | Todas las páginas |
| `.pie` | `<PieDePagina />` | Todas las páginas |
| `.titulo-pagina` | `<TituloPagina />` | Títulos con la línea coral |
| `.tarjeta-vacante` | `<TarjetaVacante />` | Listado de vacantes |
| `.chip` | `<Chip />` | Categoría de cada vacante |
| `.estatus` | `<EtiquetaEstatus />` | Mis solicitudes y panel de la empresa |
| `.campo-formulario` | `<CampoFormulario />` | Login y registros |
| `.opcion` y `.casilla` | `<Opcion />` y `<Casilla />` | Opciones y aceptación de términos |
| `.habilidad` | `<ChipSeleccionable />` | Habilidades en el registro |
| `.zona-archivo` | `<SubirArchivo />` | Subir CV, logo o banner |
| `.paso` | `<NumeroPaso />` | Partes del registro |
| `.aviso` | `<Aviso />` | Mensajes informativos |
| `.tabla` | `<TablaResponsiva />` | Solicitudes y vacantes de la empresa |
| `.pastilla` | `<FiltroEstado />` | Filtro por estado en el panel |

## Accesibilidad

Como el sitio lo van a usar personas mayores, esto fue lo que más cuidamos:

- Letra de al menos 18 px que crece con el zoom del navegador.
- Buen contraste entre texto y fondo en todas las páginas.
- Botones grandes, de al menos 44 px de alto, para que sea fácil tocarlos.
- Cada campo tiene su etiqueta escrita arriba, no solo un texto gris adentro.
- Al moverse con la tecla Tab siempre se ve en qué parte de la página estás.
- Un enlace para saltar directo al contenido.
- Los estatus llevan ícono y palabra, para no depender solo del color.
- Un solo título principal por página.
- Se puede usar con zoom al 200 % sin que se corte nada.

## Celular, tablet y computadora

Primero hicimos todo pensando en celular y luego fuimos ajustando para pantallas más grandes (a partir de 768 px y de 1024 px). En celular el menú queda abajo, como en el prototipo, y las tablas se vuelven tarjetas para que no haya que deslizar de lado. Lo revisamos en 320, 768, 1024 y 1440 px.

## Lo que cambiamos del prototipo

Hubo algunas cosas que no salieron igual que en Figma, y estas son las razones:

- **Login y registro tienen encabezado y pie.** La entrega pedía que estuvieran en todas las páginas.
- **El filtro de horario se ve como opciones y no como lista desplegable**, para que se vean todas sin tener que abrir nada. Agregamos el botón "Aplicar filtros" porque sin JavaScript hace falta.
- **Confirmar la postulación es una página aparte** y no una ventana emergente, porque sin JavaScript no se puede hacer la ventana.
- **En celular, el botón "Postularme" está debajo del título** en lugar de fijo abajo, para que no tape el menú.
- **En el menú de la empresa no pusimos "Solicitudes" ni "Perfil"**, porque esas pantallas eran opcionales. Quedan para la siguiente entrega.

Por ahora algunos botones, como "Guardar vacante", "Cancelar solicitud" o "Pausar", solo se ven pero no hacen nada; eso lo resolvemos cuando pasemos a React. Los teléfonos que aparecen son de ejemplo.

## Capturas

Página principal en celular y en computadora:

| Celular | Computadora |

| ![Página principal en celular](img/capturas/index-celular.png) | ![Página principal en computadora](img/capturas/index-escritorio.png) |



[Resultado de Lighthouse](img/capturas/lighthouse.png)

