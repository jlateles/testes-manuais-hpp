# Plano e Cenários de Testes 

## 1. Identificação
- Nome do Projeto: E-commerce médico
- Versão Avaliada: V1
- Ambiente de Testes: dev, homolog e prod.
- Tipo de Teste: Teste Funcional Manual
- Data do Documento: 30/10/2025
- Responsável: Júlia Teles

## 2. Objetivo:
> Validar as funcionalidades e fluxos principais do sistema, garantindo que os comportamentos estejam de acordo com os requisitos definidos e que as informações sejam exibidas corretamente.

## 3. Escopo 
Os teste svão cobrir: 
  - Acesso à plataforma (homepage)
  - Login e autenticação de paciente e admin (AdminMaster, Financeiro e Atendente)
  - Navegação pela área logada (sidebar e header fixo)
  - Visualização e filtros da tela de orçamentos
  - Visualização dos detalhes de orçamentos
  - Acesso e edição de informações em configurações

O que não vai ser testado no momento: 
  - Testes em dispositivos móveis
  - Testes de integração com sistemas externos
  - Testes de performance ou carga

## 4. Pré-requisitos gerais
  - O paciente deve possuir cadastro prévio com CPF e senha
  - Deve haver orçamentos associados ao CPF do paciente para exibição nas listagens

## 5. Ferramentas Utilizadas
  - Navegador Google Chrome / Edge
  - Ferramentas de inspeção do navegador (DevTools)
  - Google Sheets / Docs e Linear (reportar bugs e registrar evidências)
  - Extensões:
      - Check my links
      - Jam

## 6. Técnicas de Teste
  - Particionamento de equivalência
  - Caminho feliz (Happy Path)
  - Testes exploratórios

## 7. Critérios de Aceitação
  - Todos os casos de teste devem passar com sucesso, conforme o resultado esperado.
  - Nenhuma falha crítica deve estar presente em funcionalidades principais.
  - Mensagens de erro e validações devem ser consistentes.

## 8. Critérios de Saída 
  - Todos os testes do escopo foram executados.
  - Bugs foram registrados, analisadas e fluxos reexecutados se necessário.
  - Documentação de evidências de sucesso e falhas está completa.

## 9. Cronograma Estimado
| Atividade                   | Data Início | Data Fim   |
| --------------------------- | ----------- | ---------- |
| Planejamento de Testes      | 06/10/2025  | 10/10/2025 |
| Criação de Casos de Teste   | 10/10/2025  | 17/10/2025 |
| Execução dos Testes Manuais | 17/10/2025  |  -         | 
| Registro e Report de Bugs   | 17/10/2025  |     -      |
| Encerramento e Evidências   | 13/05/2025  |     -      |

### 10. **Módulos para serem testados**

| Código RF | Módulo                   | Prioridade |
| --------- | ------------------------ | ---------- |
| RF01      | Autenticação de Usuários |    Alta    |
| RF02      | HomePage                 |    Média   |
| RF03      | Área de Paciente         |    Alta    |
| RF04      | Área de Administração    |    Alta    |
| RF05      | Pagamento                |    Alta   |


### 11. **Gestão de Defeitos**

* Bugs serão documentados com:

  * Título
  * Descrição
  * Fluxo para reproduzir
  * Evidência (print ou vídeo)
  * Gravidade (Crítica, Alta, Média, Baixa)
* Ferramenta sugerida: homologação (para simulação)

### 12. **Riscos Identificados**
| Risco                                  | Impacto | Mitigação                        |
| -------------------------------------- | ------- | -------------------------------- |
| Sistema fora do ar                     | Alto    | Tentar novamente após intervalo  |
| Dados da demo não sendo persistentes   | Médio   | Refazer cenários se necessário   |
| Testes limitados à conta "Admin" única | Médio   | Documentar esse limite no escopo |

---

## Cenários de Testes

**Homepage** 
| ID     | Cenário de Teste                                  | Pré-condição | Passos                        | Resultado Esperado                                                      |
| ------ | ------------------------------------------------- | ------------ | ----------------------------- | ----------------------------------------------------------------------- |
| CT-001 | Validar exibição do botão “Quero acessar”         |-            | 1. Acessar homepage           | O botão “Quero acessar” é exibido na interface principal.               |
| CT-002 | Validar redirecionamento do botão “Quero acessar” | -          | 1. Clicar em “Quero acessar”  | Usuário é redirecionado para a página de login destinada aos pacientes. |

---

### Área de Paciente 

