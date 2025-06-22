
# ✅ Projeto: Codificador de Prioridade com Lógica Invertida  
**Placa: AX301 – FPGA EP4CE6F17C8 (Cyclone IV E)**

## 📌 1. Descrição do Projeto

Este projeto implementa um **Codificador de Prioridade com 4 entradas**, com **lógica invertida nas entradas**, projetado para a placa **AX301**.

- **Entradas (botões, nível baixo = ativo):**  
MNS1, MNS2, MNS3, MNS4

- **Saídas (LEDs):**  
TLD1, TLD2, TLD3

## 📌 2. Estrutura de Pastas Recomendada

```
/seu_projeto/
├── codificador_prioridade.vhd
├── tb_codificador_prioridade.vhd
├── codificador_prioridade.qsf
└── README.md
```

## 📌 3. Passos no Quartus II

### 3.1 Criação do Projeto

1. Abra o Quartus II.
2. Vá em: File → New Project Wizard → Next
3. Escolha a pasta do projeto e o nome (ex: codificador_prioridade).
4. Selecione o dispositivo:  
**Family:** Cyclone IV E  
**Device:** EP4CE6F17C8

### 3.2 Inserção dos Códigos

- Copie o conteúdo de codificador_prioridade.vhd para o seu arquivo principal.
- Copie o conteúdo de tb_codificador_prioridade.vhd para o arquivo de Testbench.

### 3.3 Mapeamento de Pinos (Pin Planner)

| Sinal | Pino | Função Física |
|---|---|---|
| MNS1 | M15 | KEY1 |
| MNS2 | M16 | KEY2 |
| MNS3 | E16 | KEY3 |
| MNS4 | N13 | RESET |
| TLD1 | E10 | LED0 |
| TLD2 | F9  | LED1 |
| TLD3 | C9  | LED2 |

Depois de mapear, salve o .qsf.

### 3.4 Compilação

- No Quartus: Processing → Start Compilation

### 3.5 Geração do .sof

Após a compilação, o arquivo .sof estará na pasta /output_files/.

### 3.6 Programação da FPGA

1. Conecte o USB-Blaster.
2. Vá em Tools → Programmer.
3. Selecione o .sof.
4. Clique em Start.

## 📌 4. Teste no Hardware (Placa AX301)

- Pressione os botões (KEY1 a RESET).
- Veja os LEDs acendendo conforme a prioridade.

## 📌 5. Simulação do Testbench via Terminal (Linux)

### ✅ Opção 1: Usando ModelSim (Modo Console)

```bash
vcom codificador_prioridade.vhd
vcom tb_codificador_prioridade.vhd
vsim -c work.tb_codificador_prioridade -do "run -all; quit;"
```

Se quiser salvar ondas para visualizar depois:

```bash
vsim -c work.tb_codificador_prioridade -do "log -r /*; run -all; write list waves.lst /*; quit;"
```

### ✅ Opção 2: Usando GHDL + GTKWave (Open Source, recomendado no Linux)

**Instalação:**

```bash
sudo apt install ghdl gtkwave
```

**Compile e execute:**

```bash
ghdl -a codificador_prioridade.vhd
ghdl -a tb_codificador_prioridade.vhd
ghdl -e tb_codificador_prioridade
ghdl -r tb_codificador_prioridade --vcd=onda.vcd
```

**Visualizar as ondas:**

```bash
gtkwave onda.vcd
```

## 📌 6. Observações Importantes

- Entradas são ativas em nível lógico baixo (lógica invertida) por causa da eletrônica da AX301.
- Saídas são LEDs: Ligam com nível lógico alto.

## ✅ 7. Arquivos Incluídos no Projeto

- codificador_prioridade.vhd
- tb_codificador_prioridade.vhd
- codificador_prioridade.qsf
- README.md
