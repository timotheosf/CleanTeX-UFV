# CleanTeX-UFV


## 🌲 Árvore de Diretórios

```Text
CleanTeX-UFV/
├── _preamble/
│   ├── config.tex              # Lógica do template (variáveis e controle de fluxo).
│   ├── packages.tex            # Pacotes (math, tikz, etc).
│   ├── standard_notation.tex   # Macros para padronizar a notação matemática (diff,...).
│   ├── format2ufv.tex          # Driver: formatação estrita ABNT/UFV.
│   └── format2publish.tex      # Driver: formatação fancy, estética internacional.
├── _title/
│   └── titlepage.tex           # Geração automática da capa.
├── _bibliography/
│   ├── bib.tex                 # Chamada e aparência do BibLaTeX.
│   └── references.bib          # Arquivo .bib: dados das referências.
│
├── main.tex                    # Arquivo principal, com inserção de dados e \input{} do texto.
└── chapters/                   # Pasta 
```

## 🚀 Como Usar (Quickstart)

```latex
\ThesisTitle{Título do documento}           % Título do trabalho
\ThesisAuthor{Nome do orientado}            % Nome do orientado
\ThesisAdvisor{Nome do orientador}          % Nome do orientador
\ThesisCoAdvisor{Coorienador}               % Para mais de um coorientador, separar nomes usando "\\"
\ThesisModality{Dissertação}                % Monografia, Dissertação ou Tese
\ThesisDegree{Mestre}                       % ou Doutor; para Monografia, pode deixar em branco
\ThesisDate{Junho/2026}                     % Data
\ThesisProgram{Física}                      % Nome do departamento
\ThesisCenter{Centro de Ciências Exatas}    % Nome do centro
\ReportCourse{Disciplina da Monografia}     % Nome da disciplina de monografia, e.g. Monografia II (FIS 497)
```

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

## 🛠️ Compilação

```bash
pdflatex main.tex
biber main
pdflatex main.tex
pdflatex main.tex
```