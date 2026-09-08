# CaptureHub

O CaptureHub é um aplicativo para Windows que grava a tela, captura imagens e
documenta o passo a passo. Durante a gravação ele registra cada clique e, ao
final, monta um relatório HTML de arquivo único e uma apresentação PowerPoint
editável.

Este repositório guarda só os downloads. O produto, com planos, conta e
perguntas frequentes, fica em [capturehub.com.br](https://capturehub.com.br).

## Requisitos

- Windows 10 versão 2004 ou superior
- Aproximadamente 400 MB de espaço livre

## Como baixar

Abra a página [Releases](https://github.com/ZaqueuLopesDaSilvaAraujo/capturehub-downloads/releases/latest)
e, em **Assets**, escolha uma das duas formas. Os nomes dos arquivos trazem o
número da versão, que muda a cada publicação.

### Instalador

1. Baixe o arquivo terminado em `-instalador.exe`.
2. Execute e siga o assistente.
3. O CaptureHub passa a abrir pelo menu Iniciar.

### Pacote portátil, sem instalar

1. Baixe o arquivo terminado em `.zip`.
2. Extraia todo o conteúdo para uma pasta.
3. Abra a pasta extraída.
4. Dê dois cliques em `Iniciar CaptureHub.cmd`.
5. A barra do CaptureHub aparece na lateral direita da tela.

> Não execute o aplicativo de dentro do ZIP. Extraia todos os arquivos antes de
> iniciar.

## Conferir o que você baixou

Cada arquivo tem um `.sha256` ao lado, na mesma release. Conferir leva um
segundo e prova que o arquivo que chegou é o mesmo que saiu daqui.

Baixe o `.sha256` junto do arquivo, abra o PowerShell na pasta onde os dois
estão e cole:

```powershell
Get-ChildItem CaptureHub-*.sha256 | ForEach-Object { $esperado = (Get-Content $_).Split()[0]; $arquivo = $_.FullName.Substring(0, $_.FullName.Length - 7); $obtido = (Get-FileHash $arquivo -Algorithm SHA256).Hash; '{0}: {1}' -f (Split-Path $arquivo -Leaf), $(if ($obtido -eq $esperado) { 'confere' } else { 'NAO CONFERE' }) }
```

Se aparecer `NAO CONFERE`, apague o arquivo e baixe de novo.

## Primeiro uso

Se o Windows exibir um aviso do SmartScreen:

1. Clique em **Mais informações**.
2. Confira se o arquivo aberto é o pacote do CaptureHub que você baixou.
3. Clique em **Executar assim mesmo**.

O aviso aparece porque o pacote ainda não tem assinatura digital. É também o
motivo de a conferência do SHA-256 acima existir: enquanto não há assinatura,
o hash é o que prova a procedência do arquivo.

## Atalhos principais

| Atalho | Ação |
|---|---|
| Ctrl+Shift+1 | Capturar uma imagem |
| Ctrl+Shift+2 | Iniciar ou parar uma gravação |
| Ctrl+Shift+3 | Pausar ou retomar a gravação |
| Ctrl+Shift+M | Marcar um momento importante |
| Ctrl+Shift+A | Ligar ou desligar o microfone |
| Ctrl+Shift+H | Mostrar ou ocultar a barra |

## Criar uma apresentação

1. Abra as configurações do CaptureHub.
2. Ative **Registrar cada clique e montar a apresentação no fim**.
3. Inicie a gravação e execute o procedimento desejado.
4. Pare a gravação.
5. Revise os passos capturados no editor.
6. Clique em **Gerar apresentação**.

O arquivo .pptx é salvo junto da evidência gravada.
