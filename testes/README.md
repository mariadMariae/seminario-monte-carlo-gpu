# Testes e desempenho

- Giuliano prepara o script de verificação CUDA e valida com alguém que tenha GPU NVIDIA.
- Marcos executa os experimentos, produz os gráficos com barras de erro e redige a conclusão.

## Registros necessários

- Versão testada: serial, OpenMP ou CUDA; MPI pode ser incluído como comparação adicional.
- Commit, comandos, compilador, bibliotecas e configuração de hardware.
- Quantidade total de amostras, sementes, threads e configuração CUDA.
- Tempos de cada repetição, média e medida de dispersão usada nas barras de erro.
- Resultado da integral e critério de validação numérica.
- Definição da região cronometrada, indicando se inclui preparação do gerador, alocações, cópias e cálculo.

O gráfico obrigatório compara tempo de execução por tamanho da entrada entre OpenMP e CUDA. Identificar a referência de cada speedup. Distinguir o erro estatístico da integral da variação dos tempos entre repetições.

Guardar as medições em `dados/` e os gráficos em `graficos/`. Não registrar resultados simulados como medições de execução.
