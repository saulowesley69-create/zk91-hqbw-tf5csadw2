# UE5 TECHNICAL BASELINE

**Projeto:** SW Games Studios — [NOME DO JOGO]
**Documento:** UE5 Technical Baseline
**Status:** DISCOVERY
**Responsável pela estratégia:** [CTGT] ChatGPT
**Responsável pela implementação/verificação:** [ATY] Antigravity
**Autoridade final:** [SILAS] Silas
**Última atualização:** 2026-09-20

---

## 1. OBJETIVO

Este documento estabelece a base técnica oficial do projeto Unreal Engine 5.

Seu objetivo é impedir que decisões de implementação sejam tomadas com base em:

* memória desatualizada de modelos de IA;
* tutoriais antigos;
* APIs depreciadas;
* workflows incompatíveis com a versão instalada;
* plugins incompatíveis;
* recursos que funcionam no PC, mas não são adequados ao Android.

### Regra fundamental

> **A versão instalada do Unreal Engine + documentação oficial correspondente + comportamento verificado no projeto têm prioridade sobre o conhecimento prévio de qualquer agente de IA.**

Nenhum agente deve assumir que uma funcionalidade continua igual sem verificar sua validade na versão utilizada pelo projeto.

---

# 2. VERSÃO OFICIAL DO UNREAL ENGINE

**Versão instalada:** `A VERIFICAR PELO [ATY]`

**Build:** `A VERIFICAR`

**Launcher/instalação:** `A VERIFICAR`

**Data da verificação:** `A PREENCHER`

### Procedimento obrigatório

O [ATY] deve:

1. abrir o projeto no ambiente real;
2. verificar a versão exata do Unreal Engine;
3. registrar a versão e build;
4. verificar mudanças relevantes dessa versão;
5. registrar qualquer incompatibilidade conhecida.

Não utilizar simplesmente a versão presumida pelo modelo.

---

# 3. HARDWARE DE DESENVOLVIMENTO

Máquina principal de desenvolvimento:

* **CPU:** AMD Ryzen 7 7735HS
* **GPU:** NVIDIA GeForce RTX 4050 Laptop GPU
* **VRAM:** 6 GB
* **RAM:** 16 GB DDR5
* **Sistema:** Windows 11 Pro
* **Display:** 1920×1080 / 165 Hz

### Observação

A máquina é adequada para desenvolvimento do projeto, porém o orçamento de memória e VRAM deve ser considerado desde o início.

O projeto não deve depender de configurações extremas do editor apenas porque a máquina de desenvolvimento consegue executá-las.

---

# 4. PLATAFORMA-ALVO

## Desenvolvimento inicial

**PC Windows**

Objetivo:

* desenvolver;
* testar;
* criar conteúdo;
* validar gameplay;
* depurar;
* perfilar.

## Plataforma comercial planejada

**Android**

O Android é o alvo de produto, portanto decisões gráficas devem considerar desde cedo:

* memória;
* GPU mobile;
* draw calls;
* overdraw;
* tamanho de textura;
* quantidade de foliage;
* sombras;
* partículas;
* iluminação;
* tempo de carregamento;
* consumo de bateria;
* temperatura;
* tamanho final do aplicativo.

### Regra

> O projeto não deve ser desenvolvido como um jogo PC que será “convertido para mobile no final”.

A arquitetura deve permitir redução controlada de qualidade.

---

# 5. RENDERIZAÇÃO

## Nanite

**Status:** A VERIFICAR NA VERSÃO DO PROJETO.

O [ATY] deve verificar:

* suporte na versão utilizada;
* limitações relevantes para Android;
* impacto sobre memória;
* compatibilidade com os assets escolhidos;
* necessidade de versões alternativas dos assets.

Não assumir que um asset marcado como “Nanite compatible” é automaticamente adequado para Android.

---

## Lumen

**Status:** A VERIFICAR.

O [ATY] deve verificar:

* suporte na plataforma-alvo;
* custo de execução;
* qualidade necessária;
* alternativas de iluminação;
* impacto sobre bateria e temperatura;
* possibilidade de utilizar iluminação pré-calculada ou híbrida quando apropriado.

### Princípio

O visual desejado é cinematográfico, mas **performance é requisito de produto**.

---

# 6. WORLD / MAPA

O ambiente principal será um cenário de:

**deserto + rancho + áreas anômalas.**

O mapa deve priorizar:

* grande sensação de escala;
* baixo custo de renderização;
* pontos de interesse;
* áreas exploráveis;
* áreas bloqueadas naturalmente;
* montanhas e formações rochosas como limites;
* caminhos e estradas;
* rancho como núcleo do gameplay.

