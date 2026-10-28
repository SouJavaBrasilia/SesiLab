# Histórias de usuário

## HU01 — Login

### DESCRIÇÃO

- **Como:** Administrador ou Controlador de estoque
- **Desejo:** entrar no sistema com meu usuário e senha
- **Para que:** eu acesse as funções do meu perfil e minhas ações fiquem registradas no meu nome

### DEFINIÇÃO DE NEGÓCIO

Só dois perfis têm login: Administrador e Controlador de estoque. A turma não tem login. Os participantes usam só o totem. O login é a base da rastreabilidade: toda movimentação grava quem registrou (P6).

### REFERÊNCIA

- P2 (login só para Admin e Controlador), P6 (rastreabilidade).
- Seção 5 — Perfis.

### PROTÓTIPOS / TELAS

- Tela de login

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Planilhas sem controle de acesso | Acesso só com login, por perfil |
| Não se sabe quem alterou o quê | Toda ação fica ligada ao usuário logado |

### CRITÉRIOS DE NEGÓCIO

- [ ] Login com usuário e senha.
- [ ] Só usuários ativos com perfil Administrador ou Controlador conseguem entrar.
- [ ] Erro de login mostra uma mensagem genérica ("Usuário ou senha inválidos"), sem dizer qual dos dois está errado.
- [ ] Após o login, o usuário vê só o menu do seu perfil (ver HU03).
- [ ] Existe a opção "Sair", que encerra a sessão.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Login válido**

- Dado que sou um usuário ativo com perfil Controlador
- Quando informo usuário e senha corretos
- Então acesso a tela inicial com o menu do Controlador

**Cenário: Senha errada**

- Dado que sou um usuário cadastrado
- Quando informo a senha errada
- Então vejo "Usuário ou senha inválidos"
- E continuo na tela de login

**Cenário: Usuário inativo**

- Dado que meu usuário foi inativado
- Quando informo usuário e senha corretos
- Então o acesso é negado

**Cenário: Sair**

- Dado que estou logado
- Quando clico em "Sair"
- Então a sessão é encerrada e volto para a tela de login

## HU02 — Cadastro de usuários

- **Status:** Não iniciada
- **Data:** Vazio
- **Responsável:** Vazio
- **Épicos:** ÉPICO 1 — ACESSO

### Comentários

> **Mayara Amorim — 22 de out.**
>
> Observação: confirmar se o Administrador pode inativar o próprio usuário e se deve existir sempre ao menos um Administrador ativo.

### DESCRIÇÃO

- **Como:** Administrador
- **Desejo:** cadastrar, editar e inativar usuários, definindo o perfil de cada um
- **Para que:** só as pessoas autorizadas operem o estoque, cada uma com as permissões do seu perfil

### DEFINIÇÃO DE NEGÓCIO

Só o Administrador gerencia usuários (seção 5, T60). Os perfis possíveis são Administrador e Controlador de estoque. O usuário é inativado, não excluído, para que o histórico continue mostrando quem fez cada movimentação (P6).

### REFERÊNCIA

T60 Usuários;
seção 5 — Perfis;
P2, P6;

### PROTÓTIPOS / TELAS

- T60 — lista de usuários e formulário de cadastro.

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Não existe cadastro de quem opera o estoque | Cadastro de usuários com perfil |

### CRITÉRIOS DE ACEITE

- [ ] Campos: nome (obrigatório), login (obrigatório e único), perfil (obrigatório; Administrador ou Controlador de estoque) e situação (ativo/inativo).
- [ ] Não é permitido cadastrar dois usuários com o mesmo login.
- [ ] Usuário inativo não consegue entrar (HU01).
- [ ] Usuário inativado continua aparecendo no histórico das movimentações que registrou.
- [ ] A lista de usuários permite buscar por nome e filtrar por perfil e situação.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Cadastrar Controlador**

- Dado que sou Administrador
- Quando cadastro um usuário com nome, login e perfil "Controlador de estoque"
- Então o usuário passa a conseguir entrar com o perfil de Controlador

**Cenário: Login repetido**

- Dado que já existe um usuário com o login "maria.silva"
- Quando tento cadastrar outro usuário com o mesmo login
- Então o sistema impede e informa que o login já está em uso

**Cenário: Inativar usuário**

- Dado que um Controlador registrou movimentações
- Quando eu o inativo
- Então ele não consegue mais entrar
- E as movimentações dele continuam mostrando o seu nome no histórico

## HU03 — Permissões por perfil

### DESCRIÇÃO

- **Como:** Administrador
- **Desejo:** que cada perfil acesse apenas as funções permitidas a ele
- **Para que:** as configurações do sistema fiquem protegidas e o Controlador trabalhe só com a operação do estoque

### DEFINIÇÃO DE NEGÓCIO

O Administrador faz tudo o que o Controlador faz e mais a administração do sistema (seção 5). O Controlador cuida da operação: itens, locais, turmas, oficinas, movimentações e consultas.

### REFERÊNCIA

- Seção 5 — Perfis; seção 6.7 — Administração.
- Resposta 3 do produto: a categoria do local é definida somente pelo Administrador.

### PROTÓTIPOS / TELAS

- Menu por perfil

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Qualquer pessoa com acesso à planilha altera tudo | Cada perfil vê e altera só o que lhe cabe |

### CRITÉRIOS DE NEGÓCIO

- [ ] Somente o Administrador acessa:
- usuários (HU02);
- cadastros auxiliares (ambientes, tipos de local, categorias de local, ícones e unidades — HU04 a HU08);
- totens (HU16).
- [ ] Administrador e Controlador acessam:
- locais (HU09) e mapa (HU10);
- item consumível (HU11), patrimônio (HU12) e caixas de oficina (HU13);
- turmas (HU14) e oficinas (HU15);
- entrada, transferência, ajuste/baixa e histórico (HU17 a HU20).
- [ ] Uma função fora do perfil não aparece no menu.
- [ ] O acesso direto a uma função fora do perfil, por endereço, é negado.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Controlador não vê administração**

- Dado que estou logado como Controlador
- Quando abro o menu
- Então não vejo Usuários, Cadastros auxiliares nem Totens

**Cenário: Acesso direto negado**

- Dado que estou logado como Controlador
- Quando acesso diretamente o endereço da tela de Usuários
- Então o acesso é negado

**Cenário: Administrador vê tudo**

