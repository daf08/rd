import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize
from collections import Counter

# Baixar recursos necessários do NLTK
nltk.download('punkt')
nltk.download('stopwords')

def extrair_palavras_chave(texto):
    # Tokenizar o texto
    palavras = word_tokenize(texto.lower())
    
    # Remover stopwords
    stop_words = set(stopwords.words('portuguese'))
    palavras_filtradas = [palavra for palavra in palavras if palavra.isalnum() and palavra not in stop_words]
    
    # Contar a frequência das palavras
    frequencia = Counter(palavras_filtradas)
    
    # Extrair as 10 palavras-chave mais comuns
    palavras_chave = frequencia.most_common(10)
    
    return palavras_chave

# Exemplo de uso
if __name__ == "__main__":
    texto = """
    A inteligência artificial está transformando o mundo. 
    Com o avanço da tecnologia, as máquinas estão se tornando mais inteligentes e capazes de realizar tarefas complexas.
    """
    
    palavras_chave = extrair_palavras_chave(texto)
    print("Palavras-chave:", palavras_chave)
