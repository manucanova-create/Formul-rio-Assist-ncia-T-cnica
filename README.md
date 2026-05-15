# Assistência Técnica — SOHOME
**Sistema de Registro de Ocorrências — Exportação**

---

## Visão Geral

Este sistema é uma aplicação web em arquivo único (`index.html`) utilizada pela equipe de exportação da SOHOME para registrar ocorrências de assistência técnica junto a lojistas internacionais. Funciona diretamente no navegador, sem necessidade de instalação ou servidor.

---

## Como Utilizar

### Pré-requisitos

- Navegador moderno (Chrome, Firefox, Edge ou Safari)
- Conexão com a internet (para carregar a fonte e enviar os dados)
- Os arquivos de logo (`LOGO GRUPO SOHOME-56.png` e `LOGO GRUPO SOHOME-60.png`) devem estar na mesma pasta que o `index.html`

### Abertura

Basta abrir o arquivo `index.html` diretamente no navegador. O sistema detecta automaticamente o idioma preferido do navegador e exibe a interface em **Português**, **Espanhol** ou **Inglês**.

---

## Fluxo de Preenchimento

O formulário é dividido em **2 etapas**, representadas na barra de progresso no topo da página.

---

### Etapa 1 — Identificação

Reúne as informações básicas da ocorrência antes de avançar ao registro.

#### 🧾 Número da Invoice

| Campo | Obrigatório | Descrição |
|---|---|---|
| Número da Invoice | Sim | Número exato da invoice comercial do produto reclamado. Um número incorreto trava o processo. |
| Ordem de Compra (PO) | Não | Número de PO do lojista, caso ele utilize rastreamento interno por ordem de compra. |
| Reincidência | Não | Toggle que indica se já houve assistência técnica anterior para este mesmo produto. Ao ativar, aparece o campo para informar a invoice da primeira ocorrência. |

#### 👤 Dados do Lojista

O sistema utiliza busca por e-mail para proteger os dados do cliente (LGPD). O usuário informa o e-mail cadastrado na invoice e clica em **Consultar**. Se encontrado, os dados são preenchidos automaticamente (somente leitura):

- Razão Social
- País
- Nome do Responsável
- Telefone(s)
- E-mail de Contato

É possível adicionar e-mails adicionais opcionais para cópia no acompanhamento.

> Para corrigir os dados preenchidos, clique em **✕ Limpar** e realize uma nova consulta.

#### 📅 Datas e Prazo de Garantia

| Campo | Obrigatório | Descrição |
|---|---|---|
| Data da Fatura (Invoice) | Sim | Data de emissão da fatura comercial |
| Data de Recebimento da Mercadoria | Sim | Data em que o contêiner foi recebido no destino |

Após preencher as datas, o sistema calcula automaticamente quantos dias se passaram desde o recebimento e exibe uma barra de progresso indicando a situação da garantia:

- **Verde** — dentro do prazo de 1 ano
- **Amarelo** — próximo do limite (menos de 30 dias)
- **Vermelho / Alerta** — fora do prazo de garantia

> Casos fora da garantia não são elegíveis para assistência técnica padrão. Apenas danos estruturais comprovados podem ser avaliados em caráter excepcional, mediante aprovação da SOHOME.

Clique em **Avançar para o Registro →** para prosseguir. Todos os campos obrigatórios devem estar preenchidos.

---

### Etapa 2 — Registro da Ocorrência

Permite registrar um ou mais produtos com defeito vinculados à mesma invoice.

#### 🛋️ Por produto, preencha:

| Campo | Obrigatório | Descrição |
|---|---|---|
| Produto | Sim | Busca pelo nome — selecione da lista de produtos cadastrados |
| Qtd. de Módulos | Sim | Quantidade de módulos afetados pelo defeito |
| Descrição do Defeito | Sim | Descreva o que ocorreu, como ocorreu e quando foi identificado |
| Embalagem avariada? | Sim | Indicar se a embalagem chegou com avarias (amassados, rasgos, umidade, impactos) |
| Fotos e Vídeos | Recomendado | Anexar 1 foto do produto completo, 1 foto do defeito, 1 foto no ambiente e 1 vídeo demonstrativo |
| O defeito impede o uso? | Sim | Indicar se o produto ficou inutilizável |
| Reparo local possível? | Sim | Indicar se há viabilidade de reparo no local do cliente |

Se o reparo local for **viável**, campos adicionais são exibidos:
- Valor estimado do reparo
- Nome do prestador de serviço
- Upload do orçamento do prestador

> Nenhum reembolso é realizado sem orçamento previamente aprovado pela SOHOME.

#### Envio por produto

Cada produto deve ser **enviado individualmente** antes de salvar o extrato, clicando no botão **📤 Enviar** no cabeçalho do bloco. Após o envio, o botão muda para **✓ Enviado** e o produto fica bloqueado para edição.

Para adicionar mais produtos à mesma ocorrência, clique em **＋ Adicionar outro produto**.

#### Salvar as informações

Após enviar pelo menos um produto, clique em **💾 Salvar as Informações**. O sistema exibirá a tela de confirmação com:

- Número do ticket gerado
- Extrato completo da ocorrência
- Botões para **Imprimir / Salvar PDF** e **Copiar Texto**
- Opção para iniciar um novo registro

---

## Idiomas Suportados

O sistema detecta automaticamente o idioma do navegador e alterna entre:

- 🇧🇷 Português (padrão)
- 🇪🇸 Espanhol
- 🇺🇸 Inglês

---

## Cobertura da Garantia

São **procedentes** de assistência técnica:
- Defeitos de fabricação comprovados
- Reincidências documentadas
- Componentes faltantes ou incorretos
- Reclamações dentro do prazo de 1 ano a partir do recebimento

**Não são procedentes:**
- Variações naturais de mármore, madeira ou textura
- Divergências de até 2 cm em produtos artesanais
- Reclamações após 1 ano do recebimento

---

## Observações Técnicas

- O sistema é **100% client-side** (sem backend próprio). O envio dos dados depende de integração configurada no script.
- A base de clientes está embutida no arquivo HTML e é consultada localmente por e-mail.
- Nenhum dado é armazenado no navegador entre sessões.
- O layout é responsivo e funciona em dispositivos móveis.
