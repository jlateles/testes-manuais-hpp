# Requisitos funcionais para Testes Manuais

## RF01 Autenticação de Usuários 
- O sistema deve permitir que o usuário realize login com nome de usuário ou CPF e senha válidos.
- O sistema deve exbibir mensagens de erro claras em caso de login inválido.
---
## RF02 Homepage Inicial 
> Observação: Após o login, o usuário deve ser redirecionado para as áreas de paciente ou administrador, de acordo com a autenticação de cada login. 

**Exibições de imagens de funcionalidades esperadas:**

- Header: Logo + Botão "Quero acessar"
  - Quando um usuário estiver logado o botão "Quero acessar" deverá ser trocado pelo texto clicável "Olá, nome-do-usuário" com menu dispovível para ser "aberto" quando clicado
      - Caso o usuário seja (login) paciente, o menu deve conter:
          - ícone com a inicial do nome do paciente
          - Nome completo do paciente
          - Opções para redirecionamento:
               - tela de `Orçamentos` na área de paciente.
               - tela de `Configurações` na área de paciente
          - Botão/texto "Sair" para deslogar
      - Caso o usuário seja (login) administrador ( `Admin Master`, `Financeiro` e `Atendente`), o menu deve conter:
          - ícone com a inicial do nome do usuário logado
          - Nome completo do usuário logado
          - Opções para redirecionamento:
              - tela de `Orçamentos` na área de administração
              - tela de `Relatórios` na área de administração
              - tela de `Cadastros` na área de administração
              - tela de `Configurações` na área de administração
          - Botão/texto "Sair" para deslogar
            
- Banners: Header, Section e Specialties
- Footer + botão "Administração"
-  Sessão de Contatos
 
**Exibições de texto esperadas:**
   - "Realize consultas, exames, procedimentos e cirurgias com médicos especializados"
   - "Tem exames preventivos, cirurgias com especialistas e atendimentos personalizados, é pra mim."
   - "Oferecemos uma gama completa de exames e procedimentos para garantir um tratamento cada vez mais personalizado e com melhores resultados para cada paciente."
   - É diferente, é inovador, é pra mim." + "Consultas, exames, tratamentos, cirurgias, transplantes e plásticas." + "Além de diversos outros procedimentos para pacientes de todas as idades, com médicos qualificados, para qual for a sua necessidade."
   - "É pra mim, é pra você, é pra todos nós." + A ----------- cuida da responsabilidade social e da excelência no atendimento."
 
   - Email e números de telefone
 
   - "Prefere escrever?" +  Direcione seu e-mail para a área de sua necessidade:[email] "
   - "Atendimento + "Sugestão, elogio ou reclamação, necessidade de apoio referente ao atendimento presencial e/ou telemedicina, apoio com agendamento ou cancelamento, soluções de questões financeiras, outros assuntos de atendimento ao cliente. [email]"
 
   - "Formas de pagamento" + "Crédito: Nas unidades e online" + "Pix: Nas unidades e online" + "Outras formas: Apenas nas unidades"
 
  > Verificar o Figma para detalhes de fonte, weight, posição, etc.
---
## RF03 Área de Paciente
 > Observação: O sistema deve permitir que pacientes façam apenas a visualização de procedimentos e orçamentos, estejam eles pagos ou não, realizados ou não. 
  
**Funcionalidades e exibição esperadas:**
> Observação: o paciente deve acessar a página de login do site a partir do botão "Quero acessar" na homepage, esse botão é exclusivamennte para logins feitos por pacientes. 

**Tela de login**

Campos e elementos obrigatórios:
- Campo CPF: deve permitir apenas números e possuir validação de formato (11 dígitos).
   - Atributo:  `formcontrolname="cpf"`
   - Comportamento(s) esperado: ao inserir menos ou mais dígitos, deve ser exibida uma mensagem de erro informando “CPF inválido”.
- Campo Senha: deve permitir a inserção de senha cadastrada pelo paciente com no mínimo de 8 caracteres
  - Atributo: `id="password" `
  - Comportamento(s) esperado:
    - o campo deve ocultar os caracteres digitados (máscara de senha)
    - o campo deve exibir uma mensagem de aviso caso a iserção de senha não tenha atinja o mínimo de caracteres esperado
- Botão “Entrar na conta”
   - Função: realizar a autenticação do paciente com base nas credenciais informadas
   - Comportamento(s) esperado:
      - Ao clicar, o sistema deve validar CPF e senha
      - Caso os dados estejam corretos, o paciente deve ser redirecionado para a área logada, exibindo a lista de orçamentos vinculados ao seu CPF
      - Caso contrário, deve ser exibida mensagem de erro, como “CPF ou senha inválidos”, apresentando a opção de "Esqueci minha senha"

