# SPIRou DRS Manual for AT-4

### 1. Structure

Main .tex file is `SPIRou_DRS_USERManual.tex`, this file contains all the usepackage imports and is the file that should be built by:

`pdflatex SPURou_DRS_UserManual.tex`

** The rendered manual is stored in SPIRou_DRS_USERManual.pdf **

The individual chapters are located in "Chapters" folder

Figures should be placed in the "figures" folder.

### 2. Constants definitions

As some variables may change (i.e. HEADER keys) we can add these as functions in `/config/constants.tex` i.e.currently defined commands:

```tex
% This sets the header value for the time in calibDB
\newcommand{\constantAcqtimeKey}{ACQTIME1}

% This sets the folder name date format
\newcommand{\constantFolderDateFormat}{YYYYMMDD}

```

### 3. Custom commands

#### \definevariable
One can define variables that are changed by the user in the set-up process and then refered to later (i.e. the install path or the data path) by {VARIABLE_NAME} - highlighted in blue - this is wrapped into a custom command:
```tex
\definevariable{VARIABLE NAME}
```

#### \definekeyword
One can define keywords (that the user should change) similarly to defined variables but highlighted in red - these are wrapped into a custom command:
```tex
\definekeyword{KEYWORD}
```

#### \customdirtree
USing the `dirtree` package one can create directory trees, the shading, spacing and style is controlled by a custom command:
```tex
\customdirtree{%
.1 Outer folder.
.2 Inner folder.
.3 Inner Inner folder.
.3 \DTcomment{This is a comment}.
}
```
Note: comments can be added with `\DTcomment{ COMMENT }` and every line must end with a period `.`

### 4. Code highlighting

There are 3 custom code highlights "text", "bash" and "python" use as following:

#### text file code (i.e. to write in a text file)
```tex
\begin{lstlisting}[style=text]
<INSTRUMENT_NAME>="SPIROU"
<DIR>="/data/spirou/drs"
<INSTALL_ROOT>="@$DIR@/INTROOT"
<DATA_ROOT>="@$DIR@/data"
\end{lstlisting}
```

#### bash code (i.e. to write in command line)
```tex
\begin{lstlisting}[style=bashstyle]
  =========================================
    Environmental setup for SPIRou Pipeline
  =========================================
    Setting up environment
    Set up for {INSTRUMENT}
      - Python located at: {PYTHON_DIR}
      - GLS located at: {GSL_DIR}
      - data located at:
            {DATA_ROOT}
            {DATA_RAW_ROOT}
            {DATA_ROOT_REDUCED}
            {DATA_ROOT_CALIB}
            {DATA_ROOT_MSG}
            {DATA_ROOT_TMP}

    Done
\end{lstlisting}
```

#### python code (i.e. to write in python)
```tex
\begin{lstlisting}[style=pythonstyle]
>>> @import@ numpy
>>> @import@ matplotlib
>>> @import@ scipy
>>> @import@ pyfits
\end{lstlisting}
```
