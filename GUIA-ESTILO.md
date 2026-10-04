# Guía de estilo — Colección "visual y simple" RH124 (v2)

Carpeta: `artefactos/v2/`. 17 apps HTML autónomas (funcionan con `file://`, sin internet, sin CDN,
sin fuentes externas, sin librerías). Una app = **un solo concepto**, bien explicado con **un diagrama**.

## Por qué esta versión
Las apps de `artefactos/` son correctas pero **recargadas**: muchos bloques, simulación de 5 pasos,
mucho texto coloquial. Aquí el criterio es:
- **Una idea por pantalla**, 3 bloques como máximo: `diagrama` → `explicación corta` → `chuleta de comandos`.
- **Ninguna simulación compleja**: como máximo **un** control interactivo (botón/select) y **una** frase de salida.
- **Lenguaje**: español técnico correcto, sin coloquialismo ("mira", "vale", "chollo", "se chupan los dedos").
  Evita|Superlativos y frases tipo "¡Boom!".
- **Gráfico > texto**: el diagrama es el protagonista; las frases son etiquetas cortas (<= 12 palabras).
- Sin cuestionarios, sin "fábricas", sinMillis, sin multiplicar puntos.

## Plantilla obligatoria (copiar tal cual, cambiar solo cabecera/body)

```html
<!DOCTYPE html><html lang="es"><head><meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>NN · Título corto</title><style>
:root{--rojo:#EE0000;--rojo-d:#B30000;--tinta:#151515;--gris:#f5f5f5;--azul:#004080;--ok:#3E9B4F;--amarillo:#F0AB00;--grisb:#c8c8c8}
*{box-sizing:border-box}
body{margin:0;font-family:system-ui,-apple-system,"Segoe UI",Roboto,sans-serif;background:var(--gris);color:var(--tinta);line-height:1.45}
header{background:var(--tinta);color:#fff;border-bottom:6px solid var(--rojo)}
.bar{max-width:1080px;margin:auto;display:flex;gap:14px;align-items:center;padding:14px 20px;flex-wrap:wrap}
.back{color:#fff;text-decoration:none;background:#333;padding:8px 12px;border-radius:8px;font-size:.85rem}
.num{background:var(--rojo);font-weight:800;font-size:.75rem;padding:4px 10px;border-radius:20px;letter-spacing:.06em}
h1{font-size:1.15rem;margin:2px 0 0}
main{max-width:1080px;margin:0 auto;padding:20px;display:grid;gap:16px}
.panel{background:#fff;border:1px solid #ddd;border-top:5px solid var(--rojo);border-radius:12px;padding:16px 18px}
.panel h2{font-size:1rem;margin:0 0 12px}
.panel h2 small{font-weight:400;color:#666;font-size:.85rem}
.btn{background:var(--rojo);color:#fff;border:0;padding:9px 15px;border-radius:8px;font-weight:700;cursor:pointer;font-size:.9rem}
.btn.sec{background:#333}
.btn:hover{background:var(--rojo-d)}
.chuleta{background:#0e0e0e;color:#d6ffd6;border-radius:10px;padding:12px 14px;font-family:ui-monospace,Consolas,monospace;font-size:.82rem;line-height:1.7;overflow-x:auto;white-space:pre}
.c{color:#7CFC98}.o{color:#F0AB00}.com{color:#8a8a8a}
table{width:100%;border-collapse:collapse;font-size:.88rem}
th,td{border:1px solid #ddd;padding:7px 9px;text-align:left;vertical-align:top}
th{background:#f0f0f0}
code{background:#111;color:#7CFC98;padding:1px 5px;border-radius:5px;font-family:ui-monospace,monospace;font-size:.85em}
svg{width:100%;height:auto;display:block}
.leyenda{font-size:.85rem;color:#555}
footer{max-width:1080px;margin:0 auto;padding:0 20px 30px;font-size:.8rem;color:#666}
</style></head><body>
<header><div class="bar"><a class="back" href="index.html">← Índice</a><div><span class="num">NN · UNIDAD X</span><h1>Título de la app</h1></div></div></header>
<main>
  <!-- PANEL 1: DIAGRAMA (obligatorio, lo más grande) -->
  <!-- PANEL 2: EXPLICACIÓN (tabla o 2-3 frases + 1 control) -->
  <!-- PANEL 3: CHULETA de comandos -->
</main>
<footer>Material didáctico · Administración de sistemas Enterprise Linux I · Sin marcas registradas</footer>
<script>
  /* máximo una función corta y sin estado global */
</script></body></html>
```

## Estilo de los diagramas
- **SVG inline** (`viewBox` 0 0 800 H, `width:100%`), texto con `font-size` 12-14, `text-anchor="middle"`.
- Iconos de distro: SVG geométricos simples (no trademarks): Fedora = círculo azul conFEDORA swirl simplificado; CentOS = dos cuadrados unidos; RHEL = cuadrado rojo con "R". Dibuja formas simples, no copies logotipos oficiales.
- Colores: cajas de sistema `fill="#151515"` texto blanco; datos/usuario `fill="#004080"`; acento `fill="#EE0000"`;
 aprovado/verde `#3E9B4F`; Physical `#F0AB00` con texto negro; líneas de flujo `stroke="#EE0000" stroke-width="2"` con
  `marker-end` para flechas (definir `<defs><marker>` una vez).
- **Una sola dirección de lectura**: izquierda → derecha o arriba → abajo. Nada de ramas imposibles.
- Flechas siempre rotuladas: `label` corto en la línea.

## Estilo del texto
- Explicación = tabla de 2 columnas (`concepto` / `qué significa`) o 3 frases cortas. Nada de párrafos > 40 palabras.
- Chuleta: 4-7 líneas de comandos reales de RHEL 10, con `comentario` alineado. Nada de comandos inventados:
  verifica que el comando exista en RHEL (`ls`, `stat`, `systemctl`, `rpm`, `dnf`, `lsns`, `ss`, `ssh-keygen`...).
- Evita el condicional coloquial: escribe "Al eliminar el archivo original, ..." no "si lo borras, pasa algo raro".
