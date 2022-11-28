# Arduino Uno LCD Keypad Shield

## Introdução

O LCD Keypad Shield nos permite desenvolver uma série de projetos que precisem de input e output visual, como relogios, menus e jogos simples. 
Nesse tutorial você aprenderá: 

* Um pouco mais sobre o LCD Keypad Shield
* Como imprimir texto no Display LCD
* Como usar o Keypad do Shield

##Informações Tecnicas


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

Preste especial atenção a ultima linha da tabela, todos os botões estão conectados no mesmo pino, para mais detalhes vá ao tópico Botões.

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
  // define a quantidade de colunas e linhas do LCD
  lcd.begin(16, 2);
  // O comando abaixo imprime no Display LCD a mensagem desejada
  lcd.print("Ola Mundo");
}

void loop() {
  // define o cursos para a coluna 0 e linha 1
  // Lembre-se que as linhas são contadas a partir do 0, logo vai a mensagem vai aparecer na segunda linha
  lcd.setCursor(0, 1);
  // imprime na tela a Ola Mundo em Inglês
  lcd.print(Hello World);
}
```

## Botões

Todos os botões são conectados em um único pino analogico e atraves de um resistor, cada botão é diferenciado pela tensão lida no analogRead(A0). Para entender melhor analise o exemplo a seguir. Ele foi retirado [desse post](https://create.arduino.cc/projecthub/electropeak/using-1602-lcd-keypad-shield-w-arduino-w-examples-e02d95), fiz algumas alterações para melhor compreensão :

#### Exemplo
```
/*
Arduino 2x16 LCD - Detect Buttons
modified on 18 Feb 2019
by Saeed Hosseini @ Electropeakd
https://electropeak.com/learn/
*/

#include <LiquidCrystal.h>

//LCD pin to Arduino
const int pin_RS = 8; 
const int pin_EN = 9; 
const int pin_d4 = 4; 
const int pin_d5 = 5; 
const int pin_d6 = 6; 
const int pin_d7 = 7; 

const int pin_BL = 10; 

LiquidCrystal lcd( pin_RS,  pin_EN,  pin_d4,  pin_d5,  pin_d6,  pin_d7);

void setup() {
  
  lcd.begin(16, 2); // declara as dimensões do display

  lcd.setCursor(0,0);

  lcd.print("Electropeak.com");
  lcd.setCursor(0,1);
  lcd.print("Press Key:");
}

void loop() {
  int x;
  x = analogRead (0);
  lcd.setCursor(10,1); //Coluna 10,linha 1(começando do 0)
  // os intervalos a seguir são onde geralmente se encontram a tensão lida no analogRead(A0) após precionar cada botão 
  if (x < 60) { // 
    lcd.print ("Right ");
  }
  else if (x < 200) {
    lcd.print ("Up    ");
  }
  else if (x < 400){
    lcd.print ("Down  ");
  }
  else if (x < 600){
    lcd.print ("Left  ");
  }
  else if (x < 800){
    LCD.print ("Select");
  }
}

```

Pode ocorrer problemas com os valores especificos devido a variação de marcas do Shield, por isso, se o codigo acima não funcionar altere os valores.



## Referencias

[Using 1602 LCD Keypad Shield w/ Arduino w/ Examples](https://create.arduino.cc/projecthub/electropeak/using-1602-lcd-keypad-shield-w-arduino-w-examples-e02d95).

[TECLADO ANALÓGICO COM LCD KEYPAD SHIELD | Curso de Arduino #076](https://www.youtube.com/watch?v=onDpyWKSJuI&list=WL&index=2&t=13s&ab_channel=WRKits).

[Como utilizar o Display LCD Shield com Teclado para Arduino](https://www.filipeflop.com/blog/como-utilizar-o-display-lcd-shield-com-teclado-para-arduino/).