- Dado que estou logado como Administrador
- Quando abro o menu
- Então vejo as funções do Controlador e as de administração

## HU04 — Cadastro de ambientes

### DESCRIÇÃO

- **Como:** Administrador
- **Desejo:** cadastrar os ambientes (ex.: Maker, Biomaker, Educativo, Estoque Educativo, Depósito externo)
- **Para que:** todo local de armazenamento pertença a um ambiente e o estoque possa ser consultado por ambiente

### DEFINIÇÃO DE NEGÓCIO

O ambiente é o primeiro nível da hierarquia Ambiente → Tipo de local → Local (seção 2). Cada ambiente é interno (onde há atividades) ou depósito externo (Guará, SAAN). Os depósitos não são ambientes de oficina (P12, P14).

### REFERÊNCIA

- Seção 2 — Ambientes e locais; P12; P14.

### PROTÓTIPOS / TELAS

- T61 — Cadastros auxiliares › Ambientes.

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Cada ambiente é um arquivo Excel separado (Maker, Biomaker, Educativo, Estoque Educativo, Depósitos) | Ambientes cadastrados em uma lista única |

### CRITÉRIOS DE NEGÓCIO

- [ ] Campos: nome (obrigatório e único), tipo (obrigatório; Interno ou Depósito externo) e prefixo de código (opcional, informativo — ex.: M, B, E).
- [ ] Carga inicial sugerida (seção 2): Maker (M), Biomaker (B), Educativo (E), Estoque Educativo (Experimento Lab) e Depósito externo.
- [ ] Não é permitido dois ambientes com o mesmo nome.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Cadastrar ambiente interno**

- Dado que sou Administrador
- Quando cadastro o ambiente "Maker" com tipo "Interno"
- Então ele passa a estar disponível no cadastro de locais

**Cenário: Nome repetido**

- Dado que já existe o ambiente "Biomaker"
- Quando tento cadastrar outro ambiente "Biomaker"
- Então o sistema impede e informa que o nome já existe

## HU05 — Cadastro de tipos de local

### DESCRIÇÃO

- **Como:** Administrador
- **Desejo:** cadastrar os tipos de local (Armário, Gaveta, Armário Suspenso, Carrinho, Prateleira, Posição, Depósito)
- **Para que:** cada local seja classificado de forma padronizada

### DEFINIÇÃO DE NEGÓCIO

O tipo é o segundo nível da hierarquia. Hoje o tipo só aparece no título das abas ("Armário Maker 01", "Gaveta Maker 2", "Carrinho Maker 4 - Impressão 3D").

### REFERÊNCIA

- Seção 2 — Ambientes e locais; P4 (listas de seleção evitam erros de grafia).

### PROTÓTIPOS / TELAS

- T61 — Cadastros auxiliares › Tipos de local — protótipo pendente.

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Tipo deduzido do título da aba | Tipo escolhido em uma lista |

### CRITÉRIOS DE NEGÓCIO

- [ ] Campo: nome (obrigatório e único).
- [ ] Carga inicial: Armário, Gaveta, Armário Suspenso, Carrinho, Prateleira, Posição e Depósito.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Cadastrar tipo**

- Dado que sou Administrador
- Quando cadastro o tipo "Gaveta"
- Então ele passa a aparecer na lista de tipos do cadastro de local

## HU06 — Cadastro de categorias de local

### DESCRIÇÃO

- **Como:** Administrador
- **Desejo:** manter a lista de categorias de local (ex.: EPIs, Eletrônica, Reagentes, Vidraria)
- **Para que:** os locais sejam classificados sem variação de grafia e a etiqueta física mostre a categoria correta

### DEFINIÇÃO DE NEGÓCIO

A categoria fica vinculada ao local, e somente o Administrador a define (resposta 3 do produto). Hoje ela é digitada livremente na aba Etiquetas de cada arquivo.

### REFERÊNCIA

- Seção 2 — Etiquetas; P4; resposta 3 do produto.
- Observação: o estoque mínimo por categoria (P13) não faz parte desta história. Está pendente porque a categoria foi para o local, e há locais que guardam materiais de todo tipo (M07, MS03, MS04).

### PROTÓTIPOS / TELAS

- T61 — Cadastros auxiliares › Categorias de local.

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Categoria digitada à mão na aba Etiquetas | Categoria escolhida em lista mantida pelo Administrador |
| Mesma categoria com grafias diferentes ("Aviamento" e "Aviamentos", "EPIs" e "EPI's", "Oficinas" e "Oficinas Educativas") | Uma grafia por categoria |

### CRITÉRIOS DE NEGÓCIO

- [ ] Campo: nome (obrigatório e único, sem diferenciar maiúsculas e minúsculas).
- [ ] Só o Administrador cria, edita e inativa categorias.
- [ ] Categoria inativa não aparece para novos locais, mas continua nos locais que já a usam.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Cadastrar categoria**

- Dado que sou Administrador
- Quando cadastro a categoria "Vidraria"
- Então ela passa a aparecer na lista de categorias do cadastro de local

**Cenário: Grafia repetida**

- Dado que já existe a categoria "Aviamentos"
- Quando tento cadastrar "aviamentos"
- Então o sistema impede e informa que a categoria já existe
(WIP) HU07 — Cadastro de ícones

### DESCRIÇÃO

- **Como:** Administrador
- **Desejo:** manter a lista de ícones usados nas etiquetas (ex.: Máscara, Chip, Cata-vento, Microscópio)
- **Para que:** cada local tenha um ícone padronizado e fácil de reconhecer no armário físico

### DEFINIÇÃO DE NEGÓCIO

O ícone é o pictograma da etiqueta física do local (seção 2 — Etiquetas). Hoje ele é só um nome digitado na aba Etiquetas.

### REFERÊNCIA

- Seção 2 — Etiquetas; P4.
- Observação: confirmar se o ícone terá imagem carregada no sistema ou se será só o nome.

### PROTÓTIPOS / TELAS

- T61 — Cadastros auxiliares › Ícones

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Nome do ícone digitado ("Erlenmeyer e proveta", "Erlenmeyerr e proveta") | Ícone escolhido em lista |

### CRITÉRIOS DE NEGÓCIO

- [ ] Campo: nome (obrigatório e único). Imagem do ícone: a confirmar.
- [ ] Só o Administrador cria, edita e inativa ícones.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Cadastrar ícone**

