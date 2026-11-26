# Integração de Monte Carlo em GPU

Seminário de Programação Paralela e Distribuída (GSI059), da Universidade Federal de Uberlândia.

O projeto propõe implementar a integração de Monte Carlo simples em três versões: serial, OpenMP e CUDA, comparando correção numérica e desempenho. A referência escolhida é a rotina `gsl_monte_plain_integrate`, da GNU Scientific Library (GSL).

## Escopo inicial

- Usar uma integral com solução conhecida para validar as estimativas, mantendo como proposta a função `f(x) = 1 / (1 + x²)` no intervalo `[0, 1]`, cujo valor exato é `π/4`.
- Implementar a versão CUDA pelo grupo, com sorteio usando cuRAND, avaliação da função e combinação das contribuições.
- Comparar serial, OpenMP e CUDA com cargas equivalentes e medições repetidas.
- Apresentar o gráfico de tempo por tamanho da entrada, com OpenMP e CUDA, incluindo barras de erro conforme a proposta da equipe.
- Manter MPI como comparação adicional, se incluído nos testes. MPI não substitui a versão OpenMP exigida.

O repositório contém inicialmente a organização do trabalho. Implementações, comandos de execução e resultados serão incluídos pelas respectivas equipes.

## Estrutura

| Pasta | Conteúdo |
|---|---|
| `serial/` | Referência serial |
| `openmp/` | Implementação com OpenMP |
| `cuda/` | Implementação para GPU NVIDIA com CUDA |
| `testes/` | Scripts, dados medidos e gráficos |
| `docs/` | Plano, mapa de dados, revisões e apresentação |

## Equipe

A divisão de funções está em [docs/equipe.md](docs/equipe.md). O plano de uma página e os prazos serão registrados pelo Lucas. A responsabilidade pela implementação OpenMP ainda precisa ser definida no plano.

## Referência do código

- Biblioteca: GNU Scientific Library (GSL).
- Rotina: `gsl_monte_plain_integrate`.
- Fonte: <https://www.gnu.org/software/gsl/>.
- Versão exata e trecho de origem: a registrar no plano antes da implementação.
- Trabalho MPI anterior: <https://github.com/mariadMariae/seminario-monte-carlo-mpi>.

Os arquivos reutilizados devem manter a indicação de origem e os avisos de licença aplicáveis. Uma implementação CUDA pronta pode servir como referência, mas não será usada como entrega do grupo.

## Fluxo de trabalho

1. Cada entrega deve ter uma issue com responsável e critério de conclusão.
2. Criar uma branch por tarefa, a partir da `main` atualizada.
3. Enviar as alterações por pull request e registrar como foram verificadas.
4. Solicitar revisão de Pedro ou Maria, conforme os arquivos e a autoria.
5. Integrar à `main` somente após aprovação de alguém que não escreveu a alteração.

Os comentários e as revisões dos pull requests registram a revisão. As regras precisam também ser configuradas nas opções de proteção da `main` no GitHub.
