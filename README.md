# chatBotByHistory

**Clonar o Repositorio**
```
   https://github.com/CharlesVilela/testDeploy.git

```

**Instalar as dependencias**
Entre no diretório do projeto que você clonou e execute o seguinte comando:


```
    pip install -r requirements

```


**Executar o script**
Após instalar todas as dependências, você poderá executar o script executando o comando abaixo:


```
    streamlit run main.py

```


**Principais tecnologias usadas**

- Python: Linguagem de programação versátil e de alto nível, amplamente utilizada para desenvolvimento web, análise de dados, automação, e inteligência artificial.

- Streamlit: Framework em Python que facilita a criação de aplicativos web interativos e dinâmicos, especialmente voltados para ciência de dados e aprendizado de máquina.

- LangChain: Biblioteca que permite a criação de cadeias de processamento de linguagem natural (NLP) usando modelos de linguagem, facilitando a integração e o uso de modelos como serviços em aplicações.

- langchain_google_genai: Módulo específico da LangChain que integra os modelos de linguagem generativa do Google, permitindo o uso desses modelos em fluxos de trabalho personalizados.

- google.generativeai: Biblioteca Python oficial para acessar os modelos de inteligência artificial generativa do Google, permitindo a criação de conteúdo e interações baseadas em IA em 


**Error que estava dando no chatbot**

```
    Traceback (most recent call last):
  File "C:\Projetos\chatbot4\env\lib\site-packages\streamlit\runtime\scriptrunner\script_runner.py", line 600, in _run_script
    exec(code, module.__dict__)
  File "C:\Projetos\chatbot4\chat.py", line 175, in <module>
    main()
  File "C:\Projetos\chatbot4\chat.py", line 143, in main
    response = process_embeddings2.user_input2(st.session_state.user_question)
  File "C:\Projetos\chatbot4\utils\process_embeddings2.py", line 221, in user_input2
    chat_session.send_message({
  File "C:\Projetos\chatbot4\env\lib\site-packages\google\generativeai\generative_models.py", line 496, in send_message
    response = self.model.generate_content(
  File "C:\Projetos\chatbot4\env\lib\site-packages\google\generativeai\generative_models.py", line 262, in generate_content
    response = self._client.generate_content(
  File "C:\Projetos\chatbot4\env\lib\site-packages\google\ai\generativelanguage_v1beta\services\generative_service\client.py", line 812, in generate_content
    response = rpc(
  File "C:\Projetos\chatbot4\env\lib\site-packages\google\api_core\gapic_v1\method.py", line 131, in __call__
    return wrapped_func(*args, **kwargs)
  File "C:\Projetos\chatbot4\env\lib\site-packages\google\api_core\retry\retry_unary.py", line 293, in retry_wrapped_func
    return retry_target(
  File "C:\Projetos\chatbot4\env\lib\site-packages\google\api_core\retry\retry_unary.py", line 153, in retry_target
    _retry_error_helper(
  File "C:\Projetos\chatbot4\env\lib\site-packages\google\api_core\retry\retry_base.py", line 212, in _retry_error_helper
    raise final_exc from source_exc
  File "C:\Projetos\chatbot4\env\lib\site-packages\google\api_core\retry\retry_unary.py", line 144, in retry_target
    result = target()
  File "C:\Projetos\chatbot4\env\lib\site-packages\google\api_core\timeout.py", line 120, in func_with_timeout
    return func(*args, **kwargs)
  File "C:\Projetos\chatbot4\env\lib\site-packages\google\api_core\grpc_helpers.py", line 78, in error_remapped_callable
    raise exceptions.from_grpc_error(exc) from exc
google.api_core.exceptions.ResourceExhausted: 429 Resource has been exhausted (e.g. check quota).


```


**Resolução**

> A solução que testei foi apagar o `chat_history.db` , aparentemente ele está dando algum conflito com o modelo usado na geração das respostas. Talvez, tenha sido por conta da forma como os dados foram salvos nesse bd.

> A função dele, básicamente era armazenar o historico de conversas do usuário, mas apenas o que o usuário falava e não as perguntas também, como foi a ideia que o senhor comentou. Isso ainda vou implementar.

## Respostas esperadas para a interação com o usuário

### **Interação 1**

Para esta interação, seria a interação básica. Usando apenas texto, onde o usuário realiza uma pergunta digitando no campo de input, por exemplo `Me fale qual é o único bioma totalmente brasileiro?`

#### **Resposta esperada**
E recebe a resposta em formato de texto

<p align="center">
    <img src="https://drive.google.com/uc?id=1ThqPoI4BXZgAD-5xZC0AC53mZTjZ0x8W" alt="resposta de texto" width="500"/>
</p>


### **Interação 2**
Para esta interação, o usuário poderá optar por realizar a pergunta digitando no campo de input, por exemplo `A terra passou por mudanças na sua formação?`

#### **Resposta esperada**
E receber como resposta um audio

<p align="center">
    <img src="https://drive.google.com/uc?id=1HLmavIUoAKOfOxnwitCP-IdMOg63QfFk" alt="resposta de texto" width="500"/>
</p>



### **Interação 3**
O usuário poderá, optar nesta interação por perguntar atrávez da voz. Primeiro clicando no botão `Gravar audio` e fazendo a pergunta `Quem descobriu o brasil?`

 e depois que finalizar a pergunta, clicar no botão `Parar gravação`. Ao fazer isso, o chatbot já vai iniciar o processo para processar a pergunta

#### **Resposta esperada**

Para essa interação ele poderá receber dois formatos possiveis de resposta, a primeira é atráves de `texto` 

<p align="center">
    <img src="https://drive.google.com/uc?id=1kMVhtjctNYkfAiHFCSPfrKK_fe-9YOFu" alt="resposta de texto" width="500"/>
</p>


e a segunda é atráves do `audio`

<p align="center">
    <img src="https://drive.google.com/uc?id=137QWAZMuC1r-B34YGQf5xZ2conWvb7tF" alt="resposta de texto" width="500"/>
</p>





