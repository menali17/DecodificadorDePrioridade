# Codificador de Prioridade 4x2 em VHDL

Este projeto implementa um codificador de prioridade 4x2 utilizando a linguagem VHDL. O codificador possui quatro entradas (`p0`, `p1`, `p2`, `p3`), onde `p0` tem a maior prioridade e `p3` a menor. As saídas são dois bits (`x1` e `x0`), que representam em binário qual entrada está ativa com maior prioridade, além de um sinal de interrupção (`int`), que indica se pelo menos uma entrada está ativa.

## Tabela Verdade

| p0 | p1 | p2 | p3 | x1 | x0 | int |
|----|----|----|----|----|----|-----|
| 0  | 0  | 0  | 0  |  0 |  0 |  0  |
| 0  | 0  | 0  | 1  |  1 |  1 |  1  |
| 0  | 0  | 1  | 0  |  1 |  0 |  1  |
| 0  | 0  | 1  | 1  |  1 |  0 |  1  |
| 0  | 1  | 0  | 0  |  0 |  1 |  1  |
| 0  | 1  | 0  | 1  |  0 |  1 |  1  |
| 0  | 1  | 1  | 0  |  0 |  1 |  1  |
| 0  | 1  | 1  | 1  |  0 |  1 |  1  |
| 1  | 0  | 0  | 0  |  0 |  0 |  1  |
| 1  | 0  | 0  | 1  |  0 |  0 |  1  |
| 1  | 0  | 1  | 0  |  0 |  0 |  1  |
| 1  | 0  | 1  | 1  |  0 |  0 |  1  |
| 1  | 1  | 0  | 0  |  0 |  0 |  1  |
| 1  | 1  | 0  | 1  |  0 |  0 |  1  |
| 1  | 1  | 1  | 0  |  0 |  0 |  1  |
| 1  | 1  | 1  | 1  |  0 |  0 |  1  |


## Arquivos

- `PriorityEncoder4.vhdl`: Código do componente codificador de prioridade.
- `tb_PriorityEncoder4.vhdl`: Código do testbench para simulação.

## Funcionalidade

- Se múltiplas entradas estiverem em nível alto, a saída corresponde à entrada com **maior prioridade** (`p0 > p1 > p2 > p3`).
- O sinal `int` fica em nível alto (`1`) quando qualquer entrada está ativa, e em nível baixo (`0`) quando todas estão desativadas.

- ## Como Usar no Quartus

1. Abra o **Quartus Prime**.
2. Crie um novo projeto (**File → New Project Wizard**).
3. Adicione os arquivos `.vhdl` ao projeto (**Project → Add/Remove Files in Project**).
4. Defina o top-level entity:
   - Para síntese → `PriorityEncoder4`
   - Para simulação → `tb_PriorityEncoder4`
5. Se desejar simular:
   - Vá em **Tools → Run Simulation Tool → RTL Simulation**.
6. Se desejar sintetizar:
   - Compile (**Start Compilation**) e faça o mapeamento dos pinos no **Pin Planner**.