- Dado que sou Administrador
- Quando cadastro o ícone "Microscópio"
- Então ele passa a aparecer na lista de ícones do cadastro de local

## HU08 — Cadastro de unidades de medida

### DESCRIÇÃO

- **Como:** Administrador
- **Desejo:** manter a lista de unidades (caixa, pacote, unidade, rolo, pote, kit…) e indicar quais aceitam fração
- **Para que:** as quantidades sejam registradas sempre na mesma unidade e com o formato correto

### DEFINIÇÃO DE NEGÓCIO

Hoje a unidade é texto livre. A quantidade é decimal para permitir frações, como meio pacote (seção 3.1), mas só nas unidades em que isso faz sentido.

### REFERÊNCIA

- Seção 3.1 (Qtd. decimal ≥ 0; Unidade via lista); P4.

### PROTÓTIPOS / TELAS

- T61 — Cadastros auxiliares › Unidades — protótipo pendente.

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| 61 grafias diferentes de unidade nos três arquivos de armários (Unidade/unidade/unidades, Caixa/caixas, "Caica") | Unidade escolhida em lista |
| Quantidade às vezes como texto ("½") | Quantidade sempre numérica |

### CRITÉRIOS DE NEGÓCIO

- [ ] Campos: nome (obrigatório e único), sigla (opcional) e "permite fração" (sim/não).
- [ ] Carga inicial (seção 3.1): caixa, pacote, unidade, rolo, pote, kit, lata, bobina, placa, maleta. A unidade "cm" depende da confirmação acima.
- [ ] Em unidades que não permitem fração, o sistema aceita só números inteiros.
- [ ] Em unidades que permitem fração, o sistema aceita números decimais.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Unidade sem fração**

- Dado que a unidade "kit" não permite fração
- Quando alguém informa 1,5 kit em uma movimentação
- Então o sistema não aceita e pede um número inteiro

**Cenário: Unidade com fração**

- Dado que a unidade "pacote" permite fração
- Quando alguém informa 0,5 pacote
- Então o sistema aceita

## HU09 — Cadastro de locais

### DESCRIÇÃO

- **Como:** Controlador de estoque ou Administrador
- **Desejo:** cadastrar cada local de armazenamento (armário, gaveta, carrinho, prateleira, posição, depósito) com código, ambiente, tipo, categoria e ícone
- **Para que:** todo material tenha um endereço físico conhecido e a etiqueta do local seja padronizada

### DEFINIÇÃO DE NEGÓCIO

O local é o último nível da hierarquia Ambiente → Tipo de local → Local. Ele substitui a aba Etiquetas e o nome das abas (M01, BG05, E12…). Pela seção 2, são 115 locais: Maker 58, Biomaker 25, Educativo 14, Estoque Educativo 16 e Depósitos 2.

### REFERÊNCIA

- Seção 2 — Ambientes e locais / Etiquetas; T23; resposta 3 do produto.

### PROTÓTIPOS / TELAS

- T23 — Cadastro de local — protótipo pendente.

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Local = nome da aba + linha na aba Etiquetas, em três arquivos | Cadastro único de locais |
| Estoque Educativo e Depósitos não têm aba Etiquetas | Todos os locais no mesmo cadastro |
| Etiqueta MS16 sem aba correspondente; aba Etiquetas fora de sincronia com as abas | O local existe uma vez só |

### CRITÉRIOS DE NEGÓCIO

- [ ] Campos:
- código (obrigatório e único — ex.: M01, BG05, E12, Experimento 33, Guará);
- ambiente (obrigatório, lista da HU04);
- tipo de local (obrigatório, lista da HU05);
- categoria (lista da HU06; obrigatoriedade a confirmar);
- ícone (lista da HU07; obrigatoriedade a confirmar);
- resumo do conteúdo (texto, opcional);
- observação (texto, opcional — ex.: "Chave no claviculário");
- link de conteúdo (opcional, reservado para uso futuro — P5).
- [ ] Não é permitido dois locais com o mesmo código.
- [ ] A lista de locais permite filtrar por ambiente, tipo e categoria.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Cadastrar gaveta**

- Dado que existem o ambiente "Maker" e o tipo "Gaveta"
- Quando cadastro o local "MG02" no ambiente Maker, tipo Gaveta, categoria Eletrônica
- Então o local passa a aparecer no mapa de ambientes (HU10)

**Cenário: Código repetido**

- Dado que já existe o local "M01"
- Quando tento cadastrar outro local "M01"
- Então o sistema impede e informa que o código já existe

**Cenário: Campo obrigatório**

- Dado que estou cadastrando um local
- Quando salvo sem informar o ambiente
- Então o sistema não salva e indica que o ambiente é obrigatório

## HU10 — Mapa de ambientes e locais

### DESCRIÇÃO

- **Como:** Controlador de estoque ou Administrador
- **Desejo:** navegar em uma árvore Ambiente → Local e abrir um local para ver o que há nele
- **Para que:** eu encontre rapidamente onde está cada material, sem procurar em várias planilhas

### DEFINIÇÃO DE NEGÓCIO

O mapa substitui a navegação pelas abas (M01, B05…) dos arquivos Excel. Abrir um local mostra os itens e as quantidades guardadas nele.

### REFERÊNCIA

- T22 — Mapa de ambientes/locais; seção 2.

### PROTÓTIPOS / TELAS

- T22.

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| 96 abas de armário em três arquivos + uma lista no Estoque Educativo + uma lista de Depósitos | Uma árvore única de ambientes e locais |

### CRITÉRIOS DE NEGÓCIO

- [ ] A árvore mostra os ambientes e, dentro de cada um, os seus locais, agrupados por tipo.
- [ ] Ao abrir um local, o sistema mostra:
- os dados do local (tipo, categoria, ícone, observação);
- os itens guardados nele, com quantidade e unidade.
- [ ] Permite buscar um local pelo código.
- [ ] É só consulta: alterações são feitas nas telas de cadastro e de movimentação.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Ver conteúdo de um local**

- Dado que o local "M01" tem itens com saldo
- Quando abro o local "M01" no mapa
- Então vejo os dados do local e a lista de itens com quantidade e unidade

**Cenário: Local vazio**

- Dado que o local "MS05" não tem itens
- Quando abro o local "MS05"
- Então vejo a mensagem "Nenhum item neste local"

