# 📊Estimativas e Gerenciamento Ágil

Estimar esforço e prazos de forma realista é um dos maiores desafios no desenvolvimento de software. Este guia reúne as principais técnicas usadas em equipes ágeis para prever prazos e dimensionar tarefas com precisão e colaboração.

---

## 1. Estimativa PERT (Program Evaluation and Review Technique)

A estimativa PERT é uma técnica estatística ideal para lidar com tarefas incertas ou complexas. Em vez de cravar um número seco de dias, ela calcula uma média ponderada considerando três cenários diferentes para o mesmo trabalho.

### A Fórmula

```text
            O + 4M + P
    E = ___________________
                 6
```

Onde:
* **O (Otimista):** O menor tempo possível se tudo correr perfeitamente bem, sem nenhum imprevisto.
* **M (Mais provável):** O cenário realista, considerando que ocorram alguns contratempos comuns do dia a dia.
* **P (Pessimista):** O pior cenário possível caso tudo dê errado (bugs críticos, dependências que quebram, etc.).

---

## 2. Story Points (Pontos de História)

No mundo ágil, costuma-se abandonar a estimativa baseada estritamente em horas e passa-se a usar os **Story Points**. Um Story Point é uma unidade de medida **relativa** que avalia três fatores combinados:
1. **Complexidade técnica** envolvida.
2. **Esforço necessário** para implementar.
3. **Incerteza ou risco** técnico do requisito.

Para facilitar essa pontuação, os times utilizam uma escala inspirada na sequência de Fibonacci (`1, 2, 3, 5, 8, 13, 21...`).

### Exemplo Prático
* **Tarefa A:** Alterar a cor de um botão na tela (Simples, rápido, sem risco): **1 Story Point**.
* **Tarefa B:** Criar uma rotina completa de autenticação com OAuth2, recuperação de senha e dupla autenticação (Mexe com segurança, banco de dados e front-end): **8 Story Points**.
* *Nota:* Tu não estás dizendo exatamente quantas horas vai levar, mas que a segunda tarefa é cerca de 8 vezes mais complexa que a primeira.

---

## 3. Planning Poker (Pôquer de Planejamento)

O **Planning Poker** é uma técnica gamificada e colaborativa usada pelo time de desenvolvimento para estimar os Story Points de cada item do backlog, evitando o famoso "efeito manada" (onde todo mundo concorda de primeira com a opinião do membro mais sênior ou mais barulhento da reunião).

### Como Funciona a Dinâmica:
1. **Apresentação:** O Product Owner (PO) apresenta uma história de usuário ou funcionalidade e esclarece todas as dúvidas técnicas do time.
2. **Votação Secreta:** Cada desenvolvedor escolhe em segredo uma carta com um número de Story Points (usando a sequência de Fibonacci).
3. **Revelação Simultânea:** Todo mundo revela a carta ao mesmo tempo na mesa (ou na ferramenta digital de reunião).
4. **Debate:** Se houver muita divergência (por exemplo, um dev votou `2` porque achou simples e outro votou `13` porque lembrou de um gargalo oculto no legado), quem votou nos extremos explica o seu ponto de vista.
5. **Consenso:** O time debate rapidamente os argumentos e vota de novo até que todos entrem em acordo.

Essa dinâmica é excelente porque força a troca de conhecimento técnico e o alinhamento de expectativas antes de o time assumir qualquer compromisso de entrega para o Sprint.
