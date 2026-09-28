# Observatório Setorial de TIC — Santa Catarina

Painel do Observatório FIESC sobre o setor de tecnologia da informação
e comunicação em Santa Catarina: emprego, perfil da mão de obra,
indústria, comércio exterior e patentes.

A página é **um arquivo só**. A biblioteca de gráficos, as malhas do
IBGE, os logotipos, as bandeiras e todos os dados vão embutidos dentro
do próprio HTML — não há requisição a servidor de dados, não há banco
remoto, e o que o visitante filtra é processado na aba dele. A única
coisa que vem de fora é a fonte tipográfica do Google, e ela tem pilha
de reserva para quando não carregar.

## O recorte

O setor é o do de-para de CNAE do Observatório, coluna **SC
Competitiva**: **33 subclasses** nas divisões 26, 61 e 62. As patentes
usam as **91 subclasses da IPC** derivadas dessa mesma definição — o
núcleo.

## Publicação

Site estático de um arquivo. Não há build, não há `vercel.json`: o
Vercel serve `index.html` na raiz do domínio por conta própria.

No import: *Framework Preset* `Other`, *Build Command* vazio, *Output
Directory* vazio, *Root Directory* na raiz.

## De onde vem o arquivo

`index.html` **não é editado à mão**. Ele é gerado por
`Observatorio TIC/montar_offline.py`, no repositório `tic-renosto`,
que grava em três lugares ao mesmo tempo: a pasta do projeto, o
Desktop e este repositório. Editar aqui é perder a edição na próxima
geração.

Para publicar uma versão nova:

```bash
python "Observatorio TIC/dados_pagina.py"     # monta os dados
python "Observatorio TIC/montar_offline.py"   # costura o arquivo
cd ~/Desktop/Observatorio_TIC_site
git commit -am "atualiza o painel" && git push
```

O terceiro destino existe por uma razão concreta: o espelho do
explorador de patentes já ficou três dias parado numa versão antiga
enquanto o código andava, e defeitos já corrigidos foram reportados de
novo. O que o gerador não escreve sai de sincronia.