### World Partition

**Status:** A VERIFICAR.

O [ATY] deve determinar se World Partition é adequado ao tamanho real do mapa.

Não utilizar World Partition apenas por ser uma tecnologia disponível.

---

# 7. LANDSCAPE

O Landscape deve ser estruturado para permitir:

* terreno desértico;
* areia;
* terra;
* pedra;
* áreas de vegetação;
* áreas de interesse;
* possíveis regiões anômalas.

### Automaterial

O sistema de material deve permitir expansão futura sem reconstrução completa do terreno.

Possíveis camadas:

* Sand
* Dirt
* Rock
* Gravel
* Dry Soil
* Anomaly Ground
* Road/Track

O sistema definitivo será decidido após análise dos assets disponíveis.

---

# 8. FOLIAGE

O ambiente desértico será utilizado como vantagem de performance.

Prioridades:

* cactos;
* arbustos secos;
* pequenas plantas;
* grama extremamente localizada;
* árvores apenas quando justificadas pela ambientação.

Evitar vegetação densa desnecessária.

### Objetivo

Criar a sensação de um enorme deserto sem exigir milhares de objetos simultaneamente visíveis.

---

# 9. NIAGARA

**Status:** A VERIFICAR.

Niagara será considerado para:

* poeira;
* vento;
* partículas;
* areia;
* efeitos de anomalias;
* luzes;
* efeitos atmosféricos;
* fenômenos UFO/UAP;
* distorções;
* eventos sobrenaturais.

Cada efeito deve possuir orçamento de performance.

---

# 10. INPUT

**Sistema preferencial:** Enhanced Input, sujeito à verificação da versão instalada.

Controles planejados:

### PC

* WASD
* mouse
* interação
* câmera
* sprint
* equipamento
* câmera de investigação

### Android

* joystick virtual
* câmera por toque
* interação contextual
* botões mínimos
* controles adaptados à tela.

O sistema de input deve ser abstraído para permitir múltiplas plataformas.

---

# 11. CÂMERA / FOUND FOOTAGE

A câmera é um dos sistemas centrais do jogo.

Ela poderá representar:

* câmera portátil;
* câmera de investigação;
* visão noturna;
* gravação;
* zoom;
* ruído;
* interferência;
* falhas;
* alterações de imagem;
* evidências visuais.

O sistema deve separar:

**Câmera real do jogador**

de

**processamento visual da gravação.**

Isso permitirá produzir efeitos como:

* glitch;
* frame perdido;
* ruído;
* distorção;
* alteração de exposição;
* timestamp;
* interferência.

---

# 12. SISTEMA DE FENÔMENOS

O jogo terá um sistema modular de fenômenos.

Categorias iniciais:

1. UAP/luzes;
2. orbs;
3. interferência eletromagnética;
4. falhas de equipamentos;
5. desaparecimento de animais;
6. sons/vozes;
7. anomalias espaciais;
8. alterações ambientais;
9. criaturas;
10. eventos de investigação;
11. evidências incompletas;
12. eventos raros.

### Princípio

Os fenômenos não devem depender exclusivamente de scripts lineares.

Sempre que tecnicamente viável, devem utilizar sistemas configuráveis para permitir:

* eventos raros;
* variação;
* condições;
* localização;
* horário;
* intensidade;
* probabilidade;
* progressão.

---

# 13. SISTEMA DE INVESTIGAÇÃO

Equipamentos planejados:

* câmera;
* lanterna;
* visão noturna;
* rádio;
* GPS;
* sensores;
* gravador;
* instrumentos de medição;
* equipamentos instaláveis.

O jogador deve poder coletar evidências e posteriormente analisá-las.

---

# 14. SISTEMA DE ENERGIA

Equipamentos poderão consumir recursos.

Exemplos:

* bateria da câmera;
* bateria da lanterna;
* gerador;
* equipamentos de monitoramento;
* veículo.

A economia de energia deve ser configurável.

---

# 15. VEÍCULO

O veículo será elemento de exploração e narrativa.

Não será o foco principal do gameplay.

Funções possíveis:

* transporte;
* armazenamento;
* iluminação;
* rádio;
* bateria;
* ponto de referência;
* início da história;
* eventual sistema de falha/anomalia.

O sistema de veículo deve ser implementado somente após definição do escopo do MVP.

---

# 16. ÁUDIO

Áudio é considerado componente crítico do horror.

