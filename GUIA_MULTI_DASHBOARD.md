# 📊 Guía de Sistema Multi-Dashboard con Pestañas

## 🎯 Descripción General

Sistema completo con **8 dashboards diferentes** en un solo portal:

1. **Overview General** - Vista panorámica
2. **Financiero** - Análisis financiero
3. **Operaciones** - Métricas operativas
4. **Proyectos** - Gestión de proyectos
5. **Analytics** - Análisis avanzado
6. **Tendencias** - Proyecciones
7. **Reportes** - Centro de reportes
8. **Exportar** - Exportación de datos

---

## 🎨 Navegación Dual

### 1. Pestañas Superiores (Top Tabs)
Navegación rápida horizontal en la parte superior:

```
┌─────────────────────────────────────────────────┐
│ [Overview] [Financiero] [Operaciones] [...]    │
└─────────────────────────────────────────────────┘
```

### 2. Menú Lateral (Sidebar)
Navegación organizada por secciones:

```
📊 Dashboards
  • Overview General
  • Financiero
  • Operaciones
  • Proyectos

📈 Análisis
  • Analytics
  • Tendencias

📋 Reportes
  • Reportes
  • Exportar
```

---

## 📁 Estructura de Archivos

```
dashboard/
│
├── dashboard-multi-tabs.html        # Dashboard principal con tabs
│
├── config/
│   ├── users.json                   # Usuarios y permisos
│   ├── dashboard-enhanced.json      # Config general
│   └── dashboards-config.json       # Config de cada dashboard
│
└── data/
    └── hotel-enhanced.json          # Datos
```

---

## 🎛️ Configuración de Dashboards

### Archivo: `config/dashboards-config.json`

Cada dashboard se configura individualmente:

```json
{
  "dashboards": {
    "nombre_dashboard": {
      "title": "Título del Dashboard",
      "icon": "icono-bootstrap",
      "description": "Descripción breve",
      "enabled": true,
      "permissions": ["admin", "manager"],
      "cards": [...],
      "charts": [...],
      "show_table": true
    }
  }
}
```

---

## 📊 Dashboards Incluidos

### 1. Overview General 🎯

**Propósito**: Vista panorámica de todos los indicadores

**Incluye**:
- ✅ 3 KPI cards principales
- ✅ Gráfico de barras por proyecto
- ✅ Gráfico de línea de evolución
- ✅ Tabla de datos completa

**Permisos**: Todos los usuarios

**Configuración**:
```json
{
  "overview": {
    "title": "Overview General",
    "enabled": true,
    "permissions": ["admin", "executive", "regional_manager", "hotel_manager"],
    "cards": [
      {
        "type": "sum",
        "label": "Inversión Total",
        "field_key": "Amount",
        "format": "currency"
      }
    ]
  }
}
```

---

### 2. Dashboard Financiero 💰

**Propósito**: Análisis financiero detallado

**Incluye**:
- ✅ Total invertido
- ✅ Inversión año actual
- ✅ Promedio por proyecto
- ✅ Comparación año anterior (YoY)
- ✅ Distribución por región

**Permisos**: Admin, Ejecutivo, Manager Regional

**KPIs**:
- Total invertido (histórico)
- Inversión año actual
- Promedio por proyecto
- Variación YoY %

---

### 3. Dashboard Operaciones ⚙️

**Propósito**: Métricas operativas

**Incluye**:
- ✅ Proyectos activos
- ✅ Tipos de proyecto
- ✅ Proyectos del mes
- ✅ Timeline de proyectos

**Permisos**: Admin, Managers

---

### 4. Gestión de Proyectos 📋

**Propósito**: Seguimiento detallado de proyectos

**Incluye**:
- ✅ Tabla completa de proyectos
- ✅ Búsqueda y filtros
- ✅ Exportación
- ✅ Ordenamiento personalizado

**Permisos**: Admin, Managers

---

### 5. Analytics Avanzado 📈

**Propósito**: Análisis predictivo

**Incluye**:
- ✅ Análisis de varianza YoY
- ✅ Tendencias acumuladas
- ✅ Proyecciones
- ✅ Correlaciones

**Permisos**: Solo Admin y Ejecutivos

---

### 6. Tendencias 📉

**Propósito**: Proyecciones futuras

**Contenido**: Por desarrollar según necesidades

**Permisos**: Admin, Ejecutivos

---

### 7. Centro de Reportes 📄

**Propósito**: Generación de reportes

**Características**:
- Reportes personalizados
- Programación de reportes
- Distribución automática

**Permisos**: Admin, Ejecutivos, Managers

---

### 8. Exportar Datos 💾

**Propósito**: Exportación de información

**Formatos disponibles**:
- Excel (.xlsx)
- PDF
- CSV
- JSON

**Permisos**: Admin, Ejecutivos, Managers

