# CleanTeX-UFV

Um template LaTeX modular, limpo e à prova de dores de cabeça (*idiot-proof*), configurado para atender às normas da Universidade Federal de Viçosa (UFV), mas flexível para formatação *fancy*.

A ideia é conferir liberdade para produzir um documento livre destas normas, mas sem comprometer o trabalho final, imprimindo o documento compatível com todas as exigências da UFV.

## 🚀 Quickstart

Basta abrir o template pelo link abaixo:

[![Abrir com Overleaf](https://overleaf.com/assets/images/color_image_button.png)](https://www.overleaf.com/docs?snip_uri=https://github.com/timotheosf/CleanTeX-UFV/archive/refs/heads/main.zip)

A primeira compilação pode demorar alguns segundos carregando os comandos de build e macros. É necessário preencher as *"variáveis de ambiente"* (comandos) do arquivo `_setup.tex` com nome, título e demais informações.

Caso queira usar localmente, baixe o [arquivo zip](https://github.com/timotheosf/CleanTeX-UFV/archive/refs/heads/main.zip) ou clone o repositório:
```bash
git clone https://github.com/timotheosf/CleanTeX-UFV.git
```
O template utiliza o `biber`, compilando com a seguinte receita:
```bash
pdflatex main.tex
biber main
pdflatex main.tex
pdflatex main.tex
```

## 👁️ Visualização do Template

Veja a diferença entre o formato estrito da UFV e a versão *fancy*:

<p align="center">
    <img src="https://github.com/user-attachments/assets/40f4012f-ed63-4bb3-be0e-52f1c2a555de" width="48%" />
    <img src="https://github.com/user-attachments/assets/898819ad-fadd-4198-bbf7-c3fd9e28a0bc" width="48%" />
</p>
<p align="center">
    <img src="https://github.com/user-attachments/assets/6303438a-375a-40da-90d1-2cc93afc5777" width="48%" />
    <img src="https://github.com/user-attachments/assets/866c8125-840c-4e7c-a038-f721235b49a5" width="48%" />
</p>

Faça o download dos exemplos gerados pelo template:
- [📄 Exemplo UFV](https://github.com/user-attachments/files/30202623/example_ufv_headers.pdf)
- [📄 Exemplo fancy](https://github.com/user-attachments/files/30202624/example_fancy_headers.pdf)

## 📝 As normas da UFV suportadas automaticamente

O template tem a opção `\UseUFVNorms{True}` para gerar um documento compatível com todas as normas de entrega de trabalho da UFV, segundo a [Normalização de Trabalhos Acadêmicos (2025)](https://www.bbt.ufv.br/wp-content/uploads/2025/02/Normalizacao-de-trabalhos-academicos-2025-UFV.pdf) e o [Manual de Normas e Procedimentos para Submissão de Dissertações e Teses (2025)](https://ppg.ufv.br/wp-content/uploads/2025/08/Manual-de-entrega-de-dissertacoes-e-teses.pdf).

Formatação:
- Fonte Arial ou Times New Roman – tamanho 12
- Papel: A4 (21 cm x 29,7 cm)
- Margens:
    - Superior e esquerda: 3 cm
    - Inferior e direita: 2 cm
- Espaçamento: 1,5
- Numeração: canto superior direito, iniciando no corpo do trabalho

Estrutura pré-textual:
- Capa e Folha de Rosto
- Ficha de Aprovação (gerada automaticamente com espaço para assinaturas)
- Dedicatória (opcional)
- Agradecimentos (obrigatório)
- Epígrafe (opcional)
- Resumo em língua vernácula
- Resumo em língua estrangeira
- Listas de elementos (opcional)
- Sumário

Bibliografia:
- ABNT com citação autor-data ou numérica (ambas permitidas)

**Observação:** após aprovação da dissertação/tese, o AcademicoPG gera as folhas pré-textuais, de modo que é necessário usar `\PreTextual{False}` e `\SetStartingPage{ }` com o número de folhas geradas para entregar o documento sem os elementos pré-textuais e com a contagem correta.

## 🌲 Árvore de Diretórios

O código é estruturado de forma modular. A lógica tipográfica fica blindada e o usuário precisa interagir apenas com arquivos de configuração e texto.

```Text
CleanTeX-UFV/
├── _preamble/
│   ├── config.tex              # Lógica do template (variáveis e controle de fluxo).
│   ├── packages.tex            # Pacotes (math, tikz, etc).
│   ├── standard_notation.tex   # Macros para padronizar a notação matemática.
│   ├── format2ufv.tex          # Driver: formatação estrita ABNT/UFV.
│   └── format2publish.tex      # Driver: formatação fancy, estética internacional.
├── _title/
│   ├── titlepage.tex           # Geração automática da capa e folha de rosto.
│   └── generalmacros.tex       # Motores de construção das páginas pré-textuais e sumário.
├── _bibliography/
│   ├── bib.tex                 # Chamada e aparência do BibLaTeX.
│   └── references.bib          # Arquivo .bib: dados das referências.
│
├── _setup.tex                  # Arquivo de configuração global (Metadados, toggles, etc).
├── main.tex                    # Ponto de entrada do documento. Totalmente limpo.
├── lero_lero.tex               # Arquivo de texto de exemplo.
└── chapters/                   # Pasta sugerida para os capítulos do trabalho.
```

## :shipit: Manual de Uso

A configuração do template é feita preenchendo os comandos no arquivo `_setup.tex`, mantendo o `main.tex` limpo, servindo apenas para chamar os capítulos e textos.

### 1. Opções de Compilação (Toggles no `_setup.tex`)
```latex
\UseUFVNorms{True}   % True para compilar nas normas UFV. False para estética internacional.
\UseHeaders{True}    % True para habilitar cabeçalho nas páginas.
\NumericFormat{True} % True para sistema de chamada numérico. False para Autor-Data.
\PreTextual{True}    % True gera o PDF com Capa, Resumo, etc. False remove o pré-texto (ideal para a submissão final do Mestrado/Doutorado no sistema da UFV).

% --> SUBMISSÃO NA UFV (AcademicoPG) <--
% Se usar \PreTextual{False} para enviar a versão final, insira aqui a página
% em que a sua Introdução deve começar (ex: 11, 12...). 
% Se deixar vazio, o LaTeX faz a contagem automaticamente.
\SetStartingPage{}
```

### 2. Dados do Documento
```latex
\DocTitle{Título do documento}           
\DocAuthor{Nome do orientado}            
\DocAdvisor{Nome do orientador}          
\DocCoAdvisor{João Silva, Maria Souza}   % Para múltiplos coorientadores, basta separar por VÍRGULA
\DocModality{Dissertação}                % Monografia, Dissertação ou Tese
\DocDegree{Mestre}                       % Mestre ou Doutor (deixe em branco para Monografia)
\DocDate{Junho/2026}                     
\DocProgram{Física}                      % Nome do departamento ou programa
\DocCenter{Centro de Ciências Exatas}    
\DocPresentation{Dissertação apresentada à Universidade Federal de Viçosa como parte das exigências para obtenção do título de Mestre em Física.}
```

### 3. Elementos Pré-textuais (Opcionais)
Se não quiser usar algum destes elementos, basta deixar as chaves vazias `{}`. O template reorganiza as páginas e o sumário sozinho.

```latex
\DocResumo{Insira o texto do resumo em português aqui em parágrafo único...}
\DocPalavrasChave{Palavra 1; Palavra 2; Palavra 3}

\DocAbstract{Insert the english abstract here...}
\DocKeywords{Keyword 1; Keyword 2; Keyword 3}

\DocDedication{Insira aqui a sua dedicatória...}
\DocAcknowledgments{Insira o texto dos seus agradecimentos aqui...}

\DocEpigraph{Texto da epígrafe com \\ para quebrar linhas}{Autor da epígrafe}

% --> BANCA EXAMINADORA E FOLHA DE APROVAÇÃO <--
% Separe os membros por VÍRGULA.
% Dentro de cada membro, separe os dados por BARRA (/) no formato: Nome / Instituição / Papel
\DocBoard{
    Prof. Dr. Fulano / UFV / Orientador,
    Profa. Dra. Ciclana / PUC / Coorientadora,
    Prof. Me. Beltrano / USP / ,
    Profa. Dra. Maria / UNB /
}
```

### 4. Fazendo citações

O template usa o padrão `natbib` em conjunto com o Biber/BibLaTeX. Consulte a tabela abaixo para saber qual comando usar no seu texto:

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