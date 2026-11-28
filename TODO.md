# Brumaforte: A Última Vigília — TODO

Este quadro acompanha resultados entregues com evidência; não trata funcionalidades planejadas como concluídas. O Blueprint aprovado é a especificação de gameplay e arte. Direção aplicada: fantasia medieval top-down com aparência de indie premium, leitura tática em primeiro lugar, paleta de verde-pinho/carvão/pedra, pergaminho e latão, silhuetas e efeitos identificáveis e interface em português brasileiro. O starter Godot 2D/Web substitui a preferência não mandatória por Phaser 3; essa limitação precisa ficar explícita na documentação.

## 1. Jogo web responsivo e controles multiplataforma — em andamento
- O jogo deverá funcionar em navegadores modernos.
- O jogo deverá ser adaptável para computadores Windows, Linux e macOS através do navegador, celulares Android e iOS através do navegador e tablets.
- Implemente interface responsiva, controles por mouse e toque, botões adaptados para telas pequenas, suporte a diferentes resoluções e proporções e desempenho adequado em dispositivos modestos.
- Não faça uma versão mobile simplificada que perca funcionalidades da versão de PC.
- Garanta controles simultâneos em dispositivos móveis.

## 2. Identidade visual, animações e assets — em andamento
- Use tema Medieval Fantasy e câmera Top-down (visão de cima). O universo deverá conter castelos medievais, florestas, montanhas, vilarejos, estradas de pedra e terra, torres defensivas, criaturas fantásticas, ambientes com iluminação e efeitos visuais.
- O estilo artístico deve ser consistente. Não misture sprites de estilos completamente diferentes. Busque aparência de jogo comercial independente, com boa composição visual, animações e interface bem trabalhada.
- Crie e integre recursos visuais necessários quando viável. Não invente que recebeu imagem não enviada, não substitua personagem importante por círculo/quadrado colorido e não use imagens temporárias como solução definitiva. Placeholders precisam ser identificados como temporários e substituídos; não bloqueie sistemas independentes esperando um sprite.
- Se precisar solicitar recurso ao usuário, para cada imagem informe nome, uso, estilo, dimensões, quadros se spritesheet, orientação/organização, transparência, formato recomendado e referência visual/descrição detalhada. Ao receber arte, verificar alinhamento, transparência, escala e animações.
- Música ambiente medieval e sons de ataques, construção, inimigos, interface, vitória e derrota devem usar recursos originais, licenciados ou de domínio público; registrar licenças.

## 3. Construção, colisões e economia de posicionamento — pendente
- Implementar terrenos permitidos para construção livre e espaços especiais para estruturas maiores.
- Indicar visualmente posições/áreas válidas e inválidas; verificar colisões entre estruturas.
- Construção tem custo; torres podem ser vendidas, substituídas e melhoradas.
- Permitir ao jogador planejar defesas estrategicamente.

## 4. Torres, combate e evolução estratégica — pendente
- Criar categorias de torres com atributos próprios, custo, alcance, velocidade de ataque e dano.
- Torre de Arqueiros: ataques rápidos, bom alcance, dano moderado.
- Torre de Canhão: dano em área, ataques lentos, boa contra grupos.
- Torre de Magia: ataques mágicos, efeitos especiais, possibilidade de atingir vários inimigos.
- Torre de Gelo: reduz velocidade dos inimigos e controla grupos.
- Torre de Catapulta: projéteis com trajetória física, dano em área e capacidade de interagir com obstáculos.
- Adicionar outras torres somente se contribuírem para variedade estratégica.
- Implementar melhorias de dano, alcance e velocidade; árvores de habilidades; caminhos alternativos de evolução com consequências estratégicas reais; evoluções visuais; combinações especiais de estruturas. Evitar melhorias apenas numéricas sem mudar a forma de jogar.

## 5. Inimigos, ondas e chefes — pendente
- Criar goblins rápidos/frágeis; orcs resistentes; trolls lentos/fortes; esqueletos comuns; criaturas mágicas com habilidades especiais; chefes com mecânicas próprias.
- Cada inimigo terá vida, velocidade, resistência, recompensa, comportamento próprio e animações; implementar IA apropriada às categorias.

