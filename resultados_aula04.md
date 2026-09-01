--------------------------------------resultados atividade 01-------------------------------------
=== RELATÓRIO DE CLASSIFICAÇÃO ===
                    precision    recall  f1-score   support

logistica_entregas       1.00      1.00      1.00         6
       reclamacoes       1.00      1.00      1.00         6
           suporte       1.00      1.00      1.00         6
 trocas_devolucoes       1.00      1.00      1.00         6
            vendas       1.00      1.00      1.00         6

          accuracy                           1.00        30
         macro avg       1.00      1.00      1.00        30
      weighted avg       1.00      1.00      1.00        30


=== MATRIZ DE CONFUSÃO ===
[[6 0 0 0 0]
 [0 6 0 0 0]
 [0 0 6 0 0]
 [0 0 0 6 0]
 [0 0 0 0 6]]

=== INICIANDO BATERIA DE TESTES (10 INPUTS OBRIGATÓRIOS) ===

[Teste 1/10]
Digite a frase do cliente: palmeiras tem mundial?
Intenção identificada: vendas
Confiança: 100.00%

[Teste 2/10]
Digite a frase do cliente: quero comprar um piano
Intenção identificada: vendas
Confiança: 66.67%

[Teste 3/10]
Digite a frase do cliente: quero comprar umas blusa
Intenção identificada: vendas
Confiança: 66.67%

[Teste 4/10]
Digite a frase do cliente: como deposito meu dinheiro ?
Intenção identificada: logistica_entregas
Confiança: 100.00%

[Teste 5/10]
Digite a frase do cliente: quero arrumar meu celular
Intenção identificada: reclamacoes
Confiança: 66.67%

[Teste 6/10]
Digite a frase do cliente: comprei meu piano e nao recebi ele ainda 
Intenção identificada: reclamacoes
Confiança: 66.67%

[Teste 7/10]
Digite a frase do cliente: quero receber um atendimento humano
Intenção identificada: reclamacoes
Confiança: 100.00%

[Teste 8/10]
Digite a frase do cliente: muito obrigado, voce me ajudou muito
Fallback: confiança abaixo de 50%.
Cliente encaminhado para a equipe humana.

[Teste 9/10]
Digite a frase do cliente: nao estou conseguindo entrar em contato
Intenção identificada: reclamacoes
Confiança: 100.00%

[Teste 10/10]
Digite a frase do cliente: meu mouse chegou muito bem 
Intenção identificada: logistica_entregas
Confiança: 100.00%

--------------------------------------resultados atividade 02-----------------------------------------------
