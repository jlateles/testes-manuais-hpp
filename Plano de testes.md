# Plano e Cenários de Testes 
## Objetivo:
> Validar as funcionalidades e fluxos principais do sistema, garantindo que os comportamentos estejam de acordo com os requisitos definidos e que as informações sejam exibidas corretamente.

## Identificação
- Nome do Projeto: E-commerce médico
- Versão Avaliada: V1
- Ambiente de Testes: dev, homolog e prod.
- Tipo de Teste: Teste Funcional Manual
- Data do Documento: 30/10/2025
- Responsável: Júlia Teles

## Escopo 
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

## Pré-requisitos gerais
  - O paciente deve possuir cadastro prévio com CPF e senha
  - Deve haver orçamentos associados ao CPF do paciente para exibição nas listagens

## Ferramentas Utilizadas
  - Navegador Google Chrome / Edge
  - Ferramentas de inspeção do navegador (DevTools)
  - Google Sheets / Docs e Linear (reportar bugs e registrar evidências)
  - Extensões:
      - Check my links
      - Jam

## Técnicas de Teste
