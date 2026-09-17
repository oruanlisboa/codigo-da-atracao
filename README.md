# Código da Atração — funil

Páginas do funil de aquisição. HTML estático, sem build.

| Caminho | Página |
|---|---|
| `/teste/` | Quiz de diagnóstico (10 perguntas) |
| `/oferta/` | DESTRAVA — R$19,90 |
| `/ma/` | Masculinidade Autêntica — R$997 |
| `/obrigado/` | Pós-compra + upsell |

## Antes de rodar tráfego

Ajustar o bloco `CONFIGURAÇÃO` no topo do `<script>` de cada página:

- **`/teste/`** — `webhook` (Zapier/Make/ActiveCampaign) e `origensQuentes`
- **`/oferta/`** — `CHECKOUT`
- **`/ma/`** — `CHECKOUT` e `DOWNSELL`
- **`/obrigado/`** — `LINKS` (acesso, canal, upsell, recusa)

O quiz funciona com `webhook: ""` — o lead só não é enviado.

## Fluxo

```
/teste  →  origem quente  →  /ma      →  recusou  →  /oferta
        →  origem fria    →  /oferta  →  comprou  →  /obrigado
```

As páginas leem `perfil`, `gargalo` e `nome` da querystring e se personalizam.
UTMs são propagados do quiz até o checkout.
