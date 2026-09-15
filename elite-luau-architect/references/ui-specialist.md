# UI Specialist — Interfaces lúdicas avançadas para Roblox

Aplicar este módulo ao criar ou melhorar ScreenGui, HUDs, menus, lojas, inventários, botões e demais interfaces Luau. Preservar integralmente a disciplina de engenharia da skill principal: strict, contratos tipados, autoridade do servidor e descarte explícito.

## Direção visual

Propor paleta e clima em 2–3 frases antes de implementar. Usar por padrão a energia vibrante de jogos infantis e familiares Roblox: cores saturadas, contraste quente/frio, formas arredondadas, ícones amigáveis e hierarquia instantaneamente legível. Usar Adopt Me, Pet Simulator e zonas lúdicas de Brookhaven como referências de clima, sem copiar marcas ou assets.

Destacar a ação principal, reduzir distrações e organizar leitura do canto superior esquerdo para o inferior direito, ou do centro para fora em celebrações. Fazer títulos e corpo terem diferença evidente de tamanho. Usar botões táteis, sombras suaves, profundidade discreta e movimento elástico em recompensas; reservar transições funcionais suaves para progresso e rolagem.

Adaptar a paleta para pedidos maduros ou administrativos mantendo legibilidade, hierarquia e feedback. Entender “addictive” como envolvente e agradável; não adicionar pressão de compra, falsa urgência ou obstáculos para sair, especialmente para crianças.

## Arte visual: imagens geradas obrigatórias

Gerar arte usando uma ferramenta de geração de imagens disponível: ícones de itens e moedas, glifos de botões, retratos, NPCs, badges, molduras ilustradas, banners, fundos, splash screens e floreios decorativos estáticos. Não simular essas artes empilhando Frames, UICorners, UIGradients ou ImageLabels geométricos; não substituir ícones por emoji.

Manter em Luau a estrutura: Frames, layouts, padding, formas arredondadas de painéis e botões, texto real e animação. UICorner em botão de cor sólida é permitido. Gradientes estruturais são permitidos; não usá-los para disfarçar arte ausente. UIStroke é contorno, não sombra projetada. Para sombras artísticas ou glows elaborados, usar imagem apropriada.

Fluxo obrigatório:
1. Inventariar arte necessária, tamanhos de exibição, transparência e consistência de estilo.
2. Gerar imagens com a ferramenta disponível e inspecionar o resultado.
3. Centralizar referências em um catálogo tipado de assets. Consumir imagens com ImageLabel/ImageButton ou Decal conforme o contexto.
4. Distinguir arquivo gerado de asset publicado no Roblox. Usar IDs reais somente quando confirmados. Se upload estiver pendente, entregar imagens e indicar exatamente os campos a preencher; nunca inventar um rbxassetid funcional.
5. Se geração estiver indisponível ou falhar, informar a limitação e entregar estrutura provisória claramente identificada. Não declarar UI artística concluída sem a arte.

Não gerar imagens só por carregar este módulo: gerar quando o pedido concreto de UI exigir arte. Respeitar autorização para publicação de assets e custos de provedores.

## UITheme tipado e centralizado

Criar ou estender UITheme.luau com --!strict e export type UITheme. Todos os componentes devem importar tokens do tema; não espalhar cores, espaçamentos, raios, tamanhos de fonte ou durações literais no código de construção.

Preservar estes grupos e campos mínimos:
- colors: primary, primaryPressed, secondary, background, backgroundPanel, success, warning, textPrimary, textOnPrimary, textMuted.
- radius: small, medium, large, pill, tipados como UDim.
- spacing: xs, sm, md, lg, xl.
- motion: buttonPress, popupEnter, popupExit, counterTick, tipados como TweenInfo.

Adicionar tokens tipados de typography, dimensions, breakpoints, shadows e interaction quando necessários: fontes, pesos disponíveis, tamanhos, dimensão do botão, espessura de contorno, escala pressionada, touch target e estados hover/focus/disabled. Manter constantes de estilo no tema. Construir UDim2 a partir desses tokens é permitido; valores estruturais normalizados como zero e um não são substitutos para medidas de estilo.

