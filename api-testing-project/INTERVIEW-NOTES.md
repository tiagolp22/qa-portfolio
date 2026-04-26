# Guia de entrevista — Projeto de QA API

Data de atualização: 2026-04-25

Este guia foi criado para te ajudar a explicar o projeto com clareza em entrevistas, mostrando **contexto**, **decisões QA** e **impacto prático**.

## 1) Pitch rápido (30–45 segundos)

> "Eu desenvolvi um projeto de testes de API com Postman usando a API pública Reqres. Estruturei cenários positivos e negativos para operações de usuários, adicionei validações de status code, tempo de resposta e contrato JSON, e automatizei a execução com Newman no GitHub Actions. Além disso, documentei achados de qualidade em bug reports com severidade e impacto, simulando um fluxo real de QA em time de produto."

## 2) O que já foi feito até aqui

- Criação de uma coleção Postman cobrindo cenários principais de CRUD em usuários.
- Cobertura de casos negativos para validar erros esperados (ex.: credenciais incompletas em register/login).
- Inclusão de testes de contrato com schema JSON para reduzir regressões silenciosas.
- Definição de limite de tempo de resposta para monitorar performance básica.
- Registro de relatório de execução com resultados consolidados dos testes.
- Registro de bug reports simulados com linguagem profissional (severidade, prioridade, impacto, plano de ação).
- Automação em CI com Newman via GitHub Actions e export de relatório JUnit.

## 3) Decisões de QA que mostram maturidade

1. **Cobrir positivo + negativo**
   - Não focar apenas em "happy path".
   - Mostrar que robustez depende de validar erro também.

2. **Validar contrato (schema), não só status code**
   - Status 200/201 não garante qualidade da resposta.
   - Schema ajuda a detectar quebra de campos esperados.

3. **Trazer visão de risco e comunicabilidade**
   - Bug report inclui impacto real para cliente/time.
   - Priorização evita dispersão em problemas de baixo valor.

4. **Automatizar cedo no pipeline**
   - CI executa testes a cada mudança e reduz regressões.

## 4) Impacto que você pode citar na entrevista

- **Confiabilidade:** maior segurança nas mudanças da API.
- **Velocidade:** feedback rápido no pull request com execução automática.
- **Colaboração:** documentação clara facilita alinhamento entre QA, Dev e produto.
- **Observabilidade de qualidade:** falhas de contrato ficam visíveis antes de chegar em produção.

## 5) Respostas prontas para perguntas comuns

### "Como você define prioridade de teste?"
"Eu priorizo por risco: impacto no usuário + probabilidade de falha. Fluxos críticos (cadastro, autenticação, consulta principal) entram primeiro, depois expandimos para bordas e cenários de robustez."

### "Como você garante que os testes não ficam frágeis?"
"Evito acoplar em dados muito voláteis, foco em contrato e comportamento essencial, e mantenho asserts objetivos (status, campos obrigatórios, formatos esperados)."

### "Qual bug mais relevante que você encontrou/documentou?"
"O gap de contrato de erro: resposta sem `errorCode` e `traceId`. Funciona para o usuário final em casos simples, mas dificulta debug e rastreabilidade em ambiente real."

### "O que você faria em seguida nesse projeto?"
"Adicionar testes de segurança básicos (headers, método inválido), ampliar cobertura de paginação e dados inválidos, e gerar relatórios históricos para acompanhar tendência de qualidade ao longo do tempo."

## 6) Próximos passos sugeridos (roadmap curto)

- Adicionar suíte de regressão rápida (smoke) separada da suíte completa.
- Incluir mais casos negativos em update/delete (IDs inexistentes, payload inválido).
- Versionar e validar contrato com estratégia mais formal (ex.: OpenAPI + validação dedicada).
- Publicar badge de CI e instruções de execução local no README.

---

Se quiser, eu também posso transformar este guia em um roteiro de 2 minutos no formato STAR (Situação, Tarefa, Ação, Resultado) para você treinar antes da entrevista.