Mensagens e modais esperados:
- Ao realizar login com sucesso, deve ser exibido o modal de confirmação com o título: "Login concluído. Seja bem-vindo!"
- O modal contém um botão "OK"
  - Ao clicar em "OK", o modal deve ser fechado e o usuário redirecionado para a tela principal (listagem de orçamentos) da área do paciente
 
**Estrutura geral área de paciente**

Sidebar lateral retrátil:
 - Possui botão de seta na parte superior para abrir/fechar o menu
 - Opções disponíveis:
     1. Orçamentos – tela principal da área de pacientes
     2. Configurações – acesso aos dados cadastrais e opções de alteração de senha
     3. Sair da conta – encerra a sessão e redireciona o usuário para a homepage
   
Header fixo: 
- Exibido em todas as páginas da área de paciente.
- Contém:
    - Título da tela atual (ex.: “Orçamentos”)
    - Ícone de usuário → redireciona para a tela de Configurações
    - Ícone de casa → redireciona para a homepage da plataforma

**Tela "Orçamentos"**

Componentes e funcionalidades:
- Filtro de mês: opções disponíveis → “Mês Atual”, “Último Mês” e “Últimos três meses”
- Filtro por período:
    - Exibe intervalo da semana (exemplo: 01/11/2025 - 10/11/2025)
    - Ícone de calendário permite selecionar outro período para exibição dos orçamentos
- Barra de pesquisa por voucher:
    - Texto acima: “Busque pelo número do voucher”
    - Placeholder no campo: “BUSCAR”
    - Permite filtrar orçamentos pelo número do voucher informado
- Quantidade de resultados:
    - Exibida abaixo da barra de pesquisa (ex.: “13 Resultado(s)”)
- Tabela de orçamentos:
    - Cabeçalho fixo com colunas:
        - Data/Hora
        - Responsável (usuário admin que gerou o orçamento)
        - Voucher
        - Pagamento (forma de pagamento)
        - Valor total
        - Status pagamento (`Pago`, `Expirado`, `Pendente`)
        - Status orçamento (`Confirmado`, `Expirado`, `Pendente`, `Cancelado`)
- Paginação:
    - Exibe número de páginas e controles de navegação (ex.: “1 de 4 > >>”)
    - Cada página exibe até 4 orçamentos por vez
 
**Tela "Configurações"**

Essa tela é dividida em três seções: `Paciente`, `Responsável Financeiro` e `Redefinir Senha`

1. Paciente
    - Exibe formulário com os seguintes campos:
        - CPF, Nome, E-mail, Confirmar e-mail, Telefone (DDD), Data de Nascimento, Sexo (select), CEP, Número, Estado, Bairro, Cidade, Endereço, Complemento
        - Campos devem ser auto-preenchidos com os dados informados no cadastro inicial
        - Caso o campo Complemento não tenha sido informado no momento de cadastro, deve exibir o texto “Não informado”
        - Todos os campos podem ser editados
        - Botão: “Salvar”

2. Responsável financeiro
    - Exibe formulário com os dados do responsável financeiro do paciente.
    - Se o paciente já possui responsável cadastrado:
        - Campos devem vir preenchidos
        - Botão exibido: “Atualizar”
    - Se não houver responsável cadastrado:
        - Campos vazios e editáveis
        - Botão exibido: “Cadastrar”

3.  Redefinir senha
     - Texto de aviso: “Sua nova senha precisa ser diferente de senhas anteriores.”
     - Campos disponíveis:
         - Senha atual
         - Nova senha
         - Confirmação de senha
     - Todos os campos devem ocultar os caracteres digitados (máscara de senha)
     - Ícone de “olho” disponível em cada campo para exibir ou ocultar os caracteres
     - Mínimo de 8 caracteres, mensagem de aviso "Sua senha deve conter letras maiúsculas, minúsculas, números e caracteres especiais."
     - Botão: “Alterar senha”
  
**Tela de "Detalhes do Orçamento"**
> Observação: a tela de detalhes é acessada a partir da tela de `Orçamentos`, ao clicar em qualquer item da listagem.
Elementos e comportamento esperado:
- Botão de retorno:
    - Ícone de seta (<) no canto superior esquerdo
        - Função: retorna o usuário para a tela principal de `Orçamentos`

