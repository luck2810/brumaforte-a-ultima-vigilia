# Brumaforte: A Última Vigília — estado da entrega

> **Status: adaptação parcial do starter; não é uma implementação completa do escopo solicitado.** Este documento separa sistemas identificados no código de funcionalidades ainda ausentes e de testes que não foram executados. Não use arte conceitual como evidência de gameplay.

## Base técnica e execução

O projeto atual é um jogo 2D em GDScript para Godot 4.7, renderizador GL Compatibility, com preset de exportação Web. O starter adotado não é Phaser 3 nem usa Matter.js; esta divergência da preferência original permanece e deve ser levada em conta ao planejar extensões.

Na raiz do projeto, instalar Node.js e pnpm compatíveis com o campo `packageManager` de `package.json`, instalar as dependências do starter conforme o fluxo Manus Game instalado e configurar `GODOT_BIN` para o executável Godot 4.7. O preset Web depende dos templates de exportação Web da mesma versão.

Com Godot configurado, os comandos disponíveis no `package.json` incluem `npm run check` (verificação gerenciada), `npm run build` (build do pacote), `npm run preview:build`, `npm run preview:status` e `npm run export` (exportação Web via Godot). Use o fluxo de preparação de release do runtime instalado antes de empacotar. Não abra os HTML gerados manualmente como prova de compatibilidade nem trate uma exportação como publicação: Preview, checkpoint e publicação são operações distintas.

## O que o código do starter contém

- Um loop de campanha com três capítulos identificados como jogáveis (`s1`–`s3`) e oito ondas por capítulo, seleção de esquadrão, vitórias/derrotas e estado de campanha persistido localmente pelo sistema de campanhas.
- Quatro guardiões elementais (`fire`, `frost`, `storm`, `earth`) implantados em plataformas elevadas. Eles têm papéis de combate distintos, melhorias por níveis e combinações/merges previstos no modelo. Isso **não** equivale às cinco torres pedidas.
- Inimigos de fantasia como goblins, orcs, trolls, dragão, Prismback, Harrier e Broodmother, com regras específicas; a lista não confirma um esqueleto jogável.
- Preparação de ondas, pausa, velocidade, tutorial, configurações e uma interface que contém lógica para layouts retrato e paisagem e entrada por toque. Isso é evidência no código, não um aceite de funcionamento em dispositivos reais.
- O loader Web `web/loading.html` com nome Brumaforte, texto em pt-BR, progresso, mensagem de demora e tentativa de recarga.

## Escopo solicitado ainda não implementado ou não comprovado

| Requisito | Situação desta entrega |
|---|---|
| Cinco torres: arqueiros, canhão, magia, gelo e catapulta, com mecânicas próprias | **Ausente como conjunto jogável.** O modelo possui quatro guardiões elementais. Imagens das cinco torres são arte conceitual e não comprovam unidades funcionais. |
| Construção híbrida em terreno livre e áreas especiais, colisões, venda e substituição | **Parcial/diferente:** o posicionamento existente é sobre sockets/plataformas; a prévia válida/inválida existe, mas não implementa o sistema híbrido completo nem venda/substituição. |
| Árvores de evolução e caminhos alternativos com consequências estratégicas | **Ausente.** Existem níveis e merges; não equivalem a árvores ramificadas por torre. |
| Sobrevivência e desafios especiais | **Ausentes no fluxo jogável identificado.** |
| Obstáculos destrutíveis, busca de rotas alternativas e física de projéteis/colisões/explosões conforme o pedido | **Não comprovados como sistemas de jogo.** Há rotas/simulação e efeitos visuais existentes; isso não demonstra as interações físicas solicitadas. |
| Co-op online para dois jogadores | **Não implementado.** O escopo atual permanece solo; multiplayer não deve ser anunciado como recurso disponível. |
| Aceite completo em desktop, Android, iOS e tablets; desempenho em aparelhos modestos | **Pendente de testes em dispositivos e navegadores-alvo.** A presença de entrada por toque e layout responsivo no código não equivale a aceite. |
| Testes completos de construção, combate, economia, progressão, salvamento e reinício | **Não realizados nesta continuação.** Não afirmar que passaram. |

## Verificação e bugs conhecidos

O primeiro `npm run check` expirou durante a importação inicial do Godot (a mensagem foi `Game import timed out`); o log não registrou erro de código. Uma importação headless separada concluiu com saída 0. Na repetição do check oficial, o resultado foi `ok:true`, perfil `source`, `outcomeChecks:12`, `fontBindings.errors:0` e `missingGlyphs:0`. Isso confirma a conclusão desse conjunto de verificações, mas não aceite completo do jogo. O próprio relatório marcou `visualCoverage.status:"incomplete"`: 0 de 8 papéis visuais do Blueprint cumpridos (`campo_de_batalha`, `torres_e_evolucoes`, `inimigos_e_animacoes`, `chefes`, `base_e_obstaculos`, `construcao_e_selecao`, `projeteis_e_efeitos` e `interface_responsiva`).

Ainda não foram executados o fluxo de release, `npm run check -- --pack`, Preview ou aceite browser/dispositivo. Não há uma triagem abrangente de bugs baseada em jogo observado; defeitos potenciais permanecem desconhecidos. O resultado `npm run check` não valida as mecânicas ausentes nem os papéis de arte não integrados.

Antes de chamar qualquer versão de pronta: executar o check indicado pelo runtime atual, preparar candidato com `save-release.mjs`, executar a verificação aplicável com `--pack`, registrar falhas reais e, se corrigidas, repetir apenas os checks afetados. Desktop/Web, toque/mobile e áudio no navegador exigem aceite correspondente; não inferir sucesso a partir de testes headless.

## Próximas etapas sugeridas

1. Resolver a cobertura visual incompleta do Blueprint, priorizando os papéis necessários para demonstrar gameplay real; não contar as ilustrações conceituais das torres como unidades jogáveis.
2. Manter a matriz de status rastreável em `TODO.md`; marcar como concluído somente o comportamento observado e validado.
3. Em trabalho futuro, escolher primeiro se as torres pedidas substituem o elenco elemental ou se serão adicionadas como operadores novos; preservar saves, identidade de campanha, balanceamento e verificações do modelo.
4. Implementar por incrementos a construção em terreno/sockets, os três modos, as categorias de torres e os inimigos/mecânicas ausentes. Só então atualizar as alegações de produto e release.

## Orientações para Claude ou outro mantenedor

- Comece lendo este arquivo, `TODO.md`, o Blueprint aprovado e as regras locais em `README.md`.
- Preserve a simulação autoritativa, a campanha e os saves existentes; mudanças em operadores, classes, inimigos ou stages podem alterar a identidade de saves e precisam de migração/versionamento deliberado e dos checks existentes.
- Preserve licenças e proveniência. Integre novos assets pelo fluxo `sync-assets.mjs` do runtime Game atual; não edite à mão `asset-provenance.json` nem `assets.lock.json`.
- Não apague ou contorne testes por causa de incompatibilidades de locale; adapte fixtures somente com justificativa e evidência. Não use capturas de automação de navegador como substituto da verificação Godot.
- Mantenha esta documentação em português e atualize datas/status apenas depois de executar as ações descritas.
