# 1 - Avaliem os resultados e verifiquem se os resultados foram corretos ou incorretos. Coloque a resposta no arquivo do relatório do laboratório
# 2 - Detectado algum erro, qual seria a maneira mais correta de melhorar o resultado do algoritmo?
# 3 - Detalhe a função do LogisticRegression no algorítmo.

----------------------- resultados -----------------------------
---- RESULTADOS DO LAB 01 ---
1- Mensagem: 'Quero consultar quanto dinheiro tenho' ==> Intenção Predita: [consultar_saldo]
Mensagem: 'Pode me ajudar a fazer um pix?' ==> Intenção Predita: [fazer_pix]
Mensagem: 'Gostaria de cancelar meu cartão de crédito' ==> Intenção Predita: [cancelar_conta]

2- vi que o erro estava em mensagem por nao ter o 'Quero consultar quanto dinheiro tenho' ai coloquei ele em mensagem e depois em intençao coloquei 'consultar_saldo' por que isso era o que a pessoa queria consultar.
 
3- o LogisticRegression ele cria um classificador enquanto o modelo.fit ele treina o classificador depois de tudo o modelo pode ser usado
 
 
 
 ---------------------- RESULTADOS DO LAB 02 ------------------------
 
 1- os resultados foram corretos 
 --- RESULTADOS DO LAB 02 ---
Mensagem de Teste: 'Gostaria de devolver o produto que comprei'
Intenção Predita: troca_devolucao

--- Distribuição de Probabilidades por Classe ---
Classe [duvida_frete]: 27.99%
Classe [rastrear_pedido]: 24.54%
Classe [troca_devolucao]: 47.46%
 
 
 2- nao houve erro.


 3-a funçao Naive Bayes ele cria e treina um modelo de classificador em algoritimo Naive Bayes.
 
 
 
 
 
 
 
 
 
 
 
[0] 0:bash*      "f561727aabec" 23:44 18-Aug-26

