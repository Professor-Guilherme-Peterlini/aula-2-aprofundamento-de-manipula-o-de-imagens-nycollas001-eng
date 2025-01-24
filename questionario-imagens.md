# Questionário Teórico: Processamento de Imagens com Python

## Instruções
* Responda todas as questões de forma clara e concisa
* Justifique suas respostas quando solicitado
* Tempo estimado: 45 minutos

## Questões

### Parte 1: Conceitos Básicos

1. (2,0 pontos) Explique a diferença entre os métodos de redimensionamento de imagem:
   * Nearest Neighbor: pega o pixel mais próximo, sem suavização
   * Bilinear: cria uma imagem mais suave, mas com possível desfoque
   * Bicubic: faz uma imagem mais suave e nítida so mais lenta
   
2. (1,5 pontos) Por que é importante fazer backup das imagens originais antes de aplicar transformações? Cite dois cenários onde isso é crítico.

 R: Perda de Qualidade ao Redimensionar ou Comprimir: não fazendo o backup pode acabar Perdendo a Qualidade fazendo Muitas transformações como por exenplo redimensionamento ou compressão
 podem degradar a qualidade da imagem se você não tiver a original, pode ser dificio recuperar os detalhes perdidos.

 R: Erro na Transformação ou Edição: pode ocorrer um erro que distorce a imagem de maneira inesperada. Sem o backup você perderia o estado original da imagem e precisaria começar do zero ou tentar corrigir com base em uma versão já alterada.

### Parte 2: Escala de Cinza

3. (2,0 pontos) Compare os dois métodos de conversão para escala de cinza vistos em aula:
   * Média simples dos canais RGB
   * Método por luminosidade (Y = 0.299R + 0.587G + 0.114B)
   
   Por que o segundo método é considerado mais preciso para a percepção humana?
   
   R: porque leva em consideração a forma como o olho vê as cores e a luminosidade, resultando em uma percepção mais realista

4. (1,5 pontos) Em processamento de imagens, por que frequentemente convertemos uma imagem para escala de cinza antes de aplicar outros algoritmos?

### Parte 3: Detecção de Bordas

5. (2,0 pontos) Explique o funcionamento dos seguintes operadores de detecção de bordas:
   * Sobel
   * Prewitt
   * Laplaciano

6. (1,5 pontos) Na função `pipeline_processamento()` implementada, por que aplicamos equalização de histograma antes da detecção de bordas?

### Parte 4: Aplicação Prática

7. (2,0 pontos) Considere o seguinte trecho de código:
```python
img_bordas = img_equalizada.filter(ImageFilter.FIND_EDGES)
img_final = img_bordas.point(lambda x: 255 if x > limiar else 0)
```
   * Qual o propósito da segunda linha?
   * Como a escolha do valor de limiar afeta o resultado final?

8. (2,5 pontos) Descreva um pipeline completo para:
   * Detectar bordas em uma imagem com ruído
   * Justifique cada etapa do processo
   * Explique como você escolheria os parâmetros

## Critérios de Avaliação
* Precisão técnica (40%)
* Clareza na explicação (30%)
* Capacidade de relacionar conceitos (30%)

## Bônus (1,0 ponto extra)
Proponha uma modificação no pipeline de processamento que poderia melhorar os resultados em imagens com baixo contraste.
---
**Autor**: [Guilherme Tavares]  
**Data**: [24/01/2025]  
**Versão**: 1.1
