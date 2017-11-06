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
Using the `dirtree` package one can create directory trees, the shading, spacing and style is controlled by a custom command:
```tex
\customdirtree{%
.1 Outer folder.
.2 Inner folder.
.3 Inner Inner folder.
.3 \DTcomment{This is a comment}.
}
```
Note: comments can be added with `\DTcomment{ COMMENT }` and every line must end with a period `.`

#### \ParamList, \ParamListCode and \KWlist

Create parameter or keyword entry (all formatted the same)
```tex
\ParamList{Name}{Default Value}{Description}{Used in}{Defined in}
\ParamListCode{Name}{Code}{Description}{Used in}{Defined in}
\KWList{Name}{Variable Name}{Description}{Used in}{Defined in}
```

Where:
* `Name` is the name of the constant, variable or keyword
* `Variable Name` is the name given in the code (for keywords)
* `Default Value` is the default value currently assigned wherever it is defined
* `Code` is python code as a default value (highlighted blue)
* `Description` is a description of the variable
* `Used in` is the program/recipe the variable is used in
* `Defined in` is the place where it is defined (put all locations in, with the top overrider first to show precedence)

### 4. Code highlighting

There are 3 custom code highlights "text", "bash" and "python" use as following:
The `@` symbol can be used to highlight custom keywords (used `\@` to use the `@` symbol natively).

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

### 5. Work in progress/to do

#### General
- [ ] Needs several people to read through it

#### The sections
- Introduction
    - [ ] Needs writing
    - [x] Notes on syntax
- Pre-Install
    - [x] prerequisites
    - [ ] Check C/Fortran codes or just required?
    - [x] GSL for C codes
    - [x] Isolated version of python
    - [x] Required python modules
    - [ ] Needs trying to verify reproducibility
- Installation
    - [x] activation
    - [x] downloading + installing
    - [x] updating
    - [ ] Needs trying to verify reproducibility
- Using the DRS
    - [x] Running the code
    - [x] Working example of the code
- Data Architecture
    - [x] Installed file structure
    - [x] The install root (bin and DRS_SPIROU)
    - [x] The data root
    - [x] The calib database
- Constants and Keywords
    - Constants
        - [x] cal_dark
        - [x] cal_loc
        - [ ] cal_slit
        - [ ] cal_ff
        - [ ] cal_extract
        - [ ] cal_drift
    - Keywords
        - [x] cal_dark
        - [x] cal_loc
        - [ ] cal_slit
        - [ ] cal_ff
        - [ ] cal_extract
        - [ ] cal_drift
- The Modules
    - [x] Needs a file tree
    - [x] spirouBACK
    - [x] spirouCDB
    - [ ] spirouEXTOR
    - [x] spirouFITS
    - [x] spirouLOCOR
    - [ ] spirouRV
    - [ ] spirouVISU
- The Recipes
    - [x] cal_DARK_spirou
    - [x] cal_loc_RAW_spirou
    - [x] cal_SLIT_spirou
    - [x] cal_FF_RAW_spirou
    - [x] cal_extract_RAW_spirou
    - [x] cal_DRIFT_RAW_spirou
- Quality control
    - [x] cal_DARK_spirou
    - [x] cal_loc_RAW_spirou
    - [ ] cal_SLIT_spirou
    - [ ] cal_FF_RAW_spirou
    - [ ] cal_extract_RAW_spirou
    - [ ] cal_DRIFT_RAW_spirou