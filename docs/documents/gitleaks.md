# 1.Talisman

[Document]: https://thoughtworks.github.io/talisman/docs
---
## 1.1 How to use？
---
### 1.1.1 Use as a hook

`before commit or push`
---
### 1.1.2 Use as a git Scanner
---
`add it to your CI/CD pipelines, to scan git history of your repository to find any sensitive content`

talisman --scan or talisman --scanWithHtml
---
### 1.1.3 Checksum Calculator

`talisman --checksum="*.lock"`

上面的意思是为所有的.lock文件生成一个值，类似于：cf97abd34cebe895417eb4d97fbd7374aa138dcb65b1fe7f6b6cc1238aaf4d48

这样你就可以设置一些过滤条件，忽视这些特殊文件，从而不让talisman报告相关错误，而当生成这个值相关的文件进行更改时，Talisman 将再次扫描文件以查找任何潜在的安全威胁。如果需要，您还可以重新计算校验和。
---
## 1.2 How it works?

https://thoughtworks.github.io/talisman/docs/how-it-works

有很多的detectors:
---
### 1.3 configuring Talisman
---
### 1.3.1 ignore from scan
---
### 1.3.2 Run Hook In Interactive Mode
---
### 1.3.3 Set by default severity threshold
----
# 2.Gitleaks
---
## 2.1检查所有的提交是否包含了secret

```
gitleaks detect .
gitleaks detect -v
```
---
## 2.2 在提交前检查你staged的文件，防止提交的文件中包含secret

```
gitleaks protect --staged
gitleaks protect --staged -v
```
---
2.3 在提交前自动化检测要commit的文件，防止提交的文件中包含secret

add `exec gitleaks protect --staged -v` to `.git/hooks/pre-commit`

add [pre-commit script supported by Gitleaks]([gitleaks/pre-commit.py at master · gitleaks/gitleaks · GitHub](https://github.com/gitleaks/gitleaks/blob/master/scripts/pre-commit.py))

install pre-commit tool and config gitleaks to your pre-commit-config.yml.

[.pre-commit-config.yaml for gitleaks · GitHub](https://gist.github.com/akashchandwani/4665bb3e211fed6197eb048ce756886a)
---
2.4  团队协作的repo，你无法确保所有team member都在本地安装了pre-commit tool并做了相关配置，所以应该在push代码时，检测代码中是否包含secret
----
# 3.GitLeaks VS Talisman

gitleaks protect --staged
> Q1:Talisman在项目中的实践？

> Q2:Talisman支持Zsh吗？