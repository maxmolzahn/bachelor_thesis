<!--
  Zentrale Variablen:
  Workaround bzw. Rückgriff auf LaTex-Befehle, um zentrale Werte immer wieder verwenden zu können.
-->
\newcommand{\titel}{Innovative Lösungsstrategien für die Personenidentifikation im Fahrzeug: Evaluierung, Auswahl und prototypische Umsetzung mit vorhandener Fahrzeugtechnologie.}
\newcommand{\datum}{15.03.2024}

\newcommand{\aVorname}{Maximilian}
\newcommand{\aNachname}{Molzahn}
\newcommand{\aGeburtsdatum}{03.07.2000}
\newcommand{\aInstitution}{Hochschule München}
\newcommand{\aStudiengruppe}{IF7}
\newcommand{\aSemester}{WS 2023/24}

\newcommand{\aName}{\aVorname\space \aNachname}

\newcommand{\pTitle}{Prof. Dr.}
\newcommand{\pVorname}{Lars}
\newcommand{\pNachname}{Wischhof}
\newcommand{\pInstitution}{Hochschule München}

\newcommand{\bTitle}{Dr.}
\newcommand{\bVorname}{Thomas}
\newcommand{\bNachname}{Kupka}
\newcommand{\bInstitution}{BMW Group}

\title{\titel}
\author{\aName}

<!--
  Titelseite
-->

\begin{titlepage}
    \begin{center}

        \includegraphics[width=0.8\textwidth]{style/header_logo2.png}

        \vspace*{0.3cm}

        \LARGE
        \titel

        \vspace{0.5cm}

        \Large
        \aName

        \vspace{0.3cm}

        \normalsize
        Bachelorarbeit Informatik

        \vfill

        \normalsize
        Prüfer:\\
        \pTitle\space \pVorname\space \pNachname,\space \pInstitution

        \vspace{0.1cm}

        % Firmenlogo
        % \includegraphics[width=0.4\textwidth]{style/bmw-group_logo.png}

        \normalsize
        Betreuer:\\
        \bTitle\space \bVorname\space \bNachname,\space \bInstitution

        % Abgabedatum
        \datum

    \end{center}
\end{titlepage}
