# Demonstração independente do detector de imagens — Fase 3.7

Este repositório público distribui uma demonstração do detector de imagens reais e sintéticas do TCC. O notebook apresenta a probabilidade estimada para cada classe, uma classificação pelo limiar calibrado internamente e uma frase explicativa. Ele não treina o modelo.

**Estado:** o checkpoint da Fase 3.7 foi publicado no Release modelo-fase3-7-v1. O download público foi conferido por tamanho e SHA-256. Para usar a demo, não é necessário Google Drive, conta do grupo ou token.

## Estrutura

| Caminho | Função |
| --- | --- |
| [demo_fase3_7_colab.ipynb](demo_fase3_7_colab.ipynb) | Interface de inferência; contém a arquitetura e analisa imagens anexadas ou colocadas no runtime. |
| [modelo/manifesto.json](modelo/manifesto.json) | Identidade, tamanho, hash e URL do checkpoint congelado. |
| [manutencao/publicar_checkpoint_colab.ipynb](manutencao/publicar_checkpoint_colab.ipynb) | Registro da publicação inicial do modelo; não é necessário para executar a demo. |
| [requirements.txt](requirements.txt) | Dependências para execução local. |

O arquivo de pesos fica em um **asset do GitHub Release**, separado dos arquivos versionados. Nenhum dataset ou token é distribuído.

## Executar no Google Colab

1. [Abra a demo diretamente no Colab](https://colab.research.google.com/github/vicemnovo/TCC_Demo_Imagens_Fase3_7/blob/main/demo_fase3_7_colab.ipynb). Você também pode abrir o notebook no GitHub e escolher a opção de execução no Colab.
2. Se houver GPU disponível, selecione um runtime com GPU. A CPU também funciona, com inferência mais lenta.
3. Execute, na ordem, as cinco primeiras **células de código**: verificação do ambiente, download do checkpoint, definição da arquitetura, funções de inferência e carregamento dos pesos. A célula de download verifica o SHA-256 antes que o arquivo seja carregado.
4. Execute a célula de upload para selecionar imagens JPG, PNG ou WebP no navegador. Para usar o VS Code conectado ao Colab, coloque as imagens em /content/tcc_demo_fase3_7/entrada pelo painel de arquivos do runtime e execute a célula de pasta local. Reexecute somente a célula escolhida para analisar outras imagens.

O notebook pode ser aberto de qualquer computador pelo link acima. O upload no navegador não depende do Drive.

## Executar em Jupyter local

Clone este repositório, instale as dependências de requirements.txt em um ambiente Python compatível e abra demo_fase3_7_colab.ipynb no Jupyter. Execute as cinco primeiras células de código. Coloque as imagens em .cache_demo/entrada e execute a célula de pasta local. A célula de upload usa a interface do Colab e não é necessária em Jupyter local.

O notebook baixa o mesmo checkpoint público para um cache local e confere seu hash. A pasta de imagens e o cache são ignorados pelo Git.

## Modelo e resultado registrado

- Arquitetura: ViT-Tiny, ramo FFT e EfficientNet-B0 com fusão por gate.
- Experimento: fase3_7_cfsmall_expansao_v1.
- Pesos: [baixar checkpoint do Release](https://github.com/vicemnovo/TCC_Demo_Imagens_Fase3_7/releases/download/modelo-fase3-7-v1/fase3_7_cfsmall_expansao_v1_phase3_final.pt).
- Tamanho: 40.628.702 bytes.
- SHA-256: cf3c9305dda7b01d05cef1520437470208b6cb3a8d45a37b4c5bdecd38215062.
- Temperatura e limiar registrados no treinamento interno: aproximadamente 0,459945 e 0,345, respectivamente. A demo lê os valores efetivos do checkpoint; não os ajusta com as imagens enviadas.
- No benchmark externo Mirage de 2.000 imagens já observado, a Fase 3.7 obteve acurácia de 62,3% e AUC de 0,6908315. A meta experimental do TCC era 85% de acurácia e não foi atingida.

A probabilidade apresentada é uma **estimativa do modelo**, não uma prova de origem, autenticidade ou veracidade da cena. A classificação pode estar errada mesmo quando a probabilidade parece alta. O benchmark Mirage já foi observado durante o projeto e não constitui um novo teste cego para esta demo.

## Conferências realizadas nesta publicação

O arquivo fornecido para publicação foi comparado com o SHA-256 registrado da Fase 3.7. O asset público foi baixado sem credenciais: retornou 40.628.702 bytes e o mesmo SHA-256. Os notebooks foram validados como JSON e suas células de código passaram na análise sintática. A inferência completa não foi executada neste computador porque PyTorch e torchvision não estão instalados aqui; execute a sequência acima no Colab para conferir a passagem do modelo com suas imagens.

O repositório original de treinamento e seus resultados históricos permanecem separados.
