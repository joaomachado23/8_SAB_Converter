# 8_SAB_Converter

**Título do projeto**: Estudos Computacionais sobre Solid-State Transformer (SST)

O objetivo deste projeto foi o desenvolvimento, simulação, conceção de PCB, montagem e testes de um protótipo de conversor CC-CC isolado baseado na topologia Single Active Bridge (SAB) para integração em redes híbridas (CA/CC). O relatório final contém a motivação, estado da arte, requisitos, simulações, design da PCB, processo de montagem, software de controlo e resultados experimentais.

Inicialmente, o objetivo do grupo era restringir-se a estudos computacionais sobre o SST global (o sistema completo). Contudo, por opção do grupo de privilegiar uma componente prática, a investigação concentrou-se no estágio intermédio, implementando na prática uma topologia SAB unidirecional para interface de fontes renováveis com uma rede CC. Esta decisão e as suas justificações estão detalhadas no relatório final.

O protótipo foi concebido para operar segundo as especificações definidas no relatório: tensão de entrada nominal de 50 V, saída ajustável entre 0–25 V, potência alvo entre 100–300 W, razão de transformação do transformador planar 2:1 e frequência de comutação 200 kHz (simulações em PSIM).

Foram realizadas simulações detalhadas em PSIM (controlo em malha fechada com controlador PI), seguidas do design da PCB (Altium), seleção de componentes de potência (MOSFET SiC, condensadores do barramento CC, bobina do filtro de saída e transformador planar), gate drivers isolados, condicionamento de sinal e fontes de alimentação de controlo. A PCB foi projetada e fabricada, a montagem SMT/THT realizada e o sistema validado em bancada.

Principais escolhas técnicas: MOSFETs SiC (modelo SCT055HU65G3AG), transformador planar PL300-100L para operação em alta frequência, e drivers isolados ADuM4221-1 em configuração meia-ponte — opções justificadas no relatório pelo desempenho em alta frequência e pela redução de área/indutância.

O controlo foi implementado num DSP TMS320F28027F (placa LAUNCHXL-F28027F). O firmware (Code Composer Studio) gere aquisição ADC, cálculo do duty-cycle a atribuir ao PWM, comunicação série e lógica de comutação; foi testado e verificado em simulação e em bancada. Note-se que o código apresentado no relatório final difere da versão mais recente disponível neste repositório — a versão atualizada encontra-se no ficheiro .txt.

A equipa concluiu que o projeto foi bem-sucedido: as simulações e os testes práticos confirmaram o comportamento esperado, tendo sido identificados pontos de melhoria (por exemplo, dissipação térmica da ponte retificadora e otimização de componentes, bem como aplicação de snubbers para diminuir o ringing e, consequentemente, o stress nos semicondutores) para iterações futuras.

Conteúdos deste repositório:

 - Pasta do projeto da PCB — ficheiros do layout (Altium), esquemáticos, renders 3D e ficheiros de produção (Gerbers). 
 - Apresentação final (PDF) — slides usados na apresentação. 
 - Relatório final (PDF) — documento completo com introdução, estado da arte, requisitos, simulações PSIM, BOM, desenvolvimento da PCB, processo de montagem, software, testes e conclusões.
 - ZIP com o projeto em C (Code Composer Studio) — código fonte para programar o TMS320F28027F na placa LAUNCHXL-F28027F (firmware de controlo) [O código neste ZIP não é a versão mais recente; a versão atualizada está no ficheiro .txt].
 - Ficheiro .txt com o código mais recente (versão plain text / auxílio). 
 - Ficheiro de simulação PSIM (.psimsch) — modelo e blocos de controlo usados nas simulações, incluindo o bloco C com o controlador PI.

Este trabalho foi fundamental para explorar novos conceitos de conversores e consolidar conhecimentos em eletrónica de potência, com foco no hardware de potência, condicionamento de sinal e firmware de controlo. Dada a novidade da topologia e a caraterística de isolamento galvânico do conversor, o projeto foi desafiante e concluído com sucesso (Avaliação final: 18).

Um grande obrigado ao colega que me acompanhou nesta jornada: Diego Brandão.

*Projeto realizado por Diego Brandão e João Machado no âmbito da UC de Projeto Integrador em Engenharia Eletrónica Industrial e Computadores, lecionada no 1º ano do MEEIC. Este projeto consistiu em estudos sobre o uso de um High-Frequency Transformer para fazer a interface de renováveis com uma Hybrid Power Grid (Main AC e DC).*
