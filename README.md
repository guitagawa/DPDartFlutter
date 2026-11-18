# Passo Livre

Aplicativo Android do desafio FIAP CitizenTech, desenvolvido em Flutter.

| Integrante | RM |
| --- | --- |
| Guilherme Tagawa | 98306 |

## Problema e público

Um buraco na calçada ou uma rampa bloqueada pode obrigar uma pessoa a desviar pela rua. O aplicativo permite que moradores registrem esses obstáculos e acompanhem os pontos que já foram resolvidos. A proposta se relaciona ao ODS 11, Cidades e comunidades sustentáveis, pelo foco na acessibilidade dos trajetos a pé.

## Como usar

1. Na tela inicial, toque em **Registrar problema**.
2. Informe a rua, uma referência e o problema encontrado. Toque em **Salvar**.
3. Em **Ver registros**, selecione um local para abrir seus detalhes.
4. Use **Editar** para alterar a descrição ou marcar o problema como resolvido. Para remover o registro, toque em **Excluir** e confirme.

O painel exibe o total de ocorrências e quantas continuam em aberto. A tela **Sobre o ODS 11** explica a ligação com o tema.

## Organização e persistência

As telas ficam em `lib/telas`. O arquivo `lib/dados.dart` contém o modelo Ocorrencia e o ChangeNotifier Registros. As telas observam o Provider, que lê e grava os dados de forma assíncrona com sqflite.

Na primeira abertura, o aplicativo cria o arquivo `passo_livre.db` e a tabela `ocorrencias` no aparelho. Os registros continuam disponíveis após fechar e reabrir o aplicativo.

| Coluna | Tipo | Conteúdo |
| --- | --- | --- |
| id | INTEGER PRIMARY KEY | Identificador gerado pelo SQLite |
| local | TEXT NOT NULL | Rua e ponto de referência |
| problema | TEXT NOT NULL | Descrição do obstáculo |
| resolvido | INTEGER NOT NULL | 0 para em aberto, 1 para resolvido |

## Execução

Com Flutter, Android SDK e um emulador ou aparelho Android disponíveis, extraia o ZIP e abra o terminal na pasta que contém `pubspec.yaml`. Se estiver usando o GitHub, copie o endereço em **Code → HTTPS**, execute `git clone <endereço copiado>` e entre na pasta clonada.

```sh
flutter pub get
flutter run
