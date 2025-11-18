# Arquitetura de Von Neumann
A Arquitetura de Von Neumann é a base dos computadores modernos e descreve como CPU, memória e periféricos interagem através de barramentos. Entender seus componentes é essencial para compreender o funcionamento do computador e os limites dessa arquitetura.

## Introdução
A Arquitetura de Von Neumann é o modelo estrutural que serviu de base para praticamente todos os computadores modernos. Ela descreve como os principais componentes (CPU, memória e dispositivos de entrada/saída) se organizam e se comunicam para executar programas.

### O que é a Arquitetura de Von Neumann?
É um modelo computacional proposto por John von Neumann na década de 1940, cujo princípio central é que dados e instruções de programa são armazenados no mesmo espaço de memória. Isso permite que o computador leia instruções e dados usando o mesmo mecanismo, tornando o processamento mais flexível e programável.

### Conceito de Programa Armazenado
Antes desse modelo, computadores eram configurados manualmente com fios e interruptores para executar tarefas específicas.
Von Neumann revolucionou isso propondo que:

<img src="./assets/img/eniac-current.webp" alt="ENIAC" width="400">

- As instruções (o programa) e os dados processados pelo programa devem ficar juntos na memória principal.

### Contexto Histórico

- Ano: Década de 1940, durante os avanços da computação pós-Segunda Guerra Mundial.

- Cenário: Computadores gigantes, baseados em válvulas, extremamente difíceis de programar.

- Contribuição de Von Neumann: criação de um documento conhecido como First Draft of a Report on the EDVAC, que descrevia pela primeira vez uma arquitetura lógica para computadores digitais programáveis.


## Gargalo de Von Neumann
Na arquitetura de Von Neumann, a memória é única: nela ficam armazenados

- os dados que o programa manipula, e
- as instruções que dizem à CPU o que fazer.

Como ambos compartilham o mesmo barramento, ocorre uma disputa natural:

- A CPU tenta buscar instruções para executar.
- A CPU também tenta buscar dados necessários para essas instruções.

Mas o barramento não consegue entregar tudo ao mesmo tempo, e isso cria um gargalo, um bloqueio que limita a velocidade do processamento.

<img src="./assets/img/gargalo-de-von-neumann.png" alt="Gargalo de von neumann" width="500">

### Consequência principal
A CPU pode ficar ociosa, esperando a memória responder.

Mesmo sendo extremamente rápida, a CPU depende da memória para continuar o processamento.
Se o fornecimento de dados e instruções é lento, a CPU literalmente para e espera, reduzindo o desempenho total do sistema.

#### Exemplo simplificado
Imagine que o barramento é uma estrada de uma única pista.
Os dados são carros.
As instruções também são carros.

Os dois precisam trafegar na mesma estrada.
Resultado: congestionamento → lentidão → gargalo.

### Impacto no desempenho
- Maior atraso para execução de programas.

- Limitação de velocidade mesmo com CPUs mais rápidas.

- Aumento do tempo total para completar tarefas complexas.

- Dificuldade para acompanhar avanços da CPU sem melhorar a memória e os barramentos.

### Soluções modernas para reduzir o gargalo
Como esse problema é estrutural, a computação moderna desenvolveu várias técnicas para “driblar” ou compensar essa limitação:

#### 1. Memória Cache

- Pequena e muito rápida.
- Fica dentro ou perto da CPU.
- Armazena instruções e dados mais utilizados.
- Reduz a necessidade de acessar a memória RAM toda hora.

Resultado: a CPU passa menos tempo esperando.

#### 2. Barramentos mais rápidos e paralelos
Ex.: DDR4/DDR5, PCIe, canais múltiplos.

Aumentam a largura de banda e diminuem o tempo de espera.

## Unidade Lógica e Aritmética (ULA/ALU)
A ULA (em português) ou ALU, Arithmetic and Logic Unit (em inglês) é um dos componentes centrais da CPU. Ela é responsável por executar todas as operações matemáticas e lógicas necessárias para que o computador funcione.

É dentro da ULA que ocorrem os cálculos e decisões que permitem que um programa avance.

<img src="./assets/img/ula.jpg" alt="ULA" width="500">

### Função principal da ALU
A ULA é responsável por processar dados, realizando:

#### Operações aritméticas:

- Soma (ADD)
- Subtração (SUB)
- Multiplicação (MUL)
- Divisão (DIV)

Algumas CPUs realizam multiplicação e divisão na ULA; outras utilizam unidades específicas, mas seguem a mesma lógica: a ULA é o núcleo do cálculo.

#### Operações lógicas:
Usadas para decisões e comparações.

- AND → retorna verdadeiro se ambos os bits forem 1
- OR → retorna verdadeiro se pelo menos um bit for 1
- NOT → inverte um bit (0 vira 1, e 1 vira 0)
- XOR → verdadeiro se os bits forem diferentes

#### Comparações:
Usadas para permitir desvios e decisões dentro dos programas (if, loops).

- Igualdade (=?)
- Diferente (≠?)
- Maior que (>)
- Menor que (<)
- Maior ou igual (≥)
- Menor ou igual (≤)

Essas comparações retornam valores internos (flags), usados pela CPU para decidir o próximo passo.

### Como a ULA trabalha internamente
A ALU recebe dois tipos de entrada:

- Dados (operandos) – valores vindos da memória ou registradores
- Instruções – comandos enviados pela Unidade de Controle (UC)

A UC diz qual operação a ALU deve executar.
A ALU então realiza o cálculo e devolve o resultado para um registrador, que será usado pela CPU ou pela próxima etapa da instrução.

### Relação entre ULA e UC
A Unidade de Controle (UC) é o "cérebro organizador" da CPU, enquanto a ULA é o "braço executor".

Podemos visualizar assim:

- A UC → interpreta as instruções
- A UC → envia sinais de controle
- A ULA → executa o cálculo
- A ULA → devolve o resultado para a CPU
- A ULA nunca decide o que fazer sozinha, ela sempre age sob comando da UC.

