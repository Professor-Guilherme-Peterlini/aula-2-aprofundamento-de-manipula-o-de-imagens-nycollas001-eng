# Atividade Prática: Processamento em Escala de Cinza e Detecção de Bordas

## Objetivo
Aprender técnicas avançadas de processamento de imagens usando Python e Pillow, focando em conversão para escala de cinza e detecção de bordas.

## Pré-requisitos
* Python 3.x
* Biblioteca Pillow (`pip install Pillow`)
* Conhecimento básico de processamento de imagens

## Exercício 4: Conversão para Escala de Cinza

### Teoria
A conversão para escala de cinza pode ser realizada por diferentes métodos:
* Média dos canais RGB
* Método por luminosidade (Y = 0.299R + 0.587G + 0.114B)

### Implementação

```python
def converter_escala_cinza(imagem):
    # Método 1: Média simples dos canais
    img_media = imagem.convert('L')
    
    # Método 2: Conversão por luminosidade
    img_luminosidade = imagem.convert('L', matrix=[
        0.299, 0.587, 0.114, 0,
        0.299, 0.587, 0.114, 0,
        0.299, 0.587, 0.114, 0
    ])
    
    return img_media, img_luminosidade
```

## Exercício 5: Detecção de Bordas Avançada

### Teoria
Exploraremos diferentes operadores de detecção de bordas:
* Sobel (gradientes horizontais e verticais)
* Prewitt
* Laplaciano

### Implementação

```python
def detectar_bordas(imagem):
    img_cinza = imagem.convert('L')
    
    # Sobel
    bordas_sobel_h = img_cinza.filter(ImageFilter.Kernel((3, 3), 
        [-1, 0, 1, -2, 0, 2, -1, 0, 1]))
    
    # Prewitt
    bordas_prewitt = img_cinza.filter(ImageFilter.CONTOUR)
    
    # Laplaciano
    bordas_laplace = img_cinza.filter(ImageFilter.Kernel((3, 3),
        [0, 1, 0, 1, -4, 1, 0, 1, 0]))
    
    return {
        'sobel_h': bordas_sobel_h,
        'prewitt': bordas_prewitt,
        'laplace': bordas_laplace
    }
```

## Exercício 6: Pipeline de Processamento

### Implementação

```python
def pipeline_processamento(imagem, limiar=128):
    # Conversão para escala de cinza
    img_cinza = imagem.convert('L')
    
    # Equalização de histograma
    img_equalizada = ImageOps.equalize(img_cinza)
    
    # Detecção de bordas
    img_bordas = img_equalizada.filter(ImageFilter.FIND_EDGES)
    
    # Limiarização
    img_final = img_bordas.point(lambda x: 255 if x > limiar else 0)
    
    return img_final
```

## Avaliação
1. Implementação das funções (40%)
2. Qualidade do código e documentação (30%)
3. Resultados visuais (30%)

## Dicas
* Aplique filtros de suavização antes da detecção de bordas
* Experimente diferentes valores de limiar
* Compare resultados entre os diferentes métodos
* Documente os parâmetros utilizados

## Entrega
* Código fonte comentado
* Imagens processadas
* Relatório comparativo dos métodos
* Análise dos resultados

---
**Autor**: [Nome do Autor]  
**Data**: [24/01/2025]  
**Versão**: 1.1