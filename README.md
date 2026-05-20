# Formulario de Assistencia Tecnica - SOHOME

Formulario publico para abertura de assistencias tecnicas de exportacao, publicado via GitHub Pages.

Link publico:
https://manucanova-create.github.io/Formul-rio-Assist-ncia-T-cnica/

## O que o formulario faz

- Identifica o cliente por e-mail cadastrado.
- Preenche dados da empresa, pais, responsavel, telefone e e-mail.
- Coleta invoice, ordem de compra, datas e recorrencia.
- Permite registrar um ou mais produtos reclamados.
- Envia cada produto individualmente para o Bitrix24 ao clicar em **Enviar**.
- Retorna o numero do atendimento do Bitrix no proprio bloco do produto.
- Bloqueia os dados ja enviados para evitar alteracao depois do envio.
- Gera um extrato final com os dados da assistencia e miniaturas das imagens anexadas.

## Arquivos principais

- `index.html`: formulario completo, regras de validacao, integracao com Bitrix24 e extrato.
- `produtos.txt`: lista de produtos exibida no campo de busca do produto.
- `Informacoes de Clientes.xlsx`: base usada para gerar/atualizar os clientes embutidos no formulario.
- `LOGO*.png` e `LOGO*.svg`: arquivos de identidade visual usados na pagina.

## Fluxo de uso

1. O cliente informa a invoice e consulta o cadastro pelo e-mail.
2. O formulario preenche os dados do lojista.
3. O cliente informa datas, recorrencia e demais dados gerais.
4. O cliente adiciona um produto, preenche defeito, anexos e perguntas.
5. Ao clicar em **Enviar**, o produto e enviado ao Bitrix24.
6. O formulario mostra o atendimento retornado, por exemplo `Bitrix #32003`.
7. Depois de enviar os produtos, o cliente pode gerar o extrato em **Salvar as Informacoes**.

## Integracao com Bitrix24

A integracao fica no bloco `Bitrix24 integration` dentro do `index.html`.

Configuracoes atuais:

- Funil: `ASSISTENCIA`
- `CATEGORY_ID`: `1`
- Etapa inicial: `Nova Assistencia`
- `STAGE_ID`: `C1:UC_WM3E1W`
- Origem da Assistencia: `Exportacao`
- `UF_CRM_1727362004`: `19451`

O titulo do negocio e atualizado depois da criacao, porque o numero do atendimento so existe apos o Bitrix retornar o ID:

```text
Exportacao || Atendimento:ID || Invoice:INVOICE || Cliente:CLIENTE
```

## Campos importantes do Bitrix

- `UF_CRM_1779124884`: prazo de garantia (`Dentro da garantia`, `Fora da garantia` ou `Data futura`)
- `UF_CRM_DEAL_1758647396824`: ordem de compra
- `UF_CRM_1664887086`: fotos e videos do produto
- `UF_CRM_1778767737`: prestador de servico
- `UF_CRM_DEAL_1668773451236`: produto
- `UF_CRM_1664886906`: numero de modulos
- `UF_CRM_1664886937`: descricao do defeito
- `UF_CRM_1778767570`: embalagem avariada
- `UF_CRM_1778767613`: defeito impede uso
- `UF_CRM_1778767696`: custo estimado do reparo
- `UF_CRM_1778767669`: reparo local possivel
- `UF_CRM_1667444111295`: arquivo de orcamento
- `UF_CRM_1748962012`: telefone
- `UF_CRM_1748961973`: e-mail principal e e-mails adicionais
- `UF_CRM_1749237856`: pessoa de contato
- `UF_CRM_1778767236`: data da fatura
- `UF_CRM_1778767167`: data de recebimento
- `UF_CRM_1727360923`: numero da fatura
- `UF_CRM_DEAL_1673889459929`: reincidencia (`907` = Sim, `909` = Nao)
- `UF_CRM_1778767501`: fatura original
- `UF_CRM_1748961942`: nome da empresa
- `UF_CRM_1702558335`: pais

## Atualizar produtos

Para alterar a lista do campo **Produto**, edite `produtos.txt`.

Regras:

- Um produto por linha.
- Manter os nomes em caixa alta, seguindo o padrao atual.
- Depois de alterar, publicar no GitHub Pages.

## Publicacao

O site e publicado pelo GitHub Pages a partir da branch `main`.

Comandos usuais:

```bash
git status
git add index.html produtos.txt README.md
git commit -m "Descricao da alteracao"
git push origin main
```

Depois do push, o GitHub Pages pode levar alguns instantes para refletir a alteracao no link publico.

## Observacoes de manutencao

- Cada produto enviado cria um negocio separado no Bitrix24.
- O botao **Enviar** envia ao Bitrix; o botao **Salvar as Informacoes** apenas gera o extrato.
- Arquivos de imagem aparecem como miniaturas no extrato.
- Videos, PDFs e documentos aparecem pelo nome do arquivo no extrato.
- O campo de orcamento do Bitrix aceita apenas um arquivo; o formulario envia o primeiro arquivo anexado.
- Evite commitar arquivos temporarios, como `~$Informacoes de Clientes.xlsx` e `Thumbs.db`.
