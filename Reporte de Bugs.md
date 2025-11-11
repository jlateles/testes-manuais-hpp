## QA responsável: Julia

**Bug 01: Logout não atualiza header na homepage (admin e paciente)**

| **ID**  | **Descrição**                                                                                                                           |
| ------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| BUG-001 | Ao clicar em “Sair da conta”, o usuário é redirecionado corretamente para a homepage, porém o header ainda exibe o usuário como logado. |

| **Severidade do Bug** | **Prioridade de Correção** | **Status** |
| :-------------------: | :------------------------: | :-----:    |
|          Alta         |            Alta            | Corrigido  |

| **Passo a passo para simular o bug** |
| ------------------------------------ |
| 1. Fazer login no painel admin       |
| 2. Clicar em “Sair da conta”         |
| 3. Observar o header na homepage     |

|              **Comportamento Esperado**              |           **Comportamento Obtido**           |
| :--------------------------------------------------: | :------------------------------------------: |
| O header deve exibir as opções de usuário deslogado. | O header ainda mostra o usuário como logado. |

| **Ambiente**                      |
| --------------------------------- |
| Área de Admin / Homepage.         |
| Navegador: Chorme /  Edge         |
| Sistema: Windows 11.              |

| **Funcionalidade Afetada** |         **Caso de Teste Relacionado**         |
| :------------------------: | :-------------------------------------------: |
| Logout / Sessão de Admin   | CT-042: Validar logout pelo botão da sidebar |
| Logout /Sessão de Paciente | CT-014	Validar opção “Sair da conta”          |

|            **Evidência(s)**            |
| :------------------------------------: |
| (vídeo da reprodução) |

------

**Bug 02: Filtro “Todos” não clicável de primeiro momento**

| **ID**  | **Descrição**                                                                                                                                                                                                                            |
| ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| BUG-002 | Na tela de orçamentos (área de admin), a opção “Todos” nos filtros **Login**, **Status Pagamento** e **Status Orçamento** não está clicável de início. É necessário selecionar outra opção antes para depois conseguir escolher “Todos”. |

| **Severidade do Bug** | **Prioridade de Correção** | **Status** |
| -----------------     | ------------------------   | --------   |
|         Média         |            Média           |  Corrigido |


| **Passo a passo para simular o bug**                             |
| ---------------------------------------------------------------- |
| 1. Acessar a área de admin                                       |
| 2. Ir até a tela de Orçamentos                                  |
| 3. Tentar selecionar a opção “Todos” em qualquer um dos filtros |
| 4. Observar que não é possível clicar                           |
| 5. Selecionar outra opção e depois retornar para “Todos”        |


|               **Comportamento Esperado**              |                          **Comportamento Obtido**                         |
| ---------------------------------------------------   | -----------------------------------------------------------------------   |
| O filtro “Todos” deve estar disponível imediatamente  | O filtro só pode ser selecionado após outra opção ser escolhida primeiro.   |

| **Ambiente**                        |
| ----------------------------------- |
| Área de Admin - Tela de Orçamentos |
| Navegador: Google Chrome    |
| Sistema: Windows 11                |

|     **Funcionalidade Afetada**    |            **Caso de Teste Relacionado**           |
| -------------------------------    | ------------------------------------------------   |
| Filtros de listagem de orçamentos  | CT-050: Aplicar filtros e pesquisa corretamente    |

|                     **Evidência(s)**                     |
| :------------------------------------------------------: |
| (vídeo da reprodução) |

-----
**Bug 03: Valor total inconsistente na listagem de orçamentos**

| **ID**  | **Descrição**                                                                                                                                                                                                             |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| BUG-003 | O valor total exibido na listagem de orçamentos não corresponde ao total exibido na tela de detalhes. Exemplo: Listagem mostra R$ 6.855,00, mas o valor correto é R$ 7.305,00 (Subtotal: R$ 7.755,00 | Desconto: R$ 450). |

| **Severidade do Bug** | **Prioridade de Correção** | **Status** |
| ------------------  -| ------------------------    | --------   |
|          Alta         |            Alta            |  Corrigido |


| **Passo a passo para simular o bug**                                                 |
| ------------------------------------------------------------------------------------ |
| 1. Fazer o login comoadmin                                                          |
| 2. Ir até a tela de Orçamentos                                                      |
| 3. Comparar o valor total da listagem com o valor exibido nos detalhes do orçamento |

|                       **Comportamento Esperado**                      |                    **Comportamento Obtido**                    |
| :-------------------------------------------------------------------: | :------------------------------------------------------------: |
| O valor total na listagem deve refletir o total correto do orçamento. | O valor exibido na listagem é incorreto (diferença de R$ 450). |

| **Ambiente**                        |
| ----------------------------------- |
| Área de Admin - Tela de Orçamentos  |
| Navegador: Chroem / Edge            |
| Sistema: Windows 11                 |

|          **Funcionalidade Afetada**         |            **Caso de Teste Relacionado**            |
| :-----------------------------------------: | :-------------------------------------------------: |
| Cálculo e exibição de valores de orçamentos | CT-  : Validar cálculo do valor total e descontos.  |

|                        **Evidência(s)**                        |
| :------------------------------------------------------------: |
| (print mostrando a diferença entre listagem e nos detalhes do orçamento) |

------
**Bug 04: Imagens do e-mail não são renderizadas**

| **ID**  | **Descrição**                                                                                                                 |
| ------- | ----------------------------------------------------------------------------------------------------------------------------- |
| BUG-004 | As imagens contidas nos e-mails enviados pelo sistema não estão sendo exibidas. Mostram-se espaços vazios ou links quebrados. |

| **Severidade do Bug** | **Prioridade de Correção** | **Status** |
|  -------------------  | ------------------------   | --------   |
|         Média         |            Média           |  Corrigido  |

| **Passo a passo para simular o bug**                                        |
| --------------------------------------------------------------------------- |
| 1. Disparar um e-mail automático do sistema (ex: confirmação de orçamento)  |
| 2. Abrir o e-mail no cliente de e-mail (Gmail, tuamaeaquelaursa, etc        |
| 3. Verificar se as imagens são exibidas corretamente                       |

|                     **Comportamento Esperado**                     |                       **Comportamento Obtido**                       |
| ----------------------------------------------------------------   | -------------------------------------------------------------        |
| As imagens devem ser renderizadas corretamente no corpo do e-mail. | As imagens não são exibidas (somente espaço vazio ou link quebrado). |

| **Ambiente**                       |
| -------------------------------    |
| E-mails automáticos do sistema     |
| Testado em Gmail e tuamaeaquelaursa|
| Sistema: Windows 11                |

|                **Evidência(s)**                |
| -------------------------------------------- |
| (print do e-mail com imagens ausentes)        |