A tela `Detalhes do Orçamento` é dividida em cards informativos, que devem ser exibidos na seguinte ordem: 

**Card 01 -** Informações gerais 
- Campos exibidos:
    - Nome do paciente
    - Unidade (local onde o orçamento foi adquirido e o procedimento será realizado)
    - Pagamento (método de pagamento)
    - Valor total (do orçamento)
    - Status de pagamento: `Pago`, `Expirado` ou `Pendente`
    - Status do orçamento: `Confirmado`, `Expirado`, `Pendente` ou `Cancelado`
- Ação disponível:
    - Ícone de envelope que permite reenviar o e-mail do orçamento (com os detalhes + link de pagamento) ao paciente

**Card 02 -** Procedimentos
- Exibe a lista de procedimentos incluídos no orçamento
- Campos:
    - Nome do procedimento
    - Quantidade (entre parênteses, ex.: "(2)")
    - Total (Valor total do orçamento)
    - Status do procedimento: `Confirmado`, `Expirado`, `Pendente` ou `Cancelado`
  
**Card 03 -** Detalhes paciente
- Campos:
    - Nome
    - CPF/CNPJ
    - Telefone
    - Data de nascimento
    - E-mail
    - Endereço
    - Número
    - Cidade
    - Complemento
    - Estado
    - CEP

**Card 04 -** Dados do responsável financeiro
- Exibe os dados do responsável pelo pagamento, caso exista
- Campos:
    - Nome
    - CPF/CNPJ
    - Telefone
    - Data de nascimento
    - E-mail
    - Endereço
    - Número
    - Cidade
    - Complemento
    - Estado
    - CEP
> Observação: este card não deve ser exibido se o paciente não possuir responsável financeiro cadastrado.

**Card 05 -** Histórico do orçamento
- Exibe o histórico completo do orçamento, desde a criação até a conclusão (pagamento ou cancelamento)
- Informações apresentadas:
    - Itens (procedimentos) incluídos
    - Status de cada item
    - Data e hora das atualizações
    - Valor (de cada item)
    - Unidade relacionada 

**Card 06 -** Detalhes do Orçamento
- Campos:
  - Responsável (usuário administrador que criou o orçamento)
  - Número de obrigação
  - Data e hora
  - Descrição do orçamento
  - Total (valor final)

**Card 07 -** Detalhes do pagamento
- Campos:
    - Método de pagamento escolhido pelo paciente
    - Método de captura (e-commerce)
    - Data e hora do pagamento
    - Valor total
    - ID de transação
- Ação disponível:
    - Botão para baixar o comprovante de pagamento
- Casos específicos:
  - Cartão de crédito (Ou múltiplos cartões):
      - Exibir número do cartão com máscara nos 12 primeiros dígitos (ex.: **** **** **** 1234)
      - Exibir quantidade de parcelas

**Card 08 -** Histórico de pagamento
- Informações exibidas:
  - Mensagem sobre o status da transação: `Aprovado`, `Aguardando` e `Recusado`
---
## RF04 Área de Administração 
> Observação: A área de administração é destinada exclusivamente a usuários administradores, responsáveis pela criação, gerenciamento e acompanhamento dos orçamentos realizados na plataforma.

**Acesso à Área de Administração**
Fluxo de acesso:
  - usuário deve rolar a homepage até o final e clicar no botão azul “Administração”
  - O botão “Administração” é de uso exclusivo para logins de administradores
  - O usuário é redirecionado para a tela de login de administrador

**Tela de login**
Campos e elementos obrigatórios:
  - `Campo Login`: deve aceitar caracteres alfanuméricos.
  - `Campo Senha`: campo do tipo senha (com máscara para os caracteres digitados).
  - Botão “Entrar na conta”
Mensagens esperadas:
  - Em caso de sucesso: modal com mensagem "Login concluído. Seja bem-vindo!"
  - Em caso de erro: modal com mensagem "Login ou senha inválidos. Tente novamente!"

**Layout geral da área de admin - (após login realizado)** 

Header fixo:
  - Título da tela (Orçamentos, Relatórios, Cadastros ou Configurações)
  - Ícone de usuário: redireciona para tela de Configurações
  - Ícone de casa: retorna à homepage da plataforma
Sidebar (menu lateral):
  - Orçamentos (tela principal)
  - Relatórios
  - Cadastros
  - Configurações
  - Sair da conta: encerra a sessão e redireciona para a homepage
  - Campo inferior: Usuário: [nome do admin] (exemplo: Usuário: Admin Unidade Clínica SP)

