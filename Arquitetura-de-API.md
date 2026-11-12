# Arquiteturas de API: Quando usar cada uma?

Escolher o padrão de comunicação certo entre serviços faz toda a diferença na performance, escalabilidade e manutenção de um sistema.

# 4 tipos principais de API

### 1️⃣ REST (Representational State Transfer)
O padrão mais adotado da web, baseado em recursos e nos verbos HTTP (`GET`, `POST`, `PUT`, `DELETE`), geralmente trafegando dados em JSON.

* **Quando usar:** APIs públicas, e-commerces, sistemas CRUD tradicionais e aplicações onde o cache HTTP é importante.
* **✅ Vantagens:** Simplicidade, baixa curva de aprendizado, suporte nativo a cache e desacoplamento.
* **⚠️ Desvantagens:** *Over-fetching* (trazer dados desnecessários) e *Under-fetching* (precisar de várias requisições para montar uma tela).
* **💡 Exemplo:** Cadastro e consulta de produtos (`GET /produtos`, `POST /pedidos`).

---

### 2️⃣ gRPC (Remote Procedure Call)
Criado pelo Google, utiliza **Protocol Buffers (Protobuf)** para trafegar dados em formato binário sobre **HTTP/2**.

* **Quando usar:** Comunicação interna entre microsserviços de alta performance, sistemas que exigem baixa latência e IoT.
* **✅ Vantagens:** Desempenho extremo (binário é muito mais leve que JSON), tipagem forte e streaming bidirecional.
* **⚠️ Desvantagens:** Maior acoplamento de contrato e difícil leitura humana (exige ferramentas específicas para debug).
* **💡 Exemplo:** Comunicação interna entre o serviço de pagamentos e o motor antifraude de uma fintech.

---

### 3️⃣ GraphQL
Linguagem de consulta criada pelo Facebook onde o cliente especifica **exatamente** os campos que deseja receber em uma única requisição.

* **Quando usar:** Aplicações com dados complexos e interconectados, ou quando múltiplos clientes (Web, Mobile) precisam de payloads diferentes.
* **✅ Vantagens:** Elimina o *over-fetching* e *under-fetching*; busca múltiplos recursos em uma única chamada.
* **⚠️ Desvantagens:** Complexidade maior no back-end, dificuldade com cache HTTP tradicional e risco de *queries* pesadas.
* **💡 Exemplo:** Feed de redes sociais e dashboards analíticos personalizados.

---

### 4️⃣ WebSocket
Protocolo que abre uma conexão persistente e bidirecional (*full-duplex*) sobre TCP, permitindo troca de mensagens em tempo real.

* **Quando usar:** Aplicações que exigem atualização instantânea sem o cliente precisar ficar perguntando ao servidor (*polling*).
* **✅ Vantagens:** Comunicação em tempo real com baixíssima latência.
* **⚠️ Desvantagens:** Consome mais memória no servidor por manter conexões abertas e exige cuidado extra para escalar horizontalmente.
* **💡 Exemplo:** Chats em tempo real, jogos online e cotações de mercado financeiro.

---

### 📊 Resumo Rápido

* **REST:** Simplicidade e padrão web (JSON)
* **gRPC:** Velocidade máxima entre microsserviços (Binário)
* **GraphQL:** Flexibilidade na busca de dados (JSON sob medida)
* **WebSocket:** Tempo real bidirecional (Conexão contínua)

