# Zilloah — Painel de Controle & Zilloah Club

Repositorio de frontend do projeto Zilloah Sao Caetano do Sul.
Desenvolvido e mantido pela LevelInteligencia.
Hospedado em: https://levelinteligencia.github.io/Zilloah/

---

## Links de acesso rapido

| O que e | Link |
|---|---|
| Dashboard da loja (vendas, estoque, clientes) | https://levelinteligencia.github.io/Zilloah/ |
| Painel do Zilloah Club (membros, tiers, saldo) | https://levelinteligencia.github.io/Zilloah/club.html |
| Check-in do cliente (QR Code) | https://levelinteligencia.github.io/Zilloah/checkin.html |
| Check-in modo Vitoria (vendedora) | https://levelinteligencia.github.io/Zilloah/checkin.html?vitoria |
| Regras do Zilloah Club (para compartilhar no WhatsApp) | https://levelinteligencia.github.io/Zilloah/regras.html |
| Repositorio dos agentes automaticos | https://github.com/Levelinteligencia/zilloah-agentes |

---

## Como funciona o check-in

O cliente escaneia o QR Code no quiosque e e direcionado para a tela de check-in.

**Primeiro acesso (cliente novo):**
1. Cliente digita o CPF
2. Sistema verifica que o CPF nao existe no banco
3. Aparece campo pedindo a data de nascimento
4. Cliente preenche e confirma — cadastro feito junto com o check-in

**Acessos seguintes:** cliente digita o CPF e o check-in e registrado automaticamente.

**Modo Vitoria** (URL com ?vitoria): mostra campo para identificar a vendedora e lista em tempo real com todos os check-ins do dia.

**Regra anti-duplicata:** cada CPF pode registrar no maximo 1 visita valida por dia (fuso horario de Sao Paulo, UTC-3).

---

## Tiers do programa

| Tier | Visitas nos ultimos 30 dias | Cashback na compra |
|---|---|---|
| Bronze | 1 visita | 4% |
| Prata | 2 visitas | 8% |
| Ouro VIP | 3 ou mais visitas | 12% |

O saldo de cashback expira em 90 dias sem atividade.

---

## Infraestrutura

| Componente | Tecnologia |
|---|---|
| Hospedagem das paginas | GitHub Pages |
| Banco de dados (check-ins, membros, saldo) | Supabase |
| Dados da loja (vendas, estoque, clientes) | API Jueri (ERP) |
| Agentes automaticos de email | GitHub Actions |
| Envio de emails | Zoho SMTP |

---

## Secrets configurados no repositorio zilloah-agentes

| Secret | Para que serve |
|---|---|
| JUERI_TOKEN | Acesso a API de dados da loja |
| JUERI_URL | Endereco da API da loja |
| SUPABASE_URL | Endereco do banco de dados |
| SUPABASE_SERVICE_KEY | Chave de acesso ao banco de dados |
| EMAIL_REMETENTE | De onde os emails sao enviados |
| EMAIL_SENHA | Senha do servidor de email |
| EMAIL_VITORIA | Email da Vitoria |
| EMAIL_LEVEL | Email da LevelInteligencia |

---

## Notas tecnicas

- A data de nascimento coletada no check-in e a fonte principal para o Agente 3 (emails de aniversario). O sistema Jueri tem esse campo vazio em ~90% dos cadastros.
- Arquivos .yml do GitHub Actions precisam ser editados direto na interface web do GitHub.
- Ao atualizar arquivos via API do GitHub, sempre buscar o SHA atual antes de atualizar.
- A contagem de visitas para o tier e feita ANTES de registrar a visita no banco, evitando bug de contagem zero.

---

Mantido por LevelInteligencia — contato@levelinteligencia.com.br
