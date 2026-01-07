<p align="center">
  <img src="https://img.shields.io/badge/Android-8.0+-green?style=for-the-badge&logo=android" />
  <img src="https://img.shields.io/badge/Arch-arm64--v8a-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Root-Required-red?style=for-the-badge&logo=magisk" />
  <img src="https://img.shields.io/badge/ImGui-Overlay-purple?style=for-the-badge" />
</p>

<h1 align="center">Overlay APK</h1>

<p align="center">
  <b>Android overlay nativo com menu ImGui para Standoff 2</b>
</p>

---

## Features

| Feature | Descricao |
|---------|-----------|
| **ESP Box** | Caixas ao redor dos jogadores |
| **ESP Name** | Nome dos jogadores |
| **ESP Health** | Barra de vida |
| **ESP Distance** | Distancia em metros |
| **Snaplines** | Linhas conectando aos jogadores |
| **Head Dot** | Ponto na cabeca |
| **Radar** | Mini-mapa com posicoes |
| **Crosshair** | Mira customizada |

## Como Usar

1. **Instalar** o APK no dispositivo
2. **Abrir** o app
3. **Conceder** acesso root (Magisk)
4. O overlay inicia automaticamente
5. O jogo abre automaticamente
6. Use o menu ImGui para configurar

## Build

### Requisitos

- Android Studio
- NDK (r25+)
- Java 8+

### Compilar

```bash
# Clone o repositorio
git clone https://github.com/0xf0000000/overlay.git
cd overlay

# Build nativo
cd app/src/main/jni
ndk-build

# Copiar binario
cp ../libs/arm64-v8a/draw.sh ../assets/

# Build APK
cd ../../../..
./gradlew assembleDebug
```

### APK gerado
```
app/build/outputs/apk/debug/app-debug.apk
```

## Logs

Filtrar no Android Studio / Logcat:

```bash
adb logcat -s @trickzqw:*
```

## Estrutura

```
app/
├── src/main/
│   ├── java/                    # App Android
│   │   └── MainActivity.java    # Launcher com loading
│   ├── jni/                     # Codigo nativo C++
│   │   ├── src/
│   │   │   ├── main.cpp         # Entry point
│   │   │   ├── ui/              # Menu ImGui
│   │   │   ├── func/            # ESP, Visuals
│   │   │   ├── game/            # Offsets, Player
│   │   │   └── other/           # Memory read
│   │   └── includes/            # ImGui, Draw
│   └── assets/
│       └── draw.sh              # Binario compilado
└── build.gradle
```

## Configuracoes Padrao

Todas as features vem desabilitadas por padrao. Ative no menu:

- `ESP` - Enable ESP
- `Misc` - Radar, Crosshair
- `Settings` - Memory options

## Notas

- Requer root (Magisk recomendado)
- Apenas arm64-v8a
- Android 8.0+ (API 26)
- Testado em Standoff 2

## Disclaimer

Este projeto e apenas para fins educacionais.

---

<p align="center">
  <a href="https://github.com/0xf0000000">0xf0000000</a>
</p>