## HU11 — Cadastro de item consumível

- **Status:** Não iniciada
- **Data:** 22 de outubro de 2026 → 22 de novembro de 2026
- **Responsável:** Vazio
- **Épicos:** ÉPICO 3 — CATÁLOGO

### Comentários

> **Mayara Amorim — 22 de out.**
>
> Observações: ◦ Categoria do item: pela resposta 3, a categoria fica no local, então o item não tem campo de categoria. Mas o 2026_Materiais_Estoque_Educativo.xlsx traz categoria por item (Papelaria, Armarinho, Eletrônica…). Confirmar se essa informação será descartada. ◦ Itens de mesmo nome: há itens com o mesmo nome e descrição diferente (ex.: "Proveta graduada 100ML" azul e vermelha, em B09). Definir se viram itens diferentes ou um só. ◦ A marcação "pode ser retirado/emprestado" está pendente e não faz parte desta história.

### DESCRIÇÃO

- **Como:** Controlador de estoque ou Administrador
- **Desejo:** cadastrar os itens consumíveis (materiais que são gastos nas oficinas) em um catálogo único
- **Para que:** cada material exista uma vez só no sistema, com o saldo controlado por local

### DEFINIÇÃO DE NEGÓCIO

Consumível é o material que sai e não volta (P9). O cadastro de consumíveis é separado do cadastro de patrimônio (resposta 2 do produto). Hoje o mesmo material aparece em várias abas como linhas independentes (ex.: "Barbante" em 3 locais do Maker). No sistema, o item é cadastrado uma vez e tem saldo em cada local.

### REFERÊNCIA

- Seções 3.1 e 3.2; T21; P4, P5, P9; resposta 2 do produto.

### PROTÓTIPOS / TELAS

- T20 — Catálogo; T21 — Cadastro de item

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Item é uma linha de planilha, repetida em várias abas | Item cadastrado uma vez, com saldo por local |
| Nome e unidade digitados livremente | Unidade escolhida em lista (HU08) |
| Unidade misturada ao nome ("Pacotes com Clipes para bateria 9V") | Nome, unidade e descrição em campos separados |

### CRITÉRIOS DE NEGÓCIO

Campos:
- nome (obrigatório);
- unidade (obrigatória, lista da HU08);
- descrição (opcional — especificação, marca, conteúdo da embalagem, dimensões);
- foto (opcional);
- situação (ativo/inativo);
- Cód. Protheus e Referência (opcionais, reservados para uso futuro — P5).
- [ ] O item não tem saldo próprio no cadastro: o saldo nasce só pela entrada de material (HU17).
- [ ] Item inativo não aceita novas entradas, mas continua no histórico.
- [ ] O catálogo permite buscar por nome e ver o saldo total e o saldo por local.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Cadastrar item**

- Dado que sou Controlador
- Quando cadastro o item "Cola bastão 40g" com unidade "unidade"
- Então ele aparece no catálogo com saldo zero

**Cenário: Saldo por local**

- Dado que o item "Barbante" tem saldo em três locais
- Quando abro o item no catálogo
- Então vejo o saldo de cada local e o saldo total

**Cenário: Unidade obrigatória**

- Dado que estou cadastrando um item
- Quando salvo sem escolher a unidade
- Então o sistema não salva e indica que a unidade é obrigatória

## HU12 — Cadastro de patrimônio

### DESCRIÇÃO

- **Como:** Controlador de estoque ou Administrador
- **Desejo:** cadastrar os equipamentos de patrimônio (notebook, câmera, ferramentas e similares) separados dos consumíveis
- **Para que:** eu saiba onde cada equipamento está, sem que ele seja tratado como material de consumo

### DEFINIÇÃO DE NEGÓCIO

Patrimônio não é consumido. Ele fica cadastrado no seu local para localização e inventário (P11). O cadastro é separado do de consumíveis, e Administrador e Controlador podem cadastrar (resposta 2 do produto). No MVP, o patrimônio só muda de lugar por transferência (HU18) ou sai por baixa patrimonial (HU19).

### REFERÊNCIA

- P11; T21 (nº de patrimônio como campo futuro); resposta 2 do produto.

### PROTÓTIPOS / TELAS

- Cadastro de patrimônio — protótipo pendente.

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Equipamentos misturados com materiais nas abas (ex.: câmeras e microfones em M10, exaustores em M05) | Cadastro próprio de patrimônio |

### CRITÉRIOS DE NEGÓCIO

- [ ] Campos:
- nome (obrigatório);
- unidade (obrigatória, lista da HU08);
- descrição (opcional);
- foto (opcional);
- situação (ativo/inativo);
- nº de patrimônio (opcional, reservado para uso futuro).
- [ ] A quantidade e o local nascem pela entrada de material (HU17).
- [ ] Patrimônio não aparece no totem de retirada (P11).
- [ ] Patrimônio aceita só transferência e baixa patrimonial com motivo. Não aceita retirada por consumo.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Cadastrar patrimônio**

- Dado que sou Controlador
- Quando cadastro o patrimônio "Câmera fotográfica"
- Então ele aparece na lista de patrimônios e não aparece no catálogo de consumíveis

**Cenário: Patrimônio fora do totem**

- Dado que existe o patrimônio "Notebook" no local M10
- Quando um participante consulta os itens no totem do Maker
- Então o "Notebook" não aparece

## HU13 — Caixas de oficina nos depósitos externos

### DESCRIÇÃO

- **Como:** Controlador de estoque
- **Desejo:** controlar quantas caixas de cada oficina estão em cada depósito externo (Guará e SAAN)
- **Para que:** eu saiba onde estão as caixas de oficina e quantas existem, sem precisar listar o que há dentro delas

### DEFINIÇÃO DE NEGÓCIO

Nos depósitos, o controle é só pela quantidade de caixas (P14, confirmado na seção 10). Cada caixa de oficina é um item do tipo "caixa de oficina", contado em caixas ou maletas, e o conteúdo não é cadastrado. A caixa sai do depósito e volta a ele sempre por transferência (F5). Ela não aparece no totem.

### REFERÊNCIA

- P14; seção 3.3; F5; seção 10 — "Depósitos: controle somente por caixas".

### PROTÓTIPOS / TELAS

