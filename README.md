# Consistent scientific writing style checklist

## Revision

- Changes in relation to previous version in blue (```\textcolor{blue}{}```)
    - May also define ```\newcommand{\rev}[1]{{\leavevmode\color{blue}#1}}``` and use ```\rev{}```
- Set status to all comments in the pdf of the revision

## Style

### Writing

- Simple enumerations with oxford comma before “and”
  - e.g. *I need to buy sugar, flour, and chocolate)*
- Long text enumerations with nonbreaking space “~”, separated by semicolon, and enumerated with (i), (ii)…
  - e.g. *I need to buy (i)~sugar; (ii)~flour; and (iii)~chocolate*
- Units should be typeset in $\mathrm{}$ style
  - e.g. ```$\omega = 7.29\times10^{-5}\,\mathrm{rad/s}$```
- Acronims should be only introduced once
   - e.g. "this is a challenge idetified by the United Nations (UN)"
   - 

### Variables

- Scalar constant: roman uppercase (e.g. ```$T\in \mathbb{R}$ is the sampling time```)
- Scalar functions: roman lowercase (e.g. ```$r(h)$ is the density as a function of altitude```)
- Matrices: bold roman uppercase (e.g. ```$\mathbf{B}$ is the incidence matrix```)
- Vectors: bold roman lower case (e.g. ```$\mathbf{v}$ is the velocity vector in the ECI frame```)
- Subscripts/Superscript:
    - if the subscript is a variable or index: normal (```$\mathbf{A}_{ij}$```)
    - if the subscript is text: text mode (```$\mathbf{v}_\mathrm{ECI}$```)

### Equations

- Only equations which are referenced are numbered  (```\begin{equation*}``` wo/ numbering)
- Equations are part of the text and have punctation, e.g.

```latex
the travel time on arc $(i,j)\in \mathcal{A}$ is given by 
\begin{equation*}
t(i,j) = t_0(i,j)(1+\alpha(f(i,j)/c_{ij})^\beta),
\end{equation*}
where $t_0(i,j)$ is the free flow travel time, $\alpha$ is (...)
```

- All symbols, variables and operators in each equation must be already defined before or immediately after the first appearance

### Tables

- All table captions are above the table
- All quantities have explicit units
- Table template:
``` latex
\begin{table}
	\centering
	\caption{This is a caption.}
	\label{tab:potential}
	%\renewcommand{\arraystretch}{1.2} % Useful depending on the template
	\begin{tabular}{ccc}
		\hline
		& Mean ($\mathrm{s}$) & Std. deviation ($\mathrm{s}$)  \\
		\hline
		Method 1 & 1.23 &  0.554 \\
		Method 2 & 1.45 &  0.729 \\
 		\hline
	\end{tabular}
\end{table}
```


### Figures

- All figure captions are below the figure
- Image files are in vector format (.eps, .pdf, .svg) whenever possible
- All plotted quantities have explicit units

#### Matlab plots

```matlab
figure('Position',4*[0 0 192 144]); % Nice aspect ratio for double column
hold on;
grid on;
box on;
set(gca,'FontSize',20);
set(gca,'TickLabelInterpreter','latex') % Latex style axis
%%%%
% Plot things here
%%%%
legend({'Temperature of agent $\nu_1$'},...
	'Location','best','Interpreter','latex');
ylabel('$T (\mathrm{K})$','Interpreter','latex');
xlabel('$t (\mathrm{s})$','Interpreter','latex');
hold off;
% Save figure to .fig and .eps formats
savefig('./fig/filename.fig');
set(gcf,'renderer','Painters');
saveas(gca,'./fig/filename.eps','epsc');
```

### References
- Bibtex references must be double checked and properly formatted:
    - Journal papers (@article) fields: author, title, journal, year, volume, number, pages, doi (no url!)
    - Conference papers (@inproceedings) fields: author, title, booktitle, year, pages, doi (no url!)
    - Do NOT just blindly copy and paste bibtex from Google Scholar :)
- References to tables, figures, algorithms with first letter capitalized (Table, Figure, Fig., Algorithm), non breaking space, and \ref{} command
    - e.g. ```Table~\ref{tab:egtable}```, ```Figure~\ref{fig:egfigure}```, ```Fig.~\ref{fig:egfigure}```, ```Algorithm~\ref{alg:egfigure}```
- References to books or specific results in papers should be specified if it helps the reader
    - e.g. ```\cite[Chapter~5]{book}```, ```\cite[Theorem~2]{paper}```
- References to equations with ```\eqref{}```
    - e.g. ```substituting \eqref{eq:covariance} in \eqref{eq:update} yields```.
    - Do NOT: ```substituting Equation \eqref{eq:covariance} (...)```
 
