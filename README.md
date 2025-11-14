# Análise Biomecânica – Processamento, Cinemática, Cinemática Angular, Músculos e Torque

## Título do Projeto
Análise de Movimento e Cálculo Biomecânico a partir de Dados de Marcadores 2D

## Autora
Nathalia Giovanna Soares da Paz + dois autores


## Descrição
Este projeto implementa um pipeline completo de análise biomecânica em Python, utilizando dados de trajetória capturados por quatro marcadores corporais (punho, cotovelo, ombro e tronco).  
O código realiza:

- Importação e normalização dos dados.
- Cálculo de velocidades, acelerações e ângulos articulares.
- Filtragem dos sinais com filtro Butterworth.
- Animações 2D e polares do movimento.
- Cálculo do comprimento muscular (bíceps e tríceps).
- Cálculo de velocidade e aceleração muscular.
- Cálculo de velocidades e acelerações angulares.
- Estimativa de torque no ombro e cotovelo.
- Estimativa de forças musculares.

Este repositório organiza a implementação desenvolvida durante o projeto de biomecânica, incluindo métodos clássicos da análise cinemática e dinâmica.

## Tecnologias Utilizadas
- Python 3
- NumPy  
- Pandas  
- Matplotlib  
- Matplotlib Animation  
- SciPy (filtro Butterworth)
- ipympl (gráficos interativos em notebook)
- Google Colab (execução original)

## Estrutura Geral do Código

### 1. Importação dos dados
O arquivo `trajetoria_ajustada (m).csv` é carregado e suas colunas são convertidas para vetores numéricos com a função `CriaVetorDados()`.

Marcadores utilizados:
- Mão (Marcador 1)
- Cotovelo (Marcador 2)
- Ombro (Marcador 3)
- Tronco (Marcador 4)

### 2. Normalização espacial
Os dados são normalizados tomando o Marcador 1 (mão) como referência:
`
marcadoresX, marcadoresY = Normalizar(marcadoresX, marcadoresY)`

### 3. Cálculo de velocidade e aceleração

Realizado para todos os marcadores:
`velocidade, aceleracao, angulo = Velocidade(X, Y, t)
`
### 4. Filtragem dos sinais

Utiliza filtro passa-baixa Butterworth de 2 Hz:
`butter_lowpass_filter(data, cutoff, fs)
`

Aplicado a:

Velocidade

Aceleração

Ângulo

Comprimento muscular

### 5. Animações

O código gera animações de:

Velocidade vs tempo.

Gráficos polares (ângulo vs magnitude).

Movimentos segmentares (antebraço, braço, tronco).

Visualização dos arcos articulares (cotovelo e ombro).

Animação completa do movimento com ossos e projeções musculares.

As animações são exportadas como:

velocidade.mp4

animated_vector_with_data.mp4

animacao.mp4

### 6. Comprimento dos músculos

Cálculo contínuo dos comprimentos do:

Bíceps

Tríceps

Utilizando funções geométricas e interpolação em linha:
 `interpolate_on_line()
calculate_length()
`
### 7. Cinemática angular

Cálculo de:

Velocidade angular

Aceleração angular

Aplicado a:

Ombro

Cotovelo

Com filtragem posterior.

### 8. Torque articular

O código implementa dois métodos de cálculo:

Método 1 — Inercial + gravitacional

Usando massa, raio de giro e ângulo articular:

`CalculaTorque(massa, comprimento, raio_giro, aceleracao_angular, angulo_articular)
`
Método 2 — Forças musculares

Usa comprimento dos músculos e momento de braço:
`torque = forca * comprimento * sin(angulo)
` 
Torques gerados:

Torque no cotovelo

Torque no ombro

### 9. Forças musculares

Estimadas por:

Braço de momento médio

Força = massa * aceleração

Torque / braço de momento

Resultados apresentados em gráficos.
