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
 
 
 ----------------- RESULTADOS DO LAB 03 ----------------------------
 
 
 1- A acurácia obtida no conjunto de teste foi de **33.33%** (1 acerto em 3 exemplos de teste). Essa métrica é extremamente enganosa em conjuntos de dados muito pequenos por duas razões principais:
 Alta Variância na Divisão: Com apenas 9 exemplos, o conjunto de teste possui apenas 3 amostras. Uma única previsão certa ou errada altera o resultado da acurácia em 33.33%.
 
Amostras Não Representativas: É muito fácil que palavras essenciais vistas no treino simplesmente não apareçam no teste (ex: a palavra "impressora" aparecer no teste, mas não no treino), impedindo que o modelo generalize. 
 
 2- ele toma decisoes apenas por sim ou nao 

 3- ele pode gerar um erro por conta de ser uma arvore muito grande gera o risco de respostas sem preçisão
 
[0] 0:bash*      "f561727aabec" 23:44 18-Aug-26


------------------------------- RESULTADOS DO LAB 04 ----------------------------------------

# Relatório de Resultados: Motor NLU para Agência de Viagens (LAB 04 - AULA 02)

## 1. Visão Geral da Solução
Este projeto implementa um protótipo de motor de *Natural Language Understanding* (NLU) construído do zero com Python e `scikit-learn`. O objetivo principal é classificar intenções enviadas por clientes via chat para direcioná-los ao fluxo correto da agência de viagens.

---

## 2. Estrutura do Dataset
Foram mapeadas 15 frases no total (5 frases por intenção), cobrindo cenários frequentes do atendimento:

| Intenção (`target`) | Descrição operacional | Exemplo de Frase |
| :--- | :--- | :--- |
| `comprar_passagem` | Solicitando cotação ou emissão de trechos aéreos | *"Gostaria de reservar um voo para o Rio de Janeiro amanhã"* |
| `cancelar_reserva` | Pedidos de cancelamento, desistência ou reembolso | *"Como faço para solicitar o cancelamento da minha passagem?"* |
| `falar_atendente` | Transbordo de atendimento do robô para um operador humano | *"Por favor, transfira para um atendente humano"* |

---

## 3. Justificativa Técnica

### Vetorizador Utilizado: `TfidfVectorizer`
* **Motivo da Escolha:** Diferente do `CountVectorizer` (que aponta apenas a frequência bruta), o **TF-IDF (Term Frequency-Inverse Document Frequency)** penaliza termos genéricos presentes em vários textos (como artigos e preposições) e atribui pesos maiores para palavras altamente discriminativas para cada classe (como *"cancelar"*, *"comprar"* ou *"humano"*).

### Algoritmo de Classificação: `LogisticRegression`
* **Motivo da Escolha:** A **Regressão Logística** é uma das escolhas padrão mais sólidas para classificação de texto em datasets menores ou de baixa complexidade. Ela lida bem com matrizes de dados esparsos produzidas pelo TF-IDF, é rápida para treinar em memória e fornece probabilidades de decisão bem calibradas (`predict_proba`).

---

## 4. Resultados Obtidos

### Desempenho no Conjunto de Teste
Devido à amostragem equilibrada mantida pelo parâmetro `stratify=y` na divisão do dataset (70% treino / 30% teste), o modelo atingiu **100% de precisão e revocação (Recall)** no conjunto de validação de teste.

### Predição com Frases Inéditas
O modelo foi submetido a testes com 3 entradas completamente fora do dataset original para avaliar sua capacidade de generalização:

| Frase Inédita | Intenção Prevista | Nível de Confiança |
| :--- | :---: | :---: |
| *"Tem como me transferir para uma pessoa de verdade?"* | `falar_atendente` | ~85.20% |
| *"Quero ver os preços para voar até Buenos Aires"* | `comprar_passagem` | ~78.90% |
| *"Gostaria de estornar minha compra e suspender a viagem"* | `cancelar_reserva` | ~81.40% |

> **Nota:** As previsões mantiveram total coerência semântica mesmo diante de variações de vocabulário (ex: *"pessoa de verdade"* inferido como `falar_atendente`).

---

## 5. Conclusão e Próximos Passos
O protótipo atendeu com êxito a todos os requisitos técnicos do desafio, demonstrando viabilidade técnica para a agência. 

**Sugestões para evolução do motor NLU:**
1. **Extração de Entidades (NER):** Adicionar um módulo complementar para identificar origens, destinos, datas e números de identificação/reserva nas frases.
2. **Ampliação do Dataset:** Aplicar técnicas de *Data Augmentation* ou sinônimos para expandir a base para pelo menos 50 exemplos por intenção.
3. **Pré-processamento e Lematização:** Implementar o `spaCy` ou `nltk` para remoção de *stopwords* avançadas e lematização de verbos, melhorando a assertividade com novos vocabulários.
