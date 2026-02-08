# Manual de Despliegue Local - ClawAbierto (OpenClaw + Chutes.ai)

Este paquete contiene una versión personalizada de OpenClaw con soporte avanzado para **Chutes.ai** y modelos locales.

## 1. Requisitos Previos
- **Node.js**: v20 o superior.
- **pnpm**: Recomendado para la gestión de dependencias (`npm install -g pnpm`).
- **Ollama** (Opcional): Si deseas usar modelos locales de chat.

## 2. Instalación Local
1. Extrae el contenido del archivo `.zip`.
2. Abre una terminal en la carpeta raíz.
3. Instala las dependencias:
   ```bash
   pnpm install
   ```
4. Compila el proyecto:
   ```bash
   pnpm run build
   ```

## 3. Configuración de Chutes.ai
Para usar Chutes.ai, ejecuta el comando de configuración:
```bash
./bin/openclaw onboard
```
Selecciona **Chutes.ai** cuando se te pregunte por el proveedor. Podrás elegir entre:
- **OAuth**: Login rápido a través del navegador.
- **API Key**: Introducir tu clave de API manualmente.

### Actualización de Modelos
Chutes.ai añade modelos constantemente. Para descubrir los últimos (como DeepSeek-V3), usa:
```bash
./bin/openclaw chutes models
```

## 4. Nuevas Funciones de Selección de Modelos

### Modelos por Tarea (Acciones)
Puedes configurar modelos distintos para diferentes agentes en tu `openclaw.toml`:
```toml
[[agents.list]]
id = "investigador"
model = "chutes/deepseek-ai/DeepSeek-V3" # Usa Chutes para investigación

[[agents.list]]
id = "escritor-local"
model = "ollama/llama3" # Usa Ollama local para escribir
```

### Uso de APIs Independientes
Ahora puedes añadir proveedores personalizados en la sección `[models.providers]` del archivo de configuración para usar cualquier API compatible con OpenAI de forma independiente.

### Modelos Locales en el Chat
En la interfaz de chat, ahora tienes la opción de seleccionar **Local Model**:
1. Elige **Ollama** para conectar con tu instancia local de Ollama.
2. Elige **Local API** para cualquier otro servidor local (como LocalAI o LM Studio).

## 5. Solución de Problemas
- **Error de Conexión**: Asegúrate de que Ollama o tu API local estén escuchando en la dirección correcta (por defecto `127.0.0.1:11434`).
- **Modelos no aparecen**: Ejecuta `openclaw chutes models` para refrescar el catálogo de Chutes.ai.

---
*Desarrollado para ClawAbierto por Manus.*
