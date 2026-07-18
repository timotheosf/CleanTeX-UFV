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

| Comando | Descrição / Uso recomendado | Exemplo de Saída (Estilo Numérico) |
| :--- | :--- | :--- |
| `\citet{chave}` | **Citação textual:** Use quando o nome do autor faz parte da sua frase. | Einstein [1] |
| `\citep{chave}` | **Citação parentética:** Use no final da frase, quando o autor não é o sujeito. | [1] |
| `\citet*{chave}` | Mesma coisa que `\citet`, mas força a impressão de **todos os autores** (ignora o *et al.*). | Einstein, Podolsky e Rosen [1] |
| `\citep*{chave}` | Mesma coisa que `\citep`, mas força a impressão de **todos os autores**. | [1] |
| `\citeauthor{chave}` | Imprime **apenas o nome** do autor. Útil para flexibilidade no texto. | Einstein |
| `\citeyear{chave}` | Imprime **apenas o ano** da publicação. | 1905 |

## 🛠️ Compilação

```bash
pdflatex main.tex
biber main
pdflatex main.tex
pdflatex main.tex
```