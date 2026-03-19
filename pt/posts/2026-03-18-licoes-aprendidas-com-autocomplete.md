---
layout: layouts/post.njk
title: Lições aprendidas com Autocomplete
date: 2026-03-18
tags:
  - autocomplete
  - autosuggest
  - produto
  - lições aprendidas
permalink: /pt/posts/licoes-aprendidas-com-autocomplete/
---

Este post é uma mera coleção de ideias que tive e apliquei ao longo da minha carreira como engenheiro de busca. Serve mais como um registro das decisões tomadas e das lições aprendidas durante essa jornada.

## Sobre o autocomplete
---

Autocomplete não é apenas “ajudar a digitar mais rápido”. Ele é um mecanismo de descoberta, direcionamento e conversão. Em muitos casos, é a primeira interação real do usuário com o sistema de busca.

Alguns **princípios importantes**:

- **Responsividade é fundamental**  
A experiência precisa ser fluida. Latência alta quebra o ritmo da digitação e reduz o uso.

- **Ambiguidade deve ser tratada explicitamente**  
Quando uma consulta tem múltiplos significados, mostre caminhos claros.
Ex: teclado → instrumento musical / acessório de computador.

- **Contexto melhora a qualidade**  
Considerar categoria atual, navegação recente ou tipo de página ajuda a refinar sugestões.

- **Personalização leve já traz ganhos**  
Não é necessário um sistema complexo. Sinais simples, como a última categoria visitada, já impactam o ranking.

## Modelagem e arquitetura
---

- **Dicionários baseados na linguagem real do usuário são mais eficazes**  
Termos vindos de logs de busca tornam o sistema mais natural e próximo da intenção real.

- **Índice invertido pode ser subestimado**  
Modelar autocomplete como busca tradicional acelera a entrega e permite reaproveitar features como ranking, filtros e scoring.

- **Árvores de prefixo (tries) são rápidas, mas nem sempre simples**  
Funcionam bem para prefix match puro, mas ficam complexas com filtros, ranking e múltiplos critérios.

- **Combinar técnicas melhora a cobertura**  
Normalização e bag-of-words ajudam a unificar variações e enriquecer sugestões.

- **Usuário e catálogo falam línguas diferentes**  
O usuário busca de um jeito, o produto é cadastrado de outro.
Logs de query devem ser a principal fonte de verdade, com o catálogo como complemento.

## Ranking e relevância
---

- **Score de popularidade é um dos sinais mais fortes**  
Queries frequentes tendem a representar melhor a intenção coletiva.

- **Prefix match deve ser priorizado**  
Mesmo com suporte a partial match, priorizar prefixo mantém a sensação de digitação natural.

- **Contexto e filtros ajudam no refinamento**  
Restringir sugestões à categoria ou ao contexto atual melhora a precisão.

## Trade-offs técnicos
---

- **Correção em tempo real é custosa**  
Pode aumentar latência e custo computacional. Funciona melhor quando aplicada com parcimônia e em momentos específicos.

## Métricas que realmente importam
---

- Taxa de uso do autocomplete
- CTR por posição de sugestão
- Taxa de zero resultado originada do autocomplete
- Taxa de uso de autocorreção
- Taxa de conversão a partir do autocomplete