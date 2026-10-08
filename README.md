# CacaoLab

Planta Virtual de Procesos Agroindustriales · planta de cacao a escala industrial.
Programa de Ingeniería Agroindustrial, Universidad Surcolombiana.
Docente: Ing. Jaime Daniel Bustos, D.Sc.

Recorrido 3D en primera persona por una planta de cacao: recepción de mazorcas, partidoras, fermentación en cajones en cascada, secador de lecho estático, análisis físico (prueba de corte), tostador de tambor, descascarilladora, molino de discos, molino de bolas, prensa hidráulica y pulverizador. Ocho turnos que se califican contra la NTC 1252 (cacao en grano), el Codex Alimentarius CXS 141-1983 (licor), CXS 105-1981 (cacao en polvo) y CXS 86-1981 (manteca), la inocuidad (Salmonella en el tueste, mohos y ocratoxina A), la orden del cliente y la eficiencia del proceso.

## Archivos

```
index.html                       la aplicación completa (un solo archivo)
manifest.json                    datos para instalarla como aplicación en el PC
sw.js                            funcionamiento sin conexión y actualización automática
icon-192.png, icon-512.png       íconos
registro_cacaolab_apps_script.gs backend del registro de uso (va en Google Apps Script, no en GitHub)
```

## Publicar en GitHub Pages (igual que NectarLab y LactoLab)

1. En GitHub, crea un repositorio nuevo llamado `CacaoLab` (público).
2. **Add file → Upload files**: sube `index.html`, `manifest.json`, `sw.js`, `icon-192.png` e `icon-512.png`.
3. **Settings → Pages → Deploy from a branch → main / (root) → Save**.
4. En uno o dos minutos queda en `https://jaimebustos1982.github.io/CacaoLab/`.

En el PC, Chrome o Edge muestran el botón **Instalar** en la barra de direcciones: así queda como aplicación de escritorio, con su ícono, y funciona sin conexión.

## Activar el registro central

Sin este paso, cada computador guarda sus propios registros y el panel docente solo ve los de ese equipo.

1. Crea una Google Sheet llamada **Registro CacaoLab**.
2. **Extensiones → Apps Script**. Borra el contenido y pega todo `registro_cacaolab_apps_script.gs`. Guarda.
3. **Implementar → Nueva implementación → tipo Aplicación web**.
   - Ejecutar como: **Yo**.
   - Quién tiene acceso: **Cualquier usuario**.
4. Autoriza y copia la URL que termina en `/exec`.
5. En `index.html`, busca `const SHEET_WEBAPP_URL="";` y pega la URL entre las comillas.
6. Sube de nuevo `index.html`. Cambia la versión en los dos archivos: `VERSION` en `index.html` (de `2026.10.07-C1` a `-C2`) y `CACHE_NAME` en `sw.js` (igual).

Cada vez que edites el Apps Script: **Implementar → Gestionar implementaciones → editar → Nueva versión** (la URL no cambia).

## Código de acceso docente

`CACAO-2026`. Está en `DOCENTE_CODE` (index.html) y en `SECRET` (Apps Script); si cambias uno, cambia el otro. El código viaja dentro del archivo, así que protege de curiosos, no de alguien que lea el código fuente.

## Qué registra

Cada ingreso, cada lote producido y cada cierre de sesión, con: integrantes y códigos, modalidad, grupo, turno, número de intento, estrellas, puntos, predicción y valor real, resultado por categoría (inocuidad, norma, cliente, eficiencia), fallas, tiempo activo en el turno, tiempo activo total y las variables que fijó el equipo. El tiempo activo solo corre con la ventana visible y actividad en los últimos 2 minutos.

El panel docente muestra el resumen por estudiante (8 turnos, 24 estrellas), la dificultad por turno y los últimos lotes, y exporta tres archivos CSV (separador `;`, abren directo en Excel en español). Desde el panel también se cambian los precios unitarios (gas natural y energía eléctrica) y se pueden habilitar todos los turnos.

## Para verificar que un cambio llegó

El pie del panel docente muestra la versión (`2026.10.07-C1`). Cámbiala en `VERSION` dentro de `index.html` y en `CACHE_NAME` de `sw.js` cada vez que publiques.
