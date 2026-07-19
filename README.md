# CleanTeX-UFV

Um template LaTeX modular, limpo e à prova de dores de cabeça, configurado para atender às normas da Universidade Federal de Viçosa (UFV), mas altamente flexível para formatação estética internacional.

## 🚀 Como Usar (Quickstart)

Toda a configuração do seu trabalho é feita preenchendo os comandos no arquivo `main.tex`. O código do documento fica completamente limpo.

### 1. Opções de Compilação (Toggles)
```latex
\UseUFVNorms{True}   % True para compilar nas normas UFV. False para estética internacional.
\UseHeaders{True}    % True para habilitar cabeçalho nas páginas.
\NumericFormat{True} % True para sistema de chamada numérico. False para Autor-Data.
\PreTextual{True}    % True gera o PDF com Capa, Resumo, etc. False remove o pré-texto (ideal para a submissão final do Mestrado/Doutorado no sistema da UFV).
```

### 2. Dados do Documento
```latex
\ThesisTitle{Título do documento}           
\ThesisAuthor{Nome do orientado}            
\ThesisAdvisor{Nome do orientador}          
\ThesisCoAdvisor{Coorientador}              % Para mais de um coorientador, separe usando "\\"
\ThesisModality{Dissertação}                % Monografia, Dissertação ou Tese
\ThesisDegree{Mestre}                       % Mestre ou Doutor (deixe em branco para Monografia)
\ThesisDate{Junho/2026}                     
\ThesisProgram{Física}                      % Nome do departamento ou programa
\ThesisCenter{Centro de Ciências Exatas}    
\ReportCourse{Disciplina da Monografia}     % Ex: Monografia II (FIS 497)
```

### 3. Elementos Pré-textuais (Opcionais)
Se não quiser usar algum destes elementos, basta deixar as chaves vazias `{}`.

```latex
\DocResumo{Insira o texto do resumo em português aqui em parágrafo único...}
\DocPalavrasChave{Palavra 1. Palavra 2. Palavra 3}
\DocAbstract{Insert the english abstract here...}
\DocKeywords{Keyword 1. Keyword 2. Keyword 3}
\DocAcknowledgments{Insira o texto dos seus agradecimentos aqui...}
\DocEpigraph{Texto da epígrafe}{Autor da epígrafe}
```

### 4. Fazendo citações

O template usa o padrão `natbib` para as citações. Consulte a tabela abaixo para saber qual comando usar no seu texto:

| Comando | Numérica | Autor-ano | ABNT Numérica | ABNT |
| :--- | :--- | :--- | :--- | :--- |
| `\citet{chave}` | Scrutinizer et al. [1] | Scrutinizer et al. (1979) | Scrutinizer et al. (2) | Scrutinizer et al. (1979) |
| `\citep{chave}` | [1] | (Scrutinizer et al., 1979) | (2) | (SCRUTINIZER et al., 1979) |
| `\citeauthor{chave}` | Scrutinizer et al. | Scrutinizer et al. | Scrutinizer et al. | (SCRUTINIZER et al.) |
| `\citeyear{chave}` | 1979 | 1979 | 1979 | (1979) |
| `\citet*{chave}` | Scrutinizer, Lucille e Joe [1] | Scrutinizer, Lucille e Joe (1979) | Scrutinizer; Lucille; Joe (2) | Scrutinizer, Lucille e Joe (1979) |
| `\citep*{chave}` | [1] | (Scrutinizer, Lucille e Joe, 1979) | (2) | (SCRUTINIZER; LUCILLE; JOE, 1979) |
| `\citeauthor*{chave}` | Scrutinizer, Lucille e Joe | Scrutinizer, Lucille e Joe | Scrutinizer; Lucille; Joe | SCRUTINIZER et al.* |
| `\citeyear*{chave}` | 1979 | 1979 | 1979 | 1979 |

## 🌲 Árvore de Diretórios

O código é dividido em arquivos que cuidam da aparência geral do documento, desde a formatação (em acordo com a ABNT ou em padrão fancy), as páginas de título e pré-textuais e a bibibliografia (biber).
```Text
CleanTeX-UFV/
├── _preamble/
│   ├── config.tex              # Lógica do template (variáveis e controle de fluxo).
│   ├── packages.tex            # Pacotes (math, tikz, etc).
│   ├── standard_notation.tex   # Macros para padronizar a notação matemática (diff,...).
│   ├── format2ufv.tex          # Driver: formatação estrita ABNT/UFV.
│   └── format2publish.tex      # Driver: formatação fancy, estética internacional.
├── _title/
│   ├── titlepage.tex           # Geração automática da capa e folha de rosto.
│   └── generalmacros.tex       # Macros para construção das páginas pré-textuais.
├── _bibliography/
│   ├── bib.tex                 # Chamada e aparência do BibLaTeX.
│   └── references.bib          # Arquivo .bib: dados das referências.
│
├── main.tex                    # Arquivo principal, com inserção de dados e \input{} do texto.
└── chapters/                   # Pasta contendo os capítulos do trabalho.
```

## 🛠️ Compilação

Para compilar o documento com a bibliografia corretamente atualizada, execute a seguinte sequência de comandos no terminal:

```bash
pdflatex main.tex
biber main
pdflatex main.tex
pdflatex main.tex
```