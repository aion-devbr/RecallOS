<div align="center">
  <img
    src="https://github.com/user-attachments/assets/aa171a4c-074c-4082-b3d1-c70f5f7f2aca"
    alt="Marca da base original XMem"
    width="100%"
  />
</div>

<div align="center">
  <h1>RecallOS</h1>
  <p><strong>Memória persistente para agentes de IA</strong></p>
  <p>Uma camada de memória para ajudar agentes e aplicações de IA a preservar contexto entre conversas, ferramentas e sessões.</p>

<img src="https://img.shields.io/badge/python-3.11+-blue?logo=python&logoColor=white" alt="Python 3.11+"/>

<img src="https://img.shields.io/badge/license-BSD--3--Clause-green" alt="Licença BSD 3-Clause"/>

<img src="https://img.shields.io/badge/FastAPI-00C7B7?logo=fastapi&logoColor=white" alt="FastAPI"/>

<br/>

<img src="https://img.shields.io/badge/LangGraph-6C47FF?logo=langchain&logoColor=white" alt="LangGraph"/>

<img src="https://img.shields.io/badge/Rust-Weaver-b7410e?logo=rust&logoColor=white" alt="Weaver em Rust"/>

<img src="https://img.shields.io/badge/Multi--LLM-Gemini%20%7C%20Claude%20%7C%20GPT%20%7C%20Bedrock%20%7C%20Ollama-orange" alt="Suporte a vários provedores de LLM"/>

</div>

<hr>

<p align="center">
  <a href="README.md">Português (Brasil)</a> &nbsp;&bull;&nbsp;
  <a href="README.zh-CN.md">简体中文</a> &nbsp;&bull;&nbsp;
  <a href="README.ja.md">日本語</a> &nbsp;&bull;&nbsp;
  <a href="README.hi.md">हिन्दी</a>
</p>

<p align="center">
  <a href="#demo">Demonstração</a> &nbsp;&bull;&nbsp;
  <a href="#recursos">Recursos</a> &nbsp;&bull;&nbsp;
  <a href="#arquitetura">Arquitetura</a> &nbsp;&bull;&nbsp;
  <a href="#benchmarks">Benchmarks</a> &nbsp;&bull;&nbsp;
  <a href="#inicio-rapido">Início rápido</a> &nbsp;&bull;&nbsp;
  <a href="#configuracao">Configuração</a> &nbsp;&bull;&nbsp;
  <a href="#contribua">Contribua</a> &nbsp;&bull;&nbsp;
  <a href="ROADMAP.md">Roteiro</a>
</p>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/chart?repos=aion-devbr/RecallOS&type=date&theme=dark&legend=top-left" />
  <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/chart?repos=aion-devbr/RecallOS&type=date&legend=top-left" />
  <img alt="Histórico de estrelas do RecallOS" src="https://api.star-history.com/chart?repos=aion-devbr/RecallOS&type=date&legend=top-left" />
</picture>

## Retomada do projeto

O RecallOS está sendo retomado publicamente a partir da base aberta do XMem, originalmente publicada por XortexAI. Estamos revisando o código, a documentação, as dependências, as integrações e os procedimentos de teste para atualizar o projeto de forma gradual.

**Status:** projeto público em retomada. Os recursos, comandos e resultados descritos abaixo vêm da base existente e ainda precisam ser revalidados nesta nova etapa. Consulte os arquivos do repositório e as discussões abertas antes de usar qualquer parte em produção.

Alguns nomes internos, caminhos e comandos ainda usam `xmem`. Eles serão mantidos enquanto a compatibilidade estiver sendo avaliada. Os avisos de direitos autorais e a licença original estão preservados nos arquivos do projeto.

Acompanhe o [roteiro público](ROADMAP.md), as [mudanças registradas](CHANGELOG.md) e as orientações para [contribuir](CONTRIBUTING.md).

## O que é o RecallOS?

Aplicações de IA muitas vezes não preservam contexto entre conversas, ferramentas ou provedores. O RecallOS busca oferecer uma camada de memória persistente que permita armazenar, organizar e recuperar informações ao longo do tempo.

A base XMem trata a memória como um processo ativo: agentes especializados classificam informações, identificam o que deve ser guardado ou atualizado e encaminham cada tipo de dado ao mecanismo adequado. A arquitetura também inclui recuperação com síntese de respostas e referências às fontes.

