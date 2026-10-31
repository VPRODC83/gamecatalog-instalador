# Game Catalog — guia de instalação

O Game Catalog é um app gratuito para controlar a sua coleção de videogames numa planilha do Google, pelo celular:

- **Identificar** um jogo pela foto e dizer se você já tem, se está na sua lista de procurados ou na lista de compras.
- **Coleção** com capas automáticas, fotos suas da caixa e do cartucho e busca manual de imagens.
- **Compras**: o que você comprou e ainda não chegou. Ao chegar, o jogo entra na coleção.
- **Preço atual** no Brasil (Mercado Livre, Shopee, OLX, Enjoei, Amazon, Magalu, Americanas, KaBuM!, Casas Bahia e lojas de games) e no mundo (PriceCharting e eBay).
- **Editar** os dados da planilha, sempre com confirmação antes de mudar qualquer célula.

**Custo: zero.** Você usa só contas e planos gratuitos: GitHub, Google e Gemini.
**Tempo:** uns 20 minutos, uma vez só. Depois as atualizações chegam sozinhas, em até 3 horas após cada versão nova.

### ➜ [Criar o meu Game Catalog](https://github.com/new?template_name=gamecatalog-instalador&template_owner=VPRODC83)

*(Se o link não abrir o formulário, use o botão verde **Use this template → Create a new repository** no alto desta página.)*

---

## Sumário

