# isabelle-vscode-docker

This is an example repository for using VSCode with Isabelle2024.

## Dependencies:

- VSCode with `ms-vscode-remote.remote-containers`
- Docker

The dockerfile that I used as a basis is the suggested one `makarius/isabelle`. 
Changes from `makarius/isabelle`:

- use `debian:latest` instead of Ubuntu container because Ubunto is getting enshittified
- install cli programs to make VSCode devcontainers work nicely
- download the official linux isabelle2024 distribution rather than finding it locally
- make sure `isabelle` is on user's `PATH`
- change entrypoint to `bash`

## Usage

1. make sure you have the dependencies installed and set up (eg. make sure you can run `docker run hello-world` in your terminal)
2. if you have `devcontainer` on your path, you can just run `decontainer open /path/to/isabelle-vscode-docker/` and skip to step 5, otherwise
3. open this directory in VSCode
4. you should be prompted to reopen in devcontainer, do so (if not, you probably need to install the devcontainer extension)
5. open `List_Demo.thy`
6. open the command palette (on my machine this is Ctrl + Shift + P)
7. run the command `Isabelle: show state`, which will open a new pane in your editor with the proof state (I would like this pane to open automatically when switching to a `.thy` file, PR for this is welcome!)
8. start proving!

## Issues

If you have a problem with the repo, feel free to open an issue and (even better) submit a pull request solving it!
