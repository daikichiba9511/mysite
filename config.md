<!--
Add here global page variables to use throughout your
website.
The website_* must be defined for the RSS to work
-->
@def website_title = "A memo of No Name."
@def website_descr = "website using Franklin"
@def website_url   = "https://daikichiba9511.github.io/mysite/"

@def author = "daiki chiba"
@def prepath = "mysite"

@def mintoclevel = 2

<!--
Add here files or directories that should be ignored by Franklin, otherwise
these files might be copied and, if markdown, processed by Franklin which
you might not want. Indicate directories by ending the name with a `/`.
-->
@def ignore = ["node_modules/", "franklin", "franklin.pub"]

<!--
Add here global latex commands to use throughout your
pages. It can be math commands but does not need to be.
For instance:
* \newcommand{\phrase}{This is a long phrase to copy.}
-->
\newcommand{\R}{\mathbb R}
\newcommand{\scal}[1]{\langle #1 \rangle}

<!-- 定義　@@~ でスタイル指定してる。設定はfranklin.css内で-->
\newcommand{\definition}[2]{
  @@definition
  **Def** : ( _!#1_ )
  \
  \
  #2
  @@
}


<!-- 定理　-->
\newcommand{\theorem}[2]{
  @@theorem
  **Thm**: ( _!#1_ )
  \
  \
  #2
  @@
}

<!-- note　-->
\newcommand{\note}[2]{
  @@NOTE
  **＊NOTE** :
  @@
  @@note
  \
  #2
  @@
}