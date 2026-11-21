# Colheitas — app para iPhone (PWA)

Página HTML que se instala no ecrã principal do iPhone e funciona sem rede.
Os dados ficam **só no telemóvel** (IndexedDB) e saem pela exportação.

## Ficheiros

| Ficheiro | Para quê |
| --- | --- |
| `index.html` | A app inteira (ecrãs, base de dados local, QR, GPS, fotos, exportação) |
| `jsQR.js` | Leitura de códigos QR (biblioteca jsQR 1.4.0, licença Apache-2.0) |
| `manifest.json` | Nome, ícone e cores quando instalada |
| `sw.js` | Guarda a app para abrir sem rede |
| `icons/` | Ícones |

## 1. Publicar (grátis, GitHub Pages)

A câmara, o GPS e o modo offline só funcionam em **HTTPS**, por isso a app tem de estar alojada.

1. Crie um repositório no GitHub (pode ser privado só com conta paga; público serve, porque não contém dados).
2. Carregue todos estes ficheiros para a raiz do repositório (Add file → Upload files).
3. Settings → Pages → Branch `main`, pasta `/ (root)` → Save.
4. Ao fim de 1–2 minutos fica em `https://<utilizador>.github.io/<repositorio>/`.

## 2. Instalar no iPhone

1. Abra o endereço no **Safari**.
2. Partilhar → **Adicionar ao ecrã principal** → Adicionar.
3. Abra pelo ícone "Colheitas". Na primeira leitura de QR e no primeiro GPS, aceite as permissões.

Em Android: abrir no Chrome → menu → Instalar app.

## 3. Usar

- **Campanhas → + Nova**, depois **+ Adicionar ponto**: cada ponto cria uma colheita.
- **Preparação**: maré alvo, data e maré previstas, frascos (QR ou à mão) → *Pronta para campo*.
- **Recolha**: *Agora*, GPS, fotos, parâmetros, confirmar frascos com nova leitura de QR.
- **Resumo**: frascos em falta com motivo, destino de cada frasco, prazo de entrega; *Fechar colheita* só fica ativo sem avisos.
- **Exportar**: ZIP por campanha com `colheitas.csv`, `frascos.csv`, `medicoes.csv`, `campanha.json` e as fotos (CSV separado por `;`, abre direto no Excel).
- **Catálogos**: destinos (laboratórios), prefixo de cada tipo de frasco e parâmetros de campo.

### Códigos dos frascos
O tipo é reconhecido pelo prefixo do código: `MB-0142` → Microbiologia, `NUT-0088` → Nutrientes.
Prefixos por omissão: MB, MT, OD, NUT, CHL, SST, FIT, COT (editáveis em Catálogos).
O QR só precisa de conter o código em texto. Um código desconhecido pede o tipo.

## Cuidados importantes

- **Faça cópias de segurança** (Exportar → Criar cópia de segurança) no fim de cada saída. Se a app for apagada do ecrã principal, os dados desaparecem com ela.
- Cada telemóvel tem os seus próprios dados; juntar campanhas de várias pessoas faz-se com os ZIP/CSV.
- Ao publicar uma versão nova, mude `VERSAO` em `sw.js` (ex.: `colheitas-v2`); os telemóveis atualizam na abertura seguinte com rede.
- Prazos e conservantes nas fichas são valores típicos: confirme com o laboratório de destino.
