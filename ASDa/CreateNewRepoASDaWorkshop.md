# ASDa Workshop Creation Guide

Each workshop has its own git repository in ~scarl/web-repos.

We've used a naming scheme with date first, followed by the group and type of workshop. 

The `.git` suffix indicates that it is a git repo. e.g. `2025-07-VSP_Course1.git`

## Initialize the git repo for a new workshop

1. SSH into `r8-asda.stat.ubc.ca` as yourself (using PuTTY or another terminal client) 

2. Run the script `~scarl/make-workshop <workshop name>`. Replace `<workshop name>` with the name of the workshop (without the .git suffix).   

    For example: `~scarl/make-workshop 2025-07-VSP_Course1` 

    Just for your information, this script will automatically do the following:  

    a. Creates an empty git repo in `~scarl/web-repos`  
    (e.g. `~scarl/web-repos/2025-07-VSP_Course1.git`)  
    b. Creates an empty directory with the same name as the workshop under `/var/www/asda-workshops` where the final HTML files will eventually go  
    (e.g. `/var/www/asda-workshops/2025-07-VSP_Course1`)  
    c. When the git repo from step a is pushed to, it runs another script (git hook) that will copy the contents of the `_site` subdirectory (where your final HTML files will be) in the repo into the directory under `/var/www/asda-workshops` from step b where it will be published on the ASDa website.

## Clone workshops and copy files from a previous workshop

When you start a new workshop the git repository for it will be completely empty. 

To start off the workshop project it's usually far easier to copy the needed files from a previous workshop's git repo.

1. SSH into `r8-asda.stat.ubc.ca` as yourself or work on your own device using a terminal with git.

2. `cd` into a suitable working directory to clone the repos into such as your home directory.

3. Clone the newly created repo.

    **If you're logged on to `r8-asda.stat.ubc.ca`:**  
    `git clone ~scarl/web-repos/<workshop name>.git`  
    (e.g. `git clone ~scarl/web-repos/2025-07-VSP_Course1.git`)

    **If you're on your own device's terminal:**  
    Replace `<username>` with your StatNet username.  
    `git clone <username>@r8-asda.stat.ubc.ca:~scarl/web-repos/<workshop name>.git`  
    (e.g. `git clone <username>@r8-asda.stat.ubc.ca:~scarl/web-repos/2025-07-VSP_Course1.git`)

4. Clone the old repo you want to copy.

    **If you're logged on to `r8-asda.stat.ubc.ca`:**  
    `git clone ~scarl/web-repos/<old workshop name>.git`  
    (e.g. `git clone ~scarl/web-repos/2024-07-VSP_Course1.git`)

    **If you're on your own device's terminal:**  
    Replace `<username>` with your StatNet username.  
    `git clone <username>@r8-asda.stat.ubc.ca:~scarl/web-repos/<old workshop name>.git`  
    (e.g. `git clone <username>@r8-asda.stat.ubc.ca:~scarl/web-repos/2024-07-VSP_Course1.git`)

    **Note:** If you get the error `fatal: detected dubious ownership in repository at '/zfs/users/scarl/scarl/web-repos/2024-07-VSP_Course1.git'`  
    It just means that the git repo was created by another member of ASDa. To silence this error, SSH in to `r8-asda.stat.ubc.ca` as yourself if you haven't already and run the command `git config --global --add safe.directory '*'`

5. Copy over the files from the old repo to the new repo.

    The primary files to copy over are:
    ```
    _site.yml
    _navbar.yml
    styles.css
    index.Rmd
    setup.Rmd and images (optional)
    ... include any other file with -slides or -notes in it, so that you can modify them as needed
    Makefile
    ```

    You can copy everything **EXCEPT** the .git file.

6. Make your changes in the new repo with the copied over files.

    Afterwards, you can run `make` to rebuild the `_site` folder. (Depending on the project framework)

    The only convention that you need to follow is that your notes files' names
    end with `-notes.Rmd` and slides with `-slides.Rmd`. To rebuild, you'll need
    the `rmarkdown` R package, Pandoc (if it`s not bundled with rmarkdown,
    I can`t remember if it is), and Latex. 

    If you use my existing slides as a template, those will require `xelatex` too, but that`s normally included with a standard Latex installation.

    Alternatively you can compile the .Rmd or other project framework files on your own computer and put them in `_site`. 

## Push your changes to publish the new workshop

1. `cd` to the location of the new repo you had cloned and made changes to.

2. Run the `git status` command and check that the files listed are what you intend to change.

3. Create a `master` branch in the repo with `git checkout -b master`

    Note: This is not necessary if you're working on `r8-asda.stat.ubc.ca` or a machine with an older git installation that defaults to a `master` branch but newer git installations will default to a `main` branch which will cause the git hook script that publishes the workshop to the website to fail.

4. Run `git add .` to stage all the changed files.

5. Run `git commit -m "<your commit message>"` to create a commit with your changes. Replace `<your commit message>` with a short description of what your changes are about or just `"First commit"` if it's the first commit in the repo. 

6. Run `git push` to push your commit(s) to the corresponding repo in `~scarl/web-repos`

    Note: If you get the error `fatal: The current branch master has no upstream branch.` then instead run the command `git push --set-upstream origin master`

7. Wait for the push to complete and then check the ASDa website to see if the workshop was published successfully under the link `https://asda.stat.ubc.ca/Workshops/<workshop name>`
