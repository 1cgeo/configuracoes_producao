# EDGV 3.0 Orto: Models QGIS

Modelos construídos para a produção EDGV 3.0 Orto, de acordo com os parâmetros definidos pelo GT Carta Ortoimagem.

Organização dos dados:

## 1. Identifica geometrias inválidas
- arquivo: identifica_geometrias_invalidas_alt_hid_carta_orto.model3
- verificacao separada: elemnat_curva_nivel_l
- camadas: aquisicao_limite_massa_dagua_l,elemnat_trecho_drenagem_l,elemnat_ponto_cotado_p,aquisicao_centroide_massa_dagua_p,aquisicao_centroide_elemento_hidrografico_p,elemnat_elemento_fisiografico_p,elemnat_elemento_fisiografico_l,cobter_massa_dagua_a,infra_barragem_a,infra_barragem_l,elemnat_elemento_hidrografico_l,elemnat_elemento_hidrografico_p,aquisicao_limite_elemento_hidrografico_l
- nome camada flags: geometrias_invalidas

## 2. Identificar geometrias com mais de uma parte
- arquivo: identifica_multipart_alt_hid_carta_orto.model3
- camadas ponto: elemnat_ponto_cotado_p,aquisicao_centroide_massa_dagua_p,aquisicao_centroide_elemento_hidrografico_p,elemnat_elemento_fisiografico_p,elemnat_elemento_hidrografico_p
- camadas linha: aquisicao_limite_massa_dagua_l,elemnat_trecho_drenagem_l,elemnat_curva_nivel_l,elemnat_elemento_fisiografico_l,infra_barragem_l,elemnat_elemento_hidrografico_l,aquisicao_limite_elemento_hidrografico_l
- camadas poligono: cobter_massa_dagua_a,infra_barragem_a
- nome camada flags: geometrias_multipart_p,geometrias_multipart_l,geometrias_multipart_a

## 3. Identificar feições duplicadas
- arquivo: identifica_feicoes_duplicadas_alt_hid_carta_orto.model3
- camadas ponto: elemnat_ponto_cotado_p,aquisicao_centroide_massa_dagua_p,aquisicao_centroide_elemento_hidrografico_p,elemnat_elemento_fisiografico_p,elemnat_elemento_hidrografico_p
- camadas linha: aquisicao_limite_massa_dagua_l,elemnat_trecho_drenagem_l,elemnat_curva_nivel_l,elemnat_elemento_fisiografico_l,infra_barragem_l,elemnat_elemento_hidrografico_l,aquisicao_limite_elemento_hidrografico_l
- camadas poligono: cobter_massa_dagua_a,infra_barragem_a
- black list de atributos: ["id","texto_edicao","label_x","label_y","justificativa_txt","tamanho_txt","visivel","carta_simbolizacao","simbolizar_carta_mini","simb_rot","rotular_carta_mini","espacamento","tamanho_txt","estilo_fonte","cor","cor_buffer","tamanho_buffer","observacao","length_otf"]
- nome camada flags: feicoes_duplicadas_p,feicoes_duplicadas_l,feicoes_duplicadas_a

## 4. Rotinas validade geométrica
- arquivo: rotinas_validade_geometrica_alt_hid.model3
- descrição: rotina que consolida as rotinas 1 a 3. Serve para rodar fora do workflow ou encapsular em alguns casos do workflow.
- nome camada flags: flags_validade_geometrica_p,flags_validade_geometrica_l,flags_validade_geometrica_a

## 5. Identificar vérfice não compartilhado nas intersecções
- arquivo: identifica_vertice_nao_compartilhado_nas_interseccoes_alt_hid_carta_orto.model3
- camadas linha: aquisicao_limite_massa_dagua_l,elemnat_trecho_drenagem_l,infra_barragem_l, elemnat_elemento_hidrografico_l
- camadas poligono: cobter_massa_dagua_a,infra_barragem_a
- nome camada flags: flag_vertice_nao_compartilhado

