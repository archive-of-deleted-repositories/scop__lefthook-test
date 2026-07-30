```shell
$ cd $(mktemp -d)

$ git init

$ cat <<\EOF >lefthook.yaml
remotes:
- git_url: https://github.com/scop/lefthook-test.git
  ref: feat/test-branch
  refetch_frequency: 24h
EOF

$ lefthook run --verbose pre-commit 
│  [lefthook] git: git version       
│             out: git version 2.53.0
│                                    
│  [lefthook] git: git rev-parse --path-format=absolute --show-toplevel --git-path hooks --git-path info --git-dir
│             out: /tmp/tmp.jTQCBYVFuF                                                                            
│                  /tmp/tmp.jTQCBYVFuF/.git/hooks                                                                 
│                  /tmp/tmp.jTQCBYVFuF/.git/info                                                                  
│                  /tmp/tmp.jTQCBYVFuF/.git                                                                       
│                                                                                                                 
│  loading config:  /tmp/tmp.jTQCBYVFuF/lefthook.yaml
│  Merging remote config: https://github.com/scop/lefthook-test.git: /tmp/tmp.jTQCBYVFuF/.git/info/lefthook-remotes/lefthook-test-feat/test-branch/lefthook.yml
╭──────────────────────────────────────────╮
│ 🥊 lefthook  v2.1.10   hook:  pre-commit │
╰──────────────────────────────────────────╯
│  Cloning remote config repository: /tmp/tmp.jTQCBYVFuF/.git/info/lefthook-remotes/lefthook-test-feat/test-branch/lefthook-test-feat/test-branch
│  [lefthook] git: git diff --name-only --cached --diff-filter=ACMR
│                                                                  
│  [lefthook] git: git diff --name-only --cached --diff-filter=ACMRD
│                                                                   
│  [lefthook] git: git status --short --porcelain -z
│             out: ?? lefthook.yaml                 
│                                                   
│  [lefthook] git: git -C /tmp/tmp.jTQCBYVFuF/.git/info/lefthook-remotes clone --quiet --origin origin --depth 1 --branch feat/test-branch https://github.com/scop/lefthook-test.git lefthook-test-feat/test-branch
│                                                                                                                                                                                                                  
│  [lefthook] git: git -C /tmp/tmp.jTQCBYVFuF/.git/info/lefthook-remotes/lefthook-test-feat/test-branch fetch --quiet --depth 1 origin -- feat/test-branch
│                                                                                                                                                         
│  [lefthook] git: git -C /tmp/tmp.jTQCBYVFuF/.git/info/lefthook-remotes/lefthook-test-feat/test-branch checkout FETCH_HEAD
│                                                                                                                          
│  Reloading config...
│  Merging remote config: https://github.com/scop/lefthook-test.git: /tmp/tmp.jTQCBYVFuF/.git/info/lefthook-remotes/lefthook-test-feat/test-branch/lefthook.yml
│  Removing stale remote:  /tmp/tmp.jTQCBYVFuF/.git/info/lefthook-remotes/lefthook-test-feat
│  hello (skip) no matching staged files
│  [lefthook] script doesn't exist: /tmp/tmp.jTQCBYVFuF/.lefthook/pre-commit/hello.sh
│  [lefthook] script doesn't exist: /tmp/tmp.jTQCBYVFuF/.lefthook-local/pre-commit/hello.sh
│  [lefthook] script doesn't exist: /tmp/tmp.jTQCBYVFuF/.config/lefthook/pre-commit/hello.sh
│  [lefthook] script doesn't exist: /tmp/tmp.jTQCBYVFuF/.config/lefthook-local/pre-commit/hello.sh
│  [lefthook] script doesn't exist: /tmp/tmp.jTQCBYVFuF/.git/info/lefthook-remotes/lefthook-test-feat/test-branch/.lefthook/pre-commit/hello.sh
│  script (skip) script does not exist: hello.sh
  ────────────────────────────────────
summary: (done in 0.00 seconds)
🥊 script: script does not exist: hello.sh (0.00 seconds)

$ ls -a .git/info/lefthook-remotes
.  ..
```
