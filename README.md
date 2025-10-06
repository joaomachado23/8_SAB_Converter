# 8_SAB_Converter

**Título do projeto**: "Estudos Computacionais sobre Solid-State Transformer (SST)"

O objetivo deste projeto era o desenvolvimento, simulação, conceção de PCB, montagem e testes de um protótipo de conversor baseado numa topologia Single Active Bridge (SAB) para integração em redes híbridas CA/CC. O relatório final contém a motivação, estado-da-arte, requisitos, simulações, design da PCB, processo de montagem, software de controlo e resultados experimentais.

O protótipo foi concebido para operar com as especificações de projeto definidas no relatório: tensão de entrada nominal de 50 V, saída ajustável entre 0–25 V, potência alvo entre 100–300 W, razão de transformação do transformador planar 2:1 e frequência de comutação 200 kHz (simulações em PSIM).

Foram realizadas simulações detalhadas em PSIM (controlo em malha fechada com controlador PI), seguidas do design da PCB (Altium), seleção de componentes de potência (MOSFET SiC, condensadores do barramento CC, bobina do filtro de saída e transformador planar), gate drivers isolados, condicionamento de sinal e fontes de alimentação de controlo. Foi projetada e fabricada a PCB, efetuada a montagem SMT/THT e validado o sistema em bancada.

Principais componentes e escolhas técnicas: uso de MOSFETs SiC (modelo SCT055HU65G3AG), transformador planar PL300-100L para operação em alta frequência, e drivers isolados ADuM4221-1 de meia ponte (High side-Low side) — escolhas justificadas no relatório pelo seu desempenho em alta frequência e pela redução de área/indutância.

O controlo foi implementado num DSP TMS320F28027F (placa LAUNCHXL-F28027F). O firmware (Code Composer Studio) gere a aquisição ADC, cálculo do duty/PWM, comunicação série e lógica de comutação, e foi testado e verificado tanto em simulador como em bancada. O código apresentado no relatório final não é o código aplicado ao protótipo real, dada a ausência do controlador PI: o código final está neste repositório num ficheiro txt.

A equipa conclui que o projeto foi bem-sucedido: as simulações e os testes práticos confirmaram o comportamento esperado, identificando pontos de melhoria (dissipação térmica da ponte retificadora, otimização de componentes) para iterações futuras.

Conteúdos deste repositório:

 - Pasta do projeto da PCB — ficheiros do layout (Altium), esquemáticos, renders 3D e ficheiros de produção (Gerbers). 
 - Apresentação final (PDF) — slides usados na apresentação. 
 - Relatório final (PDF) — documento completo com introdução, estado da arte, requisitos, simulações PSIM, BOM, desenvolvimento da PCB, processo de montagem, software, testes e conclusões.
 - ZIP com o projeto em C (Code Composer Studio) — código fonte para programar o TMS320F28027F na placa LAUNCHXL-F28027F (firmware de controlo) [O código não está atualizado, a versão mais recente está no ficheiro txt].
 - Ficheiro .txt com o código mais recente (versão plain text / auxílio). 
 - Ficheiro de simulação PSIM (.psimsch) — modelo e blocos de controlo usados nas simulações, incluindo o bloco C com o controlador PI.

Este trabalho foi fundamental para explorar novos conceitos de conversores e consolidar conhecimentos previamente abordados na área da eletrónica de potência, com foco no hardware de potência e condicionamento de sinal, e no firmware de controlo. Dadas todas as novidades da topologia, inclusive sendo um conversor galvanicamente isolado, foi um projeto desafiante, sendo concluído posteriormente com sucesso (Avaliação final: 18). Um grande obrigado ao colega que me acompanhou nesta jornada: Diego Brandão.

*Projeto realizado por Diego Brandão e João Machado no âmbito da UC de Projeto Integrador em Engenharia Eletrónica Industrial e Computadores, lecionada no 1º ano do MEEIC. Este projeto consistiu em estudos sobre o uso de um High-Frequency Transformer para fazer a interface de renováveis com uma Hybrid Power Grid (Main AC e DC).*
