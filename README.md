# Testador de Amplificadores Operacionais

## DESCRIÇÃO DO PROJETO

### Problemática:
Não é incomum a ocorrência de erros em aulas de laboratório que envolvem amplificadores operacionais. Em tais situações, o aluno/professor é muitas vezes incapaz de perceber se o problema é do Amp-OP utilizado, que acaba por estragar com facilidade durante as aulas práticas, ou da montagem do circuito feito pelo aluno. Na tentativa de compreender onde está o erro, gasta-se muito do tempo da aula.

### Projeto:
Este projeto visa desenvolver e montar um hardware capaz de testar a funcionalidade de um amplificador operacional, para a facilitação de aulas práticas. Ele será feito para funcionar com os modelos utilizados no IFSC – câmpus Florianópolis: LM324, LM741, TL082. Se um outro Amp-OP tiver o mesmo pinout de um dos citados, e sua tensão de alimentação máxima não for menor que a utilizada, o hardware também será capaz de testar a funcionalidade deste.

### Flowchart do projeto
![FlowChart](./Imagens/FlowChart.png)

## Desenvolvimento do Projeto

O projeto foi desenvolvido em blocos de funcionamento, um a um. Cada um deles seguiu a seguinte sequencia de projeção:
Projeção teorica;
Simulação utilizando softwares como Proteus e LTSpice;
Montagem em protoboard;
Testes e correção de erros;
Desenho do esquemático;

Em seguida foi-se feito um teste com todos os blocos junto, e seguiu-se para a projeção da PCB do circuito.

### Componentes
Componente                   | Quantidade
---------------------------  |-------------------
Jack Fêmea P4                | 1
Soquete Zif 40 pinos         | 1
Relé 12V                     | 1
LED Vermelho                 | 1
LED Verde                    | 14
.                            |
TL7660                       | 1
LM7805                       | 1
LM7905                       | 1
.                            |
Botton Switch DPDT           | 2
Button Switch SPST           | 1
Push Button                  | 1
.                             |
TIC106                       | 1
SS14                         | 1
1N4007                       | 3
BC548                        | 2
BC558                        | 3
2N7002                       | 21
.                            |
Capacitor Eletrolítico 10 uF | 3
Capacitor Eletrolítico 1 uF  | 2
Capacitor Cerâmico 330 nF    | 1
Capacitor Cerâmico 100 nF    | 8
.                            |
Resistor 10M                 | 7
Resistor 50k                 | 19
Resistor 10k                 | 14
Resistor 5k                  | 7
Resistor 100                 | 18
Resistor 30 (5W)             | 1
Resistor 6 (5W)              | 1


### Alimentação
Foi decidido que o projeto deveria poder alimentar os Amp-OPs com tensão simétrica e assimétrica de 9 e 5 volts. Isso foi feito usando uma fonte de 9V, um tl7660 para gerar a tensão negativa, e dois reguladores lineares (o lm7805 e lm7905) para redução das tensões para +/-5V. No final, dois botões farão o controle de qual modelo de alimentação o circuito irá fornecer ao Amp-OP.

A simulação e os testes foram inicialmente feitos sem carga. Após fazermos um teste de carga, percebemos que o tl7660 começa a sofrer grandes alterções na tensão de saída se a corrente fornecida passa de 20 mA. Assim, está definido que esta é a corrente negativa maxima do circuito. Abaixo há uma tabela com os resutados:

Corrente de saída | Tensão de saída do tl7660
------------------|----------------------------
-5,14 mA          | -8,65 V
-6,41 mA          | -8,60 V
-8,50 mA          | -8,30 V
-17,1 mA          | -8,20 V
-25,9 mA          | -7,60 V
-52,0 mA          | -6,65 V

![Esquematico_Entrada](./Imagens/Esquematico_Entrada.png)
![Esquematico_Fonte](./Imagens/Esquematico_Fonte.png)

### Proteção
Foi decidido que o projeto deveria ser capaz de proteger o Amp-OP e a si mesmo em caso de um amplificador curto-circuitado fosse testado. Assim, decidimos que limitariamos a corrente positiva à 100 mA e a negativa à 20mA. Isso foi feito usando transistores (BC548 e BC558) em modo de chaveamento, um tiristor e um relé, junto com um LED de aviso e um botão de reset.

![Esquematico_Proteção](./Imagens/Esquematico_Proteção.png)

### Oscilador e LEDs
Por fim há o teste do Amp-OP. Ele será feito ao colocar o Amp-OP em um soquete ZIF, e ligar o circuito. Um circuito oscilador irá gerar uma onda quadrada que irá piscar os LEDs verdes, indicando seu funcionamento. Para evitar o consumo de corrente do Amp-OP por parte do LED, o que poderia ativar a proteção, utilizamos de MOSFETs na saida, assim utilizando apenas a tensão de saída e não a corrente.

![Esquematico_Oscilador](./Imagens/Esquematico_Oscilador.png)
![Esquematico_LEDs](./Imagens/Esquematico_LEDs.png)