`Comportamento esperado:` menu retrátil, abrindo e fechando ao clicar na seta superior.

**Tela Principal – Orçamentos**
Funcionalidade: exibir e gerenciar todos os orçamentos criados na plataforma.

Filtros e elementos da tela:
  - Filtro por Mês:
      - Opções: “Mês Atual”, “Último Mês”, “Últimos três meses”
  - Filtro por Período:
      - Campo de data (ex.: 01/11/2025 - 10/11/2025)
      - Ícone de calendário para seleção de intervalo personalizado
  - Cards:
      1. Total de orçamentos pagos
      2. Valor recebido (somatório dos orçamentos pagos)
      3. Valor a receber (somatório dos orçamentos pendentes)
      4. Total de orçamentos enviados
  - Barra de pesquisa: *“Busque por um nome ou código"*
  - Filtros adicionais (select):
      - Login: lista de todos os logins de administradores
      - Status pagamento: “Todos”, “Pago”, “Estornado”, “Pendente”, “Expirado”
      - Status orçamento: “Todos”, “Enviado”, “Salvo”, “Expirado”, “Confirmado”, “Cancelado”
      - Botão “Limpar filtros” → restaura a listagem completa
  - Contagem de resultados: ex.: “16 Resultado(s)”
  - Botões principais:
      - “REENVIAR” → reenviar orçamento selecionado(s) ao paciente
      - “NOVO ORÇAMENTO” → abre formulário de criação de novo orçamento
  - Listagem de orçamentos:
      - Elementos do topo da listagem:
          - Checkbox para seleção múltipla de orçamentos
          - Unidade, Paciente, Obrigação, Valor total, Status orçamento, Data de pagamento, Status pagamento, Operador (login)
  - Ações disponíveis:
      - “Visualizar orçamento” (ícone de seta para baixo)
      - Paginação: exibe resultados limitados por página (ex: “1 de 4 > >>”)

**Tela de Novo Orçamento**
> Tela de criação e envio de novos orçamentos aos pacientes.

Estrutura: 
  - Botão de retorno: ícone “<” (volta à tela principal de orçamentos)
  - Título da tela: “Novo orçamento”

Campos do Formulário:
  - Campo select: “Selecione a empresa”
      - Lista de unidades disponíveis
  - Dados do paciente:
      - Campos: CPF, Nome completo, E-mail, Confirmação de e-mail, Telefone, Data de nascimento, Sexo (select), CEP, Número, Estado, Bairro, Cidade, Endereço, Complemento
      - Botão Cadastrar ou Atualizar, dependendo se o paciente já existe
          - Comportamento esperado: ao inserir o CPF, se o paciente já existir, seus dados são carregados automaticamente
          - Modais esperados: sucesso e erro nas operações
  - Selecione o responsável financeiro
      - Duas opções do tipo radio:
          - “Paciente será o responsável financeiro”
          - “Adicionar um responsável financeiro”
      - Caso seja escolhida a segunda opção:
          - Abre o card “Dados do responsável financeiro”, com os mesmos campos do paciente
          - Botão Cadastrar ou Atualizar, conforme o caso
          - Comportamento esperado: carregamento automático via CPF se já houver responsável cadastrado
      - Caso seja escolhida a primeira opção:
          - O form de responsável não deve ser exibido.
  - Procedimentos:
      - Barra de pesquisa: “Digite o código ou nome do procedimento”
      - Campo “Valor (R$)”
      - Botão “Adicionar” (inclui o procedimento na lista “Procedimentos adicionados”)
      - Campo (obrigatório) “Observações”
      - Botões:
          - Cancelar → descarta o orçamento e volta à tela principal
          - Finalizar → abre o modal de finalização
      - Modal de Finalização:
          - “Como deseja finalizar o orçamento?”
              - Enviar orçamento: envia ao email do paciente
              - Salvar orçamento → mantém como rascunho na listagem da tela principal
          - Ambos devem gerar modais de sucesso ou erro conforme o resultado da operação.
      
**Tela de Relatórios**
> Destinada à exportação e visualização de relatórios de orçamentos

Opções disponíveis:
  1. Relatórios de orçamentos em PDF
       - Ação: visualizar e/ou baixar (download)
       - Campo de seleção de período via calendário
  2. Relatórios de orçamentos em CSV
       - Ação: baixar (download)
       - Campo de seleção de período via calendário

**Tela de Configurações**
> Disponível através do ícone de usuário no header ou no sidebar (menu lateral)
Função: redefinir senha do administrador

