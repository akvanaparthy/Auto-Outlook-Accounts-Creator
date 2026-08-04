

# 🚀 Creador Automático de Cuentas de Outlook

Creador automatizado de cuentas de Outlook/Hotmail utilizando Selenium y undetected-chromedriver. Evita la detección de bots y crea múltiples cuentas de manera eficiente.

## Esto es Semi Automatizado, lo que significa que debes resolver el captcha manualmente.

## Pasos sencillos para resolver el captcha:
- El sistema de captcha actual para la creación de cuentas en Outlook es: debes presionar y mantener pulsado durante unos segundos y luego se resolverá.
- Pero, en la mayoría de los casos presenta fallos, así que el truco aquí es mantener pulsado hasta que te pida que presiones y mantengas.
- En cuanto aparezcan los iconos de carga en el botón, simplemente mueve el cursor rápidamente y verás un símbolo de carga en el formulario; si lo ves, entonces puedes soltarlo.
- Si no lo ves o fallas, inténtalo 2 o 3 veces más hasta que adquieras práctica.
- Repítelo hasta que logres resolverlo; a veces puede ser un problema de IP si no logras resolverlo, así que cámbiala antes de crear más.
- El modo proxies no ha sido probado, así que usa la VPN activada y los proxies desactivados, y todo estará listo para funcionar.

## ✨ Características

- ✅ **Creación Automatizada de Cuentas**: Crea cuentas de Outlook.com con nombres generados aleatoriamente
- 🎭 **Evitación de Detección de Bots**: Utiliza undetected-chromedriver para evitar ser detectado
- 🔄 **Soporte para Proxies**: Rotación opcional de proxies para diversificar IPs
- 📊 **Exportación a CSV**: Guarda todas las cuentas creadas en un archivo CSV
- 🛡️ **Manejo de Errores**: Manejo robusto de errores con reintentos y registros detallados
- 🖼️ **Captura de Pantallas**: Capturas automáticas en caso de errores para depuración
- ⚡ **Configurable**: Configuración sencilla mediante `config.py`

## 📋 Requisitos

- Python 3.8+
- Navegador Chrome instalado
- Windows/Linux/MacOS

## 🔧 Instalación

1. **Clona el repositorio:**
```bash
git clone <your-repo-url>
cd Auto-Outlook-Accounts-Creator
```

2. **Instala las dependencias:**
```bash
pip install -r requirements.txt
```

3. **Configura los ajustes:**
Edita `config.py` para personalizar:
- Contraseña para las cuentas
- Configuración de proxies (opcional)
- Configuración del navegador (modo headless, etc.)
- Número de cuentas a crear

## 🚀 Uso

### Uso Básico

```bash
python outlook_account_creator.py
```

El script:
1. Generará nombres y apellidos aleatorios
2. Creará direcciones de correo electrónico de outlook.com
3. Navegará por el proceso de registro de Outlook
4. Manejará los CAPTCHAs y pasos de verificación
5. Guardará las credenciales en `outlook_accounts.csv`

### Con Proxies (Opcional)

1. Crea `proxies.txt` con un proxy por línea:
```
http://ip:port
http://username:password@ip:port
socks5://ip:port
```

2. Habilita los proxies en `config.py`:
```python
USE_PROXIES_FOR_OUTLOOK = True
PROXY_FILE = "proxies.txt"
```

## 📁 Archivos de Salida

### outlook_accounts.csv
Contiene todas las cuentas creadas exitosamente:
```csv
Email,Password,First Name,Last Name
johnsmith1234@outlook.com,Outlook234!,John,Smith
maryjones5678@outlook.com,Outlook234!,Mary,Jones
```

### logs/
- `successful_accounts.log` - Creaciones de cuentas exitosas
- `failed_accounts.log` - Intentos fallidos con detalles de error

### screenshots/
- Capturas de pantalla automáticas capturadas en caso de errores
- Nominadas con el prefijo del correo para facilitar la depuración

## ⚙️ Configuración

### Opciones de config.py

```python
# Password for all accounts
FIXED_PASSWORD = "Outlook234!"

# Browser settings
HEADLESS_MODE = False  # True = run in background
DISABLE_IMAGES = False  # True = faster but may affect CAPTCHAs

# Proxy settings
USE_PROXIES_FOR_OUTLOOK = False  # Enable proxy rotation
PROXY_FILE = "proxies.txt"
PROXY_TYPE = "http"  # or "socks5", "socks4"

# Account limits
TOTAL_ACCOUNTS = None  # None = unlimited, or set a number

# Timing
DELAY_BETWEEN_ACCOUNTS = 2  # Seconds between creations
PAGE_LOAD_TIMEOUT = 30
ELEMENT_WAIT_TIMEOUT = 15
```

