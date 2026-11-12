# Guia de Padrões e Práticas em Microsserviços

Este arquivo reúne um resumo prático sobre padrões arquiteturais essenciais no desenvolvimento de sistemas distribuídos baseados em microsserviços.

---

## 1. CQRS (Command Query Responsibility Segregation)

O **CQRS** é um padrão arquitetural que separa as operações de escrita (**Commands**) das operações de leitura (**Queries**). Em vez de usar o mesmo modelo de dados e as mesmas regras para ambas as tarefas, o sistema utiliza modelos (e até bancos de dados) separados.

* **Vantagens:**
  * **Otimização de Desempenho:** Permite escalar a leitura e a escrita de forma independente (ex: usar réplicas de leitura ou bancos otimizados para busca).
  * **Modelos Especializados:** O modelo de escrita pode focar em regras de negócio complexas e consistência, enquanto o de leitura foca na velocidade de entrega para o cliente.
* **Desvantagens:**
  * **Complexidade Arquitetural:** Aumenta a quantidade de código e a infraestrutura necessária.
  * **Consistência Eventual:** Muitas vezes exige sincronização assíncrona entre o banco de escrita e o de leitura, gerando um pequeno atraso na atualização dos dados visíveis.
* **Exemplo Prático:** 
  * *E-commerce:* O fluxo para cadastrar ou alterar um produto (Command) passa por validações pesadas de estoque e preço. Já a vitrine de produtos da página inicial (Query) busca os dados pré-calculados em uma base otimizada apenas para leitura rápida, sem travar o sistema.

---

## 2. Banco de Dados por Serviço (Database-per-Service)

O padrão **Database-per-Service** determina que cada microsserviço deve ter o seu próprio banco de dados privado, acessível exclusivamente por ele. Nenhum outro serviço pode acessar esse banco de dados diretamente; a comunicação de dados entre serviços deve ser feita exclusivamente via APIs ou eventos.

* **Vantagens:**
  * **Baixo Acoplamento:** Garante que a equipe de um serviço possa alterar a estrutura ou até a tecnologia do banco sem quebrar os outros microsserviços.
  * **Escalabilidade Isolada:** Cada serviço dimensiona seu próprio banco de acordo com a sua carga real.
* **Desvantagens:**
  * **Transações Distribuídas:** Fica mais difícil garantir transações atômicas (ACID) que abrangem dados de múltiplos serviços.
  * **Duplicação de Dados:** Dados comuns podem precisar ser replicados entre diferentes bases.
* **Exemplo Prático:** 
  * *Sistema de Delivery:* O microsserviço de **Pagamentos** usa um banco relacional (como PostgreSQL) para garantir segurança e precisão financeira. Já o microsserviço de **Catálogo de Pratos** usa um banco NoSQL (como MongoDB) para flexibilidade de buscas rápidas.

---

## 3. Padrão SAGA

O **Padrão SAGA** gerencia transações distribuídas em arquiteturas de microsserviços onde cada serviço possui seu próprio banco de dados. Como o ACID tradicional não funciona entre serviços isolados, a SAGA divide uma transação de negócio global em uma sequência de transações locais. Se uma etapa falha, a SAGA executa transações compensatórias para desfazer os passos anteriores.

* **Vantagens:**
  * **Consistência Eventual em Ações Complexas:** Permite concluir fluxos de negócio longos que envolvem vários serviços sem usar bloqueios globais pesados.
  * **Desacoplamento:** Os serviços continuam independentes, comunicando-se via eventos ou orquestração.
* **Desvantagens:**
  * **Complexidade de Implementação:** Exige o desenho cuidadoso de rotinas de compensação (o "passo para trás" caso algo dê errado).
  * **Falta de Isolamento Nativo:** Como as transações são locais e sequenciais, dados intermediários podem ficar temporariamente inconsistentes para o usuário.
* **Exemplo Prático:** 
  * *Reserva de Viagem:* Um fluxo SAGA aciona o **Serviço de Voo** (reserva o bilhete) e depois o **Serviço de Hotel** (reserva o quarto). Se o hotel falhar por falta de vagas, a SAGA dispara uma ação compensatória no Serviço de Voo para cancelar o bilhete reservado anteriormente.

---

## 4. Estratégia de Gerenciamento de Log (Centralização e Rastreamento)

Como os microsserviços distribuem uma única requisição por vários processos e servidores na rede, o **Gerenciamento de Log** centralizado e o rastreamento distribuído (*Distributed Tracing*) tornam-se vitais para unificar a visibilidade do sistema.

* **Vantagens:**
  * **Agilidade na Depuração:** Permite rastrear o ciclo de vida completo de uma requisição de ponta a ponta usando um ID único de correlação (*Correlation ID*).
  * **Monitoramento Ativo:** Facilita a criação de alertas automáticos para falhas, lentidão e gargalos de infraestrutura.
* **Desvantagens:**
  * **Volume de Dados:** O fluxo de logs gerados por dezenas de microsserviços é massivo e exige armazenamento e ferramentas robustas (ex: stack ELK, Grafana Loki).
  * **Custo Operacional:** Configurar e manter a infraestrutura de observabilidade requer tempo e investimento.
* **Exemplo Prático:** 
  * *Plataforma de Streaming:* Quando um cliente clica em "Play" e o vídeo falha, a equipe de engenharia usa uma ferramenta de logs centralizados para filtrar pelo ID da sessão do usuário. O sistema mostra exatamente onde o erro ocorreu: passou pelo *API Gateway*, autenticou no serviço de contas, mas estourou timeout no microsserviço de mídia.
