# Roteiro de retomada do RecallOS

**Atualizado em:** 28 de outubro de 2026  
**Estado:** retomada pública em andamento

Este roteiro registra o trabalho planejado para recuperar, validar e manter publicamente a base XMem sob o projeto RecallOS. Os itens serão atualizados conforme houver mudanças verificáveis.

## Já realizado

- Importada para a branch `main` uma cópia dos 420 arquivos da branch principal do XMem.
- Traduzido e revisado o README principal para apresentar o RecallOS e distinguir documentação herdada de comportamento já validado.
- Criado este roteiro e atualizado o histórico de mudanças.
- Traduzidas as orientações de contribuição para facilitar a participação em português.

## Próximo foco: estabelecer uma base confiável

- Conferir os comandos de instalação e inicialização descritos nos scripts e arquivos de configuração.
- Mapear os principais componentes: API Python, scanner, extensões, plugins e implementação Go.
- Verificar o estado dos testes e dos fluxos de CI antes de anunciar compatibilidade ou publicar uma versão.
- Registrar dependências, serviços externos e variáveis de ambiente necessários para cada parte do projeto.

## Etapas seguintes

### Manutenção e compatibilidade

- Revisar dependências e identificar componentes sem suporte ou com instruções desatualizadas.
- Atualizar documentação de instalação somente depois de confirmar os comandos em um ambiente limpo.
- Avaliar nomes e metadados que ainda usam `xmem`; preservar compatibilidade enquanto uma migração para `RecallOS` não estiver definida.
- Documentar quais integrações e provedores são realmente suportados.

### Qualidade e publicação

- Estabelecer uma verificação reproduzível para as partes que puderem ser executadas localmente.
- Corrigir problemas priorizados em issues e registrar limitações conhecidas.
- Reproduzir benchmarks antes de apresentar números como resultados atuais.
- Preparar uma versão pública quando instalação, testes e documentação estiverem suficientemente validados.

## Como acompanhar e contribuir

- Consulte as [issues abertas](https://github.com/aion-devbr/RecallOS/issues) para acompanhar problemas e propostas.
- Envie mudanças pequenas e explique como foram verificadas.
- Confira [CONTRIBUTING.md](CONTRIBUTING.md) antes de abrir um pull request.
- As sugestões para alterar a ordem do roteiro também podem ser discutidas em uma issue.

O roteiro é uma direção de trabalho, não uma promessa de prazo. O status de cada item será atualizado conforme o trabalho for feito.
