flipper-tools/
├── scripts/
│   ├── prep_flipper_sd.sh
│   ├── postflash_check.sh
│   └── prep_flipper_sd_multifw.sh  (pendiente)
├── blackhat/            # tus scripts Blackhat (local)
├── docs/
│   └── INSTALL.md
├── logs/                # generado por el script (en .gitignore)
└── backups/             # generado por el script (en .gitignore)

# flipper-tools

Colección de utilidades para preparar tarjetas SD y gestionar firmwares/resources para **Flipper Zero**.

Contiene:
- `scripts/prep_flipper_sd.sh` — Script interactivo "Swiss Army Knife" para:
  - detectar y respaldar la SD,
  - preparar una SD FAT32 con los *resources* oficiales de Flipper,
  - opcionalmente añadir scripts de Blackhat,
  - detectar y flashear `.img` / `.img.gz` con `dd`,
  - modo `--noclean` (solo copia, no formatea),
  - logs y comprobaciones post-copy/flash.
- `scripts/prep_flipper_sd_multifw.sh` — (pendiente) script para multi-firmware / flasheo avanzado.
- `scripts/postflash_check.sh` — comprobaciones post-flash (integrado en el primero).
- `blackhat/` — lugar para tus scripts Blackhat (no incluido en repo público por seguridad).
- `docs/` — documentación adicional y guías.

## Requisitos (en Parrot / Debian / Ubuntu)
Instala las utilidades necesarias:

```bash
sudo apt update
sudo apt install -y git rsync parted dosfstools p7zip-full gzip util-linux jq
# opcionales (para flasheo avanzado / fbt):
sudo apt install -y build-essential python3 python3-pip dfu-util

Nota: fbt (Flipper Build Tools) viene en el repo flipperzero-firmware y puede requerir dependencias adicionales. Si ./fbt resources falla, ejecuta esa parte manualmente en el directorio clonado.