Este repositório está em retomada. As descrições de comportamento abaixo documentam a implementação herdada e serão atualizadas conforme cada parte for revisada e validada.

## Demonstração

A demonstração a seguir pertence à base original e pode não representar a versão atual do RecallOS:

https://github.com/user-attachments/assets/8e3349ab-63c9-4046-821d-ca8097948440

## Recursos

### Extensão para Chrome

A extensão da base XMem integra memória persistente ao ChatGPT, Claude, Gemini, DeepSeek e Perplexity.

**Busca e inserção de contexto** — enquanto você escreve, a extensão procura informações relevantes e pode inseri-las no campo de texto.

**Salvamento em segundo plano (Xingest)** — após o envio de uma mensagem, um processo assíncrono registra a conversa e extrai fatos e resumos.

https://github.com/user-attachments/assets/97793cf9-d247-4d02-9c31-3cc9bbbf89aa

### Plugins para agentes

A pasta [plugin/](plugin/) contém integrações da base XMem para assistentes de programação: [Claude Code](plugin/xmem-claude/), [Codex](plugin/xmem-codex/), [Cursor](plugin/xmem-cursor/), [Hermes](plugin/xmem-hermes/), [OpenClaw](plugin/xmem-openclaw/) e [OpenCode](plugin/xmem-opencode/).

Esses plugins permitem consultar memórias existentes, guardar conhecimento do projeto e compartilhar contexto entre sessões. As chaves de API devem ser fornecidas por variáveis de ambiente ou pelos mecanismos de segredos de cada cliente.

### Importação de contexto

O recurso de contexto permite importar uma conversa existente sem copiar e colar cada mensagem manualmente.

Na implementação original, é possível fornecer um link compartilhado do ChatGPT, Claude ou Gemini para extrair as mensagens e incorporá-las ao índice. Também é possível enviar uma transcrição em texto, Markdown ou JSON. Há parsers para exportações do Cursor e do Antigravity, além de uma alternativa baseada em LLM para outros formatos.

https://github.com/user-attachments/assets/4ff22405-b7ad-4b78-9189-9a6e3ebd5e40

### Scanner de repositórios

O Scanner indexa repositórios Git e cria um grafo consultável do código. Depois da indexação, é possível fazer perguntas em linguagem natural sobre arquivos, funções, dependências e impactos de mudanças.

https://github.com/user-attachments/assets/f0fd393e-3820-404b-8d0e-e452e1dd52d0

### Classificação por domínio

A arquitetura herdada classifica cada informação recebida e a encaminha para um domínio especializado:

<table>
  <tr>
    <th>Domínio</th>
    <th>O que armazena</th>
    <th>Exemplo</th>
    <th>Armazenamento</th>
  </tr>
  <tr>
    <td><strong>Perfil</strong></td>
    <td>Preferências, identidade e fatos duradouros sobre a pessoa</td>
    <td><em>“Prefiro Go a Python para back-end”</em></td>
    <td>Pinecone</td>
  </tr>
  <tr>
    <td><strong>Temporal</strong></td>
    <td>Eventos associados a datas e períodos</td>
    <td><em>“Fui promovido ontem”</em></td>
    <td>Neo4j</td>
  </tr>
  <tr>
    <td><strong>Resumo</strong></td>
    <td>Conclusões condensadas de conversas</td>
    <td><em>“Falamos sobre migrar de REST para gRPC”</em></td>
    <td>Pinecone</td>
  </tr>
  <tr>
    <td><strong>Código</strong></td>
    <td>Anotações, problemas e explicações ligadas a símbolos</td>
    <td><em>“Esta lógica de repetição pode ter uma condição de corrida”</em></td>
    <td>Neo4j + Pinecone</td>
  </tr>
  <tr>
    <td><strong>Trechos</strong></td>
    <td>Padrões e utilitários de código pessoais</td>
    <td><em>“Este é meu padrão de tratamento de erros em Go”</em></td>
    <td>Pinecone</td>
  </tr>
  <tr>
    <td><strong>Imagens</strong></td>
    <td>Observações e descrições visuais</td>
    <td><em>Captura de um diagrama de arquitetura</em></td>
    <td>Pinecone</td>
  </tr>
</table>