## 6. Identificar vérfice não compartilhado nos segmentos compartilhados
- arquivo: identifica_vertice_nao_compartilhado_nos_segmentos_compartilhados_alt_hid_carta_orto.model3
- camadas: aquisicao_limite_massa_dagua_l,elemnat_trecho_drenagem_l,cobter_massa_dagua_a,infra_barragem_a,infra_barragem_l,elemnat_elemento_hidrografico_l
- tol: 0.00001 grau
- nome camada flags: flag_vertice_nao_compartilhado_em_seg_compartilhado

## 7. Identificar vérfice próximo de aresta
- arquivo: identifica_vertice_proximo_de_aresta_alt_hid_carta_orto.model3
- camadas: aquisicao_limite_massa_dagua_l,elemnat_trecho_drenagem_l,elemnat_curva_nivel_l,cobter_massa_dagua_a,infra_barragem_a,infra_barragem_l,elemnat_elemento_hidrografico_l
- tol: 0.00001 grau
- nome camada flags: flag_vertice_proximo_aresta

## 8. Identificar geometrias com densidade incorreta de vértices
- arquivo: identifica_geometrias_com_densidade_incorreta_de_vertices_alt_hid_carta_orto.model3
- camadas: aquisicao_limite_massa_dagua_l,elemnat_trecho_drenagem_l,elemnat_curva_nivel_l,cobter_massa_dagua_a,infra_barragem_a,infra_barragem_l,elemnat_elemento_hidrografico_l
- tol: 0.00001 grau
- nome camada flags: flag_densidade_incorreta_vertices

## 9. Identificar ângulos pequenos
- arquivo: identifica_angulos_pequenos_alt_hid_carta_orto.model3
- camadas: aquisicao_limite_massa_dagua_l,elemnat_trecho_drenagem_l,elemnat_curva_nivel_l,cobter_massa_dagua_a,infra_barragem_a,infra_barragem_l,elemnat_elemento_hidrografico_l
- tol: 10 graus
- nome camada flags: flag_angulo_pequeno

## 10. Identificar ângulos pequenos entre camadas
- descrição: Identifica ângulos pequenos entre camadas. Não usa elemnat_elemento_hidrografico_l, pois estes elementos podem estar sobrepostos às drenagens. Curvas de nível também não são utilizadas, pois a verificação de coerência é feita em processo individual.
- arquivo: identifica_angulos_pequenos_entre_camadas_alt_hid_carta_orto.model3
- camadas: aquisicao_limite_massa_dagua_l,elemnat_trecho_drenagem_l,infra_barragem_l
- tol: 10 graus
- nome camada flags: flag_angulo_pequeno_entre_camadas

## 11. Identificar Z
- arquivo: identifica_z_alt_hid_carta_orto.model3
- camadas: aquisicao_limite_massa_dagua_l,elemnat_trecho_drenagem_l,elemnat_curva_nivel_l,cobter_massa_dagua_a,infra_barragem_a,infra_barragem_l,elemnat_elemento_hidrografico_l
- nome camada flags: flag_z

## 12. Rotinas validade de vértices
- arquivo: rotinas_validade_de_vertices_alt_hid.model3
- descrição: rotina que consolida as rotinas 5 a 11. Serve para rodar fora do workflow ou encapsular em alguns casos do workflow.
- nome camada flags: flags_validade_vertices_p,flags_validade_vertices_l

## 13. Identificar overlaps dentro da mesma camada
- arquivo: identifica_overlaps_linhas_alt_hid_carta_orto.model3
- camadas: aquisicao_limite_massa_dagua_l,elemnat_trecho_drenagem_l,elemnat_curva_nivel_l,infra_barragem_l,elemnat_elemento_hidrografico_l,cobter_massa_dagua_a,infra_barragem_a
- nome camada flags: flags_overlaps_l,flags_overlaps_a

