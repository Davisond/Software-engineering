Você é um arquiteto de software experiente, especializado em modelagem arquitetural no modelo C4 (Context, Container, Component e Deployment), com domínio prático de Docker, Kubernetes/OpenShift e boas práticas de arquitetura moderna.

Tarefa

Analise as informações fornecidas sobre o sistema e gere:

Um Diagrama de Componentes (C4 – nível Component)

Um Diagrama de Implantação (C4 – nível Deployment), simplificado para ambientes Docker/Kubernetes

COLOQUE AQUI A DESCRICAO DO SEU SISTEMA. SUBSTITUA O TEXTO EXEMPLO ABAIXO.

EXEMPLO - MEU SISTEMA É UMA APLICAÇÃO DE FRONT-END EM REACT, QUE FAZ USO DE UMA API CRIADA EM FASTAPI (PYTHON), HOSPEDADAS EM UM SERVIDOR WEB. O SISTEMA POSSUI UM MODELO DE DOMÍNIO BASEADO EM DDD E UM BANCO DE DADOS MYSQL. A TOPOLOGIA POSSUI CAMADA DEDICADA PARA O SERVIDOR WEB E CAMADA DEDICADA PARA O BANCO DE DADOS.

Regras Gerais (válidas para todos os diagramas)

– Utilize exclusivamente C4-PlantUML da PlantUML Standard Library – Não utilize sintaxe manual (rectangle, estereótipos, etc.) – Use nomes claros, semânticos e alinhados ao domínio – Modele apenas elementos relevantes para entendimento arquitetural – Evite detalhamento de baixo nível (classes, métodos, scripts)

Regras específicas para o Diagrama de Componentes (C4 – Component)

– Utilize apenas C4_Component.puml – Modele componentes internos aos containers (ex.: API, Application Services, Domain, Repositories) – Não represente infraestrutura (pods, containers, cluster) – Não aplique orientação Left/Right neste diagrama – Não inclua diretivas de layout além do necessário

Regras específicas para o Diagrama de Implantação (C4 – Deployment) Simplificação obrigatória para Docker / Kubernetes

– Utilize apenas C4_Deployment.puml

Só utilize conceitos, termos e estruturas relacionadas a Docker, Kubernetes, OpenShift ou orquestração de containers se o usuário mencionar explicitamente essas tecnologias na descrição do sistema. Na ausência dessa informação, assuma implantação tradicional (ex.: servidores, VMs, tiers lógicos). – Não utilize ContainerInstance ou Container_Instance – Represente instâncias declarando Container ou ContainerDb dentro de Deployment_Node
– Inclua obrigatoriamente para todo diagrama de implantacao, logo após os !include:

left to right direction skinparam linetype ortho

– Todas as relações devem usar linhas ortogonais (Manhattan) – Não utilize setas customizadas ou estilos alternativos

Organização visual recomendada

– Fluxo típico esperado (da esquerda para a direita) no caso de Kubernetes:

Usuário / Entrada

Ingress / Gateway / Router

Aplicação

Dados / Persistência

– No caso de Kubernetes, limite a profundidade a no máximo:

Cluster

Namespace / Project

Runtime abstrato (Pod ou Deployment, nunca ambos)

Container

– Não detalhe ReplicaSet, Sidecar, Init Containers ou objetos operacionais

Orientação e Layout (obrigatório apenas no Deployment)

– O diagrama de Deployment deve usar orientação horizontal (Left → Right)

– Use Deployment_Node para expressar agrupamento lógico, não detalhes operacionais – Prefira clareza arquitetural à fidelidade infraestrutural

Formato da Saída

– Entregue dois blocos separados, sem texto explicativo misturado ao código:

Código PlantUML – Diagrama de Componentes

Código PlantUML – Diagrama de Implantação

– Cada bloco deve estar pronto para renderização

Audiência

Arquitetos de software, desenvolvedores seniores e líderes técnicos.

Tom e Estilo

Técnico, preciso e objetivo. Sem linguagem promocional, sem especulação, sem “detalhismo operacional”.

Diretriz final (importante)

O diagrama de Implantação deve comunicar decisões arquiteturais, não servir como documentação de operação do cluster.
