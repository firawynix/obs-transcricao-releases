# Firaw — Transcrição OBS (instaladores)

Ao parar a gravação, o OBS Studio transcreve o vídeo sozinho e grava `.txt` e `.srt` na mesma
pasta. Em reunião do Teams ou do Google Meet, sai também quem falou o quê, e a legenda com o nome
de quem fala já abre ligada no player. Tudo roda **local e offline** (whisper.cpp na CPU e o OCR
do Windows): nada sai da máquina.

Site: <https://transcricao.firawynix.com.br>

Este repositório guarda **só os instaladores** publicados nas
[releases](https://github.com/firawynix/obs-transcricao-releases/releases). O código-fonte fica em
repositório privado.

## Qual baixar

| Arquivo | Tamanho | O que traz |
|---|---|---|
| `Instalar-Transcricao-OBS.exe` | ~1,4 MB | aplicativo + scripts; baixa só o que faltar (whisper, modelos, ffmpeg) |
| `Instalar-Transcricao-OBS-Completo.exe` | ~1,6 GB | whisper e modelos dentro; ffmpeg só se faltar |
| `Instalar-Transcricao-OBS-Offline.exe` | ~1,8 GB | tudo dentro, não usa a internet |

Cada instalador vem com um `.sha256` ao lado. Conferir no PowerShell:

```powershell
(Get-FileHash .\Instalar-Transcricao-OBS.exe -Algorithm SHA256).Hash
```

O link <https://github.com/firawynix/obs-transcricao-releases/releases/latest/download/Instalar-Transcricao-OBS.exe>
sempre entrega a versão mais recente.

## Requisitos

Windows 10 ou 11 (64 bits), OBS Studio com suporte a script Lua (o instalador tenta instalar o OBS
pelo `winget` se ele não existir). Não pede administrador. O binário não é assinado: o SmartScreen
pode avisar na primeira execução.

O instalador grava tudo em `%USERPROFILE%\obs-transcricao`, registra o script em todas as coleções
de cena do OBS, põe o microfone na faixa 2 e cria na área de trabalho os atalhos
`Transcrever vídeo` e `Legenda liga-desliga`. Pode rodar de novo: ele reaproveita o que já está
íntegro.

## Componentes de terceiros

- [whisper.cpp](https://github.com/ggml-org/whisper.cpp) (MIT) e os modelos `ggml-large-v3-turbo`
  e `ggml-silero-v5.1.2` de [huggingface.co/ggerganov/whisper.cpp](https://huggingface.co/ggerganov/whisper.cpp).
- [FFmpeg](https://ffmpeg.org) (build GPL de [BtbN/FFmpeg-Builds](https://github.com/BtbN/FFmpeg-Builds)),
  dentro do pacote Offline; o código-fonte correspondente está no repositório do BtbN.
