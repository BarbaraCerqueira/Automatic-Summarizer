# Sumarizador Automático de Texto usando Embeddings

``!`` Este trabalho foi desenvolvido como Trabalho Final da disciplina de Busca e Mineração de Texto (BMT), do período 2024.1 da Universidade Federal do Rio de Janeiro (UFRJ).

``!`` O artigo que apresenta este projeto com maiores detalhes sobre seu desenvolvimento está disponível para leitura em: [https://pt.overleaf.com/read/bfqzshwcgqfb#d26599](https://pt.overleaf.com/read/bfqzshwcgqfb#d26599)

A proposta deste trabalho é desenvolver uma Prova de Conceito no intuito de demonstrar um sumarizador automático de texto capaz de gerar resumos extrativos de documentos usando embeddings para capturar a semântica das frases. Para os testes e avaliação, será utilizado o dataset CNN/DailyMail; ele contém artigos de notícias e seus resumos, e é amplamente utilizado para tarefas de sumarização. 

O pipeline de execução do sumarizador será composto, basicamente, pelas seguintes etapas: 
1. Pré-processamento do texto;
2. Transformar cada frase do texto em um vetor (embedding); 
3. Aplicar clusterização nesses embeddings para agrupar frases contextualmente similares; 
4. Obter as frases mais representativas de cada cluster; 
5. Compor o resumo extrativo a partir das frases obtidas.

```Observações:```

Serão utilizados e testados os seguintes modelos de embedding: ``text-embedding-3-small``, ``text-embedding-3-large`` e ``text-embedding-ada-002`` (OpenAI), ``bert-base-uncased`` (BERT), ``roberta-base`` (RoBERTa), ``paraphrase-MiniLM-L6-v2`` (S-BERT ou Sentence-BERT). Os modelos BERT e RoBERTa foram obtidos através da biblioteca "transformers" da Hugging Face, enquanto o S-BERT veio da "sentence-transformers". Não confundir o S-BERT com o modelo BERT para frases, são diferentes e possuem arquiteturas diferentes.

Para utilizar os modelos da OpenAI é necessário acesso a uma chave de API da OpenAI.

```Instruções de Uso:```

- Descomentar e executar a primeira célula para instalar as dependências necessárias. As bibliotecas que trazem ferramentas de deep learning são bem pesadas e o processo pode demorar. Lembre-se de reiniciar o kernel após isso.
- Descomentar e fazer download do 'punkt' na quarta célula. Ele é necessário para algumas funcionalidades da biblioteca nltk. Talvez também seja necessário reiniciar o kernel após isso.
- Criar um arquivo .env para guardar sua chave de API da OpenAI. O arquivo deve conter uma linha com o seguinte:  ```
        API_KEY = 'SUA-CHAVE-DE-API-OPENAI'
        ```