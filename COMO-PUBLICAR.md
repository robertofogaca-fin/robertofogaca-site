# Site robertofogaca.com.br: como manter e publicar

## Estrutura

Tudo o que vai ao ar fica dentro da pasta `public/` do repositório.
Os caminhos abaixo são relativos a ela.

```
index.html                     página principal (antes: o arquivo único v9)
publicacoes.html               a aba Publicações (lista com filtro por tema)
publicacoes/
  modelo-de-artigo.html        modelo: duplique para cada artigo novo
assets/
  css/style.css                toda a identidade visual (cores, fontes, cards)
  img/roberto-fogaca.jpg       sua foto
downloads/                     planilhas para download
```

Por que separar em arquivos: o v9 tinha 275 KB, quase tudo foto e planilhas
em base64. Agora a home tem cerca de 16 KB, carrega mais rápido, e uma mudança
de cor no `style.css` vale para todas as páginas de uma vez.

## Publicar um artigo novo (cerca de 10 minutos)

1. Duplique `publicacoes/modelo-de-artigo.html` e renomeie com um nome curto,
   sem acentos e com hífens. Exemplo: `reforma-tributaria-ips.html`.
2. No novo arquivo, troque:
   - o bloco "TROQUE ESTES 4 ITENS" no topo (título, descrição e os dois links
     com o nome do arquivo);
   - a etiqueta, o título, o subtítulo e a data no cabeçalho;
   - o texto dentro de `<article class="prose">`;
   - o link de compartilhamento (`url=`... com o endereço do artigo).
3. Em `publicacoes.html`, copie um card `<article class="card post">` do tipo 1
   e cole no topo da lista, apontando para o arquivo novo.
4. Na `index.html`, seção "Últimos textos", mantenha os 3 mais recentes.
5. Salve (commit) no GitHub. O Cloudflare publica sozinho em cerca de um minuto.

## Registrar um post do LinkedIn (cerca de 2 minutos)

Copie um card do tipo 2 em `publicacoes.html`, cole o link do post (no LinkedIn:
"..." → "Copiar link para o post") e escreva um resumo de uma linha.

## Temas do filtro

O valor de `data-cat` do card precisa ser igual ao `data-filter` do botão:
`contabilidade`, `regulatorio`, `tributario`, `tesouraria`, `fpa`, `carreira`.
Para criar um tema novo, adicione um botão em `.filters` com o mesmo valor.

## Formatação dentro do artigo

| Quero... | Use |
|---|---|
| Subtítulo de seção | `<h2>Texto</h2>` |
| Parágrafo | `<p>Texto</p>` |
| Lista | `<ul><li>item</li></ul>` |
| Frase em destaque | `<blockquote>Texto</blockquote>` |
| Caixa de dica | `<div class="callout"><b>Na prática:</b> texto</div>` |
| Imagem | coloque em `assets/img/` e use `<img src="../assets/img/arquivo.jpg" alt="descrição">` |

## Antes de subir

- Abra a página no navegador e no celular.
- Remova os cards marcados como [Exemplo].
- Teste a prévia do link no LinkedIn Post Inspector:
  https://www.linkedin.com/post-inspector/
- O domínio usado nas tags `og:` e `canonical` é `https://robertofogaca.com.br`.
  Se o endereço for outro, troque com "Localizar e substituir" em todos os arquivos.

## Publicar um post com carrossel (exemplo: publicacoes/gargalo-do-time.html)

1. Exporte cada página do PDF do carrossel como imagem JPG. Pode usar o Canva
   ("Baixar" → JPG → todas as páginas) ou um conversor de PDF para JPG.
2. Salve as imagens em `assets/img/publicacoes/` com nomes em sequência:
   `tema-1.jpg`, `tema-2.jpg`, e assim por diante.
3. Duplique `gargalo-do-time.html`, troque os textos e os nomes das imagens
   no bloco `<div class="slides">`. O contador "1 / 9" se ajusta sozinho.
4. Coloque o PDF em `downloads/` para o botão "Baixar carrossel".
5. Para incorporar o post: no LinkedIn, abra o post → "..." → "Incorporar esta
   publicação". Copie só o endereço que aparece em `src="..."` e cole no
   `<iframe>` da seção "A conversa continua no LinkedIn".

## Prévia do link no LinkedIn

- A descrição (`og:description`) precisa ter **pelo menos 100 caracteres**.
- A imagem de prévia (`og:image`) fica melhor **horizontal, em 1200 x 627 px**.
  Imagens verticais, como a capa de um carrossel, aparecem cortadas.
- Depois de publicar, cole o link em https://www.linkedin.com/post-inspector/
  e clique em **Inspect**. Isso também força o LinkedIn a atualizar a prévia.
