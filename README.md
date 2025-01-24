# Entendendo a Imagem Colorida

Uma imagem digital é composta por pontos chamados pixels. Cada pixel contém três componentes:

* **R** - 🔴 Vermelho
* **G** - 🟢 Verde
* **B** - 🔵 Azul

Cada componente varia de:
* `0` = Cor ausente
* `255` = Cor na intensidade máxima

## Processo de Conversão

## Método `convert('L')`

O método `imagem.convert('L')` da biblioteca Pillow converte imagens RGB para escala de cinza usando a fórmula:

```python
L = R * 0.299 + G * 0.587 + B * 0.114
```

## Exemplos de Conversão

| Pixel RGB        | Cálculo                                      | Valor L |
|-----------------|---------------------------------------------|---------|
| RGB(255, 0, 0)  | 255 * 0.299 + 0 * 0.587 + 0 * 0.114 = 76  | 76      |
| RGB(0, 255, 0)  | 0 * 0.299 + 255 * 0.587 + 0 * 0.114 = 150 | 150     |
| RGB(0, 0, 255)  | 0 * 0.299 + 0 * 0.587 + 255 * 0.114 = 29  | 29      |

## Pesos e Percepção

Os pesos utilizados são baseados na sensibilidade do olho humano:
- Verde: 0.587 (mais sensível)
- Vermelho: 0.299 (sensibilidade média)
- Azul: 0.114 (menos sensível)

### O Comando Básico
```python
imagem_pb = imagem.convert('L')  # L = Luminância (brilho)
```

### A Fórmula
```
Valor_Cinza = (Vermelho × 0.30) + (Verde × 0.59) + (Azul × 0.11)
```

## Por que Esses Percentuais?

Nossos olhos têm sensibilidade diferente para cada cor:

| Cor       | Sensibilidade | Percentual |
|-----------|---------------|------------|
| Verde     | Alta          | 59%        |
| Vermelho  | Média         | 30%        |
| Azul      | Baixa         | 11%        |

## Exemplo Prático

Convertendo um vermelho puro:
```
Pixel Original:
🔴 R = 255
🟢 G = 0
🔵 B = 0

Cálculo:
Cinza = (255 × 0.30) + (0 × 0.59) + (0 × 0.11)
Cinza = 76
```

## Resultado Visual
* **Antes**: Pixel colorido 🔴
* **Depois**: Tom de cinza 🌫️ (valor 76)

## Escala Final
* `0` = ⚫ Preto total
* `127` = 🔘 Cinza médio
* `255` = ⚪ Branco total

---
**Nota**: Este método produz imagens em preto e branco que se aproximam da forma como o olho humano percebe o brilho das cores.