## 14. Identificar undershoot com moldura e conexão de linhas
- arquivo: identifica_undershoot_moldura_conexao_linhas_alt_hid.model3
- camadas linha: aquisicao_limite_massa_dagua_l,elemnat_trecho_drenagem_l,elemnat_curva_nivel_l,infra_barragem_l,elemnat_elemento_hidrografico_l
- camadas poligono: cobter_massa_dagua_a,infra_barragem_a
- camada de moldura: aux_moldura_area_continua_a | aux_moldura_a | moldura
- nome camada flags: flags_undershoot_l,flags_undershoot_a

## 15. Identificar linhas segmentadas com mesmo conjunto de atributos
- arquivo: identifica_linhas_segmentadas_com_mesmo_conjunto_de_atributos.model3
- descrição: não roda em curva de nível, pois elas são intencionalmente cortadas.
- camadas: aquisicao_limite_massa_dagua_l,elemnat_trecho_drenagem_l,infra_barragem_l,elemnat_elemento_hidrografico_l
- camada de moldura: aux_moldura_area_continua_a | aux_moldura_a | moldura
- black list de atributos: ["id","texto_edicao","label_x","label_y","justificativa_txt","tamanho_txt","visivel","carta_simbolizacao","simbolizar_carta_mini","simb_rot","rotular_carta_mini","espacamento","tamanho_txt","estilo_fonte","cor","cor_buffer","tamanho_buffer","observacao","length_otf"]
- nome camada flags: flags_linhas_nao_unidas

## 16. Identificar linhas não segmentadas nas intersecções
- arquivo: identificar_linhas_nao_segmentadas_nas_interseccoes_alt_hid.model3
- camadas: elemnat_trecho_drenagem_l
- camadas filtro linha: aquisicao_limite_massa_dagua_l,infra_barragem_l,infra_barragem_l,elemnat_elemento_hidrografico_l
- nome camada flags: flags_drenagens_nao_segmentadas
## 17. Identificar elementos pequenos na rede
- arquivo: identificar_elementos_pequenos_na_rede.model3
- camada: elemnat_trecho_drenagem_l
- tamanho: 1000 m (0.01 grau)
- nome camada flags: flags_linhas_pequenas

## 18. Identificar erros na construção da rede de drenagem
- arquivo: identificar_erros_rede_drenagem.model3
- camadas: elemnat_trecho_drenagem_l
- camadas filtro linha: aquisicao_limite_massa_dagua_l,infra_barragem_l
- black list de atributos: ["id","texto_edicao","label_x","label_y","justificativa_txt","tamanho_txt","visivel","carta_simbolizacao","simbolizar_carta_mini","simb_rot","rotular_carta_mini","espacamento","tamanho_txt","estilo_fonte","cor","cor_buffer","tamanho_buffer","observacao","length_otf"]
- nome camada flags: flags_rede_drenagem

## 19. Identificar erros na construção das curvas de nível
- arquivos:
    - identificar_erros_na_construcao_das_curvas_de_nivel_25k.model3
    - identificar_erros_na_construcao_das_curvas_de_nivel_50k.model3
    - identificar_erros_na_construcao_das_curvas_de_nivel_100k.model3
    - identificar_erros_na_construcao_das_curvas_de_nivel_250k.model3
- camadas: elemnat_curva_nivel_l
- equidistancias:
    - 25k: 10
    - 50k: 20
    - 100k: 40
    - 250k: 100
- black list de atributos: ["id","texto_edicao","label_x","label_y","justificativa_txt","tamanho_txt","visivel","carta_simbolizacao","simbolizar_carta_mini","simb_rot","rotular_carta_mini","espacamento","tamanho_txt","estilo_fonte","cor","cor_buffer","tamanho_buffer","observacao","length_otf"]
- nome camada flags: flags_modelo_p, flags_modelo_l, flags_modelo_a
- camada de moldura: aux_moldura_area_continua_a | aux_moldura_a | moldura

## 20. Fechar Polígonos de Massa D'água (Altimetria e Hidrografia) Carta Orto
- arquivo: fechar_poligonos_massa_dagua.model3
- camadas de flags: delimitadores_nao_utilizados,flags_poligonos,flag_invalida_poligono