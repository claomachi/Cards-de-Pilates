# Sistema de Agentes para Geração de Cards de Exercícios de Pilates com Google Gemini

Este projeto utiliza um sistema multiagente construído com a SDK do Google Gemini e o Google Agent Development Kit (ADK) para gerar "cards" informativos sobre exercícios de Pilates. Os cards são projetados para serem usados em aplicativos móveis e contêm instruções detalhadas e adaptadas para diferentes níveis de praticantes: iniciante, intermediário e avançado.

## 📖 Descrição

O objetivo principal é automatizar a criação de conteúdo de alta qualidade para exercícios de Pilates. O sistema recebe o nome de um exercício como entrada e, através de uma cadeia de agentes especializados, pesquisa informações, planeja o conteúdo, redige os cards e revisa o material final.

## ✨ Funcionalidades

O sistema é composto por quatro agentes principais, cada um com uma responsabilidade específica:

1.  **Agente Buscador (`agente_buscador`)**:
    * Utiliza a ferramenta de busca do Google (`Google Search`).
    * Coleta informações confiáveis de até 10 sites relevantes sobre o exercício de Pilates solicitado, focando em execução segura e detalhes técnicos.

2.  **Agente Planejador (`agente_planejador`)**:
    * Baseia-se nas informações coletadas pelo Agente Buscador.
    * Utiliza a ferramenta `Google Search` para refinar a pesquisa.
    * Cria um plano de conteúdo detalhado, identificando os pontos mais importantes para a execução do exercício em três níveis: iniciante, intermediário e avançado.
    * Define um passo a passo e os aspectos a serem abordados nos cards.

3.  **Agente Redator (`agente_redator`)**:
    * Utiliza o plano de conteúdo gerado pelo Agente Planejador.
    * Redige os cards para o aplicativo mobile, mantendo o nome original do exercício e usando linguagem em português.
    * Cada card deve incluir:
        * `titulo`: Nome do exercício.
        * `base`: Informações de nível básico.
        * `topicos`: Lista de como realizar o exercício.
        * `modificacoes`: Detalhes sobre variações (se aplicável).
        * `progressoes`: Detalhes para progressões para níveis intermediário e avançado (se aplicável).
        * `erros_comuns`: Erros comuns e seus ajustes para cada nível.
    * Enfatiza a respiração e os músculos trabalhados.
    * Formata cada card com marcadores `***INÍCIO DO CARD***` e `***FIM DO CARD***`.

4.  **Agente Revisor (`agente_revisor`)**:
    * Analisa os cards redigidos pelo Agente Redator.
    * Verifica clareza, concisão, correção gramatical e o tom do conteúdo, assegurando que seja preciso e informativo para um público exigente.
    * Se o rascunho estiver adequado, aprova-o. Caso contrário, aponta os problemas e sugere melhorias.

## ⚙️ Como Funciona

1.  O usuário é solicitado a inserir o nome de um exercício de Pilates.
2.  O **Agente Buscador** pesquisa informações online sobre o exercício.
3.  O **Agente Planejador** utiliza essas informações para estruturar o conteúdo dos cards para diferentes níveis de dificuldade.
4.  O **Agente Redator** cria os cards com base no plano, detalhando a execução, progressões e erros comuns.
5.  O **Agente Revisor** avalia a qualidade dos cards, garantindo que atendam aos padrões estabelecidos.
6.  Os resultados de cada agente são impressos no console.

## 🚀 Tecnologias Utilizadas

* **Python 3.x**
* **Google Gemini API**: Para acesso aos modelos de linguagem generativa do Google.
    * `google-genai`
* **Google Agent Development Kit (ADK)**: Para construir e orquestrar os agentes.
    * `google-adk`
* **Google Search**: Utilizado como ferramenta pelos agentes para coleta de informações.
* **IPython.display**: Para formatação da saída no ambiente Colab (e potencialmente outros notebooks).

## 🛠️ Pré-requisitos

* Python 3.7 ou superior.
* Uma chave de API do Google Gemini.

## 📦 Instalação e Uso

1.  **Clone o repositório (se aplicável):**
    ```bash
    git clone [https://github.com/seu-usuario/seu-repositorio.git](https://github.com/seu-usuario/seu-repositorio.git)
    cd seu-repositorio
    ```

2.  **Instale as dependências:**
    O código original usa `%pip` para instalação em ambientes como Google Colab. Para um ambiente local, você pode usar:
    ```bash
    pip install google-genai google-adk requests
    ```
    *(Observação: `requests` e `json` são importados, mas `json` não é explicitamente usado nas funções principais dos agentes. `textwrap` e `datetime` são da biblioteca padrão.)*

3.  **Configure sua Chave de API do Google Gemini:**
    O script original carrega a chave da API do `google.colab.userdata`. Para executar localmente, você precisará definir a variável de ambiente `GOOGLE_API_KEY`:
    ```bash
    export GOOGLE_API_KEY="SUA_CHAVE_API_AQUI"
    ```
    Ou modifique o script para carregar a chave de outra forma (por exemplo, de um arquivo `.env` ou diretamente no código - **não recomendado para produção**).
    ```python
    # Exemplo de modificação no script (substitua pela sua lógica de carregamento de chave):
    # import os
    # os.environ["GOOGLE_API_KEY"] = "SUA_CHAVE_API_AQUI"
