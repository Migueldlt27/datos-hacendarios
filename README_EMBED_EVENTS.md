# Power BI JavaScript API + GA4 (sin botones externos)
Registra eventos del **reporte maestro** y envíalos a **GTM/GA4**.

## ¿Qué mide?
- `pbi_loaded`, `pbi_rendered`
- `pbi_page_changed` → incluye `page_name` (ej. “Ingresos”)
- `pbi_data_selected` (si el visual lo soporta)

## Requisitos rápidos
- Reporte **para tu organización** o **Embed token** (no funciona con “Publicar en la web”).
- **ACCESS TOKEN**, **EMBED URL** y **REPORT ID** del maestro.
- Contenedor **GTM** con **GA4 Configuration**.

## Pasos
1. Abre `pbi_embed_events.html` (en GitHub Pages).
2. Pega tus credenciales: `ACCESS_TOKEN`, `EMBED_URL`, `REPORT_ID`.
3. En **GTM** crea triggers (Custom Event) y etiquetas GA4 para:
   - `pbi_page_changed` (parámetros: `page_name`, `report_id`)
   - `pbi_loaded`, `pbi_rendered`
   - `pbi_data_selected` (opcional)
4. Publica GTM y valida en **GA4 → DebugView**.

## Análisis (GA4)
Explorar → Free Form → Dimensión `page_name`, Métrica `event_count`, Filtro `event_name = pbi_page_changed`.