### Recuperação com agentes

Na implementação original, a recuperação pode combinar diferentes buscas em vez de depender de uma única consulta vetorial:

1. **Seleção de ferramentas** — o modelo analisa a pergunta e escolhe buscas de perfil, eventos, resumos, trechos ou código.
2. **Síntese** — os resultados são reunidos e usados para produzir uma resposta com referências às fontes.

### Integração com vários provedores de LLM

A base inclui integrações com Gemini, Claude, OpenAI, OpenRouter, Amazon Bedrock e Ollama, com uma ordem configurável de alternativas:

```text
gemini -> claude -> openai -> bedrock -> ollama
```

O provedor e o modelo usados dependem da configuração. A disponibilidade e o funcionamento de cada integração ainda serão verificados durante a retomada.

### Execução local

A base inclui opções de execução local com Ollama para LLMs, FastEmbed para embeddings e Chroma ou SQLite para armazenamento vetorial:

```bash
pip install -e ".[local]"
```

## Arquitetura

<img width="1536" height="1024" alt="Diagrama da arquitetura herdada do XMem" src="https://github.com/user-attachments/assets/424d1c77-63e3-48ac-b457-6beecd437f65" />

A arquitetura original organiza agentes especializados em fluxos de ingestão e recuperação. O LangGraph coordena etapas com LLM, enquanto o Weaver executa decisões de forma determinística sobre os armazenamentos configurados.

### Fluxo de ingestão

```text
Entrada (SDK / extensão do Chrome / API)
                 |
                 v
          Classificador
     identifica os domínios relevantes
                 |
     +-----------+-----------+----------+
     v           v           v          v
 Perfil       Temporal     Resumo     Código / Trechos
                 |
                 v
          Agentes de domínio
     extraem dados estruturados
                 |
                 v
            Agente Judge
     ADD / UPDATE / DELETE / NOOP
                 |
                 v
         Weaver (núcleo Rust)
     aplica as decisões nos armazenamentos
```

1. **Classificador** — encaminha a entrada para os domínios relevantes.
2. **Agentes de domínio** — extraem dados de perfil, eventos, resumos, código, trechos ou imagens.
3. **Agente Judge** — compara as extrações com as memórias existentes e decide entre adicionar, atualizar, excluir ou não alterar.
4. **Weaver** — executa essas decisões nos mecanismos de armazenamento. O núcleo Rust é descrito como uma camada determinística, sem chamadas a LLM.

O modo de processamento de alto esforço da base divide entradas longas em partes sobrepostas, processa-as em paralelo e combina os resultados. Esse comportamento ainda precisa ser revalidado nesta retomada.

### Fluxo de recuperação

```text
Pergunta
   |
   v
LLM de recuperação
escolhe as ferramentas de busca
   |
   +----------+-----------+
   v          v           v
 Perfil     Eventos     Resumos / código
   |          |           |
   +----------+-----------+
              v
      Síntese da resposta
       com referências
```

### Armazenamento

<table>
  <tr>
    <th>Mecanismo</th>
    <th>Finalidade</th>
    <th>Usos descritos na base</th>
  </tr>
  <tr>
    <td><strong>Pinecone</strong></td>
    <td>Busca vetorial por similaridade</td>
    <td>Perfis, resumos, trechos e anotações de código</td>
  </tr>
  <tr>
    <td><strong>Neo4j</strong></td>
    <td>Consultas em grafo e raciocínio temporal</td>
    <td>Eventos, grafo de código e anotações</td>
  </tr>
  <tr>
    <td><strong>MongoDB</strong></td>
    <td>Armazenamento de documentos</td>
    <td>Código analisado, metadados de arquivos e estado da indexação</td>
  </tr>
</table>

> [!NOTE]
> A base também descreve alternativas locais ao Pinecone, como Chroma, pgvector e SQLite. A compatibilidade atual será confirmada durante a revisão.

## Benchmarks

Os números abaixo foram publicados pela base original do XMem. Eles **ainda não foram reproduzidos nem validados pela retomada do RecallOS** e não devem ser interpretados como resultados atuais.

### LoCoMo

O LoCoMo avalia raciocínio sobre informações distribuídas em conversas, relações temporais e perguntas abertas.

