-------------- RESULTADOS LAB 01-------------
1 o impacto da remoçao das palavras é que ele tera mais chances de erro
2 significa que ele ajuda os stopwords ter mais alcance e chance de acerto 
3 a remoçao das palavras genericas evita erros de classificaçao porque elimina o ruido do texto 

-------------RESULTADOS LAB 02-------------------
1- **Precision:** Mede a exatidão das predições. Responde à pergunta: *"Quando o modelo prevê a intenção X, qual é a porcentagem de vezes que ele está correto?"*. Uma precisão baixa indica excesso de falsos positivos.
* **Recall:** Mede a abrangência do modelo. Responde à pergunta: *"De todas as mensagens que eram realmente da intenção X, qual porcentagem o modelo conseguiu capturar?"*. Um recall baixo indica que o modelo está deixando passar muitos casos reais (falsos negativos).
* **F1-Score:** É a média harmônica entre a Precisão e a Revocação. É a métrica mais recomendada para resumir o desempenho geral de uma classe, pois penaliza discrepâncias grandes entre Precision e Recall.

  2- **Diagonal Principal:** Cruzamento correto entre a classe real e a classe prevista pelo modelo (Verdadeiros Positivos). Quanto mais próximos de 100% estiverem os valores contidos ao longo da diagonal principal (do canto superior esquerdo ao inferior direito), maior é a eficiência do classificador.
* **Fora da Diagonal:** Qualquer valor fora da diagonal principal representa uma classificação incorreta (erros de confusão entre as intenções do Chatbot).

  3- A **acurácia** calcula simplesmente a razão entre o total de predições corretas e o total geral de amostras. Ela torna-se uma métrica enganosa em cenários desbalanceados devido ao **paradoxo da acurácia**:


  ----------------RESULTADOS LAB 03------------------

  1-
  import pandas as pd
from sklearn.pipeline import Pipeline
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

dados_rh = {
    'mensagem': [
        'Como solicitar minhas ferias?', 'Quero agendar meu periodo de ferias',
        'Onde baixo meu holerite do mes?', 'Preciso do comprovante de rendimentos',
        'Como cadastrar meu atestado medico?', 'Onde envio o atestado de consulta?',
        'como solicitar uma carta de demissao', 'onde entrego a carta de demissao',
        'quero pedir meu aviso previo', 'como funciona o aviso previo'
    ],
    'intencao': [
        'solicitar_ferias', 'solicitar_ferias',
        'obter_holerite', 'obter_holerite',
        'enviar_atestado', 'enviar_atestado',
        'carta_demissao', 'carta_demissao',
        'solicitar_aviso_previo', 'solicitar_aviso_previo'
    ]
}

df3 = pd.DataFrame(dados_rh)


X = df3['mensagem']
y = df3['intencao']


X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.50, random_state=42, stratify=y
)

pipeline = Pipeline([
    ('vectorizer', TfidfVectorizer(stop_words=['de', 'o', 'meu', 'minhas', 'como', 'onde'])),
    ('classifier', LogisticRegression())
])

pipeline.fit(X_train, y_train)

predicoes = pipeline.predict(X_test)
print(f"Acuracia via Pipeline: {accuracy_score(y_test, predicoes) * 100:.2f}%")

2-A grande vantagem de utilizar o objeto Pipeline no Scikit-Learn é o encapsulamento de todo o fluxo de trabalho de Machine Learning em um único objeto e diminui o vazamento de dados.

3- O Pipeline evita esses erros ao trancar o fluxo de transformação dentro do mesmo processo do modelo. Na prática, ele impede três falhas humanas muito comuns quando o pré-processamento é feito manualmente:
