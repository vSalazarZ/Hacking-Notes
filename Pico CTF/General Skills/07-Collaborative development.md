## Descripción 
My team has been working very hard on new features for our flag printing program! I wonder how they'll work together?You can download the challenge files here:
- [challenge.zip](https://artifacts.picoctf.net/c_titan/71/challenge.zip)

Hint:
1. `git branch -a` will let you see available branches
2. How can file 'diffs' be brought to the main branch? Don't forget to `git config`!
3. Merge conflicts can be tricky! Try a text editor like nano, emacs, or vim.
## Solución 1

Con consola linux
Primero descargamos el zip con wget, le damos unzip
En los hints nos dice que tenemos que usar branch y merge, usamos branch para ver que tenemos 3 partes separadas y con merge los juntamos, pero cada que usamos uno nos dice que hay un error, el primero sale bien, el segundo nos dice que tenemos que identificarnos y el último que usemos git add para agregarlos todos

```
vSalazarZ-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/71/challenge.zip
--2025-02-22 04:57:32--  https://artifacts.picoctf.net/c_titan/71/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.18, 3.160.5.71, 3.160.5.93, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 24467 (24K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip                                              100%[=======================================================================================================================================>]  23.89K  --.-KB/s    in 0.008s  

2025-02-22 04:57:32 (2.98 MB/s) - 'challenge.zip' saved [24467/24467]

vSalazarZ-picoctf@webshell:~$ ls
challenge.zip
vSalazarZ-picoctf@webshell:~$ unzip challenge.zip
Archive:  challenge.zip
   creating: drop-in/
   creating: drop-in/.git/
   creating: drop-in/.git/branches/
  inflating: drop-in/.git/description  
   creating: drop-in/.git/hooks/
  inflating: drop-in/.git/hooks/applypatch-msg.sample  
  inflating: drop-in/.git/hooks/commit-msg.sample  
  inflating: drop-in/.git/hooks/fsmonitor-watchman.sample  
  inflating: drop-in/.git/hooks/post-update.sample  
  inflating: drop-in/.git/hooks/pre-applypatch.sample  
  inflating: drop-in/.git/hooks/pre-commit.sample  
  inflating: drop-in/.git/hooks/pre-merge-commit.sample  
  inflating: drop-in/.git/hooks/pre-push.sample  
  inflating: drop-in/.git/hooks/pre-rebase.sample  
  inflating: drop-in/.git/hooks/pre-receive.sample  
  inflating: drop-in/.git/hooks/prepare-commit-msg.sample  
  inflating: drop-in/.git/hooks/update.sample  
   creating: drop-in/.git/info/
  inflating: drop-in/.git/info/exclude  
   creating: drop-in/.git/refs/
   creating: drop-in/.git/refs/heads/
 extracting: drop-in/.git/refs/heads/main  
   creating: drop-in/.git/refs/heads/feature/
  inflating: drop-in/.git/refs/heads/feature/part-1  
 extracting: drop-in/.git/refs/heads/feature/part-2  
 extracting: drop-in/.git/refs/heads/feature/part-3  
   creating: drop-in/.git/refs/tags/
 extracting: drop-in/.git/HEAD       
  inflating: drop-in/.git/config     
   creating: drop-in/.git/objects/
   creating: drop-in/.git/objects/pack/
   creating: drop-in/.git/objects/info/
   creating: drop-in/.git/objects/77/
 extracting: drop-in/.git/objects/77/d6ceca6fe23b57d88cf16f20003e10d6715690  
   creating: drop-in/.git/objects/b9/
 extracting: drop-in/.git/objects/b9/32e8c048154a46d224cd7691c99dc8cb88164a  
   creating: drop-in/.git/objects/6c/
 extracting: drop-in/.git/objects/6c/e09adec311b859780caf89d993c58e34b53fa6  
   creating: drop-in/.git/objects/6e/
 extracting: drop-in/.git/objects/6e/17fb3a35364b4f9bb8bef8b5e6a5af2d3e7dfa  
   creating: drop-in/.git/objects/43/
 extracting: drop-in/.git/objects/43/e44dd37ba0c0adc3d78d0b85d699859ec8d75c  
   creating: drop-in/.git/objects/74/
 extracting: drop-in/.git/objects/74/ae5215b93a82ddf3dd37df3d4c6b5aff0a93ed  
   creating: drop-in/.git/objects/7a/
 extracting: drop-in/.git/objects/7a/b4e25c0cd108374b2275fdb1fcdf635e591833  
   creating: drop-in/.git/objects/d1/
 extracting: drop-in/.git/objects/d1/f3407cee4479c075997b497fa290ca636fe258  
   creating: drop-in/.git/objects/b4/
 extracting: drop-in/.git/objects/b4/612c914d8461d1b1a50652cc303b76813ee142  
 extracting: drop-in/.git/objects/b4/5df8ce6725e05ed8f45745793f91c26f6529dc  
   creating: drop-in/.git/objects/59/
 extracting: drop-in/.git/objects/59/d9bf3f55055654fda549be87499374805f28e3  
   creating: drop-in/.git/objects/5c/
 extracting: drop-in/.git/objects/5c/6d493ac583a95117d3a70eb5b10d9d76991c48  
  inflating: drop-in/.git/index      
 extracting: drop-in/.git/COMMIT_EDITMSG  
   creating: drop-in/.git/logs/
  inflating: drop-in/.git/logs/HEAD  
   creating: drop-in/.git/logs/refs/
   creating: drop-in/.git/logs/refs/heads/
  inflating: drop-in/.git/logs/refs/heads/main  
   creating: drop-in/.git/logs/refs/heads/feature/
  inflating: drop-in/.git/logs/refs/heads/feature/part-1  
  inflating: drop-in/.git/logs/refs/heads/feature/part-2  
  inflating: drop-in/.git/logs/refs/heads/feature/part-3  
  inflating: drop-in/flag.py         
vSalazarZ-picoctf@webshell:~$ ls
challenge.zip  drop-in
vSalazarZ-picoctf@webshell:~$ cd drop-in/
vSalazarZ-picoctf@webshell:~/drop-in$ git branch -a
 a-
  feature/part-1
  feature/part-2
  feature/part-3
* main
(END)
vSalazarZ-picoctf@webshell:~/drop-in$ git branch -a

[2]+  Stopped                 git branch -a
vSalazarZ-picoctf@webshell:~/drop-in$ git merge feature/part-1
Updating 6ce09ad..74ae521
Fast-forward
 flag.py | 1 +
 1 file changed, 1 insertion(+)
vSalazarZ-picoctf@webshell:~/drop-in$ cat flag.py
print("Printing the flag...")
print("picoCTF{t3@mw0rk_", end='')vSalazarZ-picoctf@webshell:~/drop-in$ 
vSalazarZ-picoctf@webshell:~/drop-in$ git merge feature/part-2
Committer identity unknown

*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: unable to auto-detect email address (got 'vSalazarZ-picoctf@webshell.(none)')
vSalazarZ-picoctf@webshell:~/drop-in$ git config
usage: git config [<options>]

Config file location
    --global              use global config file
    --system              use system config file
    --local               use repository config file
    --worktree            use per-worktree config file
    -f, --file <file>     use given config file
    --blob <blob-id>      read config from given blob object

Action
    --get                 get value: name [value-pattern]
    --get-all             get all values: key [value-pattern]
    --get-regexp          get values for regexp: name-regex [value-pattern]
    --get-urlmatch        get value specific for the URL: section[.var] URL
    --replace-all         replace all matching variables: name value [value-pattern]
    --add                 add a new variable: name value
    --unset               remove a variable: name [value-pattern]
    --unset-all           remove all matches: name [value-pattern]
    --rename-section      rename section: old-name new-name
    --remove-section      remove a section: name
    -l, --list            list all
    --fixed-value         use string equality when comparing values to 'value-pattern'
    -e, --edit            open an editor
    --get-color           find the color configured: slot [default]
    --get-colorbool       find the color setting: slot [stdout-is-tty]

Type
    -t, --type <>         value is given this type
    --bool                value is "true" or "false"
    --int                 value is decimal number
    --bool-or-int         value is --bool or --int
    --bool-or-str         value is --bool or string
    --path                value is a path (file or directory name)
    --expiry-date         value is an expiry date

Other
    -z, --null            terminate values with NUL byte
    --name-only           show variable names only
    --includes            respect include directives on lookup
    --show-origin         show origin of config (file, standard input, blob, command line)
    --show-scope          show scope of config (worktree, local, global, system, command)
    --default <value>     with --get, use default value when missing entry

vSalazarZ-picoctf@webshell:~/drop-in$ git config --global user.email "you@example.com"
vSalazarZ-picoctf@webshell:~/drop-in$   git config --global user.name Your Name
vSalazarZ-picoctf@webshell:~/drop-in$ git merge feature/part-2
Auto-merging flag.py
CONFLICT (content): Merge conflict in flag.py
Automatic merge failed; fix conflicts and then commit the result.
vSalazarZ-picoctf@webshell:~/drop-in$ cat flag.py
print("Printing the flag...")
<<<<<<< HEAD
print("picoCTF{t3@mw0rk_", end='')
=======

print("m@k3s_th3_dr3@m_", end='')
>>>>>>> feature/part-2
vSalazarZ-picoctf@webshell:~/drop-in$ git merge feature/part-3
error: Merging is not possible because you have unmerged files.
hint: Fix them up in the work tree, and then use 'git add/rm <file>'
hint: as appropriate to mark resolution and make a commit.
fatal: Exiting because of an unresolved conflict.
vSalazarZ-picoctf@webshell:~/drop-in$ git add flag.py
vSalazarZ-picoctf@webshell:~/drop-in$ git merge feature/part-3
fatal: You have not concluded your merge (MERGE_HEAD exists).
Please, commit your changes before you merge.
vSalazarZ-picoctf@webshell:~/drop-in$ git add flag.py
vSalazarZ-picoctf@webshell:~/drop-in$ git commit -m part3
[main cce8f6e] part3
vSalazarZ-picoctf@webshell:~/drop-in$ git merge feature/part-3
Auto-merging flag.py
CONFLICT (content): Merge conflict in flag.py
Automatic merge failed; fix conflicts and then commit the result.
vSalazarZ-picoctf@webshell:~/drop-in$ git add flag.py
vSalazarZ-picoctf@webshell:~/drop-in$ cat flag.py
print("Printing the flag...")
<<<<<<< HEAD
<<<<<<< HEAD
print("picoCTF{t3@mw0rk_", end='')
=======

print("m@k3s_th3_dr3@m_", end='')
>>>>>>> feature/part-2
=======

print("w0rk_4c24302f}")
>>>>>>> feature/part-3
vSalazarZ-picoctf@webshell:~/drop-in$ 

flag: picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_4c24302f}
```

## Referencias 
https://primer.picoctf.org/#_git_version_control