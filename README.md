# 🎹 Mini Piano com Joystick e FreeRTOS

Este projeto implementa um **Mini Piano Interativo** usando Arduino, joystick, buzzer e um display LCD 16x2. O sistema é multitarefa, controlado pelo **FreeRTOS**, e permite **tocar notas musicais**, **gravar sequências** e **reproduzi-las** automaticamente com feedback visual e sonoro.

## 🎯 Objetivo

Permitir que o usuário interaja com um sistema musical através de um joystick, tocando diferentes notas, gravando sequências e reproduzindo automaticamente — tudo em tempo real, com controle de tarefas assíncronas usando o FreeRTOS.

## 🛠️ Componentes Utilizados

- Arduino Uno/Nano
- Joystick analógico (2 eixos + botão)
- Buzzer (saída sonora)
- Display LCD 16x2 (usando `LiquidCrystal`)
- Biblioteca FreeRTOS para Arduino
- Protoboard e fios

## 🧩 Funcionalidades

- 🎵 **Tocar notas musicais** ao mover o joystick:
  - CIMA → C
  - CIMA DIREITA → D
  - DIREITA → E
  - BAIXO → F
  - BAIXO ESQUERDA → G
  - ESQUERDA → A
  - CIMA ESQUERDA → B

- 📼 **Gravação** de sequência de notas:
  - 1 clique no botão → Inicia ou finaliza a gravação

- 🔁 **Reprodução automática**:
  - 2 cliques rápidos → Reproduz a sequência gravada

- 📺 **LCD** exibe:
  - Nota atual
  - Frequência da nota (em Hz)
  - Modo de operação: NORMAL, GRAVANDO ou PLAY

## ⚙️ Organização das Tarefas (FreeRTOS)

- `taskInterface`: Atualiza o display LCD com a nota atual e o modo.
- `taskJoystick`: Detecta a direção e clique do joystick e envia comandos.
- `taskSom`: Recebe a nota da fila e toca no buzzer.
- `taskReproducao`: Reproduz as notas gravadas quando o modo PLAY é ativado.

## 🧠 Conceitos Envolvidos

- Multitarefa com **FreeRTOS**
- Comunicação entre tarefas com **filas** (`xQueue`)
- Exclusão mútua com **mutex** (`xSemaphore`)
- Controle de estados (`NORMAL`, `GRAVANDO`, `REPRODUZINDO`)
- Detecção de múltiplos cliques (1x e 2x) no botão do joystick
- Mapeamento direcional do joystick para notas musicais

## ▶️ Como Usar

1. Faça upload do código no Arduino.
2. Movimente o joystick para tocar notas musicais.
3. Pressione o botão **1 vez** para iniciar ou parar a gravação.
4. Pressione o botão **2 vezes rapidamente** para reproduzir a sequência gravada.
5. Observe o LCD para acompanhar o modo e nota atual.

## 📌 Observações

- O buzzer reproduz a nota durante 500 ms.
- O LCD é atualizado a cada 250 ms.
- A fila de gravação tem capacidade para 50 notas.
- A reprodução reenvia os índices das notas à fila de som e os reinsere na fila de gravação, permitindo repetições.

---

## 📷 Montagem

![Visão geral](Montagem.heif)

---

## 📷 Video Ilustrando

![Video de Exemplo](https://drive.google.com/file/d/1_IjcnxcwU_l-pyCUBajQsjXOCKP3EbEg/view?usp=drive_link)

---

## 🤝 Contribuição

Contribuições são bem-vindas! Sugestões de melhorias incluem:
- Suporte a reprodução contínua
- Salvamento em EEPROM
- Adição de efeitos sonoros ou mais oitavas

---
