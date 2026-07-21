# Nexus Legacy

Site institucional de academia desenvolvido em **Flask**, com identidade visual voltada ao fisiculturismo clássico e um assistente de IA integrado (**MyCoach**) para tirar dúvidas sobre treinos e dieta.

> Projeto acadêmico — UNIP, disciplinas de Web e IHC.

---

##  Sobre o projeto

A Nexus Legacy é uma landing page de academia com múltiplas páginas navegáveis, formulário de matrícula e um chatbot com IA (MyCoach) que responde perguntas sobre treinos e nutrição, deixando claro que não substitui acompanhamento profissional.

---

##  Funcionalidades

- **Página inicial** com banner de destaque e apresentação dos serviços
- **História** do fisiculturismo com linha do tempo e lendas do esporte
- **Treinos** divididos por grupo muscular (Peito, Costas, Inferiores, Ombros, Braços), com GIFs demonstrativos
- **Matrícula** com formulário de cadastro e seleção de planos (Black / Premium)
- **MyCoach IA** — chat integrado que responde dúvidas sobre treino e dieta via modelo de linguagem
- Layout responsivo para dispositivos móveis

---

##  Tecnologias utilizadas

- [Flask](https://flask.palletsprojects.com/) — framework web em Python
- [OpenAI SDK](https://github.com/openai/openai-python) (apontando para a [OpenRouter API](https://openrouter.ai/)) — integração com modelos de IA gratuitos
- HTML5 / CSS3 (Poppins & Oswald via Google Fonts)
- JavaScript puro (fetch API, manipulação de DOM)
- [Marked.js](https://marked.js.org/) — renderização de Markdown nas respostas do chat
- [Vercel](https://vercel.com/) — deploy serverless (`@vercel/python`)

---

##  Estrutura do projeto

```
nexuslegacy/
├── api/
│   └── index.py          # Aplicação Flask (rotas e integração com IA)
├── templates/
│   ├── index.html         # Página inicial
│   ├── historia.html       # História do fisiculturismo
│   ├── treinos.html        # Divisão de treinos
│   ├── Cadaspage.html      # Formulário de matrícula
│   └── IA.html             # Chat do MyCoach
├── static/
│   ├── style/
│   │   ├── estilo.css       # Estilo geral do site
│   │   ├── cadaspage.css    # Estilo da página de matrícula
│   │   └── nexusia.css      # Estilo do chat MyCoach
│   └── seets/                # Imagens, ícones e GIFs
├── requirements.txt
├── vercel.json
└── README.md
```

---

##  Rodando localmente

### Pré-requisitos
- Python 3.10+
- Git

### Passo a passo

```bash
# 1. Clone o repositório
git clone https://github.com/kiransilveira-lgtm/nexuslegacy.git
cd nexuslegacy

# 2. Crie e ative um ambiente virtual (opcional, mas recomendado)
python -m venv venv
venv\Scripts\activate      # Windows
source venv/bin/activate   # Linux/Mac

# 3. Instale as dependências
pip install -r requirements.txt

# 4. Configure a variável de ambiente da API (veja seção abaixo)

# 5. Rode o servidor
python api/index.py
```

O site ficará disponível em `http://localhost:5000` (ou na porta configurada pelo Flask).

---

##  Variáveis de ambiente

O chat **MyCoach** depende de uma chave de API da [OpenRouter](https://openrouter.ai/):

| Variável          | Descrição                              |
|-------------------|------------------------------------------|
| `OPENAI_API_KEY`  | Chave de API da OpenRouter, usada pelo SDK da OpenAI apontando para `https://openrouter.ai/api/v1` |

Crie um arquivo `.env` (ou configure diretamente no ambiente/painel da Vercel):

```
OPENAI_API_KEY=sua_chave_aqui
```

>  Nunca faça commit da sua chave de API no repositório.

---

##  Deploy

O projeto está configurado para deploy na **Vercel** via `vercel.json`, utilizando o runtime `@vercel/python` apontando para `api/index.py`.

Para publicar:
1. Faça push do repositório para o GitHub
2. Importe o projeto na Vercel
3. Configure a variável `OPENAI_API_KEY` nas configurações do projeto
4. Deploy 

---

## Rotas disponíveis

| Rota          | Descrição                     |
|---------------|--------------------------------|
| `/`           | Página inicial                 |
| `/historia`   | História do fisiculturismo     |
| `/treinos`    | Divisão de treinos             |
| `/cadastro`   | Formulário de matrícula        |
| `/mycoach`    | Chat com a IA MyCoach          |
| `/perguntar`  | Endpoint (POST) usado pelo chat |

---

##  Licença

Projeto acadêmico desenvolvido para fins de estudo  por mim Kiran (UNIP — Web/IHC). Sem licença comercial definida.
