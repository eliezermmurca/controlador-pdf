# Controlador de PDF

Ferramenta web de página única para **separar** PDFs de boletos em vários arquivos e **juntar** vários PDFs em um só.

Todo o processamento acontece no navegador: nenhum arquivo é enviado para servidor.

## Funcionalidades

### Separar boletos
Recebe um PDF com vários boletos (um por página), agrupa as páginas por um critério e gera um PDF por grupo, todos num `.zip` junto com um `resumo.csv` (página → grupo).

Critérios disponíveis:

| Critério | Como identifica |
| --- | --- |
| Cidade do pagador | Linha no formato `Bairro - Cidade / UF` |
| Estado (UF) | UF da mesma linha |
| Pagador | Nome antes de `, CNPJ` / `, CPF` |
| Vencimento | Data após o rótulo "Vencimento" |
| Linha abaixo de um texto | Rótulo e deslocamento definidos pelo usuário |
| Padrão avançado | Expressão regular (o 1º grupo vira o nome do grupo) |

Páginas sem a informação vão para o grupo "Sem identificação" ou podem ser juntadas ao boleto anterior (boletos com 2+ páginas). O painel "Ver o texto de uma página" mostra como o programa lê a página e permite escolher um rótulo clicando na linha.

### Juntar PDFs
Adiciona vários PDFs, permite reordenar (subir/descer, ordenar por nome) e baixa um único PDF.

## Como usar

1. Abra o `index.html` em um navegador moderno (Chrome, Edge, Firefox).
2. Escolha a aba desejada e arraste os arquivos.

Também pode ser publicado no GitHub Pages sem nenhuma configuração.

> Requer internet para carregar as bibliotecas pela CDN. Funciona apenas com PDFs que têm texto selecionável (não escaneados).

## Tecnologias

- [PDF.js](https://mozilla.github.io/pdf.js/) – extração de texto
- [pdf-lib](https://pdf-lib.js.org/) – criação dos PDFs
- [JSZip](https://stuk.github.io/jszip/) – geração do `.zip`

HTML, CSS e JavaScript puros, sem build.

## Observações

Os padrões de "Cidade", "Pagador" e "Vencimento" seguem o layout comum de boletos bancários brasileiros. Para outros layouts, use "Linha abaixo de um texto" ou "Padrão avançado".
