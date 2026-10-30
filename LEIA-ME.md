# Aniversários da família

Página pública no GitHub Pages. Qualquer pessoa com o link vê a lista, sem login.
Para incluir, alterar ou excluir é preciso a senha da família. Os dados ficam no Firebase (plano gratuito).

## Arquivos

- `index.html`: a página.
- `firebase-config.js`: os dados do seu projeto Firebase (você preenche).
- `firestore.rules`: as regras que protegem o banco (você cola no Firebase).

## Passo a passo

### 1. Criar o projeto no Firebase
1. Entre em https://console.firebase.google.com com sua conta Google.
2. Clique em **Criar um projeto**, dê um nome (por exemplo `aniversarios-familia`) e desative o Google Analytics.
3. Na tela inicial do projeto, clique no ícone **Web** (`</>`), dê um apelido ao app e registre. **Não** marque o Firebase Hosting.
4. Copie o bloco `firebaseConfig` que aparece e cole os valores em `firebase-config.js`.

### 2. Criar a senha da família
1. No menu, abra **Criação > Authentication** e clique em **Vamos começar**.
2. Em **Método de login**, ative **E-mail/senha** (só a primeira opção).
3. Na aba **Usuários**, clique em **Adicionar usuário**.
   - E-mail: `familia@aniversarios.app` (o mesmo de `firebase-config.js` e `firestore.rules`).
   - Senha: a senha que a família vai usar, com pelo menos 6 caracteres.

Crie o usuário você mesmo, antes de divulgar o link. Assim ninguém consegue registrar a conta da família primeiro.

### 3. Criar o banco e publicar as regras
1. Abra **Criação > Firestore Database** e clique em **Criar banco de dados**.
2. Escolha a localização `southamerica-east1` (São Paulo) e o modo **produção**.
3. Abra a aba **Regras**, apague o texto que estiver lá, cole o conteúdo de `firestore.rules` e clique em **Publicar**.

### 4. Publicar no GitHub Pages
1. Crie um repositório no GitHub (pode ser público; ele só guarda o código, não os aniversários).
2. Envie os arquivos `index.html`, `firebase-config.js` e `firestore.rules` (pelo botão **Add file > Upload files**).
3. Em **Settings > Pages**, escolha **Deploy from a branch**, branch `main`, pasta `/ (root)`, e salve.
4. Depois de um ou dois minutos o endereço aparece: `https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/`.

Se aparecer erro de domínio não autorizado ao digitar a senha, adicione `SEU-USUARIO.github.io` em **Authentication > Configurações > Domínios autorizados**.

## Como usar

- Quem abre o link vê a lista, os próximos aniversários e as idades (quando há o ano).
- **Adicionar pessoa**, **Editar** e **Excluir** pedem a senha da família.
- Em **Senha e acesso** você troca a senha e pode ligar **Pedir senha também para ver os aniversários**. Com isso ligado, o servidor só entrega a lista a quem digitar a senha.
- Para vincular pessoas, use a seção **Vínculos** do cadastro (por exemplo "Filho(a) de Sicrano"). A ficha de Sicrano passa a mostrar "Pai/mãe de Fulano".

## Esqueci a senha

No Firebase Console, abra **Authentication > Usuários**, exclua o usuário `familia@aniversarios.app` e crie de novo com a nova senha. Os aniversários cadastrados não são afetados.

## Limites

- A senha é uma só para a família. Quem a souber pode incluir, alterar e excluir.
- O plano gratuito do Firebase (Spark) comporta uma lista de família com folga.
- Para testar no seu computador, não abra o `index.html` direto no navegador. Rode `python3 -m http.server` na pasta e abra `http://localhost:8000`.
