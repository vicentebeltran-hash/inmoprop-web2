# Inmoprop AI — landing (versión 4)

Rehecha con el lenguaje visual de **Adobe** y **Tesla**, y pensada desde el móvil.

Web estática de una sola página, sin build: `index.html` + los recursos de la raíz.

## De dónde sale cada cosa

**De Tesla** — la página se recorre por *capítulos a pantalla completa*. Cada uno
ocupa `100svh`, con una foto a sangre y una sola idea encima. Se avanza deslizando,
con `scroll-snap` suave. Los botones van en pareja, en píldora, al alcance del pulgar.

**De Adobe** — la navegación es una *píldora flotante* que se despega del borde y
cambia de claro a oscuro según el capítulo. Titulares enormes con el interletrado
muy cerrado. El capítulo de precios es una hoja clara que corta el ritmo de las fotos.

## Los siete capítulos

| | Capítulo | Idea |
|---|---|---|
| 01 | Hero | Tu equipo inmobiliario, entrenado por IA |
| 02 | El problema | Nadie practica. Todos improvisan |
| 03 | Role play | Practica la objeción antes de oírla |
| 04 | En directo | Y una persona al otro lado |
| 05 | Panel | Deja de volar a ciegas |
| 06 | Precios | Dos licencias y los sumadores |
| 07 | Cierre | Tu mejor agente ya está en tu oficina |

## Pensado para el móvil

- `100svh` en vez de `100vh`: no salta cuando aparece y desaparece la barra de Safari
- `env(safe-area-inset-*)` en nav, botones y barra inferior: respeta la muesca y la barra de gestos
- Cada foto tiene **dos recortes**: apaisado para escritorio y vertical 9:16 para el móvil,
  servidos con `<picture>`. En el teléfono nunca se ve una foto recortada a lo bruto
- Botones a ancho completo por debajo de 560 px, con 54 px de alto
- Los mandos − / + de los precios miden 38 px: se aciertan con el pulgar
- En el móvil solo se ve **una tarjeta de precio cada vez**, con un selector arriba
- Barra de compra fija abajo que aparece al salir del hero y se esconde al llegar a precios
- Barra de progreso arriba en el móvil; índice de puntos a la derecha en escritorio
- Todas las imágenes suman **~570 KB**

## Precios

Los mismos que la ver3: Agente 49 € y Agencia 125 € (1 gerente + 1 agente), más IVA.

| Añadido | Mensual | Regla |
|---|---|---|
| Staff | 22 € | Solo dentro de un plan. Máx. 3 en Agente |
| Gerente de más | 83,30 € | −15 % sobre los 98 € sueltos |
| Agente de más | desde 39 € | Un 5 % menos cada uno, suelo de 29 € |

Anual: −20 % sobre todo.

## Dónde se edita

| Qué | Dónde |
|---|---|
| Precio base | `data-mes` / `data-anual` de cada `.card__precio b` |
| Staff, gerente, curva de agentes | Bloque `CFG` del script |
| Topes de los sumadores | `data-min` / `data-max` de cada `.paso` |
| Textos de cada capítulo | Busca `<!-- ============ 0N` |
| Colores | Bloque `:root` del `<style>` |

## Imágenes

Salen de tu carpeta de Drive `7. Imagenes Cursos y role plays`, no de un banco de stock:

| Fichero | Original |
|---|---|
| cap-hero | elegir_mi_maquina |
| cap-problema | miedoexclusiva |
| cap-roleplay | llamada_telefonica |
| cap-directo | presentacion |
| cap-panel | indicadoresplan |
| cap-cierre | mivalor |

## Ver en local

```bash
python3 -m http.server 8080
```
