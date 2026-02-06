# Automatizador Inteligente de Feedback de Clientes com Make + IA

## Visão Geral

Este projeto é uma solução de automação no-code/low-code que coleta feedbacks de clientes via Google Forms, analisa automaticamente o sentimento e insights usando IA Generativa (Google Gemini), armazena os resultados em Google Sheets e envia alertas/notificações resumidas no Slack.

**Objetivo principal:** Transformar opiniões de clientes em ações acionáveis de forma automática, reduzindo o tempo de análise manual de horas para minutos e permitindo monitoramento contínuo da satisfação.

**Valor para o negócio:**
- Economia de tempo: ~80-90% em análise manual de feedbacks.
- Insights rápidos: Detecção precoce de problemas (ex: sentimento negativo alto em "Suporte").
- Decisões baseadas em dados: Score médio, tendências e sugestões automáticas.
- Escalável para milhares de respostas sem intervenção humana.

## Como Funciona (Fluxo Principal)

1. **Coleta de Dados**  
   Novo feedback submetido no Google Forms → nova linha adicionada automaticamente na planilha vinculada (Google Sheets).

2. **Trigger Automático**  
   Make monitora novas linhas na planilha (Google Sheets > Watch New Rows).

3. **Análise com IA**  
   O texto do feedback é enviado ao Google Gemini com prompt engenheirado para extrair:  
   - Sentimento (positivo/neutro/negativo)  
   - Score numérico (1 a 10)  
   - Insight/resumo curto  
   - Data da análise  
   Saída forçada em JSON puro.

4. **Processamento**  
   Parse do JSON → atualização da própria linha na planilha com os resultados da IA (colunas: "Nota da IA", "Data de avaliação da IA").

5. **Notificação**  
   Envio imediato de alerta no Slack com resumo do feedback analisado (sentimento, score, insight).

**Futuro/planejado:** Relatório diário agregado (média de scores, % positivos, top insights) via Scheduler no Make.

## Tecnologias e Ferramentas Utilizadas

- **Make (ex-Integromat)**: Orquestração de workflows no-code.
- **Google Gemini AI**: LLM para análise de sentimento e extração de insights (prompt engineering avançado com saída JSON estruturada).
- **Google Forms + Google Sheets**: Coleta e armazenamento de dados (banco relacional simples).
- **Slack**: Notificações em tempo real.
- **JSON Parse**: Manipulação de respostas estruturadas da IA.

**Hard skills demonstradas:**
- Integração de LLMs e prompt engineering
- Automação de workflows com Make
- Consumo e manipulação de APIs (Google ecosystem)
- Trabalho com bancos de dados (Sheets como relacional)
- Exportação de blueprint para Git (controle de versão)

## Prints do Fluxo no Make

- Print 1: Visão geral do cenário
- Print 2: Módulo Gemini com prompt
- Print 3: Update Row mapeando Row number dinâmico
- Print 4: Exemplo de mensagem no Slack

## Como Rodar / Testar

1. Crie um Google Form simples com campos: Nome, E-mail, Nota de Satisfação, Comentário, Área.
2. Vincule o Form a uma planilha Google Sheets.
3. Importe o blueprint do Make (disponível na pasta /blueprint neste repo).
4. Configure conexões: Google Sheets, Gemini API, Slack.
5. Submeta um teste no Form → veja a mágica acontecer!

## Próximas Melhorias Planejadas

- Relatório diário/semanal agregado no Slack (Scheduler + Aggregator).
- Few-shot prompting para maior precisão no Gemini.
- Integração com Airtable (para banco mais robusto).
- Error handling avançado e logs.
- Adição de RAG simples (busca de feedbacks semelhantes via embeddings).

## Autor

Lucas – Desenvolvedor de Automação e IA  
Curitiba, BR  
[LinkedIn] https://www.linkedin.com/in/lucasdsgomes/

Última atualização: Fevereiro 2026