## 🛠️ Cómo Funciona

1. **Generación de Nombres**: Genera aleatoriamente nombres y apellidos a partir de listas predefinidas
2. **Creación de Correo**: Combina el nombre con números aleatorios (ej., johnsmith1234@outlook.com)
3. **Automatización del Navegador**: 
   - Inicia el navegador Chrome no detectable
   - Navega a la página de registro de Outlook
   - Completa la información personal
   - Maneja la creación de la contraseña
   - Gestiona los desafíos CAPTCHA
   - Completa los pasos de verificación
4. **Almacenamiento de Datos**: Guarda las credenciales en CSV en tiempo real

## 🐛 Solución de Problemas

### Problemas Comunes

**Problema**: "Chrome version mismatch"
```bash
# Solution: Update undetected-chromedriver
pip install --upgrade undetected-chromedriver
```

**Problema**: Errores "Element not found"
- **Solución**: La estructura del sitio web cambió. Puede ser necesario actualizar selectores en el código
- Intenta ejecutar en modo no headless para ver qué está ocurriendo

**Problema**: Atascado en CAPTCHA
- **Solución**: Se requiere intervención manual
- El script se pausará y esperará a que lo resuelvas
- Alternativa: Usa proxies residenciales para reducir la frecuencia de CAPTCHAs

**Problema**: Límite de velocidad en la creación de cuentas
- **Solución**: 
  - Aumenta `DELAY_BETWEEN_ACCOUNTS`
  - Usa proxies diferentes
  - Usa una VPN y cambia de ubicación

## 📊 Consejos para Mejorar la Tasa de Éxito

Para mejorar la tasa de éxito:
- ✅ Usa proxies residenciales (mejores que los de datacenter)
- ✅ Agrega retardos entre intentos (2-5 segundos)
- ✅ Usa una VPN y rota las ubicaciones
- ✅ Ejecuta en modo no headless inicialmente para depurar
- ✅ Revisa la carpeta de capturas de pantalla para patrones de error
- ✅ Monitorea los registros para puntos de fallo comunes

## ⚠️ Notas Importantes

### Uso Legal y Ético
- Esta herramienta es con fines educativos y necesidades legítimas de automatización
- Asegúrate de cumplir con los Términos de Servicio de Microsoft
- No la uses para spam, fraude o actividades maliciosas
- Respeta los límites de velocidad y las directrices del servicio
- Considera las políticas de creación de cuentas de Microsoft

### Mejores Prácticas
- No crees cuentas demasiado rápido (usa retardos)
- Usa proxies para distribuir las solicitudes
- Mantén una tasa de éxito razonable (no 100 cuentas/hora)
- Almacena las credenciales de forma segura
- Actualiza regularmente las dependencias

### Limitaciones
- Microsoft puede actualizar el flujo de registro (requiere actualizaciones de código)
- Los CAPTCHAs pueden requerir intervención manual
- Puede haber limitación de velocidad basada en IP
- Puede requerirse verificación por teléfono (aleatorio)

## 🤝 Contribuciones

¡Aceptamos contribuciones! Por favor:
1. Haz fork del repositorio
2. Crea una rama de funcionalidad
3. Realiza tus cambios
4. Prueba exhaustivamente
5. Envía un pull request

## 📝 Licencia

Este proyecto es con fines educativos. Úsalo responsablemente y bajo tu propio riesgo.

## 🔗 Dependencias

- `undetected-chromedriver` - Evita la detección de bots
- `selenium` - Automatización del navegador
- `fake-useragent` - Aleatoriza los user agents

## 📧 Soporte

Si encuentras problemas:
1. Revisa la sección de solución de problemas
2. Revisa los registros en la carpeta `logs/`
3. Revisa las capturas en la carpeta `screenshots/`
4. Abre un issue con los detalles

---

**⚠️ Aviso Legal**: Esta herramienta se proporciona "tal cual" con fines educativos. Los usuarios son responsables de cumplir con todas las leyes aplicables y los términos de servicio. Los autores no asumen ninguna responsabilidad por su uso indebido.
