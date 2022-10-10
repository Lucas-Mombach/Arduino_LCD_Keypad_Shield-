# Arduino Uno LCD Keypad Shield

## Introdução

## LiquidCrystal
Vamos utilizar a Biblioteca LiquidCrystal para mostar o que quisermos no Display LCD. Mas primeiro precisamos instala-la, já com o Arduino IDE aberto:

![](/includeLib.png)

Agora busque por LiquidCrystal e aperte em instalar:

![](/includeLib2.png)

Depois de instalar a biblioteca devemos inclui-la no nosso codigo:

![](/includeLib3.png)


## Pinos

Com a biblioteca já instalada, devemos ainda saber quais são os pinos que o Shield está conectado, mais detalhes abaixo:

![](https://hackster.imgix.net/uploads/attachments/869014/untitled_mu5aKDOZ1V.png?auto=compress%2Cformat&w=1280&h=960&fit=max)


## Hello World

Agora para utilizar-mos a função mais primordial do Display LCD copie o codigo a seguir, leia com atenção, algumas alterações devem ser feitas.

```
// inclue a Biblioteca LiquidCrystal
#include <LiquidCrystal.h>

// inicaliza associando um lcd aos pinos
// Esses são os pinos que o Shield está ligado no arduino
const int rs = 12 , en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2; // lembre-se do que aprendemos na seção sobre os pinos
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);

void setup() {
  // set up the LCD's number of columns and rows:
  lcd.begin(16, 2);
  // O comando abaixo imprime no Display LCD a mensagem desejada
  lcd.print("Ola Mundo");
}

void loop() {
  // define o cursos para a coluna 0 e linha 1
  // Lembre-se que as linhas são contadas a partir do 0, logo vai a mensagem vai aparecer na segunda linha
  lcd.setCursor(0, 1);
  // imprime na tela o tempo decorrido desde a execução:
  lcd.print(millis() / 1000);
}
```

## Botões

## Exemplo

## Referencias

[Using 1602 LCD Keypad Shield w/ Arduino w/ Examples](https://create.arduino.cc/projecthub/electropeak/using-1602-lcd-keypad-shield-w-arduino-w-examples-e02d95).

[TECLADO ANALÓGICO COM LCD KEYPAD SHIELD | Curso de Arduino #076](https://www.youtube.com/watch?v=onDpyWKSJuI&list=WL&index=2&t=13s&ab_channel=WRKits).
