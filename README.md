# Demo independente do detector de imagens ? Fase 3.7

Este reposit?rio cont?m um notebook de infer?ncia independente do reposit?rio de treinamento. Ele estima a probabilidade de uma imagem ser real ou sint?tica e mostra a classifica??o pelo limiar calibrado internamente.

## Executar de qualquer lugar

Abra demo_fase3_7_colab.ipynb no Google Colab a partir deste GitHub. Execute as c?lulas 1 a 5 na ordem. Para enviar imagens no navegador, execute a c?lula 6. No VS Code ou Jupyter local, coloque JPG, PNG ou WebP em /content/tcc_demo_fase3_7/entrada (Colab) ou .cache_demo/entrada (local) e execute a c?lula 7. CPU funciona, mas GPU ? mais r?pida.

A execu??o normal n?o requer Google Drive, conta do grupo ou token. A c?lula 2 baixa o modelo de um Release p?blico e verifica seu SHA-256 antes do carregamento.

## Publica??o inicial do checkpoint

O asset do Release ainda depende de publica??o ?nica pelo respons?vel pelo Drive. Execute publicar_checkpoint_colab.ipynb no Colab pelo navegador: ele monta o Drive, verifica o hash do modelo da Fase 3.7, solicita um token GitHub de escrita temporariamente, publica o asset e confere o download p?blico. A demo s? funciona depois que esta etapa estiver conclu?da.

Modelo esperado: fase3_7_cfsmall_expansao_v1/phase3_final.pt; SHA-256 cf3c9305dda7b01d05cef1520437470208b6cb3a8d45a37b4c5bdecd38215062. O script n?o substitui assets j? publicados.

## Resultado e limite

No benchmark Mirage de 2.000 imagens j? observado, a Fase 3.7 obteve 62,3% de acur?cia. A meta experimental do TCC era 85% e n?o foi atingida. A probabilidade exibida ? uma estimativa do modelo, n?o prova da origem ou veracidade da imagem.

O notebook reutiliza a arquitetura ViT-Tiny + FFT + EfficientNet-B0 e a infer?ncia da Fase 3.7. N?o distribui datasets ou resultados de treinamento.
