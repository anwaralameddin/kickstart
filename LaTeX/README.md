# $\LaTeX$

A $\LaTeX$ document may need to be compiled multiple times to resolve cross-references, bibliographies, and other dependencies. This process can be automated using <code>latexmk</code> and <code>make</code>.

## Installation

### Linux

#### TexLive

On Debian-based systems, you could install <code>latexmk</code> using <code>apt</code>:

```bash
sudo apt-get update
sudo apt-get install -y latexmk make
```

<code>latexmk</code> is not available as a package in all distributions and may be installed using <code>tlmgr</code> or built from the source code, as described below. Below, you should replace <code>apt</code> with your package manager if you use a different Linux distribution. Also, some packages may be named slightly differently in other distributions.

To install <code>latexmk</code> using <code>tlmgr</code>, you could use the following commands:

```bash
# Install needed dependencies
sudo apt-get update
sudo apt-get install -y texlive make
# Install `latexmk` using `tlmgr`
tlmgr init-usertree
export TEXMFHOME=~/texmf
tlmgr install latexmk
```

<!-- ```bash
sudo tlmgr install latexmk
# or
sudo tlmgr install latexmk --repository http://mirror.ctan.org/systems/texlive/tlnet
``` -->

FIXME: So far, using <code>tlmgr</code> has proven to be a pain; it doesn't seem to work as expected. Consult the guides [tlmgr - TeX Live package manager](https://tug.org/texlive/tlmgr.html) and [TeX Live - Quick install for Unix](https://www.tug.org/texlive/quickinstall.html) for further instructions.

To build <code>latexmk</code> from the source code, you could use the following commands:

```bash
# Install needed dependencies
sudo apt-get update
sudo apt-get install -y texlive make wget unzip
# Download and install `latexmk`
wget https://mirrors.ctan.org/support/latexmk.zip
unzip latexmk.zip
cd latexmk
sudo install -Dm 755 latexmk.pl /usr/bin/latexmk
sudo install -Dm 644 latexmk.1 /usr/share/man/man1/
sudo install -Dm 644 latexmk.pdf latexmk.txt COPYING CHANGES /usr/share/doc/latexmk/
```

### MacOS

#### MacTeX

1. Install a [MacTeX](https://www.tug.org/mactex/) distribution:

You could also install the full <code>MacTeX</code> distribution and <code>make</code> using [Homebrew](https://brew.sh/):

```bash
brew install --cask mactex
brew install make
```

However, it is quite large, and you could instead use the smaller [BasicTeX](https://www.tug.org/mactex/morepackages.html) distribution and install additional packages as needed.

```bash
brew install --cask basictex
brew install make
```

2. Install <code>latexmk</code> using <code>tlmgr</code> or build it from the source code, as described in the [Linux](#linux) section.

FIXME: This doesn't seem to work on GitHub Actions as <code>tlmgr</code> does not seem to be available when using <code>BasicTex</code>. Consult the guide [TeX Live - Quick install for Unix](https://www.tug.org/texlive/quickinstall.html) for further instructions.

### Windows

#### MiKTeX

1. Install [MiKTeX](https://miktex.org/), [Strawberry Perl](http://strawberryperl.com/), and <code>GnuWin32</code>'s [make](http://gnuwin32.sourceforge.net/packages/make.htm) using <code>winget</code>:

```powershell
winget install MiKTeX.MiKTeX StrawberryPerl.StrawberryPerl GnuWin32.Make
```

2. You could install <code>latexmk</code> using MiKTeX Package Manager <code>mpm</code>:

Running the command <code>latexmk</code> opens MiKTeX Package Manager, prompting the installation of <code>latexmk</code>. If a non-interactive installation is needed, you could use the following command:

```powershell
mpm --verbose --package-level=complete --upgrade
```

However, this will install all packages, which is overkill, and you may instead consider building <code>latexmk</code> from the source code, as described in the [Linux](#linux) section.

FIXME: Specify the Windows installation path for <code>latexmk</code> when building it from the source code.

3. Add <code>GnuWin32</code>'s and <code>Strawberry Perl</code>'s binaries to the <code>PATH</code>:

```powershell
setx /M PATH "%PATH%;C:\Program Files (x86)\GnuWin32\bin\"
setx /M PATH "%PATH%;C:\Strawberry\perl\bin"
```

#### TexLive

1. Install [Strawberry Perl](http://strawberryperl.com/) and <code>GnuWin32</code>'s [make](http://gnuwin32.sourceforge.net/packages/make.htm) using <code>winget</code>:

```powershell
winget install StrawberryPerl.StrawberryPerl GnuWin32.Make
```

and add their binaries to the <code>PATH</code>:

```powershell
setx /M PATH "%PATH%;C:\Program Files (x86)\GnuWin32\bin\"
setx /M PATH "%PATH%;C:\Strawberry\perl\bin"
```

2. Install <code>TexLive</code> using [Chocolatey](https://chocolatey.org/):

```powershell
choco install texlive
```

3. Install <code>latexmk</code> either using <code>tlmgr</code>, as described in the [Linux](#linux) section, or by building it from the source code.

<!-- TODO: Add instructions for building <code>latexmk</code> from the source code. -->


## Project setup

Copy the [template](template) files to the $\LaTeX$ project directory, especially the [Makefile](template/Makefile). Alternatively, you could initialise a new $\LaTeX$ project using <code>kickstart</code>:

```bash
kickstart latex <project-name>
```

## Building

Run <code>make</code> in the project directory to build the $\LaTeX$ document.
