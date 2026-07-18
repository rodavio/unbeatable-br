# Tradução brasileira de UNBEATABLE

Projeto comunitário de tradução para português do Brasil de **UNBEATABLE**.

Este repositório reúne os textos extraídos do jogo e o material de trabalho da tradução. A distribuição no jogo é feita com **BepInEx 5** e o plugin [UnbeatableTranslations](https://github.com/ErikGXDev/UnbeatableTranslations), que torna a tradução mais resistente a atualizações do jogo.

> Este é um projeto de fãs, sem vínculo com a desenvolvedora ou publicadora de UNBEATABLE. É necessário possuir uma cópia legítima do jogo.

## Como a tradução funciona

As falas de UNBEATABLE ficam em assets da Unity. Elas são extraídas com o [UABEA](https://github.com/nesrak1/UABEA), traduzidas preservando a estrutura do arquivo e recolocadas temporariamente no jogo. Em seguida, o plugin exporta as falas para um arquivo de tradução separado.

Na próxima execução, o plugin carrega esse arquivo da pasta `Translation` no diretório do jogo. Assim, a tradução não fica dependente dos IDs internos dos assets, que podem mudar a cada atualização de UNBEATABLE.

Fluxo resumido:

1. Extrair um arquivo de falas com UABEA.
2. Traduzir o texto, preservando o formato e o nome original do arquivo.
3. Reimportar o arquivo no jogo com UABEA.
4. Usar o plugin para exportar as falas para `translations_dumped`.
5. Copiar `lines.json` para a pasta `Translation` do jogo.
6. O plugin aplica as falas dessa pasta sempre que o jogo é iniciado ou a tradução é recarregada.

## Dependências

- [BepInEx 5](https://github.com/BepInEx/BepInEx)
- [UnbeatableTranslations](https://github.com/ErikGXDev/UnbeatableTranslations/releases)
- [UABEA](https://github.com/nesrak1/UABEA), para extrair e reimportar textos

## Instalando para testar

1. Instale o BepInEx 5 na pasta principal de UNBEATABLE.
2. Baixe a versão mais recente de UnbeatableTranslations e mescle o conteúdo do ZIP com a pasta do BepInEx.
3. Copie a pasta `Translation` da tradução para a pasta principal do jogo, ao lado do executável.
4. Inicie o jogo. Para compartilhar uma versão de teste, compacte o BepInEx já configurado junto da pasta `Translation`; quem receber deve extrair os dois na pasta do jogo.

## Atalhos do plugin

Use-os no menu principal e confira o console do BepInEx caso algo não saia como esperado.

| Atalho | Ação |
| --- | --- |
| `Ctrl` + `Shift` + `1` | Ativa ou desativa a tradução personalizada. |
| `Ctrl` + `Shift` + `2` | Recarrega os arquivos da pasta `Translation`. |
| `Ctrl` + `Shift` + `3` | Exporta os textos atuais do jogo para `translations_dumped`. |
| `Ctrl` + `Shift` + `4` | Recarrega a cena atual. Útil para recuperação após uma falha visual ou de carregamento. |

## Extraindo e traduzindo falas

1. Faça uma cópia de segurança de `UNBEATABLE/UNBEATABLE_data/resources.assets`.
2. Abra `resources.assets` no UABEA.
3. Ordene por **Path ID** e localize os assets de texto `Default (en-US)` — os IDs podem mudar a cada atualização. Abra **View Data** para identificar o capítulo pelas falas.
4. Use **Export Dump** para salvar o arquivo de texto. Guarde sempre uma cópia do original para consulta durante a tradução.
5. Traduza apenas o conteúdo das falas. **Não altere o nome de quem está falando** nos arquivos de diálogo e preserve marcações, chaves, IDs e a estrutura do dump.
6. No mesmo asset e caminho, use **Import Dump** e escolha o arquivo traduzido. O nome do arquivo importado deve ser exatamente o mesmo do arquivo exportado.
7. Abra o jogo e pressione `Ctrl` + `Shift` + `3`. O plugin cria `translations_dumped` com, entre outros, `lines.json` e `unity_translations.json`.
8. Copie `lines.json` para `Translation/lines.json`. Essa é a fonte que o plugin lê para aplicar os diálogos em qualquer instalação compatível.

## Arquivos de tradução

- `translations_dumped/lines.json`: falas e diálogos; é o principal arquivo para a tradução narrativa.
- `translations_dumped/unity_translations.json`: textos da interface, interações, notificações, legendas de Translator Notes e nomes de falantes.
- `Translation/`: pasta lida pelo plugin. Ela pode conter `lines.json`, `unity_translations.json` e arquivos `*.yarnproject.json`.

No estado atual do plugin, diálogos, falantes e notificações são os itens mais confiáveis. Partes da interface ainda podem funcionar parcialmente ou não funcionar, portanto devem ser testadas no jogo antes de serem consideradas prontas.

## Boas práticas

- Nunca trabalhe diretamente sobre o único arquivo original.
- Mantenha o nome do arquivo e a estrutura exatamente como foram exportados.
- Não altere os nomes de falantes nos dumps de diálogo; quando necessário, use `unity_translations.json`.
- Teste cada bloco importado no jogo antes de prosseguir para o próximo.
- Após atualizações de UNBEATABLE, extraia novamente os assets: os Path IDs podem ter mudado.

## Créditos

- Plugin de carregamento de traduções: [ErikGXDev/UnbeatableTranslations](https://github.com/ErikGXDev/UnbeatableTranslations)
- Ferramenta de assets Unity: [UABEA](https://github.com/nesrak1/UABEA)
