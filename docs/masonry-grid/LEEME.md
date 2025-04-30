# Guía pedagógica: Crear una Masonry Grid totalmente responsive con CSS3

## Introducción

Una **masonry grid** es un diseño visual en el que los elementos se organizan como ladrillos en una pared, apilados verticalmente sin una altura uniforme. Es muy usada en sitios como Pinterest para mostrar contenidos visuales de forma atractiva y flexible.

Esta guía está pensada para que los estudiantes puedan:

- Comprender qué es una _masonry grid_.
- Aplicar dos técnicas modernas usando solo **CSS3** (sin JavaScript).
- Usar buenas prácticas para que el diseño sea 100% responsive.

Incluye:

- Explicaciones teóricas.
- HTML y CSS separados.
- Ejemplo visual con imágenes reales (Unsplash).
- Dos técnicas: `column-count` y `grid-auto-flow: dense`.
- Versiones completas en archivos `.html` para práctica.

---

## Técnica 1: `column-count` (multicolumnas)

### HTML completo (masonry-column.html)

```html
<!DOCTYPE html>
<html lang="es">
	<head>
		<meta charset="UTF-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<title>Galería Masonry con Columnas</title>
		<style>
			body {
				font-family: sans-serif;
				background: #f4f4f4;
				padding: 2rem;
			}

			h1 {
				text-align: center;
				margin-bottom: 2rem;
			}

			.masonry-column {
				column-count: 3;
				column-gap: 1rem;
			}

			.masonry-column img {
				width: 100%;
				margin-bottom: 1rem;
				border-radius: 6px;
				display: block;
				break-inside: avoid;
			}

			@media (max-width: 768px) {
				.masonry-column {
					column-count: 2;
				}
			}

			@media (max-width: 480px) {
				.masonry-column {
					column-count: 1;
				}
			}
		</style>
	</head>
	<body>
		<h1>Galería Masonry (Columnas)</h1>
		<section class="masonry-column">
			<img src="https://images.unsplash.com/photo-1517694712202-14dd9538aa97" alt="imagen 1" />
			<img src="https://images.unsplash.com/photo-1526170375885-4d8ecf77b99f" alt="imagen 2" />
			<img src="https://images.unsplash.com/photo-1519985176271-adb1088fa94c" alt="imagen 3" />
			<img src="https://images.unsplash.com/photo-1506744038136-46273834b3fb" alt="imagen 4" />
			<img src="https://images.unsplash.com/photo-1504198458649-3128b932f49b" alt="imagen 5" />
		</section>
	</body>
</html>
```

### Ventajas

- Muy fácil de aplicar.
- No requiere cálculos.
- Totalmente responsive.

### Limitaciones

- El orden visual es por columna (no fila).
- Espaciado vertical puede ser desigual.

---

## Técnica 2: `CSS Grid` con `grid-auto-flow: dense`

### HTML completo (masonry-grid.html)

```html
<!DOCTYPE html>
<html lang="es">
	<head>
		<meta charset="UTF-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<title>Galería Masonry con CSS Grid</title>
		<style>
			body {
				font-family: sans-serif;
				background: #f4f4f4;
				padding: 2rem;
			}

			h1 {
				text-align: center;
				margin-bottom: 2rem;
			}

			.grid-wrapper {
				display: grid;
				grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
				grid-auto-rows: 10px;
				grid-gap: 10px;
				grid-auto-flow: dense;
			}

			.item {
				width: 100%;
				object-fit: cover;
				border-radius: 6px;
				box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
				transition: transform 0.2s ease-in-out;
			}

			.item:hover {
				transform: scale(1.02);
			}

			.tall {
				grid-row: span 30;
			}

			.wide {
				grid-column: span 2;
				grid-row: span 20;
			}
		</style>
	</head>
	<body>
		<h1>Galería Masonry (CSS Grid)</h1>
		<section class="grid-wrapper">
			<img class="item" src="https://images.unsplash.com/photo-1526170375885-4d8ecf77b99f" alt="img 1" />
			<img class="item tall" src="https://images.unsplash.com/photo-1517694712202-14dd9538aa97" alt="img 2" />
			<img class="item" src="https://images.unsplash.com/photo-1506744038136-46273834b3fb" alt="img 3" />
			<img class="item wide" src="https://images.unsplash.com/photo-1504198458649-3128b932f49b" alt="img 4" />
			<img class="item" src="https://images.unsplash.com/photo-1519985176271-adb1088fa94c" alt="img 5" />
		</section>
	</body>
</html>
```

### Ventajas

- Control total de ubicación y flujo.
- `grid-auto-flow: dense` rellena huecos inteligentemente.
- Flexible y fácil de extender.

### Limitaciones

- Si se desea calcular `span` según altura real, se requiere JS (no cubierto aquí).

---

## Conclusiones pedagógicas

- Ambas técnicas permiten resolver el problema de diseño sin necesidad de librerías externas.
- La versión multicolumna es la más fácil para comenzar.
- La versión con CSS Grid y `dense` permite más control y efectos visuales atractivos.

---

## 🔹 Propuesta de actividad final para el aula

1. Crear una galería con 10 imágenes usando la técnica de `column-count`.
2. Duplicar el proyecto y transformarlo usando `grid-auto-flow: dense`.
3. Agregar una versión con `grid-row: span x` para ajustar manualmente algunas alturas.
4. Compartir el proyecto en GitHub Pages.

---

¡Ahora sí, que empiece la magia del CSS! Sorpréndete viendo cómo tus cuadrículas cobran vida con solo unas líneas de código.