---

## 🔐 Control de Acceso por Dashboard

### Por Tipo de Usuario

| Dashboard | Admin | Executive | Regional Mgr | Hotel Mgr | Viewer |
|-----------|-------|-----------|--------------|-----------|--------|
| Overview | ✅ | ✅ | ✅ | ✅ | ✅ |
| Financiero | ✅ | ✅ | ✅ | ❌ | ❌ |
| Operaciones | ✅ | ❌ | ✅ | ✅ | ❌ |
| Proyectos | ✅ | ❌ | ✅ | ✅ | ❌ |
| Analytics | ✅ | ✅ | ❌ | ❌ | ❌ |
| Tendencias | ✅ | ✅ | ❌ | ❌ | ❌ |
| Reportes | ✅ | ✅ | ✅ | ❌ | ❌ |
| Exportar | ✅ | ✅ | ✅ | ❌ | ❌ |

### Configurar Permisos

En `dashboards-config.json`:

```json
{
  "overview": {
    "permissions": ["admin", "executive", "regional_manager", "hotel_manager", "demo"]
  },
  "financial": {
    "permissions": ["admin", "executive", "regional_manager"]
  },
  "analytics": {
    "permissions": ["admin", "executive"]
  }
}
```

---

## 🎨 Personalización Visual

### Cambiar Íconos

Los íconos usan Bootstrap Icons:

```json
{
  "overview": {
    "icon": "speedometer2"
  },
  "financial": {
    "icon": "currency-dollar"
  },
  "custom": {
    "icon": "star-fill"
  }
}
```

