---
title: Latex tricks
--- 

*TeX tricks and advises from different sources*  
From [CS Theory toolkit](https://www.youtube.com/watch?v=YFUIPg8P2sY&list=PLm3J0oaFux3ZYpFLwwrlv_EHH9wtH6pnX&index=2){:target="_blank"}

- To use text within `"quotes"`, use left and right ticks for opening and closing the quote ``` ``quote´´ ```

- Instead of `$ log(1+x) $`, use `$ \log(1+x) $`

- Instead of `$ <u,v> $`, use `$ \langle u, v \rangle $`

- Use `~` for a non-breaking space. Ex.  
`Lemma \ref{lem:big} is due to Blum \cite{Blu99}` can be update to  
`Lemma~\ref{lem:big} is due to Blum~\cite{Blu99}`

- When writing proof block,  
`\begin{proof}... \end{proof}`, use `\qedhere` such that  
`\begin{proof}... \[... \qedhere \] \end{proof}`

- Instead of `\begin{eqnarray}`, use `\begin{align}`

- Always include `\usepackage{float}` for activating the placement specifiers for figures. Ex. `\begin{figure}[H]...`