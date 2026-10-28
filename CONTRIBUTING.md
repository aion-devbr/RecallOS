# Como contribuir com o RecallOS

Obrigado por ajudar a melhorar o RecallOS. Este guia reúne orientações para entender a base, propor mudanças com segurança e abrir pull requests que possam ser revisados com clareza.

> **Status da retomada:** os comandos e requisitos abaixo foram herdados do XMem e ainda estão sendo revalidados. Consulte o [roteiro](ROADMAP.md) e relate instruções que não funcionarem.

## Antes de começar

- Confira as [issues abertas](https://github.com/aion-devbr/RecallOS/issues) e comente na issue relacionada ao trabalho.
- Para mudanças maiores, apresente a proposta antes de abrir um pull request.
- Mantenha cada pull request focado em um problema, recurso ou tarefa de documentação.
- Não envie segredos, arquivos `.env` locais, caches gerados nem chaves de API.

## Áreas do projeto

A base contém o back-end Python, agentes, integrações de armazenamento, rotas da API, scanner e testes.

Áreas comuns:

- `src/agents/` — classificador, extração de memórias, agente Judge e agentes de domínio.
- `src/pipelines/` — fluxos de ingestão, recuperação e Weaver.
- `src/api/` — aplicação FastAPI, rotas, dependências e middleware.
- `src/storage/` — interface de armazenamento vetorial e implementação Pinecone.
- `src/graph/` — clientes Neo4j e esquemas do grafo.
- `src/scanner/` e `src/scanner_v1/` — indexação de repositórios e análise de AST.
- `src/schemas/` — modelos Pydantic usados pelos agentes e pela API.
- `tests/` — testes unitários e de integração.
- `docs/` — documentação para usuários e desenvolvimento.

SDKs, integrações MCP, extensões e páginas do ecossistema podem estar em outros repositórios. Ao trabalhar nesses componentes, siga a documentação própria de cada um.

## Configuração de desenvolvimento

Requisitos documentados pela base:

- Python 3.11 ou superior.
- Acesso aos serviços externos necessários para a área em que você está trabalhando, como Pinecone, Neo4j, MongoDB ou um provedor de LLM.

Crie e ative um ambiente virtual:

```powershell
python -m venv .venv
.venv\Scripts\activate
```

No macOS ou Linux:

```bash
python -m venv .venv
source .venv/bin/activate
```

Instale o projeto com as dependências de desenvolvimento:

```bash
pip install -e ".[dev]"
```

## Testes

A base declara usar `pytest`, `pytest-asyncio` e `pytest-cov`. Os testes são organizados por escopo:

- `tests/unit/` — funções auxiliares, validação de esquemas e lógica determinística.
- `tests/integration/` — pipelines e dependências da API com serviços externos simulados.
- `tests/e2e/` — fluxos completos usando substitutos locais para serviços externos.

Comandos documentados:

```bash
pytest
pytest tests/unit
pytest tests/integration
pytest tests/e2e
```

A verificação de cobertura configurada na documentação original é:

```bash
pytest --cov=src/utils --cov=src/schemas --cov=src/pipelines --cov=src/enterprise --cov=src/api --cov-report=term-missing --cov-report=xml --cov-fail-under=70
```

Política de simulação descrita pela base:

- Não acesse provedores de LLM, Pinecone, Neo4j, MongoDB ou GitHub reais na suíte padrão.
- Use os objetos simulados compartilhados em `tests/conftest.py` para modelos de chat, armazenamentos vetoriais e clientes de grafo.
- Mantenha o comportamento específico de provedores atrás de adaptadores pequenos.
- Cubra interações entre pipelines com testes de integração e a lógica determinística com testes unitários.

## Lint e formatação

O projeto documenta o uso de Ruff:

```bash
ruff check src tests
```

Siga o estilo existente:

- Prefira funções pequenas e focadas.
- Mantenha os esquemas de domínio em `src/schemas/`.
- Mantenha os prompts em `src/prompts/`.
- Concentre gravações nos armazenamentos no Weaver ou nos clientes de armazenamento.
- Evite refatorações amplas em mudanças de correção.

## Padrões de código

- Use modelos Pydantic para dados estruturados que cruzam limites entre agentes, API e pipelines.
- Valide explicitamente as saídas dos agentes sempre que possível.
- Prefira lógica determinística no agente Judge quando houver chaves de identidade estáveis.
- Isole chamadas a serviços externos para que possam ser simuladas nos testes.
- Ao alterar comportamento, atualize ou acrescente testes e documente caminhos de falha.
- Preserve a compatibilidade de registros armazenados e respostas públicas da API.

## Documentação

- Mantenha instruções de configuração copiáveis e atualizadas.
- Prefira exemplos curtos.
- Atualize a documentação ao mudar comportamento público, configuração ou instalação.
- Não inclua credenciais reais, URLs privadas ou tokens pessoais.

## Checklist de pull request

Antes de enviar:

- Sincronize sua branch com a branch `main`.
- Mantenha o pull request ligado a uma mudança específica.
- Atualize os testes quando o comportamento mudar.
- Execute as verificações relevantes e informe o que foi executado.
- Atualize a documentação quando alterar instalação, API ou configuração.
- Explique o que mudou, por que mudou e como verificou.

Sugestão de descrição:

```md
## Resumo
- ...

## Verificações
- ...

## Observações
- ...
```
