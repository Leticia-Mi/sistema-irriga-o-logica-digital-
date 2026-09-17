# sistema irrigação logica digital 


Sistema de Irrigação Automática com Lógica Digital

Projeto de um Sistema de Irrigação Automática desenvolvido utilizando
circuito de lógica digital e simulado no Tinkercad.

O sistema analisa quatro condições de entrada e decide automaticamente se
deve acionar a bomba de irrigação ou emitir um alerta.


       Objetivo

Desenvolver um circuito lógico capaz de controlar um sistema de irrigação
considerando:

- Condição do solo;
- Presença de chuva;
- Disponibilidade de água;
- Acionamento manual.

O circuito possui duas saídas:

- S1:acionamento da bomba de irrigação;
- S2:acionamento do sistema de alerta.

---

 Entradas do sistema


|Entrada|
-A
-B
-C
-D

|Significado|

-A-Condição do solo

-B-Sensor de chuva

-C-Disponibilidade de água

-D-Controle manual

|Quanto vale|

-A-Solo seco

-B-Está chovendo

-C-Água disponível

-D-Pedido manual ativado


Os valores são representados utilizando lógica binária:

- `0` = condição inativa
- `1` = condição ativa

Por exemplo:

`1010`

representa:

- A = 1 solo seco
- B = 0 não está chovendo
- C = 1 existe água
- D = 0 pedido manual desligado

Nesse caso, a irrigação é acionada automaticamente.


Saídas

S1 — Irrigação

Quando `S1 = 1`:

- LED verde acende;
- Transistor NPN é acionado;
- Motor/bomba é ligado.

S2 — Alerta

Quando `S2 = 1`:

- LED vermelho acende;
- Buzzer é acionado.


   Expressões booleanas

Após a análise da tabela-verdade e simplificação utilizando
Mapa de Karnaugh, foram obtidas as seguintes expressões:

    Saída S1

S1 = AB'C + CD

Onde:

- `AB'C` solo seco, sem chuva e com água disponível;
- `CD` água disponível e pedido manual ativado.

Portanto, a bomba pode ser acionada automaticamente ou manualmente.

   Saída S2

S2 = AC' + C'D

Onde:

- `AC'` solo seco e sem água disponível;
- `C'D` pedido manual realizado sem água disponível.

Nessas situações, o sistema gera um alerta.



    Componentes utilizados

- 1 × CI 74HC04 — portas NOT;
- 2 × CI 74HC08 — portas AND;
- 1 × CI 74HC32 — portas OR;
- 4 × interruptores SPDT;
- LEDs verde e vermelho;
- Resistores de 330 Ω;
- 1 × buzzer;
- 1 × motor CC, representando a bomba;
- 1 × transistor NPN;
- 1 × resistor de 1 kΩ para a base do transistor;
- 1 × diodo de proteção do motor;
- Protoboard;
- Fonte de alimentação de 5 V;
- Jumpers.



     Funcionamento do circuito

As entradas A, B, C e D são controladas através dos interruptores SPDT.

O CI 74HC04 é responsável pelas inversões necessárias:

B → B'

C → C'

Os CIs 74HC08 realizam as operações AND, formando:

AB'C

CD

AC'

C'D

Por fim, o 74HC32 realiza as operações OR:

S1 = AB'C + CD

S2 = AC' + C'D

A saída S1 controla o LED verde e o transistor responsável pelo motor.

A saída S2 controla o LED vermelho e o buzzer.



    Controle da bomba

O motor não é conectado diretamente à saída da porta lógica.

Um transistor NPN é utilizado como chave eletrônica.

A saída S1 chega à base do transistor através de um resistor de 1 kΩ.
Quando S1 assume nível lógico alto, o transistor permite o acionamento
do motor.

Também foi utilizado um diodo de proteção (flyback) em paralelo com o motor.



    Testes

O circuito foi testado utilizando diferentes combinações das quatro
entradas.

Exemplo de irrigação automática:

A = 1
B = 0
C = 1
D = 0

Resultado:

Bomba ligada  
Alerta desligado

Exemplo de alerta:

A = 1
B = 0
C = 0
D = 0

Resultado:

Bomba desligada  
LED vermelho ligado  
Buzzer ligado


        Simulação

O projeto foi desenvolvido e testado utilizando o *Tinkercad Circuits*.

A simulação permitiu verificar o comportamento das portas lógicas,
LEDs, buzzer e motor antes da implementação física do circuito.


       Conceitos utilizados

O projeto aplica conceitos de:

- Álgebra Booleana;
- Sistemas digitais;
- Portas lógicas;
- Tabela-verdade;
- Mapas de Karnaugh;
- Circuitos combinacionais;
- Eletrônica digital;
- Automação.


        Autores

Projeto desenvolvido por:

- Letícia Miranda, Haitla lima, Lilia Maria.


        Status
Circuito lógico desenvolvido  
Tabela-verdade validada  
Mapas de Karnaugh realizados  
Simulação concluída  
LEDs e buzzer funcionando  
Motor/bomba funcionando