**Login Paciente**
| ID     | Cenário de Teste                       | Pré-condição        | Passos                                                                                          | Resultado Esperado                                                                                                              |
| ------ | -------------------------------------- | ------------------- | ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| CT-003 | Validar login com credenciais válidas  | Paciente cadastrado | 1. Acessar tela de login.<br>2. Inserir CPF e senha válidos.<br>3. Clicar em “Entrar na conta”. | Login é efetuado com sucesso, modal “Login concluído. Seja bem-vindo!” exibido e usuário é redirecionado à tela “Orçamentos”. |
| CT-004 | Validar login com CPF inválido         |-                   | 1. Inserir CPF com menos de 11 dígitos.<br>2. Clicar em “Entrar na conta”.                      | Exibir mensagem “CPF inválido”.                                          |
| CT-005 | Validar login com senha incorreta      | Paciente cadastrado | 1. Inserir CPF válido e senha incorreta.<br>2. Clicar em “Entrar na conta”.                     | Exibir mensagem “CPF ou senha inválidos”.                                      |
| CT-006 | Validar campo de senha com máscara     | -                   | 1. Digitar senha no campo “Senha”.                                                              | Dígitos devem estar ocultos.                                                   |
| CT-007 | Validar fechamento do modal de sucesso | Login bem-sucedido  | 1. Após login, clicar no botão “OK” do modal.                                                   | Modal é fechado e usuário é redirecionado à área de paciente.         |

**Área Logada (Layout e navegação)**

| ID     | Cenário de Teste                          | Pré-condição    | Passos                                 | Resultado Esperado                                             |
| ------ | ----------------------------------------- | --------------- | -------------------------------------- | -------------------------------------------------------------- |
| CT-008 | Validar exibição do header fixo           | Paciente logado | 1. Verificar topo da tela.             | Header exibe título da tela, ícone de usuário e ícone de casa. |
| CT-009 | Validar funcionamento do ícone de casa    | Paciente logado | 1. Clicar no ícone de casa.            | Usuário é redirecionado para a homepage.                       |
| CT-010 | Validar funcionamento do ícone de usuário | Paciente logado | 1. Clicar no ícone de usuário.         | Usuário é redirecionado para a tela “Configurações”.           |
| CT-011 | Validar funcionamento do sidebar retrátil | Paciente logado | 1. Clicar na seta superior da sidebar. | Sidebar é expandida ou recolhida.                              |
| CT-012 | Validar opção “Orçamentos” na sidebar     | Paciente logado | 1. Clicar em “Orçamentos”.             | Usuário é redirecionado para a tela principal de orçamentos.   |
| CT-013 | Validar opção “Configurações” na sidebar  | Paciente logado | 1. Clicar em “Configurações”.          | Tela de configurações é exibida.                               |
| CT-014 | Validar opção “Sair da conta”             | Paciente logado | 1. Clicar em “Sair da conta”.          | Sessão é encerrada e usuário é redirecionado para a homepage.  |

**Tela "Orçamentos"**
| ID     | Cenário de Teste                           | Pré-condição            | Passos                                                                             | Resultado Esperado                                       |
| ------ | ------------------------------------------ | ----------------------- | ---------------------------------------------------------------------------------- | -------------------------------------------------------- |
| CT-015 | Validar exibição da listagem de orçamentos | Paciente com orçamentos | 1. Acessar tela “Orçamentos”.                                                      | Listagem exibe orçamentos vinculados ao CPF do paciente. |
| CT-016 | Validar filtro de mês                      | -                       | 1. Selecionar opção “Último Mês”.                                                  | Listagem atualiza conforme filtro.                       |
| CT-017 | Validar filtro por período (calendário)    | -                     | 1. Abrir calendário.<br>2. Selecionar intervalo de datas.<br>3. Confirmar seleção. | Exibir apenas orçamentos do período escolhido.           |
| CT-018 | Validar busca por voucher                  |-                     | 1. Inserir número de voucher existente.<br>2. Clicar em “BUSCAR”.                  | Exibir apenas o orçamento correspondente.                |
| CT-019 | Validar contador de resultados             |-                        | 1. Aplicar filtro ou busca.<br>2. Verificar contador.                              | Texto exibe número correto de resultados.                |
| CT-020 | Validar paginação da listagem              | -                       | 1. Clicar em “>” ou “>>”.                                                          | Exibir demais páginas de resultados.                     |
| CT-021 | Validar redirecionamento para detalhes     | Paciente com orçamentos | 1. Clicar em um orçamento da tabela.                                               | Redirecionar para “Detalhes do orçamento”.               |

