# Autocontrole

Sistema web para gestão de PACs, APPCC, rastreabilidade e controle de qualidade. Aplicação full-stack com Next.js, React e PostgreSQL.

## Importante: GitHub não é a hospedagem da aplicação

Este repositório guarda o código. Como o sistema usa API do Next.js e banco PostgreSQL, enviar os arquivos ao GitHub **não coloca o site funcionando na internet sozinho**. Para publicar, conecte o repositório a uma hospedagem compatível com Next.js (por exemplo, Vercel) e configure um banco PostgreSQL.

## Enviar ao GitHub pelo navegador

1. Extraia o ZIP no computador.
2. No GitHub, crie um repositório novo e deixe-o vazio (não marque para criar README).
3. Abra o repositório e escolha **Add file → Upload files**.
4. Abra a pasta extraída no computador e arraste os arquivos e pastas que estão dentro dela para a página do GitHub. Não envie apenas o arquivo ZIP.
5. Clique em **Commit changes**.

> Se o navegador não aceitar pastas/arquivos ocultos, use GitHub Desktop ou Git no computador para enviar o repositório completo. O arquivo `.gitignore` precisa ser mantido.

## Publicar o site

1. Crie uma conta/ projeto na Vercel e importe o repositório GitHub.
2. Crie um banco PostgreSQL hospedado.
3. Na configuração do projeto de hospedagem, adicione as variáveis de ambiente necessárias:
   - `DATABASE_URL`: URL de conexão do PostgreSQL.
   - `SENHA_PADRAO`: senha compartilhada de acesso definida por você.
   - `UPLOAD_DIR`: diretório de uploads, se o serviço usar armazenamento persistente.
4. Execute `database/schema.sql` no PostgreSQL para criar as tabelas. Use `database/seed.sql` apenas se quiser inserir os dados iniciais previstos nele.
5. Faça o deploy e teste login, páginas, API e gravação de dados.

**Não publique senhas, chaves ou o arquivo `.env` no GitHub.** O arquivo `.env.example` contém apenas valores de exemplo.

## Rodar localmente

Requisitos: Node.js 20 ou superior e um PostgreSQL acessível.

```bash
npm install
cp .env.example .env
# Edite .env com os dados reais do seu banco e uma senha própria
npm run dev
```

Abra `http://localhost:3000`.

## Scripts

- `npm run dev` — servidor local de desenvolvimento
- `npm run build` — compila para produção
- `npm start` — inicia o servidor de produção compilado
- `npm run migrate` — executa o script de migração existente

## Arquivos principais

- `src/app/` — páginas e endpoints de API
- `src/components/` — componentes da interface
- `src/lib/` — autenticação, banco de dados e lógica compartilhada
- `database/` — schema e dados iniciais do PostgreSQL
- `public/` — ícone, manifesto e service worker

## Verificação

O projeto foi organizado para a estrutura do Next.js, mas o build de produção precisa ser executado no ambiente com as dependências instaladas e as configurações necessárias. Não considere a publicação concluída até confirmar que o build passa e que o banco/login funcionam no ambiente de hospedagem.
