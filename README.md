# anonterm — Terminal anónima para OSINT en Arch/Linux
====================================================

`anonterm` es un script para lanzar una terminal segura y anónima desde tu sistema real (como Warp o cualquier terminal en Arch Linux). Está diseñado para tareas de OSINT, navegación segura o situaciones donde necesites ocultar tu IP, MAC y evitar dejar rastros en el sistema.

🛡️ Características
------------------

- 🔄 Detecta automáticamente la interfaz de red activa (eth0, wlan0, enpXsY…)
- 🕵️‍♂️ Cambia tu dirección MAC aleatoriamente
- 🧅 Inicia Tor y enruta comandos sensibles por Proxychains
- 🚫 No guarda historial de comandos
- 🧠 Usa tu shell Zsh habitual, con plugins y configuración completa
- 🧼 Restaura la configuración original al salir (MAC, Tor, historial)

📦 Requisitos
-------------

Asegúrate de tener instalados:

```bash
sudo pacman -S tor proxychains-ng macchanger zsh
```

📁 Instalación
--------------

1. Crea un directorio local si no lo tienes:
   ```bash
   mkdir -p ~/bin
   ```

2. Copia el script `anonterm` en `~/bin/anonterm` y hazlo ejecutable:
   ```bash
   chmod +x ~/bin/anonterm
   ```

3. Asegúrate de tener `~/bin` en tu `$PATH`. Añade esto a tu `~/.zshrc` si no lo tienes:
   ```bash
   export PATH="$HOME/bin:$PATH"
   ```

4. Recarga tu Zsh:
   ```bash
   source ~/.zshrc
   ```

▶️ Uso
------

Para lanzar la terminal anónima:
```bash
anonterm
```

Verás mensajes como:

```
[*] Interfaz activa detectada: wlan0
[*] Cambiando MAC...
[*] Iniciando Tor...
[✔] IP anónima actual: 185.x.x.x
[*] Terminal anónima iniciada. Todo el tráfico OSINT irá por Tor.
```

Al salir de la terminal (`exit`), el script:
- Restaura tu MAC real
- Detiene Tor (si lo inició él)
- Borra el historial temporal

🔁 Alias útiles dentro de `anonterm`
------------------------------------

Una vez dentro del entorno, puedes usar comandos comunes con protección automática:

```bash
curl          -> proxychains curl
nmap          -> proxychains nmap
whois         -> proxychains whois
amass         -> proxychains amass
theHarvester  -> proxychains theHarvester
```

💡 Sugerencia
-------------

Usa `anonterm` solo cuando necesites una sesión verdaderamente anónima. Así mantienes tu sistema limpio y tus rastros ocultos.