- Cadastro de caixa de oficina

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| 26 linhas na planilha de Depósitos: Guará 21 linhas / 38 volumes; SAAN 5 linhas / 24 volumes | Caixas cadastradas com saldo por depósito |
| "Data Entrada", "Descrição dos itens", "Link Etiqueta" e "Observação" sempre vazios | Data de entrada automática pela movimentação; demais campos reservados (P5) |
| A mesma caixa em dois depósitos é repetida em duas linhas ("Sesi Lab Escolas": 4 no Guará, 10 no SAAN) | Um item com saldo em cada depósito |

### CRITÉRIOS DE NEGÓCIO

- [ ] Campos:
- nome da caixa/oficina (obrigatório — ex.: "Ativação Robô na Rodô");
- unidade (obrigatória: caixa ou maleta);
- descrição dos itens (opcional, reservado — P5);
- link da etiqueta (opcional, reservado — P5);
- observação (opcional).
- [ ] A quantidade é sempre um número inteiro.
- [ ] O saldo nasce pela entrada (HU17) e muda por transferência (HU18) ou baixa (HU19).
- [ ] Caixa de oficina não aparece no totem.
- [ ] Só o Controlador e o Administrador movimentam caixas de oficina.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Caixa em dois depósitos**

- Dado que a caixa "Sesi Lab Escolas" tem 4 maletas no Guará e 10 no SAAN
- Quando consulto a caixa
- Então vejo 4 no Guará, 10 no SAAN e 14 no total

**Cenário: Quantidade fracionada**

- Dado que estou registrando caixas de oficina
- Quando informo 1,5 caixa
- Então o sistema não aceita e pede um número inteiro

## HU14 — Cadastro de turmas

### DESCRIÇÃO

- **Como:** Controlador de estoque ou Administrador
- **Desejo:** cadastrar as turmas que participam das oficinas
- **Para que:** o consumo de material possa ser atribuído à turma agendada

### DEFINIÇÃO DE NEGÓCIO

A turma não é usuário e não tem login (P2). É um cadastro que será ligado ao agendamento da oficina. Tudo o que sair do estoque no dia da oficina será atribuído à turma agendada (P3, resposta 1 do produto).

### REFERÊNCIA

- P2, P3; T40; resposta 1 do produto.

### PROTÓTIPOS / TELAS

- T40 — Cadastro de turmas — protótipo pendente.

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Não se sabe qual turma consumiu cada material | Turma cadastrada, pronta para ser ligada ao agendamento |

### CRITÉRIOS DE NEGÓCIO

- [ ] Campos: nome (obrigatório), instituição, nome do responsável, contato e situação (ativa/inativa).
- [ ] Turma inativa não pode ser usada em novos agendamentos, mas continua no histórico.
- [ ] A lista permite buscar por nome e instituição.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Cadastrar turma**

- Dado que sou Controlador
- Quando cadastro uma turma com nome, instituição e responsável
- Então a turma aparece na lista de turmas ativas

**Cenário: Inativar turma**

- Dado que a turma já tem consumo registrado
- Quando eu a inativo
- Então ela não aparece para novos agendamentos
- E o consumo dela continua no histórico

## HU15 — Cadastro de oficinas

### DESCRIÇÃO

- **Como:** Controlador de estoque ou Administrador
- **Desejo:** cadastrar as oficinas com seu ambiente e a lista de materiais prevista por realização
- **Para que:** eu saiba quanto material cada oficina costuma usar e possa planejar a reposição

### DEFINIÇÃO DE NEGÓCIO

A oficina (ex.: "Robô Treme-Treme", "Light Play") acontece em um ambiente. A lista de materiais prevista (item + quantidade) é a base para avisar quando o estoque não cobre uma oficina agendada (P10). A lista pode começar vazia e ser preenchida aos poucos (T41).

### REFERÊNCIA

- P10; T41.

### PROTÓTIPOS / TELAS

- T41 — Cadastro de oficinas

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Materiais das oficinas guardados em caixas sem lista ("Caixa organizadora com materiais da oficina Insetos Elétricos", E13) | Oficina cadastrada com lista de materiais prevista |

### CRITÉRIOS DE NEGÓCIO

- [ ] Campos:
- nome (obrigatório e único);
- descrição (opcional);
- ambiente (obrigatório, lista da HU04, só ambientes internos);
- lista de materiais prevista (opcional) — itens consumíveis (HU11) com quantidade por realização.
- [ ] A quantidade da lista respeita a regra de fração da unidade do item (HU08).
- [ ] O mesmo item não pode aparecer duas vezes na lista da mesma oficina.
- [ ] Patrimônio e caixa de oficina não entram na lista (não são consumidos — P11, P14).
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Cadastrar oficina com materiais**

- Dado que sou Controlador
- Quando cadastro a oficina "Robô Treme-Treme" no ambiente Maker com 2 itens na lista de materiais
- Então a oficina é salva com a lista prevista

**Cenário: Oficina sem lista**

- Dado que ainda não sei os materiais da oficina "Light Play"
- Quando cadastro a oficina sem lista de materiais
- Então ela é salva normalmente

**Cenário: Item repetido na lista**

- Dado que a oficina já tem "Motor 3v" na lista
- Quando tento adicionar "Motor 3v" de novo
- Então o sistema impede e sugere alterar a quantidade existente

## HU16 — Cadastro de totens

### DESCRIÇÃO

- **Como:** Administrador
- **Desejo:** cadastrar os totens e vincular cada um a um ambiente
- **Para que:** cada totem mostre apenas os itens do ambiente em que está instalado

### DEFINIÇÃO DE NEGÓCIO

Os participantes fazem a retirada nos totens da sala, sem login (P7). Pode haver um ou mais totens no mesmo ambiente (resposta 1 do produto). O Administrador cadastra o totem uma única vez e o vincula ao ambiente (T63).

### REFERÊNCIA

- P7; T63; resposta 1 do produto.

### PROTÓTIPOS / TELAS

- T63 — Totens — protótipo pendente.

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Não existe registro de retirada | Totens cadastrados por ambiente, prontos para o fluxo de retirada |

### CRITÉRIOS DE NEGÓCIO

- [ ] Campos: nome/identificação do totem (obrigatório e único), ambiente (obrigatório, só ambientes internos) e situação (ativo/inativo).
- [ ] Um ambiente pode ter vários totens.
- [ ] Totem inativo não funciona.
- [ ] Só o Administrador cadastra, edita e inativa totens.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Dois totens no mesmo ambiente**

