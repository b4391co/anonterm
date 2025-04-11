# **anonterm.sh** — Terminal Privada con Cloudflare WARP

Este script configura una **terminal efímera** en tu sistema que:

- Cambia automáticamente tu **dirección MAC** para mayor privacidad
- Se **conecta automáticamente a Cloudflare WARP** al iniciarse
- **No guarda historial** de comandos ni rastro al salir
- Restaura tu **dirección MAC** y se **desconecta de WARP** cuando sales

---

## 🚀 **Instalación**

2. **Hazlo ejecutable**:

   ```bash
   chmod +x ~/bin/anonterm
   ```

3. **Lánzalo**:

   ```bash
   ./anonterm
   ```

---

## ⚙️ **Cómo Funciona**

- **Inicio**: 
   - Cambia tu **MAC** (al azar) para ocultar la identidad de tu dispositivo.
   - Se conecta a **Cloudflare WARP** para asegurar tu tráfico.
   - Inicia **Zsh** con tu configuración habitual (sin historial guardado).

- **Al Salir**: 
   - Restaura tu **MAC** original.
   - **Desconecta WARP** si lo conectó este script.
   - **Borra el historial de comandos** creado en la sesión.

---

## 🔧 **Requisitos**

Este script requiere que tengas instalados los siguientes programas en tu sistema:

- **Zsh**: Tu shell preferido.
- **Cloudflare WARP**: Asegúrate de tener instalado `warp-cli` y tener acceso a la red WARP.
- **macchanger**: Para cambiar la dirección MAC.

Puedes instalar los requisitos con los siguientes comandos (si no los tienes ya):

```bash
sudo pacman -S zsh macchanger cloudflare-warp-bin
```

---

## 🌐 **Verificación de IP**

Una vez que el script se ejecuta, puedes verificar que tu IP está protegida por WARP con este comando:

```bash
curl https://ifconfig.co
```

Tu IP aparecerá como la proporcionada por Cloudflare WARP, no la de tu red local.

---

## ⚡ **Comandos adicionales**

Puedes también **consultar el estado de WARP** antes de ejecutar el script con:

```bash
warp-cli status
```

---

## 🧹 **Personalización**

Puedes modificar los siguientes parámetros en el script:

- **Dirección MAC predeterminada**: Actualmente el script genera una MAC aleatoria. Si deseas utilizar una MAC estática, puedes modificar la línea que ejecuta `macchanger`.
- **Cambio de configuración de Zsh**: El prompt de Zsh tiene un color temporal (verde o magenta). Puedes personalizarlo según tus preferencias en el archivo `~/.zshrc`.

---

## 🚨 **Notas**

- **El script no realiza cambios permanentes** en tu configuración. Todo es temporal y solo afecta a la sesión de terminal iniciada con el script.
- **WARP y la dirección MAC se restauran al salir**, por lo que no tienes que preocuparte por rastros dejados por el script.