Usar como direção inicial coral rosa (255,92,141), azul (94,189,255), creme (255,247,235), texto escuro (46,41,61), sucesso verde e aviso laranja avermelhado. Esses valores são referências visuais, não garantia de contraste. Ajustar textOnPrimary, textMuted e estados pressionados após calcular contraste. Nunca copiar automaticamente branco sobre coral ou cinza claro sobre branco.

Raios iniciais: 8/16/24 e pill. Espaçamentos iniciais: 4/8/16/24/32. Movimento inicial: press 0,12s Quad Out, entrada 0,35s Back Out, saída 0,2s Quad In, contador 0,4s Quart Out. Registrar tudo no tema; adaptar após testes. Back produz overshoot, portanto verificar clipping e reduzir movimento conforme preferência.

## Acessibilidade e interação

Calcular explicitamente contraste de cada par texto/fundo de corpo, incluindo estados interativos: mínimo 4,5:1. Converter canais sRGB para luminância linear e usar (LmaisClaro + 0,05)/(LmaisEscuro + 0,05). Para gradientes/imagens, considerar o pior fundo atrás do texto ou usar superfície legível. Não afirmar conformidade completa apenas por verificar cores.

Associar cor a rótulo, ícone ou forma para sucesso, falha e seleção. Reservar vermelho intenso a erros destrutivos; usar laranja avermelhado em avisos leves. Respeitar redução de movimento, legibilidade, localização e ausência de áudio.

Implementar estados explícitos idle, hover/focus, pressed e disabled; selected/equipped quando aplicável. Disabled deve impedir a ação, não apenas mudar aparência. Usar ativação compatível com mouse, toque e controle, verificando APIs suportadas. Hover é para ponteiro; controle precisa de foco visível, não MouseEnter.

Aplicar escala pressionada próxima de 0,95 através de token e UIScale em container apropriado para não disputar tamanho com layout. Restaurar estado em soltura, cancelamento do toque, saída relevante do ponteiro, perda de foco, desativação e desmontagem. Evitar botão permanentemente pressionado quando a soltura ocorre fora dele.

Cancelar/substituir tweens concorrentes e usar política determinística de prioridade de estado. Som de clique é opcional quando houver asset de áudio do projeto, com volume e variação de pitch controlados por tokens.

## Componentes, layout e produção

Construir componentes coesos com props tipadas, controller/handle explícito e Destroy ou equivalente. Separar apresentação, estado e comandos. Cada componente deve possuir e liberar conexões, tweens, tasks e instâncias. Não usar o exemplo de botão do prompt como implementação final: ele omite disabled, foco, descarte e tokens completos.

Suportar telefone em retrato e desktop 16:9, além de controle quando aplicável ao projeto. Usar layouts, constraints, UIScale e breakpoints derivados do tamanho disponível; não depender apenas de redução uniforme de um canvas fixo. Considerar strings longas, textos localizados e rolagem de inventários.

Respeitar safe areas e a barra superior pelas propriedades de ScreenGui e APIs de inset adequadas ao alvo; evitar aplicar inset duas vezes. Verificar a API oficial quando necessário. Testar HUD com notch, mudança de resolução e abertura de modais.

Manter compras/equipamento como intenções enviadas ao servidor. Exibir pending, sucesso e erro segundo confirmação autoritativa, sem conceder itens localmente. Para listas extensas, medir instâncias, memória de texturas e custo de atualização; aplicar virtualização ou atualização incremental quando necessário.

## Entrega e verificação

Entregar direção visual, módulos Luau avançados totalmente tipados, arte gerada necessária, mapeamento de assets e instruções de integração. Informar estados implementados e pendências reais de upload. Não rasterizar texto ou layout para substituir componentes acessíveis.

Verificar contraste, portrait/desktop, safe areas, foco, touch cancel, clique repetido, disabled durante tween, reabertura/destruição e falha no carregamento de assets. Relatar apenas testes realmente executados, distinguindo validação estática de inspeção no Roblox Studio. Não alegar ganhos de retenção ou desempenho sem dados.