## 6. Caminhos, comportamento dinâmico e física — pendente
- Caminhos clássicos: inimigos seguem trajetos definidos em mapas com rotas estratégicas.
- Comportamento dinâmico: determinados inimigos procuram rotas alternativas, alguns reagem às construções e outros podem atacar obstáculos.
- Implementar física consistente sem comprometer desempenho: projéteis com trajetórias, colisões, explosões, objetos destrutíveis, efeitos ambientais e interações entre objetos.

## 7. Modos e progressão — pendente
- Campanha: fases progressivas, mapas diferentes, missões, chefes, progressão de dificuldade e desbloqueio de conteúdo.
- Sobrevivência: ondas progressivamente mais difíceis, recordes, recompensas e inimigos variados.
- Desafios especiais: regras diferentes, objetivos específicos, limitações de construção e recompensas exclusivas.

## 8. Economia, salvamento e arquitetura solo/cooperativa — em andamento
- Implementar moedas, recompensas por inimigos derrotados, custos de construção/melhorias, desbloqueio de torres, sistema de progressão e salvamento de progresso local.
- Equilibrar economia para não permitir comprar tudo facilmente nem impedir avanço.
- A experiência solo completa é prioridade inicial. Planejar arquitetura para adição futura de coop online para dois jogadores, com compartilhamento de recursos, construção conjunta, defesa do mesmo território e coordenação estratégica; multiplayer incompleto não pode comprometer o solo.

## 9. Telas e interface — pendente
- Criar menu principal, seleção de modos, seleção de fases, tela de jogo, painel de construção, painel de melhorias, indicador de moedas, indicador de vida da base, contador de ondas, menu de pausa, configurações, tela de vitória e tela de derrota.
- A interface deverá ser intuitiva, bonita e adaptável a todas as plataformas.

## 10. Organização, desempenho e manutenção — em andamento
- Organizar módulos legíveis, documentados e fáceis de modificar: combate, física, economia, ondas, construção, progressão, salvamento, entidades (torres, inimigos e projéteis), cenas/modos e UI/menus.
- Evitar repetição desnecessária, funções gigantescas, globais desnecessárias, dependências sem necessidade e sistemas que apenas simulam funcionalidades.
- Manter desempenho estável, limitar partículas, otimizar colisões, evitar processamento desnecessário, adaptar efeitos para dispositivos modestos e evitar consumo excessivo de memória.

## 11. Verificação, documentação e entrega — em andamento
- Verificar de fato construção, colisões, ataques, caminhos dos inimigos, física, evoluções, economia, progressão das ondas, salvamento, interface mobile/desktop e reinicialização de partidas; corrigir erros encontrados.
- Não declarar teste que não foi executado.
- Entregar código-fonte e arquivos organizados, assets utilizados e licenças, documentação, instruções de execução local e publicação web, lista de funcionalidades implementadas, pendentes e bugs conhecidos, e orientações para futuras melhorias com Claude.
- O projeto deverá ser executável e não depender de arquivos não entregues. Se houver limitação técnica, explicá-la e apresentar alternativa funcional.

## 12. Otimização, novas fusões, inimigos e campanha — em andamento

### 12.1 Desempenho em celulares e computadores — em andamento
- “otimize o jogo para celular e pc”: reduzir trabalho repetido de renderização/terreno sem remover recursos nem quebrar os controles por mouse e toque, pinça, redimensionamento e leitura em telas pequenas.

### 12.2 Novas fusões — concluído; checks do modelo e das ultimates passaram
- “adicione novas fusões”: acrescentar as quatro receitas tri-elementais que combinam três dos elementos existentes; as novas combinações precisam funcionar na seleção, posicionamento, combate, ultimate, representação visual e localização em português, inglês e chinês.

### 12.3 Novos inimigos — concluído; dados integrados à campanha e checks passaram
- “novos bixos”: acrescentar duas classes jogáveis de inimigo com atributos de combate próprios e identificação visual/textual localizada; preservar a compatibilidade dos inimigos atuais.

### 12.4 Campanha ampliada — concluído; progressão e compatibilidade passaram nos checks
- “almente a campanha”: acrescentar fases jogáveis s11 e s12 com progressão sequencial e desbloqueio normal; preservar s1–s10, os saves existentes e a projeção legada V2 de oito fases.
