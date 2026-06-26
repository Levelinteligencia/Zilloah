# Zilloah — Painel de Controle & Zilloah Club

Repositório de frontend do projeto Zilloah São Caetano do Sul.
Desenvolvido e mantido pela LevelInteligencIA.

> Os links de acesso são restritos e disponibilizados diretamente para o cliente.

---

## Como funciona o check-in

O cliente escaneia o QR Code no quiosque e é direcionado para a tela de check-in.

**Primeiro acesso (cliente novo):**
1. Cliente digita o CPF
2. Sistema verifica que o CPF não existe no banco
3. Aparece campo pedindo a data de nascimento
4. Cliente preenche e confirma — cadastro feito junto com o check-in

**Acessos seguintes:** cliente digita o CPF e o check-in é registrado automaticamente.

**Modo Vitória** (URL com ?vitoria): mostra campo para identificar a vendedora e lista em tempo real com todos os check-ins do dia.

**Regra anti-duplicata:** cada CPF pode registrar no máximo 1 visita válida por dia (fuso horário de São Paulo, UTC-3).

---

## Tiers do programa

| Tier | Visitas nos últimos 30 dias | Cashback na compra |
|---|---|---|
| Bronze | 1 visita | 4% |
| Prata | 2 visitas | 8% |
| Ouro VIP | 3 ou mais visitas | 12% |

O saldo de cashback expira em 90 dias sem atividade.

---

## Infraestrutura

| Componente | Tecnologia |
|---|---|
| Hospedagem das páginas | GitHub Pages |
| Banco de dados (check-ins, membros, saldo) | Supabase |
| Dados da loja (vendas, estoque, clientes) | API Jueri (ERP) |
| Agentes automáticos de email | GitHub Actions |
| Envio de emails | Zoho SMTP |

---

## Notas técnicas

- A data de nascimento coletada no check-in é a fonte principal para o Agente de emails de aniversário. O sistema Jueri tem esse campo vazio em ~90% dos cadastros.
- Arquivos .yml do GitHub Actions precisam ser editados direto na interface web do GitHub.
- Ao atualizar arquivos via API do GitHub, sempre buscar o SHA atual antes de atualizar.
- A contagem de visitas para o tier é feita ANTES de registrar a visita no banco, evitando bug de contagem zero.

---

Mantido por LevelInteligencIA — contato@levelinteligencia.com.br