**Tela “Detalhes do Orçamento”** 
| ID     | Cenário de Teste                                    | Pré-condição                  | Passos                                               | Resultado Esperado                                                                                   |
| ------ | --------------------------------------------------- | ----------------------------- | ---------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| CT-022 | Validar botão de retorno                            | Estar na tela de detalhes     | 1. Clicar na seta (“<”).                             | Retorna à tela “Orçamentos”.                                                                         |
| CT-023 | Validar exibição de informações principais        | Orçamento existente       | 1. Verificar card principal                               | Exibir nome do paciente, unidade, pagamento, valor total, status de pagamento e status doorçamento. |
| CT-024 | Validar ação de reenviar e-mail                     | Orçamento existente           | 1. Clicar no ícone de e-mail.                        | E-mail de orçamento é reenviado e mensagem de sucesso exibida.                      |
| CT-025 | Validar exibição dos procedimentos                  | Orçamento com itens           | 1. Verificar card “Procedimentos”.                   | Exibir nome, quantidade, valor e status de cada procedimento.                                        |
| CT-026 | Validar exibição de dados do paciente               | -                              | 1. Verificar card “Detalhes paciente”.               | Exibir dados cadastrais completos do paciente.                      |
| CT-027 | Validar exibição de dados do responsável financeiro | Paciente com responsável      | 1. Verificar card “Dados do responsável financeiro”. | Exibir informações completas do responsável.                                                       |
| CT-028 | Validar ausência do card de responsável financeiro  | Paciente sem responsável      | 1. Verificar cards exibidos.                         | Card não deve aparecer.                                                                            |
| CT-029 | Validar histórico do orçamento                      | -                              | 1. Verificar card “Histórico do orçamento”.          | Exibir eventos em ordem cronológica com data, hora e status.                                      |
| CT-030 | Validar card “Detalhes orçamento”                   | -                              | 1. Verificar card correspondente.                    | Exibir responsável, número de obrigação, data/hora e valor total.                                 |
| CT-031 | Validar detalhes de pagamento                       | Orçamento pago                | 1. Verificar card “Detalhes pagamento”.              | Exibir método, captura, data/hora, valor e ID de transação.                                        |
| CT-032 | Validar cartão de crédito mascarado                 | Pagamento via cartão          | 1. Verificar campo de número do cartão.              | Exibir formato “**** **** **** 1234”.                                                              |
| CT-033 | Validar download do comprovante                     | Pagamento aprovado            | 1. Clicar em “Baixar comprovante”.                   | Download do comprovante é iniciado.                                                                |
| CT-034 | Validar histórico de pagamento                      | Orçamento com status definido | 1. Verificar card “Histórico pagamento”.             | Exibir status correto (Aprovado, Pendente, Recusado, Cancelado).                                   |

**Tela “Configurações”**
| ID     | Cenário de Teste                                                 | Pré-condição                        | Passos                                                                       | Resultado Esperado                                    |
| ------ | ---------------------------------------------------------------- | ----------------------------------- | ---------------------------------------------------------------------------- | ----------------------------------------------------- |
| CT-035 | Validar exibição do formulário “Paciente”                        | Paciente logado                     | 1. Acessar “Configurações”.                                                  | Exibir formulário com dados auto preenchidos.         |
| CT-036 | Validar edição e salvamento de dados do paciente                 | -                                   | 1. Alterar campo e clicar em “Salvar”.                                       | Dados atualizados com sucesso.                        |
| CT-037 | Validar campo “Complemento” sem informação                       | Paciente sem complemento cadastrado | 1. Acessar “Configurações”.                                                  | Campo exibe texto “Não informado”.                    |
| CT-038 | Validar formulário “Responsável financeiro” com dados existentes | Paciente com responsável            | 1. Acessar seção “Responsável financeiro”.                                   | Campos exibem dados e botão “Atualizar”.              |
| CT-039 | Validar cadastro de novo responsável financeiro                  | Paciente sem responsável            | 1. Preencher campos e clicar em “Cadastrar”.                                 | Novo responsável é criado e dados exibidos.           |
| CT-040 | Validar redefinição de senha                                     |   -                                  | 1. Inserir senha atual, nova e confirmação.<br>2. Clicar em “Alterar senha”. | Senha é alterada com sucesso.                         |
| CT-041 | Validar máscara e ícone de olho nas senhas                       | -                                   | 1. Digitar senhas e clicar no ícone de olho.                                 | Senhas ficam ocultas por padrão e visíveis ao clicar. |

**Encerramento de Sessão**
| ID     | Cenário de Teste                     | Pré-condição    | Passos                        | Resultado Esperado                                       |
| ------ | ------------------------------------ | --------------- | ----------------------------- | -------------------------------------------------------- |
| CT-042 | Validar logout pelo botão da sidebar | Paciente logado | 1. Clicar em “Sair da conta”. | Sessão é encerrada e usuário é redirecionado à homepage. |

---

### Área de Administração 

**Login Admin** 
| ID     | Cenário de Teste                    | Pré-condição                    | Passos                                                                                                      | Resultado Esperado                                        |
| ------ | ----------------------------------- | ------------------------------- | ----------------------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| CT-043 | Login válidos       | Ter um usuário admin cadastrado | 1. Acessar a página de login da administração<br>2. Inserir login e senha válidos<br>3. Clicar em “Entrar” | O sistema deve autenticar e redirecionar o usuário para a tela de orçamentos |
| CT-044| Login inválidos     | —                               | 1. Inserir login e/ou senha incorretos<br>2. Clicar em “Entrar”                                            | Exibir mensagem de erro “Login ou senha inválidos”           |
| CT-045 | Campos obrigatórios não preenchidos | —                               | 1. Clicar em “Entrar” sem preencher campos                                                                  | Exibir mensagem de aviso que os campos de login e senha são obrigatórios        |
| CT-046 | Logout do sistema                   | Usuário logado como admin       | 1. Clicar em “Sair” ou ícone correspondente                                                                 | Sistema deve encerrar a sessão e redirecionar para a homepage              |

















---
### Pagamento 