- Dado que o Maker já tem o "Totem Maker 1"
- Quando cadastro o "Totem Maker 2" no Maker
- Então o Maker passa a ter dois totens ativos

**Cenário: Depósito não recebe totem**

- Dado que o "Depósito externo" é do tipo depósito
- Quando tento vincular um totem a ele
- Então o depósito não aparece na lista de ambientes disponíveis

### DESCRIÇÃO

- **Como:** Controlador de estoque ou Administrador
- **Desejo:** registrar a entrada de material em um local, informando a validade quando houver
- **Para que:** o saldo do local aumente e fique registrado quem incluiu, quando e com qual validade

### DEFINIÇÃO DE NEGÓCIO

A entrada é a única forma de o saldo nascer ou aumentar (fora o ajuste com motivo). Vale para consumível, patrimônio e caixa de oficina. A validade é opcional (P15 — ex.: reagentes do Biomaker). A data de entrada e o usuário são gravados automaticamente (P6), e o saldo nunca é editado à mão.

### REFERÊNCIA

- T30; F3; P6; P15; seção 3.3 (Data Entrada automática).

### PROTÓTIPOS / TELAS

- T30 — Entrada de material — protótipo pendente.

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Quantidade sobrescrita na planilha, sem histórico | Cada entrada é um registro com usuário e data/hora |
| Não se sabe quem incluiu o material (P6) | Usuário logado gravado automaticamente |
| "Data Entrada" sempre vazia nos Depósitos | Data/hora preenchida automaticamente |
| Validade não registrada | Validade opcional por entrada |

### CRITÉRIOS DE NEGÓCIO

- [ ] Campos: item (obrigatório, só itens ativos), local de destino (obrigatório), quantidade (obrigatória, maior que zero), validade (opcional) e observação (opcional — ex.: "1 com defeito").
- [ ] A unidade é a do item e aparece só para leitura.
- [ ] A quantidade respeita a regra de fração da unidade (HU08). Caixa de oficina aceita só inteiros (HU13).
- [ ] Data/hora e usuário são gravados automaticamente e não podem ser alterados.
- [ ] Ao salvar, o saldo do item no local aumenta na quantidade informada.
- [ ] Entradas com validade diferente do mesmo item no mesmo local ficam separadas, para que a validade de cada uma não se perca (P15).
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Entrada sem validade**

- Dado que o item "Cola bastão 40g" tem saldo 10 no local MG13
- Quando registro a entrada de 20 no MG13
- Então o saldo no MG13 passa a 30
- E a entrada fica registrada com meu usuário e a data/hora

**Cenário: Entrada com validade**

- Dado que o item é um reagente do Biomaker
- Quando registro a entrada informando a validade
- Então a entrada fica registrada com aquela validade

**Cenário: Quantidade inválida**

- Dado que estou registrando uma entrada
- Quando informo quantidade zero ou negativa
- Então o sistema não aceita

## HU18 — Transferência entre locais

### DESCRIÇÃO

- **Como:** Controlador de estoque ou Administrador
- **Desejo:** transferir material de um local para outro
- **Para que:** o saldo de cada local reflita onde o material realmente está (ex.: do depósito para o armário do ambiente da oficina)

### DEFINIÇÃO DE NEGÓCIO

A transferência tira o saldo da origem e coloca no destino, na mesma operação. Ela vale para consumível, patrimônio e caixa de oficina; patrimônio e caixa de oficina só mudam de lugar por transferência (P11, P14, F5). A transferência não é atribuída a nenhuma turma (F2).

### REFERÊNCIA

- T31; F2; F3a; F5; P6; P11; P14.

### PROTÓTIPOS / TELAS

- T31 — Transferência entre locais — protótipo pendente.

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Mudar material de lugar exige editar duas abas (ou dois arquivos) à mão | Uma operação baixa da origem e soma no destino |
| Não fica registro da mudança | Transferência registrada com usuário e data/hora |

### CRITÉRIOS DE NEGÓCIO

- [ ] Campos: item (obrigatório), local de origem (obrigatório, só locais com saldo do item), local de destino (obrigatório), quantidade (obrigatória, maior que zero) e observação (opcional).
- [ ] Origem e destino não podem ser o mesmo local.
- [ ] A quantidade não pode passar do saldo da origem. O saldo nunca fica negativo.
- [ ] A quantidade respeita a regra de fração da unidade (HU08).
- [ ] Origem e destino são atualizados juntos: ou os dois mudam, ou nenhum muda.
- [ ] A validade do material transferido é mantida no destino.
- [ ] Usuário e data/hora são gravados automaticamente.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Transferir do depósito para o carrinho**

- Dado que a caixa "Light Play" tem 8 caixas no SAAN
- Quando transfiro 2 caixas do SAAN para o carrinho MC02
- Então o SAAN fica com 6 e o MC02 com 2
- E a transferência fica registrada com meu usuário e a data/hora

**Cenário: Quantidade maior que o saldo**

- Dado que o item tem saldo 5 na origem
- Quando tento transferir 6
- Então o sistema impede e mostra o saldo disponível
- E nenhum saldo é alterado

**Cenário: Mesmo local**

- Dado que escolhi o local M07 como origem
- Quando escolho M07 também como destino
- Então o sistema não permite

## HU19 — Ajuste e baixa de estoque

### DESCRIÇÃO

- **Como:** Controlador de estoque ou Administrador
- **Desejo:** corrigir o saldo de um item ou dar baixa por perda, avaria ou vencimento, sempre informando o motivo
- **Para que:** o saldo fique correto e toda correção tenha justificativa registrada

### DEFINIÇÃO DE NEGÓCIO

O saldo nunca é editado diretamente: correção vira ajuste com motivo. A baixa tira material do estoque por perda, avaria ou vencimento. No patrimônio, é a baixa patrimonial (P11). Uso interno da equipe fora de oficina também é registrado aqui, sem turma (F2).

### REFERÊNCIA

- T32; F2; F6; P6; P11; seção 3.4 (motivo obrigatório em ajuste e baixa).

### PROTÓTIPOS / TELAS

- T32 — Ajuste / Baixa — protótipo pendente.

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Quantidade alterada na planilha sem motivo nem autor | Ajuste e baixa com motivo, usuário e data/hora |

### CRITÉRIOS DE NEGÓCIO