<table>
  <tr>
    <th>Método</th>
    <th>Uma etapa (%)</th>
    <th>Várias etapas (%)</th>
    <th>Domínio aberto (%)</th>
    <th>Temporal (%)</th>
    <th>Geral (%)</th>
  </tr>
  <tr><td><strong>XMem (resultado publicado)</strong></td><td><strong>90.6</strong></td><td><strong>92.3</strong></td><td><strong>91.2</strong></td><td><strong>91.9</strong></td><td><strong>91.5</strong></td></tr>
  <tr><td>Zep</td><td>74.11</td><td>66.04</td><td>67.71</td><td>79.79</td><td>75.14</td></tr>
  <tr><td>Memobase (v0.0.37)</td><td>70.92</td><td>46.88</td><td>77.17</td><td>85.05</td><td>75.78</td></tr>
  <tr><td>Mem0g (YC 24)</td><td>65.71</td><td>47.19</td><td>75.71</td><td>58.13</td><td>68.44</td></tr>
  <tr><td>Mem0 (YC 24)</td><td>67.13</td><td>51.15</td><td>72.93</td><td>55.51</td><td>66.88</td></tr>
  <tr><td>LangMem</td><td>62.23</td><td>47.92</td><td>71.12</td><td>23.43</td><td>58.10</td></tr>
  <tr><td>OpenAI</td><td>63.79</td><td>42.92</td><td>62.29</td><td>21.71</td><td>52.90</td></tr>
</table>

A publicação original informa 91,5% no resultado geral e 92,3% em perguntas de várias etapas. A metodologia descrita usa avaliação por LLM e históricos e perguntas iguais para os sistemas comparados. Esses resultados precisam ser repetidos para serem tratados como atuais.

### LongMemEval-S

O LongMemEval-S avalia recuperação de fatos, mudanças de preferência, raciocínio temporal e manutenção de contexto entre sessões.

<table>
  <tr>
    <th>Categoria</th>
    <th>XMem (Gemini 3 Flash)</th>
    <th>Backboard.io (GPT-4o)</th>
    <th>Mastra (GPT-4o)</th>
    <th>Supermemory (GPT-4o)</th>
  </tr>
  <tr><td><strong>Várias sessões</strong></td><td><strong>93.6</strong></td><td>91.7</td><td>79.7</td><td>71.43</td></tr>
  <tr><td><strong>Raciocínio temporal</strong></td><td><strong>94.5</strong></td><td>91.7</td><td>85.7</td><td>76.69</td></tr>
  <tr><td><strong>Assistente em uma sessão</strong></td><td><strong>96.43</strong></td><td>98.2</td><td>82.1</td><td>96.43</td></tr>
  <tr><td><strong>Usuário em uma sessão</strong></td><td><strong>97.1</strong></td><td>97.1</td><td>98.6</td><td>97.14</td></tr>
  <tr><td><strong>Atualização de conhecimento</strong></td><td><strong>91.2</strong></td><td>93.6</td><td>85.9</td><td>88.46</td></tr>
  <tr><td><strong>Preferência em uma sessão</strong></td><td><strong>87.0</strong></td><td>90.0</td><td>73.3</td><td>70.0</td></tr>
</table>

A tabela e as conclusões são reproduzidas da documentação original e aguardam validação independente nesta retomada.

## Início rápido

### Ambiente local

Clone este repositório e inicie a configuração local:

```bash
git clone https://github.com/aion-devbr/RecallOS.git
cd RecallOS
npm run dev
```

O comando `npm run dev` está definido em `package.json`. O script `scripts/xmem.js` executa `setup` quando a instalação local ainda não está pronta e, em seguida, inicia a API. Para instruções detalhadas e inicialização manual, consulte o [guia local](Local.md). Alguns scripts, diretórios e variáveis ainda mantêm o nome interno `xmem`.

Os requisitos documentados pela base são:

- Git
- Node.js 20 ou superior
- Python 3.11 ou superior
- Docker Desktop
- Ollama, a menos que uma chave de LLM na nuvem seja configurada em `.env`

A documentação original indica a extensão compilada em:

```text
repos/xmem-extension/dist
```

No Chrome: abra `chrome://extensions`, ative o modo de desenvolvedor e escolha **Carregar sem compactação**.

### Comandos locais

```bash
npm run setup
npm run start
npm run verify
npm run doctor
```

