# Supabase PDF Report Generator

API simples em FastAPI que gera relatórios PDF a partir de dados no Supabase.

## Arquivos principais
- `api.py` - aplicação FastAPI com endpoint `/generate-report`.
- `requirements.txt` - dependências necessárias.
- `render.yaml` - configuração para deploy no Render.
- `Procfile` - comando de inicialização (compatível com alguns PaaS).

## Instalação local
1. Crie e ative um virtualenv:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

2. Instale dependências:

```bash
pip install -r requirements.txt
```

3. Execute localmente:

```bash
uvicorn api:app --reload --host 0.0.0.0 --port 8000
```

## Uso
Enviar um POST para `/generate-report` com JSON (exemplo):

```json
{
  "table_name": "clientes",
  "fields": ["id", "nome", "email"],
  "supabase_url": "https://<projeto>.supabase.co",
  "anon_key": "eyJhbGciOi...",
  "report_title": "Relatório de Clientes"
}
```

Resposta: download de um arquivo PDF com os dados.

## Variáveis de ambiente (Render)
É possível definir `SUPABASE_URL` e `SUPABASE_ANON_KEY` no painel do Render e ajustar `api.py` para usá-las em vez de recebê-las no payload.

## Observações de segurança e melhorias
- Evitar enviar chaves no corpo do request em produção.
- Adicionar paginação/limites se a tabela for grande.
- Sanitizar nome do arquivo e validar campos solicitados.

## Licença
Este projeto é fornecido como exemplo.