- [ ] Tipo da operação (obrigatório): Ajuste ou Baixa.
- [ ] Campos: item (obrigatório), local (obrigatório), quantidade (obrigatória), motivo (obrigatório) e observação (opcional).
- [ ] Motivos de baixa: perda, avaria, vencimento e uso interno da equipe. A lista de motivos pode ser ampliada pelo Administrador (a confirmar).
- [ ] O ajuste pode aumentar ou diminuir o saldo, conforme a opção definida na observação acima.
- [ ] A baixa só diminui o saldo e não pode passar do saldo do local. O saldo nunca fica negativo.
- [ ] A quantidade respeita a regra de fração da unidade (HU08).
- [ ] Sem motivo, a operação não é salva.
- [ ] Usuário e data/hora são gravados automaticamente.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Baixa por avaria**

- Dado que o item tem saldo 10 no local B07
- Quando registro baixa de 2 com motivo "avaria"
- Então o saldo no B07 passa a 8
- E a baixa fica registrada com motivo, usuário e data/hora

**Cenário: Sem motivo**

- Dado que estou registrando um ajuste
- Quando salvo sem motivo
- Então o sistema não salva e indica que o motivo é obrigatório

**Cenário: Baixa maior que o saldo**

- Dado que o item tem saldo 3 no local
- Quando tento dar baixa de 5
- Então o sistema impede e mostra o saldo disponível

## HU20 — Histórico de movimentações

### DESCRIÇÃO

- **Como:** Controlador de estoque ou Administrador
- **Desejo:** consultar todas as movimentações com filtros
- **Para que:** eu saiba quem incluiu, transferiu, ajustou ou baixou cada material, e quando

### DEFINIÇÃO DE NEGÓCIO

Hoje não se sabe quem incluiu ou retirou material (P6). O histórico mostra todas as movimentações gravadas pelo sistema. Ele é só consulta: nenhum registro pode ser alterado ou apagado.

### REFERÊNCIA

- T34; P6; seção 3.4.

### PROTÓTIPOS / TELAS

- T34 — Histórico de movimentações — protótipo pendente.

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Planilha mostra só a quantidade atual, sem passado | Histórico completo de cada movimentação |
| Não se sabe quem mexeu | Cada registro mostra o usuário responsável |

### CRITÉRIOS DE NEGÓCIO

- [ ] Cada registro mostra:
- data/hora;
- tipo (entrada, transferência, ajuste, baixa);
- item;
- local de origem e/ou destino;
- quantidade e unidade;
- usuário que registrou;
- motivo e observação, quando houver.
- [ ] Filtros: item, local, tipo, usuário, período, turma e agendamento.
- [ ] Ordem padrão: da mais recente para a mais antiga.
- [ ] Nenhum registro pode ser editado ou excluído pela tela.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Filtrar por item**

- Dado que o item "Bateria 9v" teve entradas e transferências
- Quando filtro o histórico por "Bateria 9v"
- Então vejo só as movimentações desse item, da mais recente para a mais antiga

**Cenário: Ver quem registrou**

- Dado que um Controlador registrou uma baixa
- Quando abro o histórico
- Então vejo o nome dele, a data/hora e o motivo da baixa

**Cenário: Registro não editável**

- Dado que estou no histórico
- Quando abro uma movimentação
- Então não há opção de editar nem excluir

## HU21 — Cadastro de agendamento de oficina

- **Status:** Não iniciada
- **Data:** Vazio
- **Responsável:** Vazio
- **Épicos:** Não informado
Vazio

### Comentários

> **Mayara Amorim — 22 de out.**
>
> Observações: ◦ Fora desta história: liberar e encerrar o formulário no totem (T12). Está pendente saber se o totem abre pelo horário da agenda ou por um botão. Nesta história o agendamento só tem as situações Agendado e Cancelado. ◦ Saldo usado no aviso: pelo P12, considerar só os locais do ambiente do agendamento. Confirmar, porque o Estoque Educativo (Experimento 33–48) ainda não tem ambiente definido (seção 10). ◦ Pontos a confirmar:   se o ambiente pode ser diferente do ambiente cadastrado na oficina;   se é permitido agendar com data no passado;   se a mesma turma pode estar agendada em dois ambientes no mesmo horário;   se agendamentos "colados" (um termina 10h00, outro começa 10h00) são permitidos;   se o cancelamento exige motivo.

### DESCRIÇÃO

- **Como:** Controlador de estoque ou Administrador
- **Desejo:** agendar uma oficina para uma turma, informando ambiente, data e horário
- **Para que:** o sistema saiba qual turma está em cada ambiente e o material retirado durante a oficina seja atribuído a ela

### DEFINIÇÃO DE NEGÓCIO

O agendamento liga turma, oficina, ambiente e horário. É a partir dele que tudo o que sair do estoque no dia da oficina é atribuído à turma agendada (P3, resposta 1 do produto). Não pode haver duas turmas ao mesmo tempo no mesmo ambiente (P8). Ao salvar, o sistema avisa se o estoque não cobre a lista de materiais da oficina, mas não impede o agendamento (T11).

### REFERÊNCIA

- P3, P7, P8, P10; T11; resposta 1 do produto.

### PROTÓTIPOS / TELAS

- T11 — Cadastro de agendamento — protótipo pendente.

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Não existe agenda ligada ao estoque | Agendamento com turma, oficina, ambiente e horário |
| Não se sabe qual turma consumiu o material | O agendamento é a base para atribuir o consumo à turma |
| Falta de material descoberta na hora da oficina | Aviso no momento do agendamento |

### CRITÉRIOS DE NEGÓCIO

- [ ] Campos (todos obrigatórios):
- turma (lista de turmas ativas — HU14);
- oficina (HU15);
- ambiente (vem preenchido com o ambiente da oficina; só ambientes internos);
- data;
- hora de início;
- hora de fim.
- [ ] A hora de fim precisa ser maior que a hora de início.
- [ ] O sistema impede salvar um agendamento cujo horário se sobrepõe a outro agendamento não cancelado no mesmo ambiente (P8). A mensagem informa o agendamento em conflito (turma e horário).
- [ ] Agendamentos em ambientes diferentes no mesmo horário são permitidos.
- [ ] Ao salvar, se a oficina tem lista de materiais e o saldo atual não cobre algum item, o sistema mostra um aviso com os itens insuficientes (quantidade prevista × saldo). O agendamento é salvo mesmo assim.
- [ ] Oficina sem lista de materiais é agendada sem aviso.
- [ ] Agendamento novo nasce com a situação Agendado.
- [ ] O agendamento pode ser editado enquanto estiver como Agendado. A edição passa pelas mesmas validações.
- [ ] O agendamento pode ser cancelado. Cancelado não bloqueia o horário e não pode voltar a Agendado.
- [ ] Usuário e data/hora de criação, alteração e cancelamento são registrados (P6).
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Agendar oficina**