1. [Como funciona (e por que é seguro)](#1-como-funciona-e-por-que-é-seguro)
2. [O que você precisa](#2-o-que-você-precisa)
3. [Parte A — GitHub: criar a sua cópia](#parte-a--github-criar-a-sua-cópia-5-min)
4. [Parte B — Google Cloud: criar o seu login](#parte-b--google-cloud-criar-o-seu-login-10-min)
5. [Parte C — Instalar](#parte-c--instalar-2-min)
6. [Parte D — Primeiro uso no celular](#parte-d--primeiro-uso-no-celular-5-min)
7. [Atualizações](#atualizações)
8. [Problemas comuns](#problemas-comuns)
9. [Privacidade, outros aparelhos e desinstalação](#privacidade-outros-aparelhos-e-desinstalação)

---

## 1. Como funciona (e por que é seguro)

```
 VPRODC83/gamecatalog-app          SEU repositório (cópia deste modelo)         SEU celular
 ┌──────────────────────┐   todo  ┌─────────────────────────────────┐         ┌──────────────┐
 │ versões assinadas    │──dia──▶ │ workflow "Instalar ou atualizar"│──────▶  │ app no Chrome│
 │ (só o dono publica)  │         │ 1. baixa a versão               │ GitHub  │ (instalável) │
 └──────────────────────┘         │ 2. confere a assinatura         │ Pages   └──────┬───────┘
                                  │ 3. publica no SEU GitHub Pages  │                │
                                  └─────────────────────────────────┘                ▼
                                                              SUA conta Google: planilha + fotos no Drive
```

- **Você tem a sua própria instalação**, no seu GitHub, com o seu login Google. Ninguém mais, nem o autor do app, tem acesso à sua planilha, às suas fotos ou às suas chaves.
- **Atualizações seguras:** o seu repositório só instala versões que tenham um **atestado de proveniência** assinado, provando que o arquivo foi gerado pelo processo oficial do repositório [VPRODC83/gamecatalog-app](https://github.com/VPRODC83/gamecatalog-app). Se alguém tentar entregar um arquivo alterado, a verificação falha e nada é publicado.
- **Só o dono escreve no repositório oficial.** Você tem controle total sobre a sua cópia e pode pausar as atualizações quando quiser.
- **As chaves do Gemini e do Tavily ficam só no seu celular.** Não vão para o GitHub nem para a planilha.

## 2. O que você precisa

| Item | Para quê | Custo |
| --- | --- | --- |
| Conta no **GitHub** ([criar](https://github.com/signup)) | Hospedar o seu app (GitHub Pages) e receber as atualizações | Grátis |
| Conta **Google** (Gmail) | Login, planilha e fotos no Drive | Grátis |
| **Celular Android com Chrome** (ou um computador) | Usar o app | — |
| Chave do **Gemini** | Identificar por foto e ler os preços dos anúncios | Grátis |
| Chave do **Tavily** *(opcional)* | Busca de preços mais completa (1.000 buscas/mês) | Grátis |

> 💡 **Anote o seu nome de usuário do GitHub.** O endereço do seu app vai ser
> `https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/`, por exemplo `https://mariasilva.github.io/game-catalog/`.
> Neste guia, troque `SEU-USUARIO` pelo seu nome de usuário, sempre em minúsculas.

Dica: faça as Partes A, B e C num **computador**, que é mais fácil. A Parte D é no celular.

---

## Parte A — GitHub: criar a sua cópia (5 min)

### A1. Criar a conta (se ainda não tiver)
1. Abra [github.com/signup](https://github.com/signup) e siga os passos (e-mail, senha, nome de usuário).
2. Confirme o e-mail. O plano **Free** é suficiente.

### A2. Criar o seu repositório a partir deste modelo
1. Entre no GitHub e clique em **[Criar o meu Game Catalog](https://github.com/new?template_name=gamecatalog-instalador&template_owner=VPRODC83)**. Ou, no alto desta página, clique em **Use this template → Create a new repository**.
2. Preencha:
   - **Owner:** você.
   - **Repository name:** `game-catalog` (ou outro nome, sem espaços).
   - **Visibility:** **Public**. É obrigatório para o GitHub Pages gratuito. O repositório não guarda nada pessoal: só a identificação pública do seu login (Client ID) e o processo de atualização.
   - Deixe **Include all branches** desmarcado.
3. Clique em **Create repository**.

### A3. Ligar o GitHub Pages
1. No seu repositório novo, clique em **Settings** (engrenagem, no alto).
2. No menu da esquerda, clique em **Pages**.
3. Em **Build and deployment → Source**, escolha **GitHub Actions**.

   Não precisa clicar em mais nada nessa tela.

### A4. Conferir se as Actions estão ligadas
1. Clique na aba **Actions** do seu repositório.
2. Se aparecer *“Workflows aren’t being run on this repository”*, clique em **I understand my workflows, go ahead and enable them**.
3. Você deve ver o workflow **Instalar ou atualizar o app** na lista da esquerda. Não rode ainda.

---

## Parte B — Google Cloud: criar o seu login (10 min)

O app precisa de uma “identificação de login” (Client ID) para pedir à sua conta Google permissão de usar a sua planilha. Você cria essa identificação no **Google Cloud**, de graça e **sem cartão de crédito**.

> Os nomes dos menus podem aparecer em português ou em inglês. Os dois estão indicados.

### B1. Criar o projeto
1. Abra [console.cloud.google.com](https://console.cloud.google.com) com a sua conta Google. Na primeira vez, aceite os termos.
2. No alto, à esquerda, clique no **seletor de projetos** e depois em **Novo projeto** (*New project*).
3. **Nome do projeto:** `Game Catalog`. Em **Local**, deixe *Sem organização*. Clique em **Criar** (*Create*).
4. Quando terminar, **selecione o projeto “Game Catalog”** no seletor do alto. Confira que o nome dele aparece lá antes de seguir.
5. Se o Google oferecer teste grátis ou pedir faturamento, **ignore**. Nada aqui precisa de faturamento.

### B2. Ativar as APIs da planilha e do Drive
1. Abra [Google Sheets API](https://console.cloud.google.com/apis/library/sheets.googleapis.com) e clique em **Ativar** (*Enable*).
2. Abra [Google Drive API](https://console.cloud.google.com/apis/library/drive.googleapis.com) e clique em **Ativar** (*Enable*).

   Confira que o projeto selecionado no alto é o **Game Catalog**.

### B3. Configurar a tela de login (Google Auth Platform)
1. Abra [console.cloud.google.com/auth/overview](https://console.cloud.google.com/auth/overview), ou o menu ☰ → **APIs e serviços** → **Tela de permissão OAuth** (*OAuth consent screen*).
2. Clique em **Primeiros passos** (*Get started*) e preencha:
   1. **Informações do app** (*App information*): nome **Game Catalog**; e-mail de suporte: o seu. **Próxima**.
   2. **Público-alvo** (*Audience*): **Externo** (*External*). **Próxima**.
   3. **Dados de contato** (*Contact information*): o seu e-mail. **Próxima**.
   4. Marque a concordância com a política de dados do usuário e clique em **Criar** (*Create*).

### B4. Colocar você como usuário de teste
1. No menu da esquerda do Google Auth Platform, clique em **Público-alvo** (*Audience*).
2. Em **Usuários de teste** (*Test users*), clique em **Adicionar usuários** (*Add users*).
3. Digite o **seu Gmail**, o mesmo que vai usar no app, e **Salvar**.

   Se mais alguém da casa for usar a **sua** instalação, adicione o e-mail dessa pessoa também (até 100).
4. **Não** clique em “Publicar app”. Deixe em **Teste**: assim não é preciso nenhuma verificação do Google, porque o app é só seu.

### B5. Criar o Client ID
1. No menu da esquerda, clique em **Clientes** (*Clients*) e depois em **Criar cliente** (*Create client*).
2. **Tipo de aplicativo** (*Application type*): **Aplicativo da Web** (*Web application*).
3. **Nome:** `Game Catalog web`.
4. Em **Origens JavaScript autorizadas** (*Authorized JavaScript origins*), clique em **Adicionar URI** e digite exatamente:
   ```
   https://SEU-USUARIO.github.io
   ```
   - Tudo em minúsculas.
   - **Sem** barra no final e **sem** o nome do repositório.
   - Deixe **URIs de redirecionamento autorizados** em branco.
5. Clique em **Criar** (*Create*).
6. Aparece o **ID do cliente** (*Client ID*), parecido com `123456789012-abcdef123456.apps.googleusercontent.com`. **Copie-o.**
   - Se fechou a janela, clique no nome do cliente na lista para ver o ID de novo.
   - A **chave secreta do cliente** (*client secret*) **não é usada**: não copie e não compartilhe.

---

## Parte C — Instalar (2 min)

1. No **seu** repositório do GitHub, clique na aba **Actions**.
2. Na lista da esquerda, clique em **Instalar ou atualizar o app**.
3. À direita, clique em **Run workflow**.
4. No campo **Client ID do Google**, cole o ID copiado em B5.
5. Clique no botão verde **Run workflow**.
6. Espere 1 a 3 minutos (recarregue a página). Quando o círculo ficar **verde ✅**, clique na execução: o **resumo** mostra o endereço do seu app.

| Resultado | O que fazer |
| --- | --- |
| ✅ **Game Catalog vX publicado** | Pronto! Vá para a Parte D. |
| ❌ **O GitHub Pages ainda não está ligado** | Refaça o passo A3 e rode de novo. |
| ❌ **Client ID inválido** | Copie de novo o ID inteiro (termina em `.apps.googleusercontent.com`). |
| ❌ Erro em **Baixar e verificar a versão** | A verificação de segurança falhou: **nada foi instalado**. Veja [Problemas comuns](#problemas-comuns). |

O Client ID fica salvo no arquivo `config.json` do seu repositório. Nas próximas vezes, rode o workflow **sem** preencher o campo.

---

## Parte D — Primeiro uso no celular (5 min)

### D1. Abrir e instalar
1. No **Chrome** do celular, abra `https://SEU-USUARIO.github.io/game-catalog/`, usando o nome do seu repositório no lugar de `game-catalog`.
2. Toque no menu **⋮** → **Instalar app** (ou **Adicionar à tela inicial**). O ícone do Game Catalog aparece junto com os outros apps.

### D2. Entrar com Google
1. Toque em **Entrar com Google** e escolha a sua conta (a mesma da Parte B4).
2. Vai aparecer **“O Google não verificou este app”**. É esperado: o app é seu e está em modo de teste. Toque em **Avançado** → **Acessar Game Catalog (não seguro)**.
3. Marque as duas permissões e toque em **Continuar**:
   - *Ver, editar, criar e excluir planilhas*: para ler e gravar a sua coleção.
   - *Ver, editar, criar e excluir apenas os arquivos do Drive que você usa com este app*: a pasta de fotos.

     O app **não** enxerga os seus outros arquivos do Drive.

> A sessão do Google dura cerca de 1 hora. Quando expirar, o app mostra **Entrar de novo**: é só tocar.

### D3. Escolher a planilha
- **Já tem uma planilha da coleção?** Abra-a no Google Sheets, copie o link e cole no app → **Usar esta planilha**.
- **Não tem?** Toque em **Criar uma planilha nova**. O app cria “Coleção de games” no seu Drive com as abas COLECAO, PROCURADOS e COMPRAS.

### D4. Dizer ao app como é a sua planilha
O app mostra as abas e as colunas da sua planilha:
1. **Coleção:** a aba dos jogos que você tem e as colunas de **console**, **nome** e **região**. As outras colunas com título (ex.: CIB, CAIXA, MANUAL) aparecem como detalhes de cada jogo.
2. **Procurados** *(opcional)*: uma ou mais abas com jogos que você quer. Para cada uma, indique a coluna do nome e, se houver, a coluna de **status**, onde o app escreve **COMPRADO**. Se a aba é de um console só (ex.: SFC), escreva-o em **console fixo da aba**.
3. **Lista de compras:** o nome da aba (é criada se não existir).
4. Toque em **Salvar e começar**.

Essa configuração fica na própria planilha, numa aba **APP_CONFIG**. Por isso vale para todos os seus aparelhos. Não apague nem edite essa aba à mão.

### D5. Cadastrar a chave do Gemini (para identificar por foto)
1. Abra [aistudio.google.com/apikey](https://aistudio.google.com/apikey) com a sua conta Google e aceite os termos.
2. Toque em **Criar chave de API** (*Create API key*) e copie a chave (começa com `AIza…`).
3. No app: **Ajustes** → cole em **Chave do Gemini** → **Salvar chaves** → **Testar Gemini**.
   - Se aparecer que o modelo não existe, toque em **Listar modelos** e escolha um com “flash” no nome.
4. ⚠️ No plano gratuito, o Google pode usar o que você envia (fotos e textos) para melhorar os produtos dele. Não fotografe documentos ou nada sigiloso.

### D6. *(Opcional)* Chave do Tavily, para preços mais completos
1. Crie a conta grátis em [app.tavily.com](https://app.tavily.com) (sem cartão) e copie a **API key** (`tvly-…`).
2. No app: **Ajustes** → **Chave do Tavily** → **Salvar chaves**.

Sem o Tavily, o app usa a busca do Google embutida no Gemini.

### Pronto! 🎮
- **Identificar:** fotografe a frente (e o verso, se quiser), toque em **Identificar**.
- **Coleção:** toque num jogo para fotografar, buscar outra imagem, editar ou ver o preço.
- **Compras:** toque em **Recebi** quando o jogo chegar.

As chaves ficam salvas **só no aparelho**. Em outro celular ou computador, cadastre de novo em **Ajustes**.

---

## Atualizações

- **Automáticas:** a cada 3 horas, o seu repositório verifica se há versão nova no repositório oficial. Havendo, ele baixa, **confere a assinatura** e publica. Você não precisa fazer nada. Quando a verificação não encontra versão nova, ela termina em poucos segundos e não publica nada.
- **Atualizar agora:** **Actions → Instalar ou atualizar o app → Run workflow**, sem preencher o Client ID.
- **Ver a versão instalada:** no app, em **Ajustes** (rodapé), ou no arquivo `versao-instalada.txt` do seu repositório.
- **Pausar as atualizações:** **Actions → Instalar ou atualizar o app → ⋯ (três pontos) → Disable workflow**. Para voltar, **Enable workflow**.
- **O que é verificado:** a soma SHA-256 do arquivo e o atestado de proveniência, com `gh attestation verify --repo VPRODC83/gamecatalog-app --signer-workflow VPRODC83/gamecatalog-app/.github/workflows/release.yml`. Se qualquer verificação falhar, a versão **não** é instalada e o app continua na versão anterior.
- O workflow grava uma linha por mês em `ultima-verificacao.txt`. Isso mantém o repositório “ativo”: o GitHub pausa rotinas de repositórios parados há 60 dias.

---

## Problemas comuns

| Mensagem ou sintoma | Causa | Solução |
| --- | --- | --- |
| Página **404** ao abrir o endereço | Pages desligado, workflow ainda não rodou ou endereço errado | Confira A3, rode a Parte C e espere 2 a 3 minutos. O endereço é `https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/`, com a barra no final |
| **“Instalação incompleta”** no app | Falta o Client ID | Parte C, preenchendo o campo **Client ID do Google** |
| Google: **Erro 400: origin_mismatch** ou **redirect_uri_mismatch** | Origem errada no Client ID | Em B5, a origem precisa ser exatamente `https://SEU-USUARIO.github.io`, em minúsculas, sem barra e sem o nome do repositório. Corrija, espere 5 minutos e tente de novo |
| Google: **“Acesso bloqueado: o app não concluiu o processo de verificação”** | O seu e-mail não está nos usuários de teste | Refaça B4 com o e-mail exato que você usa para entrar |
| Google: **“O Google não verificou este app”** | Normal no modo de teste | **Avançado → Acessar Game Catalog** (D2) |
| **“O Google negou o acesso a esta planilha”** | A planilha é de outra conta, ou faltou marcar a permissão | Entre com a conta dona da planilha (ou peça para compartilharem com você como Editor). Se não marcou as permissões, toque em **Ajustes → Sair** e entre de novo marcando tudo |
| **“Sessão do Google expirou”** | O login dura cerca de 1 hora | Toque em **Entrar de novo** |
| **“A chave do Gemini foi recusada”** | Chave errada ou apagada | Copie de novo em [aistudio.google.com/apikey](https://aistudio.google.com/apikey) |
| **“O modelo escolhido não existe mais”** | O Google trocou os nomes dos modelos | **Ajustes → Listar modelos** e escolha um “flash” |
| **“Limite gratuito do Gemini atingido”** | Muitas consultas em pouco tempo | Espere; o limite diário zera de madrugada (horário do Pacífico) |
| Capas não aparecem num console | Console da planilha com um nome que o app não reconhece | **Ajustes → Plataformas das capas automáticas** e escolha a plataforma certa |
| ❌ no passo **Baixar e verificar a versão** | A verificação de segurança falhou | **Não** tente contornar. O app continua na versão anterior. Avise o autor abrindo uma *issue* em [VPRODC83/gamecatalog-app](https://github.com/VPRODC83/gamecatalog-app/issues) |
| O workflow diário parou de rodar | Repositório inativo por muito tempo, ou workflow desativado | **Actions → Instalar ou atualizar o app → Enable workflow**, depois **Run workflow** |

---

## Privacidade, outros aparelhos e desinstalação

**Onde ficam os seus dados**

| Dado | Onde fica | Quem acessa |
| --- | --- | --- |
| Coleção, procurados, compras, capas escolhidas e últimos preços | A sua planilha no Google Sheets | Você (e quem você compartilhar) |
| Fotos que você tira | Pasta **“Game Catalog - fotos”** no seu Google Drive | Você |
| Chaves do Gemini e do Tavily | Só no navegador de cada aparelho seu | Você |
| Client ID do Google | `config.json` no seu repositório (público, mas não é segredo) | Qualquer um pode ver; sozinho, ele não dá acesso a nada |

O autor do app **não** recebe nenhum dado seu. As fotos de identificação vão direto do seu celular para o Gemini (Google), e as buscas de preço vão para o Tavily ou o Google.

**Outros aparelhos:** abra o mesmo endereço, entre com a mesma conta Google e cadastre as chaves em **Ajustes**. A planilha e a configuração já estão lá.

**Outras pessoas:** o ideal é cada uma fazer a própria instalação, seguindo este guia, com a própria planilha. Para dividir a **sua** coleção com alguém da casa, adicione o e-mail da pessoa em B4 e compartilhe a planilha com ela como Editor.

**Desinstalar**
1. Desinstale o app do celular, como qualquer outro.
2. Apague o seu repositório no GitHub: **Settings → Danger Zone → Delete this repository**.
3. Apague o projeto no Google Cloud: **IAM e administrador → Configurações → Encerrar** (*Shut down*).
4. Remova o acesso em [myaccount.google.com/connections](https://myaccount.google.com/connections).
5. Se quiser, apague a chave do Gemini em [aistudio.google.com/apikey](https://aistudio.google.com/apikey).

A sua planilha e a pasta de fotos continuam no seu Drive até você apagá-las.