[Ver todos los íconos disponibles](https://icons.getbootstrap.com/)

### Cambiar Colores

En `dashboards-config.json`:

```json
{
  "theme": {
    "primary_color": "#1E90FF",
    "secondary_color": "#001f3f",
    "success_color": "#10b981",
    "warning_color": "#f59e0b"
  }
}
```

---

## ➕ Agregar Nuevo Dashboard

### Paso 1: Definir en la configuración

Editar `config/dashboards-config.json`:

```json
{
  "dashboards": {
    "mi_dashboard": {
      "title": "Mi Dashboard Personalizado",
      "icon": "star-fill",
      "description": "Descripción del dashboard",
      "enabled": true,
      "permissions": ["admin"],
      "cards": [
        {
          "type": "sum",
          "label": "Mi Métrica",
          "field_key": "MiCampo",
          "format": "currency"
        }
      ],
      "charts": [
        {
          "title": "Mi Gráfico",
          "type": "bar",
          "group_by_key": "Categoria",
          "value_key": "Valor"
        }
      ],
      "show_table": true
    }
  }
}
```

### Paso 2: Agregar navegación

En el sidebar del HTML:

```html
<div class="menu-item" data-tab="mi_dashboard">
  <i class="bi bi-star-fill"></i>
  <span>Mi Dashboard</span>
</div>
```

### Paso 3: Agregar pestaña

En las tabs superiores:

```html
<button class="tab-button" data-tab="mi_dashboard">
  <i class="bi bi-star-fill"></i>Mi Dashboard
</button>
```

### Paso 4: Agregar contenido

```html
<div id="tab-mi_dashboard" class="tab-content">
  <div class="kpi-grid" id="miDashboardKpis"></div>
  <div class="chart-grid" id="miDashboardCharts"></div>
</div>
```

### Paso 5: Agregar lógica de renderizado

En el JavaScript:

```javascript
function loadTabContent(tabId) {
  switch(tabId) {
    // ... casos existentes ...
    case 'mi_dashboard':
      renderMiDashboard();
      break;
  }
}

function renderMiDashboard() {
  renderKPIs('miDashboardKpis');
  renderCharts('miDashboardCharts');
}
```

---

## 🔄 Navegación entre Dashboards

### Métodos de Navegación

1. **Click en pestaña superior**
   - Navegación rápida horizontal
   - Siempre visible

2. **Click en menú lateral**
   - Navegación organizada por secciones
   - Mejor para muchos dashboards

3. **Ambos sincronizados**
   - Al hacer click en cualquiera, ambos se actualizan

### Animaciones

- ✅ Transición suave entre tabs
- ✅ FadeIn al mostrar contenido
- ✅ Indicador visual de tab activo

---

## 📱 Responsive

El sistema es completamente responsive:

### Desktop
- Sidebar visible
- Tabs horizontales
- Grid de 2-3 columnas

### Tablet
- Sidebar colapsable
- Tabs horizontales con scroll
- Grid de 1-2 columnas

### Mobile
- Sidebar oculto (toggle)
- Tabs horizontales con scroll
- Grid de 1 columna

---

## 🎯 Casos de Uso

### Caso 1: Dashboard Ejecutivo Simple

**Necesidad**: CEO quiere ver solo overview y financiero

**Solución**:
```json
{
  "navigation": {
    "sidebar": {
      "sections": [
        {
          "title": "Ejecutivo",
          "items": ["overview", "financial"]
        }
      ]
    }
  }
}
```

### Caso 2: Portal Operativo Completo

**Necesidad**: Manager operativo necesita múltiples vistas

**Solución**: Habilitar todos los dashboards operativos
```json
{
  "permissions": ["operations", "projects", "reports"]
}
```

### Caso 3: Dashboard por Departamento

**Necesidad**: Diferentes dashboards por departamento

**Solución**: Crear dashboard personalizado por departamento
```json
{
  "dashboard_finanzas": {...},
  "dashboard_operaciones": {...},
  "dashboard_marketing": {...}
}
```

---

## 🚀 Características Avanzadas

### 1. Carga Lazy de Dashboards

Los dashboards solo se cargan cuando se accede a ellos:

```javascript
function loadTabContent(tabId) {
  if (!loadedTabs.includes(tabId)) {
    renderDashboard(tabId);
    loadedTabs.push(tabId);
  }
}
```

### 2. Cache de Datos

Evita recargar datos innecesariamente:

```javascript
let cachedData = {};

function getData(dashboardId) {
  if (!cachedData[dashboardId]) {
    cachedData[dashboardId] = loadData(dashboardId);
  }
  return cachedData[dashboardId];
}
```

### 3. Favoritos

Marcar dashboards favoritos:

```javascript
const favorites = ['overview', 'financial'];
// Mostrar estrella en favoritos
```

### 4. Notificaciones

Alertas en dashboards específicos:

```html
<span class="badge">3</span> <!-- 3 nuevos proyectos -->
```

---

## 📊 Ejemplos de Configuración

### Dashboard Simple

```json
{
  "simple_dashboard": {
    "title": "Dashboard Simple",
    "icon": "bar-chart",
    "enabled": true,
    "permissions": ["admin"],
    "cards": [
      {
        "type": "count_rows",
        "label": "Total Registros"
      }
    ],
    "show_table": true
  }
}
```

### Dashboard Completo

```json
{
  "complete_dashboard": {
    "title": "Dashboard Completo",
    "icon": "grid-3x3",
    "description": "Vista completa con todas las métricas",
    "enabled": true,
    "permissions": ["admin", "executive"],
    "cards": [
      {
        "type": "sum",
        "label": "Total Ventas",
        "field_key": "Sales",
        "format": "currency"
      },
      {
        "type": "count_distinct",
        "label": "Clientes Únicos",
        "field_key": "Customer"
      },
      {
        "type": "custom",
        "label": "Promedio Ticket",
        "calculation": "average",
        "field_key": "Sales"
      }
    ],
    "charts": [
      {
        "title": "Ventas por Mes",
        "type": "line",
        "group_by_key": "Date",
        "value_key": "Sales",
        "enable_comparison": true
      },
      {
        "title": "Top Productos",
        "type": "bar",
        "group_by_key": "Product",
        "value_key": "Sales",
        "limit": 10
      }
    ],
    "show_table": true,
    "table_config": {
      "sortable": true,
      "searchable": true,
      "export": true,
      "pageLength": 25
    }
  }
}
```

---

## 🎓 Best Practices

### 1. Organización
- Agrupar dashboards relacionados en secciones
- Usar nombres descriptivos
- Mantener consistencia en íconos

### 2. Performance
- Cargar dashboards solo cuando se necesitan
- Usar cache para datos comunes
- Limitar número de gráficos por dashboard

### 3. UX
- Máximo 8-10 dashboards en navegación principal
- Usar breadcrumbs si hay sub-dashboards
- Mostrar indicadores de carga

### 4. Seguridad
- Validar permisos en cada dashboard
- Filtrar datos según usuario
- Auditar accesos

---

## ✅ Checklist de Implementación

- [ ] Crear archivo `dashboards-config.json`
- [ ] Definir todos los dashboards necesarios
- [ ] Configurar permisos por dashboard
- [ ] Agregar navegación en sidebar
- [ ] Agregar tabs superiores
- [ ] Implementar lógica de renderizado
- [ ] Probar navegación
- [ ] Verificar permisos
- [ ] Optimizar performance
- [ ] Documentar para usuarios

---

## 🎯 Resultado Final

Un sistema profesional multi-dashboard con:

✅ **8 dashboards** diferentes  
✅ **Navegación dual** (tabs + sidebar)  
✅ **Control de acceso** por dashboard  
✅ **Filtrado automático** por permisos  
✅ **Animaciones suaves** entre tabs  
✅ **Responsive** en todos los dispositivos  
✅ **Modular y extensible**  

¡Sistema multi-dashboard completo y listo para producción! 🚀