Os nomes dos comandos locais foram conferidos com `package.json` e `scripts/xmem.js`. O fluxo completo de instalação ainda não foi executado nesta retomada: ele inicia serviços Docker, instala dependências e pode baixar modelos do Ollama.

### Exportação e importação de contexto

```bash
npm run context:export
npm run context:import -- --file ./exports/xmem-context.json
npm run context:sync -- --file ./exports/xmem-context.json --server https://api.xmem.in --api-key <key>
```

Na base, `context:export` gera um pacote local de contexto para importar depois ou sincronizar com um servidor XMem. O endpoint mostrado é herdado e pode não estar disponível ou ser mantido pelo RecallOS.

### Indexar um repositório

```bash
python -m src.scanner.runner --org sua-organizacao --repo seu-repositorio --url https://github.com/sua-organizacao/seu-repositorio.git --enrich
```

> [!TIP]
> Para uma configuração totalmente local, a base sugere:
>
> ```ini
> FALLBACK_ORDER='["ollama"]'
> EMBEDDING_PROVIDER=ollama
> VECTOR_STORE_PROVIDER=pgvector
> ```
>
> Em seguida, instale as dependências locais: `pip install -e ".[local]"`.

## Configuração

A base permite configurar modelos, a ordem de alternativas entre provedores e o equilíbrio entre velocidade e qualidade. Os valores padrão podem mudar durante a retomada.

<table>
  <tr>
    <th>Configuração</th>
    <th>Valor padrão documentado</th>
    <th>Descrição</th>
  </tr>
  <tr><td><code>FALLBACK_ORDER</code></td><td><code>openrouter,gemini,claude,openai</code></td><td>Ordem de alternativas entre provedores</td></tr>
  <tr><td><code>DEEPSEEK_API_KEY</code></td><td>vazio</td><td>Chave da API DeepSeek compatível com a API da OpenAI</td></tr>
  <tr><td><code>MIMO_API_KEY</code></td><td>vazio</td><td>Chave da API Xiaomi MiMo compatível com a API da OpenAI</td></tr>
  <tr><td><code>CLASSIFIER_MODEL</code></td><td>modelo padrão</td><td>Modelo do agente classificador</td></tr>
  <tr><td><code>JUDGE_MODEL</code></td><td>modelo padrão</td><td>Modelo do agente Judge</td></tr>
  <tr><td><code>RETRIEVAL_MODEL</code></td><td>modelo padrão</td><td>Modelo para sintetizar resultados de busca</td></tr>
  <tr><td><code>EMBEDDING_MODEL</code></td><td><code>gemini-embedding-001</code></td><td>Modelo de embeddings de texto</td></tr>
  <tr><td><code>EMBEDDING_PROVIDER</code></td><td><code>auto</code></td><td><code>auto</code>, <code>gemini</code>, <code>bedrock</code>, <code>ollama</code> ou <code>fastembed</code></td></tr>
  <tr><td><code>VECTOR_STORE_PROVIDER</code></td><td><code>pinecone</code></td><td><code>pinecone</code>, <code>pgvector</code>, <code>chroma</code> ou <code>sqlite</code></td></tr>
  <tr><td><code>PINECONE_DIMENSION</code></td><td><code>768</code></td><td>Dimensão do vetor de embedding</td></tr>
  <tr><td><code>RATE_LIMIT</code></td><td><code>60</code></td><td>Solicitações à API por minuto</td></tr>
  <tr><td><code>TEMPERATURE</code></td><td><code>0.4</code></td><td>Temperatura de geração do LLM</td></tr>
</table>

## Contribua

O RecallOS continuará público. Relatos de problemas, sugestões de atualização e contribuições são bem-vindos:

- [Abra uma issue](https://github.com/aion-devbr/RecallOS/issues) para relatar um problema ou propor uma melhoria.
- [Envie um pull request](https://github.com/aion-devbr/RecallOS/pulls) com mudanças pequenas e explicadas.
- Ao alterar código herdado, preserve os avisos de direitos autorais e respeite os termos da licença BSD 3-Clause em [LICENSE](LICENSE).

## Licença

Este repositório mantém o arquivo de licença BSD 3-Clause recebido com a base XMem. Consulte [LICENSE](LICENSE) para o texto completo e os avisos de direitos autorais.
