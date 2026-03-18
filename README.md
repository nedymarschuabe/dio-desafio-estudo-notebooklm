📘 Caderno Temático com IA - SQL Inteligente: Otimizando Consultas com IA
📌 Contexto

Este projeto foi desenvolvido como parte do desafio da DIO, com o objetivo de explorar o uso da Inteligência Artificial como ferramenta de aprendizado ativo.

O tema escolhido foi: O uso de Inteligência Artificial para otimização e construção de consultas SQL

A proposta consiste em entender como a IA pode auxiliar desenvolvedores e analistas a escrever queries mais eficientes, legíveis e performáticas, além de apoiar no aprendizado contínuo.

🎯 Objetivos

Aprimorar conhecimentos em SQL

Aprender a utilizar IA para gerar e otimizar queries

Entender boas práticas de performance em banco de dados

Desenvolver habilidades de engenharia de prompts

Criar um guia reutilizável para consultas SQL

📚 Curadoria de Fontes

🔗 https://www.oracle.com/database/what-is-sql/
🔗 https://mode.com/sql-tutorial/
🔗 https://www.w3schools.com/sql/
🔗 https://use-the-index-luke.com/
🔗 https://learn.microsoft.com/en-us/sql/

🤖 Engenharia de Prompts

Uso de índices, redução de colunas, filtros mais eficientes e análise de plano de execução.

Aprendizado:
 - Evitar SELECT *
 - Garantir índices nas colunas de JOIN
 - Filtrar o máximo possível antes dos JOINs

🧠 Prompt 1 (Query Real - Antes):
SELECT *
FROM pedidos p
JOIN clientes c ON p.cliente_id = c.id
JOIN itens_pedido i ON i.pedido_id = p.id
WHERE c.nome LIKE '%JOAO%'
AND p.data_pedido >= SYSDATE - 30;

✅ Query Otimizada (Depois):
SELECT 
    p.id,
    p.data_pedido,
    c.nome,
    i.produto_id,
    i.quantidade
FROM pedidos p
INNER JOIN clientes c ON p.cliente_id = c.id
INNER JOIN itens_pedido i ON i.pedido_id = p.id
WHERE c.nome LIKE 'JOAO%'
AND p.data_pedido >= SYSDATE - 30;

Melhorias aplicadas:
 - Remoção do SELECT *
 - Redução de colunas
 - Ajuste no LIKE (evitando % no início)

🧠 Prompt 2 (Query com Subquery - Antes):
SELECT nome
FROM clientes
WHERE id IN (
    SELECT cliente_id
    FROM pedidos
    WHERE valor_total > 1000
);
✅ Query Otimizada (JOIN):
SELECT DISTINCT c.nome
FROM clientes c
INNER JOIN pedidos p ON p.cliente_id = c.id
WHERE p.valor_total > 1000;

Aprendizado:
 - JOIN geralmente é mais performático que subqueries
 - Uso de DISTINCT evita duplicidade

🔁 Iterações e melhorias
 - Adição de contexto da tabela nos prompts
 - Solicitação de otimização com foco em performance
 - Comparação entre abordagens (JOIN vs SUBQUERY)

⚠️ "Cicatrizes" do Aprendizado

Desafios enfrentados:
 - IA sugerindo otimizações genéricas
 - Falta de contexto de índices
 - Diferença entre teoria e prática

💡 Soluções:
 - Testar queries no banco
 - Analisar plano de execução (EXPLAIN PLAN)
 - Validar com boas práticas

📖 Miniguia de Estudo
📌 Resumo do Tema

A Inteligência Artificial pode acelerar significativamente o desenvolvimento de queries SQL, auxiliando tanto iniciantes quanto profissionais experientes.

Entretanto, a validação prática e o conhecimento técnico continuam sendo fundamentais para garantir performance e eficiência.

🧩 Principais Conceitos
 - Índices: Melhoram a velocidade de busca
 - Plano de Execução: Define como a query será executada
 - JOIN vs SUBQUERY: Escolha impacta diretamente na performance
 - Filtro antecipado: Reduz volume de dados processados

🚀 Conclusão

Este projeto demonstrou como a IA pode ser utilizada como uma poderosa aliada no desenvolvimento com SQL.

Principais aprendizados:
 - A IA acelera a escrita de queries
 - Ajuda a identificar melhorias
 - Não substitui conhecimento técnico

O equilíbrio entre IA + experiência prática é o que gera melhores resultados.

✨ Autor
Desenvolvido por NEDYMAR SCHUABE