Possíveis sistemas:

* vento;
* rádio;
* interferência;
* animais;
* passos;
* vozes;
* sons distantes;
* sons posicionais;
* silêncio dinâmico;
* eventos sonoros anômalos.

Evitar depender exclusivamente de jumpscares visuais.

---

# 17. PERFORMANCE

O projeto deve possuir orçamento técnico desde o início.

O [ATY] deverá registrar posteriormente:

* FPS alvo;
* resolução alvo;
* memória máxima;
* VRAM;
* draw calls;
* custo de shaders;
* custo de foliage;
* custo de partículas;
* tamanho dos mapas;
* tempo de carregamento;
* consumo aproximado de bateria.

### Regra

> Toda funcionalidade visual deve possuir uma estratégia de redução de qualidade.

Exemplo:

**High → Medium → Low → Mobile**

---

# 18. FAB / ASSETS DE TERCEIROS

Assets externos serão avaliados antes de integração.

Para cada asset relevante:

* origem;
* licença;
* compatibilidade com UE5;
* compatibilidade com Android;
* Nanite;
* materiais;
* quantidade de LODs;
* tamanho das texturas;
* colisão;
* animações;
* custo de performance.

### Regra

Não adicionar dezenas de assets ao projeto apenas porque são visualmente atraentes.

Primeiro validar:

**licença + compatibilidade + performance + necessidade.**

---

# 19. PLUGINS

Nenhum plugin deve ser adicionado sem registrar:

* nome;
* versão;
* fornecedor;
* finalidade;
* licença;
* compatibilidade com a versão do UE;
* impacto sobre Android;
* dependências;
* risco de abandono;
* necessidade real.

Plugins não essenciais devem ser evitados durante o MVP.

---

# 20. DOCUMENTAÇÃO OFICIAL

Sempre que uma decisão técnica depender de comportamento específico do Unreal Engine, o [ATY] deverá priorizar:

1. documentação oficial da Epic Games;
2. documentação específica da versão instalada;
3. testes no projeto;
4. resultados de profiling;
5. fontes secundárias somente como complemento.

Tutoriais antigos não devem ser tratados como autoridade.

---

# 21. PROTOCOLO DE VERIFICAÇÃO DO [ATY]

Antes de implementar uma tecnologia relevante:

### PASSO 1

Identificar a versão exata do UE5.

### PASSO 2

Verificar a documentação correspondente.

### PASSO 3

Verificar compatibilidade com Android.

### PASSO 4

Criar teste mínimo quando houver dúvida.

### PASSO 5

Validar no projeto real.

### PASSO 6

Registrar resultado.

### PASSO 7

Somente então utilizar a tecnologia no sistema principal.

---

# 22. REGISTRO DE ALTERAÇÕES

| Data       | Item             | Estado      | Responsável |
| ---------- | ---------------- | ----------- | ----------- |
| 2026-09-20 | Documento criado | Inicial     | [CTGT]      |
| —          | Versão UE5       | A verificar | [ATY]       |
| —          | Android baseline | A verificar | [ATY]       |
| —          | Nanite           | A verificar | [ATY]       |
| —          | Lumen            | A verificar | [ATY]       |
| —          | World Partition  | A verificar | [ATY]       |
| —          | Niagara          | A verificar | [ATY]       |
| —          | Enhanced Input   | A verificar | [ATY]       |

---

# 23. DECISÕES PENDENTES

Antes do início da produção:

* [ ] confirmar versão exata do UE5;
* [ ] confirmar target Android;
* [ ] definir FPS alvo;
* [ ] definir resolução alvo;
* [ ] avaliar Lumen;
* [ ] avaliar Nanite;
* [ ] avaliar World Partition;
* [ ] definir estratégia de Landscape;
* [ ] definir sistema de foliage;
* [ ] avaliar assets Fab;
* [ ] definir pipeline de iluminação;
* [ ] pipeline de build Android;
* [ ] definir orçamento de memória;
* [ ] definir orçamento de draw calls;
* [ ] definir estratégia de qualidade gráfica;
* [ ] realizar teste de performance inicial.

---

# 24. REGRA FINAL

Este documento não deve ser tratado como uma especificação permanente.

Ele é um **baseline técnico vivo**.

Sempre que a versão do Unreal Engine, plataforma, plugin, renderer ou requisito técnico mudar, o documento deve ser atualizado.

---

**[CTGT]** estratégia e arquitetura.
**[ATY]** implementação e verificação técnica.
**[SILAS]** autoridade final sobre decisões do projeto.
