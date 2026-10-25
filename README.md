# Site Processos — Cloudflare Worker

Este diretório contém o site e a API de leitura e edição pública dos textos existentes da Visão geral.

## Cloudflare Builds
- Worker existente: site-processos-notion
- Diretório raiz: cloudflare-worker
- Branch de produção: main
- Comando de build: vazio
- Comando de deploy: npx wrangler deploy

Mantenha NOTION_API_TOKEN somente como Secret de execução do Worker. Não adicione tokens a arquivos nem a variáveis de build.
A conexão do Notion precisa da capacidade Atualizar conteúdo para salvar.

A última consulta fica salva no navegador. Não há atualização automática. Faz uma consulta inicial se ainda não houver cópia local; depois, consulta novamente somente pelo botão Atualizar. Os resultados confirmados de edições são incorporados à cópia local sem uma nova leitura completa. Limpar os dados do navegador remove essa cópia.
Edição pública sem login, conforme solicitado; somente textos existentes da Visão geral. Demais abas não são editáveis nesta versão.
Defina PUBLIC_EDITING_DISABLED=true no Worker para desativar a edição pública.

O arquivo worker.js é independente e contém o HTML codificado em base64, para evitar corrupção ao copiar. Não é necessário compilar.
