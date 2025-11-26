# 🐧 ThinkBook 13s G4 ARB - Linux Setup Guide

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Fedora](https://img.shields.io/badge/Fedora-40+-blue.svg)](https://getfedora.org/)
[![Nobara](https://img.shields.io/badge/Nobara-Compatible-purple.svg)](https://nobaraproject.org/)

**English** | [Español](#español)

Complete setup guide and configuration resources for running Linux on the Lenovo ThinkBook 13s G4 ARB. This repository serves as a central hub linking specialized configuration projects and providing additional setup information.

---

## 📋 Table of Contents

- [Hardware Information](#-hardware-information)
- [Specialized Repositories](#-specialized-repositories)
- [BIOS Configuration](#-bios-configuration)
- [Known Issues & Solutions](#-known-issues--solutions)
- [Useful Resources](#-useful-resources)

---

## 💻 Hardware Information

### Model Specifications
- **Model**: Lenovo ThinkBook 13s G4 ARB
- **Processor**: AMD Ryzen (varies by configuration)
- **Audio**: Realtek ALC287 (PCI Subsystem ID: 17AA:3844)
- **Fingerprint Reader**: FPC 10a5:9800 (may vary by model)
- **Display**: 13.3" (resolution varies by config)
- **Wi-Fi**: (check with `lspci | grep -i network`)
- **Bluetooth**: (check with `lsusb | grep -i bluetooth`)

### Verify Your Hardware
```bash
# Check audio chipset
lspci | grep -i audio

# Check fingerprint reader
lsusb | grep -i fingerprint

# Check full hardware info
sudo lshw -short
```

---

## 🔗 Specialized Repositories

### 🎵 Audio Configuration - EasyEffects Profiles
**Repository**: [thinkbook-13s-g4-easyeffects](https://github.com/mintriago123/thinkbook-13s-g4-easyeffects)

Optimized audio profiles extracted from the official Realtek driver, converted for EasyEffects on Linux.

**What it includes:**
- 5 professionally tuned audio profiles (Game, Movie, Music, Universal, Voice)
- Based on Dolby Atmos tuning from official Windows drivers
- Plug-and-play installation

**Quick Install:**
```bash
# Install EasyEffects
sudo dnf install easyeffects  # Fedora/Nobara
sudo apt install easyeffects  # Ubuntu/Debian

# Clone and install profiles
git clone https://github.com/mintriago123/thinkbook-13s-g4-easyeffects.git
cd thinkbook-13s-g4-easyeffects
mkdir -p ~/.config/easyeffects/output
cp profiles/*.json ~/.config/easyeffects/output/
```

---

### 🔐 Fingerprint Reader Driver
**Repository**: [FPC-10a5-9800-Fedora-Nobara](https://github.com/mintriago123/FPC-10a5-9800-Fedora-Nobara)

Modified installation scripts for the FPC 10a5:9800 fingerprint reader, adapted for Fedora/Nobara from the original Ubuntu driver.

**What it includes:**
- Modified installation scripts for Fedora-based systems
- Complete step-by-step installation guide
- Troubleshooting tips

**Quick Install:**
```bash
# Verify you have the FPC fingerprint reader
lsusb | grep 10a5:9800

# Clone repository
git clone https://github.com/mintriago123/FPC-10a5-9800-Fedora-Nobara.git
cd FPC-10a5-9800-Fedora-Nobara

# Follow the detailed instructions in the repository README
```

---

## ⚙️ BIOS Configuration

Recommended BIOS settings for optimal Linux compatibility:

### Essential Settings
1. **Secure Boot**: `Disabled` (required for fingerprint driver)
2. **Boot Mode**: `UEFI`
3. **Fast Boot**: `Disabled` (for dual-boot)

### Optional Settings
- **Battery Conservation Mode**: Configure based on your usage
- **USB Always On**: Configure based on your needs

### Access BIOS
- Press `F2` or `Fn + F2` during boot
- Or: `Shift + Restart` → Troubleshoot → UEFI Firmware Settings

---



---

## 🐛 Known Issues & Solutions

### Audio Issues

#### No Sound or Low Volume
1. Install EasyEffects profiles (see [Audio Configuration](#-audio-configuration---easyeffects-profiles))
2. Check PipeWire status:
```bash
systemctl --user status pipewire pipewire-pulse wireplumber
```
3. Restart audio services:
```bash
systemctl --user restart pipewire pipewire-pulse wireplumber
```

#### Crackling or Distorted Audio
- Use the "Universal" profile for daily use
- Lower the system volume to 80-90%
- Check for conflicting audio applications

---

### Fingerprint Reader

#### Reader Not Detected
1. Verify BIOS settings (Secure Boot disabled)
2. Check device presence:
```bash
lsusb | grep -i fingerprint
```
3. Reinstall driver following the [FPC repository](https://github.com/mintriago123/FPC-10a5-9800-Fedora-Nobara) instructions

#### Fingerprint Enrollment Fails
- Clean the fingerprint sensor
- Try different fingers
- Re-enroll in GNOME Settings → Users → Fingerprint Login

---





---

## 📚 Useful Resources

### Official Documentation
- [Lenovo Support Page](https://pcsupport.lenovo.com/)
- [Arch Wiki - Lenovo Laptops](https://wiki.archlinux.org/title/Laptop/Lenovo)
- [Fedora Documentation](https://docs.fedoraproject.org/)
- [Nobara Project](https://nobaraproject.org/)

### Community Resources
- [r/Fedora](https://reddit.com/r/Fedora)
- [Fedora Discussion](https://discussion.fedoraproject.org/)
- [ThinkBook Linux Users](https://forums.lenovo.com/)

---

## 🤝 Contributing

Found a solution to an issue? Have an optimization tip? Contributions are welcome!

1. Fork this repository
2. Create a branch (`git checkout -b feature/new-tweak`)
3. Commit your changes (`git commit -m 'Add new optimization'`)
4. Push to the branch (`git push origin feature/new-tweak`)
5. Open a Pull Request

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- **Audio Profiles**: Extracted from official Realtek drivers
- **Fingerprint Driver**: Modified from Lenovo's Ubuntu driver, based on [Lukáš Maňák's tutorial](https://lukan.cz/)
- **Community**: Thanks to all Linux on ThinkBook users who share their experiences

---

## ⚠️ Disclaimer

These configurations and scripts are provided "as is" without warranty of any kind. Always backup your data before making system changes. The author is not responsible for any hardware or software damage.

---

# Español

---

## 📋 Tabla de Contenidos

- [Información del Hardware](#-información-del-hardware)
- [Repositorios Especializados](#-repositorios-especializados)
- [Configuración del BIOS](#-configuración-del-bios)
- [Problemas Conocidos y Soluciones](#-problemas-conocidos-y-soluciones)
- [Recursos Útiles](#-recursos-útiles)

---

## 💻 Información del Hardware

### Especificaciones del Modelo
- **Modelo**: Lenovo ThinkBook 13s G4 ARB
- **Procesador**: AMD Ryzen (varía según configuración)
- **Audio**: Realtek ALC287 (PCI Subsystem ID: 17AA:3844)
- **Lector de Huellas**: FPC 10a5:9800 (puede variar según modelo)
- **Pantalla**: 13.3" (resolución varía según config)
- **Wi-Fi**: (verificar con `lspci | grep -i network`)
- **Bluetooth**: (verificar con `lsusb | grep -i bluetooth`)

### Verifica tu Hardware
```bash
# Verificar chipset de audio
lspci | grep -i audio

# Verificar lector de huellas
lsusb | grep -i fingerprint

# Información completa del hardware
sudo lshw -short
```

---

## 🔗 Repositorios Especializados

### 🎵 Configuración de Audio - Perfiles EasyEffects
**Repositorio**: [thinkbook-13s-g4-easyeffects](https://github.com/mintriago123/thinkbook-13s-g4-easyeffects)

Perfiles de audio optimizados extraídos del driver oficial de Realtek, convertidos para EasyEffects en Linux.

**Qué incluye:**
- 5 perfiles de audio profesionalmente ajustados (Juegos, Películas, Música, Universal, Voz)
- Basados en la optimización Dolby Atmos de los drivers oficiales de Windows
- Instalación plug-and-play

**Instalación Rápida:**
```bash
# Instalar EasyEffects
sudo dnf install easyeffects  # Fedora/Nobara
sudo apt install easyeffects  # Ubuntu/Debian

# Clonar e instalar perfiles
git clone https://github.com/mintriago123/thinkbook-13s-g4-easyeffects.git
cd thinkbook-13s-g4-easyeffects
mkdir -p ~/.config/easyeffects/output
cp profiles/*.json ~/.config/easyeffects/output/
```

---

### 🔐 Driver del Lector de Huellas
**Repositorio**: [FPC-10a5-9800-Fedora-Nobara](https://github.com/mintriago123/FPC-10a5-9800-Fedora-Nobara)

Scripts de instalación modificados para el lector de huellas FPC 10a5:9800, adaptados para Fedora/Nobara desde el driver original de Ubuntu.

**Qué incluye:**
- Scripts de instalación modificados para sistemas basados en Fedora
- Guía completa paso a paso
- Consejos de solución de problemas

**Instalación Rápida:**
```bash
# Verificar que tienes el lector FPC
lsusb | grep 10a5:9800

# Clonar repositorio
git clone https://github.com/mintriago123/FPC-10a5-9800-Fedora-Nobara.git
cd FPC-10a5-9800-Fedora-Nobara

# Seguir las instrucciones detalladas en el README del repositorio
```

---

## ⚙️ Configuración del BIOS

Configuraciones recomendadas del BIOS para compatibilidad óptima con Linux:

### Configuraciones Esenciales
1. **Secure Boot**: `Deshabilitado` (requerido para el driver de huellas)
2. **Modo de Arranque**: `UEFI`
3. **Fast Boot**: `Deshabilitado` (para arranque dual)

### Configuraciones Opcionales
- **Modo de Conservación de Batería**: Configurar según tu uso
- **USB Always On**: Configurar según tus necesidades

### Acceder al BIOS
- Presiona `F2` durante el arranque

---



---

## 🐛 Problemas Conocidos y Soluciones

### Problemas de Audio

#### Sin Sonido o Volumen Bajo
1. Instalar perfiles de EasyEffects (ver [Configuración de Audio](#-configuración-de-audio---perfiles-easyeffects))
2. Verificar estado de PipeWire:
```bash
systemctl --user status pipewire pipewire-pulse wireplumber
```
3. Reiniciar servicios de audio:
```bash
systemctl --user restart pipewire pipewire-pulse wireplumber
```

#### Audio Entrecortado o Distorsionado
- Usar el perfil "Universal" para uso diario
- Bajar el volumen del sistema al 80-90%
- Verificar aplicaciones de audio en conflicto

---

### Lector de Huellas

#### Lector No Detectado
1. Verificar configuración del BIOS (Secure Boot deshabilitado)
2. Verificar presencia del dispositivo:
```bash
lsusb | grep -i fingerprint
```
3. Reinstalar driver siguiendo las instrucciones del [repositorio FPC](https://github.com/mintriago123/FPC-10a5-9800-Fedora-Nobara)

#### Falla el Registro de Huellas
- Limpiar el sensor de huellas
- Probar con diferentes dedos
- Re-registrar en Configuración de GNOME → Usuarios → Inicio de sesión con huella

---





---

## 📚 Recursos Útiles

### Documentación Oficial
- [Página de Soporte de Lenovo](https://pcsupport.lenovo.com/)
- [Arch Wiki - Laptops Lenovo](https://wiki.archlinux.org/title/Laptop/Lenovo)
- [Documentación de Fedora](https://docs.fedoraproject.org/)
- [Proyecto Nobara](https://nobaraproject.org/)

### Recursos de la Comunidad
- [r/Fedora](https://reddit.com/r/Fedora)
- [Discusión de Fedora](https://discussion.fedoraproject.org/)
- [Usuarios Linux de ThinkBook](https://forums.lenovo.com/)

---

## 🤝 Contribuir

¿Encontraste una solución a un problema? ¿Tienes un consejo de optimización? ¡Las contribuciones son bienvenidas!

1. Haz fork de este repositorio
2. Crea una rama (`git checkout -b feature/nuevo-ajuste`)
3. Haz commit de tus cambios (`git commit -m 'Agregar nueva optimización'`)
4. Haz push a la rama (`git push origin feature/nuevo-ajuste`)
5. Abre un Pull Request

---

## 📜 Licencia

Este proyecto está licenciado bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para más detalles.

---

## 🙏 Agradecimientos

- **Perfiles de Audio**: Extraídos de drivers oficiales de Realtek
- **Driver de Huellas**: Modificado del driver de Ubuntu de Lenovo, basado en el [tutorial de Lukáš Maňák](https://lukan.cz/)
- **Comunidad**: Gracias a todos los usuarios de Linux en ThinkBook que comparten sus experiencias

---

## ⚠️ Descargo de Responsabilidad

Estas configuraciones y scripts se proporcionan "tal cual" sin garantía de ningún tipo. Siempre haz respaldo de tus datos antes de hacer cambios en el sistema. El autor no es responsable de ningún daño de hardware o software.
