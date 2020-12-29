## QUCS-PKG - Quite Universal Circuit Simulator Packaging

Qucs is an integrated circuit simulator which means you are able to setup a circuit with a graphical user interface (GUI) and simulate the large-signal, small-signal and noise behaviour of the circuit. After that simulation has finished you can view the simulation results on a presentation page or window.

## Resources
  - Website: <http://qucs.sourceforge.net/>
  - Main repository: <http://sourceforge.net/p/qucs/git/>
  - Mirror repository: <https://github.com/Qucs/qucs>
  - Mailing lists: <http://sourceforge.net/p/qucs/mailman/>
  - Forum: <http://sourceforge.net/p/qucs/discussion/>
  - Bug trackers:
    - <http://sourceforge.net/p/qucs/_list/tickets>
    - <https://github.com/Qucs/qucs/issues>
  - Source code documentation:
    - <http://qucs.github.io/qucs-doxygen/qucs/index.html>
    - <http://qucs.github.io/qucs-doxygen/qucs-core/index.html>
  - Downloads: <http://sourceforge.net/projects/qucs/files/>
  - Translation platform: <https://www.transifex.com/qucs/public/>

## Currently Supported Platforms
  - GNU/Linux
  - Darwin/OS X
  - FreeBSD
  - Windows

## Source Download and Compilation

TODO: update these sections.

The source code is available as distribution tarballs and clones of the Git repository.

The distributed tarballs can be downloaded from: <http://sourceforge.net/projects/qucs/files/qucs/>.
Compilation and install from tarball is expected to work as follows (see dependencies below):

    tar xvfz qucs[version].tar.gz
    cd qucs[version]
    ./configure
    make install

All versions of the code may be accessed by cloning one of the Git repositories (the first is updated more frequently):

    git clone git://github.com/Qucs/qucs-pkg.git
    git clone git://git.code.sf.net/p/qucs/git @ not yet

Packages such as, qucsator (simulator) and qucs-test (test suite) are provided
as Git submodules. To retrieve the submodules you may

   * clone submodules recursively:
     * `git clone --recursive [repository]`
   * or after cloning, do:
     * `git submodule init`
     * `git submodule update`

After an initial clone operation, the local copy is set by the default as the `master` branch.
Branches can be listed and selected with the following commands:

    git branch
    git checkout [branch name]

Compilation and installation depends on the operation system. See below for an example.

## Contributing to QUCS

Some general contribution guidelines can be found on our Wiki <https://github.com/Qucs/qucs/wiki/Contribution>.

## More compile instructions on GNU/Linux

(This section may be outdated. Find up to date documentation in */README.md)

For the GUI tools and simulation engine the following packages are required
when building from git (package names on non-Debian may vary).

	 adms automake build-essential libqt4-dev libqt4-qt3support libtool libtool-bin
    gperf flex bison pkg-config

To build the manuals and user documentation further dependencies are needed.
Please check the `qucs-doc/README` file.  See below the `--disable-doc` to skip
building the documentation from source.  To build the documentation from source
the following packages are needed (package names on non-Debian may vary).

	 doxygen latex2html octave octave-epstk ps2eps pgf python-tk
    texlive-publishers texlive-science texlive texlive-font-utils
    texlive-math-extra transfig gnuplot graphviz

Bootstrap, build, install everything (after cloning):

    $ cd qucs
    $ ./bootstrap
    $ ./configure
    $ make
    $ sudo make install # optional

Compile Qucs GUI tools only:

    $ cd qucs
    $ [./bootstrap] #if not executed in the top level
    $ ./configure
    $ make

Compile qucs-core tools only:

    $ cd qucs-core
    $ [./bootstrap] #if not executed in the top level
    $ ./configure
    $ make

Compile qucs-doc documentation only:

    $ cd qucs-doc
    $ [./bootstrap] #if not executed in the top level
    $ ./configure
    $ make

Tests may be executed at the top level with:

    $ make check

Note:

 * Qucs will be installed to `/usr/local` by default. You may override this
   by passing `--prefix=[some location]` to the `./configure` script.

 * ADMS should be installed e.g. from a released tarball (>= 2.3.0).
   To use a different `admsXml` pass the option `--with-admsxml=[path/to/]anotherAdmsXml`
   to `./configure`.

 * The LaTex documentation compilation in qucs-doc can be skipped passing
   `--disable-doc` to the top level `configure` script.

 * Consider INSTALL and the output of `./configure --help` for more and
   definitive build options.

## License

Qucs is under GNU General Public License, version 2.0 or 3.0 or any later
version. See COPYING file.
