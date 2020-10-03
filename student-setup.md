Student Setup
-------------
Normally, repositories house code that all developers use as a base to build their changes off of.
When other developers make changes, all developers pull them in and continue their work on top.
In our case, however, each student will have a separate fork of this repository in order to complete
their assignments. Furthermore, each student must keep their fork private so as to prevent any
possible plagiarism. Unfortunately, GitHub doesn't allow private forks of public repositories.

For this reason, we won't be using the standard GitHub workflow here. Instead, we have to jump
through some hoops in order to support our specific use case, while also using GitHub's repository
hosting platform.

Part 1: Operating System Specific Setup
---------------------------------------
Use the following instructions to properly set up your environment and your repository. The
instructions are slightly different for different operating systems.

### Mac OS X
Mac OS X doesn't come standard with a lot of the developer tools necessary for this course. To get
these developer tools, you will have to install XCode tools on your computer. To do so, follow the
instructions below:

- Install XCode Tools
  - In a terminal, run the command `xcode-select --install`
- Install Bazel (via [homebrew](https://brew.sh))
  - In a terminal window, run the following commands:
    ```
    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    brew tap bazelbuild/tap
    brew install bazelbuild/tap/bazel
    ```

### Windows
Windows doesn't come standard with a lot of the developer tools necessary for this course. To get
these developer tools, you will have to install a few different programs. To do so, follow the
instructions below:

- Download and install the Microsoft Visual C++ Redistributable
  - Navigate to the [Microsoft Downloads](https://visualstudio.microsoft.com/downloads/) page
  - At the bottom of the page, you'll find a section entitled "All Downloads" with a search bar
  - Search for "redistributable"
  - Download and run the appropriate package for your architecture (e.g. 32 bit or 64 bit Windows)
- [Download](https://git-scm.com/download/win) and install `git`
  - The default settings already selected during installation are fine to use
- Install Bazel
  - In a new PowerShell window, execute the following commands:
    ```
    Set-ExecutionPolicy RemoteSigned -scope CurrentUser
    iwr -useb get.scoop.sh | iex
    scoop install sudo
    sudo scoop install bazel --global
    ```

Part 2: Bootstrap Your Repository
---------------------------------
Use the following instructions to properly set up your environment and your repository.

- Ensure you have a GitHub account, have verified your email address, and are signed in
- [Create a new repository](https://github.com/new) on GitHub
  - Name your repository `cs404.1`
  - Ensure the repository is marked private
  - Create the repository
- Add `fsareshwala` as a collaborator
  - Visit the `Settings` tab
  - Select the `Manage access` section on the left
  - Click `Invite a collaborator` near the bottom of the page
  - Add the `fsareshwala` user as a collaborator to your repository
- Email `fsareshwala@berkeley.edu` that you have created your repository. I will complete the
  remaining bootstrap steps to fill your repository with the code you need to complete your
  assignments.
- Wait for a response from me before continuing on to the next section.

Part 3: Cloning Your Repository
-------------------------------
Now that your repository contains the code necessary to complete your assignments, you can clone
your repository using GitHub Desktop or whatever other method you prefer.

**Note**: some of the tools we use in this course don't work well with paths that contain spaces. If
you are using Windows, make sure to clone your repository to a location that doesn't have a space in
its path.

Part 4: Installing an IDE
-------------------------
An integrated development environment (IDE) is a tool that developers use to work on code. The IDE
includes all of the elements necessary to compile, run, and debug our programs. You aren't required
to use any specific set of tools for this class outside of `git` and `bazel`. You may use whatever
tools you prefer using and that includes your choice of IDE. It is up to you to determine whichever
development environment works best for your personal tastes. As such, detailed instructions on how
to set up your IDE or perform various environment related operations won't be provided. I assume
that by this stage of your software engineering career, you are familiar with your tools of choice.

Having said that, I offer you the following suggestions:

- [IntelliJ IDEA](https://www.jetbrains.com/idea/download/other.html)
  - **WARNING**: use the latest version that starts with `2019`. Avoid version numbers starting with
    `2020`. The Bazel plugin doesn't work with some of the latter versions of IntelliJ.
  - Once installed, open IntelliJ IDEA and open the preferences pane
  - Search for and install the following extensions within IntelliJ IDEA
    - `Bazel` by Google
    - `google-java-format` by Google`
  - Restart IntelliJ IDEA after installing your plugins
  - Open the preferences pane for IntelliJ IDEA
  - Open the `Other Settings` dropdown on the left side pane
  - Click on `Bazel Settings` to enter Bazel specific preferences
  - Enter the location of the `bazel` binary into the `Bazel binary location` text field. This
    instructs IntelliJ IDEA where Bazel lives on your system.
    - Windows: `C:\ProgramData\scoop\apps\bazel\current\bazel.exe`
    - Mac OS/Linux: `/usr/local/bin/bazel`
    - You may also place the Bazel binary on your `PATH` environment variable if you prefer
  - Load your assignment repository by importing a Bazel project in IntelliJ IDEA
  - Click through until the repository is loaded (default settings are fine to use)

Part 5: Making Your First Commit
--------------------------------
Now that you have properly configured your system, let's start making some changes.

- Identify yourself within your repository
  - Open the `name.md` file in the top level root of the repository
  - Replace the contents with your name
  - Commit the addition and push the change to GitHub
  - This is how I know who the repository belongs to

Troubleshooting
---------------
For most students, the above instructions should work. However, on some systems, you may receive one
of the following errors. Follow the instructions below to fix them. If you receive an error that
isn't listed here, please reach out to me and we can look into it together.

**Error: Deriving targets from project directories failed**
- Open the project view file within IntelliJ: `Bazel | Project | Open Project View File`
- Replace the contents of the file with the following:

  ```
  derive_targets_from_directories: false
  directories:
    .
  targets:
    //...
  ```

- Sync the project once more by clicking the green heart button on the top right of IntelliJ IDEA