- Dado que existem a turma "Turma A", a oficina "Robô Treme-Treme" e o ambiente Maker livre das 9h às 11h
- Quando agendo a Turma A na oficina Robô Treme-Treme, no Maker, das 9h às 11h
- Então o agendamento é salvo com a situação "Agendado"

**Cenário: Horário sobreposto no mesmo ambiente**

- Dado que a Turma A está agendada no Maker das 9h às 11h
- Quando tento agendar a Turma B no Maker das 10h às 12h
- Então o sistema impede
- E informa que o horário conflita com a Turma A (9h às 11h)

**Cenário: Mesmo horário em outro ambiente**

- Dado que a Turma A está agendada no Maker das 9h às 11h
- Quando agendo a Turma B no Biomaker das 9h às 11h
- Então o agendamento é salvo

**Cenário: Aviso de material insuficiente**

- Dado que a oficina prevê 20 "Motor 3v" e o saldo no ambiente é 12
- Quando salvo o agendamento
- Então vejo o aviso "Motor 3v: previsto 20, disponível 12"
- E o agendamento é salvo mesmo assim

**Cenário: Hora de fim inválida**

- Dado que estou cadastrando um agendamento
- Quando informo início às 11h e fim às 9h
- Então o sistema não salva e indica que o fim deve ser depois do início

**Cenário: Cancelar libera o horário**

- Dado que a Turma A está agendada no Maker das 9h às 11h
- Quando cancelo esse agendamento
- Então ele passa para "Cancelado"
- E o horário das 9h às 11h no Maker fica livre para outro agendamento

## HU22 — Agenda de oficinas

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Não existe visão das oficinas agendadas junto do estoque | Calendário por ambiente com situação e alerta de material |

### CRITÉRIOS DE NEGÓCIO

- [ ] Visões por dia e por semana, com navegação para o período anterior e o próximo.
- [ ] Filtro por ambiente; sem filtro, mostra todos os ambientes internos.
- [ ] Cada agendamento mostra turma, oficina, ambiente, horário e situação (Agendado ou Cancelado).
- [ ] Agendamentos cancelados aparecem diferenciados e podem ser ocultados por filtro.
- [ ] Agendamentos cuja oficina tem item insuficiente mostram um indicador. Ao abrir o agendamento, aparecem os itens insuficientes (previsto × disponível).
- [ ] Clicar em um horário livre abre o cadastro de agendamento (HU21) já com ambiente, data e hora preenchidos.
- [ ] Clicar em um agendamento abre os detalhes, com as opções editar e cancelar quando estiver como Agendado.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Ver semana do Maker**

- Dado que há três agendamentos no Maker nesta semana
- Quando abro a agenda na visão semana com filtro "Maker"
- Então vejo os três agendamentos com turma, oficina, horário e situação

**Cenário: Indicador de material**

- Dado que um agendamento tem item com saldo menor que o previsto
- Quando abro a agenda
- Então esse agendamento aparece com o indicador de material insuficiente
- E ao abri-lo vejo os itens que faltam

**Cenário: Agendar a partir do calendário**

- Dado que o Biomaker está livre na quinta-feira às 14h
- Quando clico nesse horário
- Então o cadastro de agendamento abre com ambiente Biomaker, data de quinta e início às 14h preenchidos

### DESCRIÇÃO

- **Como:** Controlador de estoque ou Administrador
- **Desejo:** ver os agendamentos em um calendário por dia e por semana, filtrando por ambiente
- **Para que:** eu acompanhe quais oficinas vão acontecer, onde, e quais têm risco de faltar material

### DEFINIÇÃO DE NEGÓCIO

A agenda mostra os agendamentos de cada ambiente com a situação e um indicador de material insuficiente quando a oficina tem lista de materiais (T10). É o ponto de partida para cadastrar, editar e cancelar agendamentos (HU21).

### REFERÊNCIA

- T10; P7, P8, P10.

### PROTÓTIPOS / TELAS

- T10 — Agenda de oficinas (calendário dia/semana) — protótipo pendente.

### AS IS → TO BE

| Agora | Depois |
| --- | --- |
| Não existe visão das oficinas agendadas junto do estoque | Calendário por ambiente com situação e alerta de material |

### CRITÉRIOS DE NEGÓCIO

- [ ] Visões por dia e por semana, com navegação para o período anterior e o próximo.
- [ ] Filtro por ambiente; sem filtro, mostra todos os ambientes internos.
- [ ] Cada agendamento mostra turma, oficina, ambiente, horário e situação (Agendado ou Cancelado).
- [ ] Agendamentos cancelados aparecem diferenciados e podem ser ocultados por filtro.
- [ ] Agendamentos cuja oficina tem item insuficiente mostram um indicador. Ao abrir o agendamento, aparecem os itens insuficientes (previsto × disponível).
- [ ] Clicar em um horário livre abre o cadastro de agendamento (HU21) já com ambiente, data e hora preenchidos.
- [ ] Clicar em um agendamento abre os detalhes, com as opções editar e cancelar quando estiver como Agendado.
- [ ] A responsividade deve estar contemplada.
- [ ] A acessibilidade deve estar contemplada.

### BDD

**Cenário: Ver semana do Maker**

- Dado que há três agendamentos no Maker nesta semana
- Quando abro a agenda na visão semana com filtro "Maker"
- Então vejo os três agendamentos com turma, oficina, horário e situação

**Cenário: Indicador de material**

- Dado que um agendamento tem item com saldo menor que o previsto
- Quando abro a agenda
- Então esse agendamento aparece com o indicador de material insuficiente
- E ao abri-lo vejo os itens que faltam

**Cenário: Agendar a partir do calendário**

- Dado que o Biomaker está livre na quinta-feira às 14h
- Quando clico nesse horário
- Então o cadastro de agendamento abre com ambiente Biomaker, data de quinta e início às 14h preenchidos
