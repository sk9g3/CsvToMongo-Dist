# 🏴‍☠️ Csv To Mongo

<div align="center">
  <img src="https://github.com/user-attachments/assets/b82abb69-6d3c-4321-a304-5e87c82e5efe" alt="Logo" width="120">
  <br>
  <br>

[![Version](https://img.shields.io/github/v/release/sk9g3/CsvToMongo-Dist?include_prereleases&label=Versão&style=for-the-badge&color=orange)](https://github.com/sk9g3/CsvToMongo-Dist/releases)
[![Downloads](https://img.shields.io/github/downloads/sk9g3/CsvToMongo-Dist/total?label=Downloads&style=for-the-badge&color=success)](https://github.com/sk9g3/CsvToMongo-Dist/releases)
[![Platform](https://img.shields.io/badge/Plataforma-macOS%20%7C%20Windows%20%7C%20Linux-important?style=for-the-badge)](https://github.com/sk9g3/CsvToMongo-Dist/releases)

  <br>
  
  **A ferramenta definitiva para converter CSV em scripts MongoDB sem dor de cabeça.**
  <br>
  Rapidez nativa. Interface moderna. Multiplataforma.
</div>

---

## 🚀 O que é?

O **Csv To Mongo** é uma aplicação desktop feita para desenvolvedores que precisam transformar `.csv` em scripts de atualização (`update`) para MongoDB instantaneamente.

Com o **Csv To Mongo**, você resolve tudo visualmente, mapeando colunas e gerando arquivos `.js` prontos para rodar no Mongo Shell ou Compass.

## 📸 Screenshots

<div align="center">
  <img src="https://github.com/user-attachments/assets/a5d014d5-9b86-4ace-817b-12aadb157acb" alt="Screenshot do App" width="100%">
</div>

---

## 📖 Como Usar

O processo é simples e dividido em 3 etapas:

### 1. Seleção de Arquivos 📁

- **Arquivo CSV:** Clique no ícone de arquivo e selecione sua planilha. O app lerá os cabeçalhos automaticamente.
- **Pasta Destino:** Escolha onde o script final será salvo.
- **Nome Script:** Defina o nome do arquivo gerado (ex: `update_2024.js`).

### 2. Configurações do Mongo ⚙️

- **Nome da Coleção:** O nome da collection no banco (ex: `clientes`, `produtos`).
- **Tipo de Operação:**
  - `UpdateOne`: Atualiza apenas o primeiro documento encontrado.
  - `UpdateMany`: Atualiza todos os documentos que corresponderem ao filtro.
  - 🚧 **Em Breve:** A opção `InsertOne` (para criar novos registros).\*
- **Filtro (Where):** Define o operador lógico (`AND` / `OR`) usado caso você selecione múltiplas chaves de busca.

### 3. Mapeamento de Colunas (O Pulo do Gato) 🗺️

Aqui você define a "inteligência" do script. Para cada coluna do CSV, você pode configurar:

| Opção            | Descrição                                                                                                                                                                           |
| :--------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nome Mongo**   | Nome do campo no banco de dados. Ex: CSV é `cd_cli`, no Mongo vira `codigo_cliente`.                                                                                                |
| **Tipo**         | Formato do dado no script. Opções: `Text`, `Number`, `Boolean`, `Guid` (UUID), `ISODate`.                                                                                           |
| **Chave (Val)**  | **Filtro por Valor:** Usa o valor da linha do CSV para buscar o registro. <br>Ex: `WHERE codigo = '123'`.                                                                           |
| **Chave (Null)** | **Filtro por Nulo:** Busca registros onde este campo está vazio/nulo no banco, ignorando o valor do CSV. <br>Ex: `WHERE data_cancelamento IS NULL`.                                 |
| **Ignorar**      | **Não Atualizar:** O campo **não** será incluído no comando `$set` (update). <br>Use isso em campos que servem apenas como Chave (Filtro) mas que não devem ter seu valor alterado. |

#### 💡 Exemplos de Combinação

**Cenário 1: Atualizar dados buscando pelo ID**

- Coluna `ID`: Marque `Chave (Val)` + `Ignorar`.
  - _Explicação:_ O app usa o ID para encontrar o registro, mas **não** altera o ID (porque está ignorado no `$set`).
- Outras Colunas: Deixe desmarcado.
  - _Explicação:_ Serão atualizadas normalmente.

**Cenário 2: Preencher campo apenas se ele for nulo**

- Coluna `Status`: Marque `Chave (Null)` + `Ignorar`.
  - _Explicação:_ O script buscará apenas documentos onde o Status é `null`.
- Coluna `NovoStatus`: Deixe desmarcado.
  - _Explicação:_ O script preencherá o novo status apenas nesses registros encontrados.

---

## 📥 Download e Instalação

Baixe a versão mais recente na nossa aba de **[Releases](https://github.com/sk9g3/CsvToMongo-Dist/releases/latest)**.

| SO             | Arquivo   | Descrição                                |
| :------------- | :-------- | :--------------------------------------- |
| **🍎 macOS**   | `.zip`    | Versão portátil (Extrair e Rodar).       |
| **🪟 Windows** | `.zip`    | Extraia e execute o `CsvToMongoGui.exe`. |
| **🐧 Linux**   | `.tar.xz` | Extraia e execute o binário.             |

### ⚠️ Notas Importantes para usuários de Mac

Como este é um software Open Source gratuito, o sistema pode tentar bloquear a abertura na primeira vez.

Ao extrair o zip, o Mac pode dizer que o _"Arquivo está danificado"_. Isso é um falso-positivo do sistema de quarentena. Para corrigir, abra o Terminal na pasta do app e rode:

```bash
xattr -cr "Csv To Mongo.app"
```

---

## 🛠 Tecnologias

- [C# / .NET 9](https://dotnet.microsoft.com/)
- [Avalonia UI](https://avaloniaui.net/) (Cross-Platform XAML)

---

Caso encontre bugs ou tenha sugestões, sinta-se à vontade para abrir uma [Issue](https://github.com/sk9g3/CsvToMongo-Dist/issues).
