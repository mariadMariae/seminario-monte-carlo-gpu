# Plano do seminário: Monte Carlo com CUDA

## Escopo

A paralelização, utilizando CUDA, será feita sobre a integração Monte Carlo simples (método PLAIN), com a mesma função f(x) = 1/(1 + x²), x ∈ [0,1], vista em sala de aula, cujo valor exato é π/4. Como a rotina `gsl_monte_plain_integrate` da GSL não roda na GPU, o método será implementado diretamente em CUDA, com números aleatórios gerados pela biblioteca cuRAND. Os resultados serão comparados com as versões serial e MPI, sempre medidas na mesma máquina, para testar a hipótese de que esse tipo de código tende a ter desempenho pior na GPU. A comparação principal usa precisão double, como nas versões anteriores; uma versão mista, com cálculos em float e somas em double, será testada como experimento adicional. Os métodos MISER e VEGAS e o uso de OpenMP não serão contemplados e, portanto, estão fora de escopo.

## Papéis

| Função | Nome | Responsabilidade |
| --- | --- | --- |
| Gestão e planejamento | Lucas Mendes Lacerda e Maria Eduarda Dutra Silva | Lucas: plano e cronograma (até 27/11). Maria: acompanhamento (28/11 a 8/12) |
| Arquitetura paralela | Lucas Mendes Lacerda | Diagrama e texto explicativo da versão CUDA |
| Desenvolvedor I | Joel Silveira Marques Pereira | Kernel: sorteio com cuRAND e cálculo de f(x) |
| Desenvolvedor II | Arthur Rodrigues Cândido | Soma final (f e f²), cálculo da média e do sigma, e medição do tempo por fase (aquecimento, preparação e cálculo) |
| Revisor de Código I | Pedro Tavares Oliveira | Revisão dos pull requests |
| Revisor de Código II | Maria Eduarda Dutra Silva | Revisão dos pull requests |
| Testes I | Giuliano Maradei Carneiro Zacharias | Script de testes da versão CUDA (double e versão mista, com tempo por fase), validado numa máquina com GPU NVIDIA |
| Testes II | Marcos Antônio da Silva Júnior | Execução das versões serial, MPI e CUDA; gráficos com barras de erro; conclusão sobre a hipótese |
| Documentação | Maria Eduarda Dutra Silva | Slides com o material do grupo |
| Apresentação | Todos | Coordenação do seminário |

## Cronograma

| Dia | Atividade | Envolvidos |
| --- | --- | --- |
| Quarta-feira (25/11) | Papéis | Lucas Mendes Lacerda |
| Quinta-feira (26/11) | Cronograma + Arquitetura: diagrama e texto explicativo | Lucas Mendes Lacerda |
| Sexta-feira (27/11) | Revisão da arquitetura com o grupo | Lucas e Maria Eduarda |
| Sábado a quinta (28/11 a 3/12) | Versão CUDA por pull request; revisão dos pull requests | Joel e Arthur; Pedro Tavares e Maria Eduarda |
| Sexta e sábado (4 e 5/12) | Testes CUDA, serial e MPI na mesma máquina | Giuliano e Marcos |
| Domingo e segunda (6 e 7/12) | Slides e ensaio | Maria Eduarda; todos |
| Terça-feira (8/12) | Seminário | Todos |

## Regras

Toda alteração no repositório entra por pull request aprovado por um revisor, e quem escreveu um trecho não revisa esse trecho. Os comentários dos pull requests servem como registro das revisões. As medições oficiais comparam as três versões dentro da mesma máquina; resultados de máquinas diferentes não são comparados entre si.