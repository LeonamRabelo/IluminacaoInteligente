# Sistema de Monitoramento Inteligente com BitDogLab

Este projeto simula um sistema de **monitoramento de ambientes** utilizando a placa **BitDogLab** com o microcontrolador **RP2040**. O sistema monitora a presença de atividade e o nível de iluminação em áreas específicas, utilizando os periféricos embarcados para representar funcionalidades reais de um sistema de segurança ou automação predial.

## 🎯 Objetivo

Criar um sistema capaz de simular o controle de presença e luminosidade em áreas monitoradas, com feedback visual, sonoro e exibição em tela. O joystick é utilizado como entrada analógica para simular sensores de luz e movimento.

---

## 🔍 Descrição Funcional

- O **eixo X do joystick** simula o nível de iluminação da área:
  - Quanto mais distante do centro, maior a intensidade da luz.
  - No centro, simula ausência de luz.
- O **eixo Y do joystick** simula a detecção de presença:
  - Quanto mais distante do centro, há presença detectada.
  - No centro, simula ausência de movimento.
- O sistema entra em **modo de economia de energia** após 2 segundos sem presença detectada:
  - A matriz de LEDs se apaga.
  - O LED vermelho é ativado.
  - O buzzer emite bipes intercalados via PWM.
- A **matriz de LEDs WS2812B** representa áreas monitoradas enumeradas de 0 a 9.
- O **display OLED SSD1306** exibe:
  - Número da área monitorada
  - Intensidade da luz (%)
  - Status da presença ("Sim" ou "Não")
- O **botão A** alterna entre as áreas monitoradas (de 0 a 9).
- O **botão B** alterna entre o modo de visualização do quadrado e o modo de exibição das informações.
- Todos os dados são também transmitidos via UART para visualização em um terminal serial.

---

## 🧰 Uso dos Periféricos da BitDogLab

| Periférico             | Utilização                                                                 |
|------------------------|----------------------------------------------------------------------------|
| **Joystick (ADC)**     | Eixo X: simula controle de luz (intensidade)<br>Eixo Y: simula detecção de movimento |
| **Botão A (com debounce)**    | Alterna entre as áreas monitoradas (0 a 9)                                      |
| **Botão B (com debounce)**    | Alterna o display entre o quadrado e tela de informações                       |
| **Matriz de LEDs WS2812B**   | Representa visualmente a área selecionada com números de 0 a 9                  |
| **Display OLED (I2C)** | Exibe informações da simulação (área, luz, presença) ou o quadrado movimentado |
| **LED Vermelho**       | Indica ausência de movimento (modo economia)                                 |
| **Buzzer (PWM)**       | Emite bipes em modo de economia de energia                                   |
| **UART**               | Mostra logs com área atual, intensidade de luz e status de presença           |
| **Interrupções**       | Responsável pelo acionamento dos botões de forma eficiente                   |
| **Debounce**           | Garante que os botões não gerem múltiplos acionamentos por ruído             |

---

## 📂 Organização do Projeto

- `CondominioRuido.c`: Código-fonte principal
- `inc/ssd1306.h`, `font.h`: Bibliotecas auxiliares para o display
- `ws2812.pio.h`: Programa PIO para controlar a matriz WS2812B

---

## 📌 Tópicos Importantes
Simulação apenas com fins didáticos.

Idealizado com foco em sistemas embarcados e práticas com a placa BitDogLab.

Projeto totalmente desenvolvido em linguagem C com o SDK do RP2040.

---

## 👤 Autor
Leonam Rabelo
Repositório: github.com/LeonamRabelo

**Link para vídeo explicativo:**