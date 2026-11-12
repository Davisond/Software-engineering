# 📋 Engenharia de Requisitos: Tipos, Processos e Priorização

A engenharia de requisitos é a base de qualquer software de sucesso. Ela é responsável por descobrir, analisar, documentar e gerenciar os serviços e restrições que um sistema deve cumprir. Este guia aborda desde a classificação essencial dos requisitos até o ciclo de vida e métodos de priorização.

---

## 1. Tipos de Requisitos

### 1.1. Requisitos Funcionais (RF)
Descrevem **o que o sistema deve fazer**, ou seja, as funcionalidades, comportamentos, ações e transformações de dados que a aplicação precisa suportar para atender às necessidades do usuário e do negócio.
* **Características:** Focam nas entradas, processamentos e saídas esperadas. Respondem à pergunta: *"O que o software faz?"*.
* **Exemplo Prático (E-commerce):** 
  * *"O sistema deve permitir que o cliente realize o pagamento utilizando cartão de crédito ou Pix."*
  * *"O sistema deve gerar um comprovante em PDF automaticamente após a confirmação da compra."*

### 1.2. Requisitos Não Funcionais (RNF)
Descrevem **como o sistema executa suas funções**, definindo restrições de qualidade, desempenho, segurança, usabilidade, escalabilidade e confiabilidade. Eles não mudam o *que* o software faz, mas determinam *quão bem* ele o faz.
* **Características:** Focam em atributos de sistema (ex: velocidade, segurança, disponibilidade). Respondem à pergunta: *"Quão bem o software faz o que faz?"*.
* **Exemplo Prático:** 
  * *"A página de login do sistema deve carregar em no máximo 2 segundos."*
  * *"Os dados sensíveis e senhas dos usuários devem ser armazenados utilizando criptografia forte (ex: bcrypt)."*
  * *"O sistema deve operar com disponibilidade de 99,9% no ar, 24/7."*

### 1.3. Requisitos de Sistema
Os requisitos de sistema são uma evolução detalhada e abrangente dos requisitos do usuário. Enquanto o requisito de usuário define a necessidade em alto nível, o requisito de sistema especifica de forma técnica como os diferentes subsistemas (hardware, software, rede e banco de dados) vão interagir entre si.
* **Características:** Nível mais técnico e detalhado, muitas vezes servindo de especificação para arquitetos e desenvolvedores.
* **Exemplo Prático (Aplicativo de Mobilidade):** 
  * *"O módulo de rastreamento GPS deve enviar a localização atual do veículo para o servidor central via protocolo WebSocket a cada 5 segundos, consumindo no máximo 15 MB de dados por hora de corrida."*

### 1.4. Requisitos de Domínio
Estes requisitos vêm diretamente do **domínio de negócio** da aplicação, ou seja, das regras específicas daquele setor de indústria (como saúde, financeiro, industrial ou automotivo). Eles refletem as leis, normas ou lógicas próprias daquele ecossistema e podem ser funcionais ou não funcionais.
* **Características:** Estão atrelados ao conhecimento do negócio e conformidade legal/regulatória. Se ignorados, tornam o software inutilizável para o setor ao qual se destina.
* **Exemplo Prático (Sistema Hospitalar/Farmacêutico):** 
  * *"O sistema deve manter um registro imutável de log de todas as alterações feitas em receitas médicas pelo período mínimo de 5 anos, em conformidade estrita com as normas da ANVISA."*

---

## 2. Processos e Etapas da Engenharia de Requisitos

O ciclo de vida dos requisitos é composto por etapas interconectadas que garantem que o software construído seja exatamente o que o negócio e o usuário precisam.

1. **Concepção (Inception):** 
   * *O que é:* O momento inicial em que se descobre a ideia do projeto, identificando o valor de negócio básico, os principais stakeholders e o escopo macro do sistema.
   * *Resumo:* Responde à pergunta "Por que estamos construindo isso e quem vai usar?".
2. **Levantamento (Elicitation):** 
   * *O que é:* A fase de coleta ativa de informações junto aos clientes, usuários e especialistas sobre o que o sistema deve fazer.
   * *Resumo:* Descobrir dores, fluxos atuais e expectativas de negócio.
3. **Elaboração (Elaboration):** 
   * *O que é:* O refinamento e a modelagem técnica do que foi levantado. Aqui os requisitos brutos são transformados em modelos de classes, diagramas de fluxo, regras de negócio e restrições técnicas.
   * *Resumo:* Dar forma estruturada e lógica aos dados coletados.
4. **Negociação (Negotiation):** 
   * *O que é:* O alinhamento de expectativas entre o que o cliente quer, o que o orçamento/prazo permite e a viabilidade técnica apontada pelos desenvolvedores.
   * *Resumo:* Equilibrar escopo, tempo, custo e prioridades.
5. **Especificação (Specification):** 
   * *O que é:* A documentação formal do sistema. Pode resultar em um Documento de Requisitos de Software (DRS), backlog refinado ou protótipos detalhados.
   * *Resumo:* Registrar de forma clara e inequívoca o comportamento do software.
6. **Validação (Validation):** 
   * *O que é:* A checagem final com os stakeholders para garantir que o que foi especificado atende corretamente às necessidades e está livre de ambiguidades ou erros.
   * *Resumo:* Garantir que estamos construindo o produto certo.
7. **Gestão de Requisitos (Management):** 
   * *O que é:* O controle contínuo das mudanças de escopo ao longo de todo o ciclo de vida do projeto (controle de versão e impacto de novas demandas).
   * *Resumo:* Administrar alterações sem quebrar o projeto.

---

## 3. Técnicas de Elicitação de Requisitos

A elicitação é a arte de extrair informações dos stakeholders. Algumas das principais técnicas utilizadas são:

* **Entrevistas:** Conversas estruturadas ou abertas com usuários e especialistas de domínio para entender rotinas e dores.
* **Brainstorming:** Reuniões criativas em equipe para gerar ideias rápidas sobre funcionalidades e cenários de uso.
* **Workshops (JAD - Joint Application Development):** Sessões colaborativas intensivas reunindo desenvolvedores, clientes e gestores para definir requisitos em conjunto.
* **Prototipagem:** Criação de telas de baixa ou alta fidelidade para validar visualmente fluxos e necessidades com o usuário final.
* **Observação / Etnografia:** Acompanhar o dia a dia do usuário no seu ambiente real de trabalho para identificar gargalos que ele próprio não saberia explicar.
* **Análise de Documentos:** Estudo de relatórios, manuais, planilhas ou sistemas legados atuais para extrair regras de negócio embutidas.

---

## 4. Técnicas de Especificação e Estrutura

Especificar é transformar ideias abstratas em artefatos claros e acionáveis para o time técnico.

### Principais Técnicas de Especificação:
* **Histórias de Usuário (User Stories):** Focadas em metodologias ágeis, descrevem o requisito sob a perspectiva de quem usa, usando o formato clássico: *"Como [tipo de usuário], eu quero [uma funcionalidade] para que [benefício/valor]"*.
* **Casos de Uso (Use Cases):** Descrevem interações passo a passo entre o usuário (ator) e o sistema, detalhando o fluxo principal, fluxos alternativos e exceções.
* **Critérios de Aceitação:** Regras objetivas (geralmente usando a estrutura *Dado / Quando / Então* - BDD) que definem exatamente quando uma funcionalidade está pronta e aprovada.

### Especificação de Estrutura:
A **especificação de estrutura** organiza como a documentação e os modelos do sistema são estruturados de forma modular, garantindo legibilidade e manutenção. Ela engloba:
* **Dicionário de Dados:** Definição clara do significado, tipo, tamanho e restrições de cada entidade e atributo do sistema.
* **Modelagem Conceitual e de Arquitetura:** Diagramas de entidade-relacionamento (DER), diagramas de classes e fluxos de dados que mostram a arquitetura lógica da aplicação.

---

## 5. Método MoSCoW (Priorização de Requisitos)

Quando há muitos requisitos e o tempo é curto, o método **MoSCoW** ajuda a classificar o que é indispensável do que pode ficar para depois. A sigla divide as demandas em quatro categorias:

* **M - Must have (Deve ter):** Requisitos críticos e obrigatórios para o sistema funcionar. Se faltar um destes, o projeto não pode ser lançado (ex: o sistema de e-commerce precisa obrigatoriamente processar pagamentos).
* **S - Should have (Deveria ter):** Requisitos importantes e de alto valor, mas que não impedem o lançamento imediato caso haja restrição de prazo (ex: filtros avançados de busca por faixa de preço).
* **C - Could have (Poderia ter):** Requisitos desejáveis, mas de baixo impacto se forem deixados de fora. São implementados se sobrar tempo e orçamento (ex: modo escuro na interface).
* **W - Won't have (Não terá agora):** Requisitos acordados para serem descartados ou adiados para versões futuras do sistema (ex: integração com uma API de realidade aumentada).
