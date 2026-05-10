Este projeto implementa um banco de dados acadêmico completo (OLTP) e sua integração analítica em Star Schema (OLAP), conforme exigido no trabalho final.

O script foi construído para ser idempotente, ou seja, pode ser executado várias vezes sem gerar inconsistências.

Pré-requisitos:
MySQL Community Server 8.0+
Cliente MySQL (terminal, Workbench ou similar)

Como executar o Script Único?
Abra o terminal do MySQL:
mysql -u root -p
Cole todo o conteúdo do arquivo:
Script de Instalação SISGESC-Entrega Final.sql
Execute de uma única vez. O script já contém toda a ordem correta.

O que o script faz (na ordem do PDF)?
Reseta e prepara o ambiente
Limpa tabelas antigas e cria o banco sisgesc.
Cria toda a estrutura do banco (DDL)
Tabelas normalizadas (1FN → 3FN), chaves estrangeiras, checks e índices.
Insere dados de teste (DML)
Pessoas, alunos, disciplinas, turmas, matrículas e notas.
Prova que é idempotente
Roda a mesma inserção duas vezes e demonstra que não quebra o banco.
Cria consultas acadêmicas
Subselect e a View vw_boletim.
Monta o Data Warehouse (OLAP)
Cria o banco sisgesc_dw em Star Schema com:
dim_aluno
fato_desempenho
Executa o ETL (OLTP → OLAP)
Leva as notas do transacional para o DW.
Otimiza com índices e valida com EXPLAIN
Mostra Using index no plano de execução.
Valida a integridade dos dados
Compara a soma das notas no OLTP e no OLAP (devem ser iguais).

Ao final deve aparecer: contagens corretas, EXPLAIN Using index e soma OLTP = OLAP, o script executou 100% correto.
