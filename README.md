# Testador de Amplificadores Operacionais

## DESCRIÇÃO DO PROJETO

### Problemática:
Não é incomum a ocorrência de erros em aulas de laboratório que envolvem amplificadores operacionais. Em tais situações, o aluno/professor é muitas vezes incapaz de percebe se o problema é do Amp-OP utilizado, que acaba por estragar com facilidade durante as aulas práticas, ou da montagem do circuito feito pelo aluno. Na tentativa de compreender onde está o erro, gasta-se muito do tempo da aula.

### Projeto:
Este projeto visa desenvolver e montar um hardware capaz de testar a funcionalidade de um amplificador operacional, para a facilitação de aulas práticas. Ele será feito para funcionar com os modelos utilizados no IFSC – campus Florianópolis: LM324, LM741, TL082. Se um outro Amp-OP tiver o mesmo pinout de um dos citados, e sua tensão de alimentação maxima não for menor que a utilizada, o hardware também será capaz de testar a funcionalidade deste.

### Flowchart do projeto
![FlowChart](./Imagens/FlowChart.png)

## Desenvolvimento do Projeto

### Componentes
Componente                   | Quantidade
---------------------------  |-------------------
TL7660                       | 1
LM7805                       | 1
LM7905                       | 1
Capacitor Eletrolitico 10 uF | 2
Capacitor Eletrolitico 1 uF  | 2
Capacitor Ceramico 330 nF    | 1
Capacitor Ceramico 100 nF    | 1
Jack Femea P4                | 1
Soquete Zif 40 pinos         | 1

### Alimentação
Foi decidido que o projeto deveria poder alimentar os Amp-OPs com tensões simetricas e assimetricas de 9 e 5 volts. Isso foi feito usando uma fonte de 9V, um tl7660 para criar a tensão negativa, e dois reguladores lineares (o lm7805 e lm7905) para reduzir essas tensões para +/-5V. No final, dois botões farão o controle de qual modelo de aimentação o circuito irá fornecer ao Amp-OP.

Começamos com uma simulação feita no LTspice, utilizando componentes equivalentes aos citados, dado que o LTspice não tem eles.
(Inserir Fotos)

Fizemos então a montagem em protoboard, e fizemos os testes necessarios, para averiguar se as saídas eram como esperavamos.
(Inserir fotos)

Por fim começamos a fazer o esquematico do circuito, utilizando o software Kikad.
(Inserir fotos)

## Referencias
- Ainda não há nenhuma
