pre-commit HOOK code!

#!/bin/sh

echo " Prettier is runnig to check ..."

npx prettier . --check

if [ $? -ne 0 ]; then
echo "Prettier foun error and stopped!"
exit 1
fi

echo "Prettier pass all and conitnue with commit!"

steps that working in!
valeri@win11-teslab MINGW64 /c/Exam/Automating Workflow with Git Hooks and CICD Integration (main)
$ git status
On branch main
Untracked files:
(use "git add <file>..." to include in what will be committed)
.gitignore
README.md
app.js
package-lock.json
package.json

nothing added to commit but untracked files present (use "git add" to track)

valeri@win11-teslab MINGW64 /c/Exam/Automating Workflow with Git Hooks and CICD Integration (main)
$ git add .
warning: in the working copy of 'package-lock.json', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'package.json', LF will be replaced by CRLF the next time Git touches it

valeri@win11-teslab MINGW64 /c/Exam/Automating Workflow with Git Hooks and CICD Integration (main)
$ git commit -m "added app.js and readme.md"
Prettier is runnig to check ...
Checking formatting...
[warn] README.md
[warn] Code style issues found in the above file. Run Prettier with --write to fix.
Prettier foun error and stopped!

valeri@win11-teslab MINGW64 /c/Exam/Automating Workflow with Git Hooks and CICD Integration (main)
$ git add .

valeri@win11-teslab MINGW64 /c/Exam/Automating Workflow with Git Hooks and CICD Integration (main)
$ git commit -m "added app.js and readme.md"
Prettier is runnig to check ...
Checking formatting...
[warn] app.js
[warn] README.md
[warn] Code style issues found in 2 files. Run Prettier with --write to fix.
Prettier foun error and stopped!

valeri@win11-teslab MINGW64 /c/Exam/Automating Workflow with Git Hooks and CICD Integration (main)
$ npx prettier . --write
app.js 107ms
package-lock.json 763ms (unchanged)
package.json 55ms (unchanged)
README.md 97ms

valeri@win11-teslab MINGW64 /c/Exam/Automating Workflow with Git Hooks and CICD Integration (main)
$ git status
On branch main
Changes to be committed:
(use "git restore --staged <file>..." to unstage)
new file: .gitignore
new file: README.md
new file: app.js
new file: package-lock.json
new file: package.json

Changes not staged for commit:
(use "git add <file>..." to update what will be committed)
(use "git restore <file>..." to discard changes in working directory)
modified: README.md
modified: app.js

$ git add .
warning: in the working copy of 'README.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'app.js', LF will be replaced by CRLF the next time Git touches it

valeri@win11-teslab MINGW64 /c/Exam/Automating Workflow with Git Hooks and CICD Integration (main)
$ git commit -m "updated formating in app.js and readme.md"
Prettier is runnig to check ...
Checking formatting...
All matched files use Prettier code style!
Prettier pass all and conitnue with commit!
[main 06b25d2] updated formating in app.js and readme.md
5 files changed, 4453 insertions(+)
create mode 100644 .gitignore
create mode 100644 README.md
create mode 100644 app.js
create mode 100644 package-lock.json
create mode 100644 package.json

Pre-push HOOK code!

#!/bin/sh

echo "Test is running ..."

npm test

if [ $? -ne 0 ]; then
echo "Tests failed and cannot push in remote repo!"
exit 1
fi

echo "All test passed and push is allowed to remote repo!"

netxt steps in working!
$ git commit -m "added new file app.tets for testing push"
Prettier is runnig to check ...
Checking formatting...
app.test.js
[error] app.test.js: SyntaxError: Unexpected token, expected "," (3:63)
[error] 1 | import sum from "./sum";
[error] 2 |
[error] > 3 | test("adds 1 + 2 to equal 3"), () => { expect(sum(1,2).toBe(3); )};
[error] | ^
Error occurred when checking code style in the above file.
Prettier foun error and stopped!

valeri@win11-teslab MINGW64 /c/Exam/Automating Workflow with Git Hooks and CICD Integration (main)
$ git add app.test.js

valeri@win11-teslab MINGW64 /c/Exam/Automating Workflow with Git Hooks and CICD Integration (main)
$ git commit -m "added new file app.tets for testing push"
Prettier is runnig to check ...
Checking formatting...
[warn] app.test.js
[warn] Code style issues found in the above file. Run Prettier with --write to fix.
Prettier foun error and stopped!

valeri@win11-teslab MINGW64 /c/Exam/Automating Workflow with Git Hooks and CICD Integration (main)
$ npx prettier . --write
app.js 102ms (unchanged)
app.test.js 25ms
package-lock.json 386ms (unchanged)
package.json 31ms (unchanged)
README.md 137ms (unchanged)

$ git status
On branch main
Changes to be committed:
(use "git restore --staged <file>..." to unstage)
new file: app.test.js

Changes not staged for commit:
(use "git add <file>..." to update what will be committed)
(use "git restore <file>..." to discard changes in working directory)
modified: app.test.js

valeri@win11-teslab MINGW64 /c/Exam/Automating Workflow with Git Hooks and CICD Integration (main)
$ git add app.test.js
warning: in the working copy of 'app.test.js', LF will be replaced by CRLF the next time Git touches it

valeri@win11-teslab MINGW64 /c/Exam/Automating Workflow with Git Hooks and CICD Integration (main)
$ git commit -m "updated new file app.tets for testing push"
Prettier is runnig to check ...
Checking formatting...
All matched files use Prettier code style!
Prettier pass all and conitnue with commit!
[main d67f868] updated new file app.tets for testing push
1 file changed, 5 insertions(+)
create mode 100644 app.test.js

$ git commit -m "modify app.test.js"
Prettier is runnig to check ...
Checking formatting...
[warn] app.test.js
[warn] Code style issues found in the above file. Run Prettier with --write to fix.
Prettier foun error and stopped!

valeri@win11-teslab MINGW64 /c/Exam/Automating Workflow with Git Hooks and CICD Integration (main)
$ npx prettier . --write
app.js 102ms (unchanged)
app.test.js 24ms
package-lock.json 338ms (unchanged)
package.json 50ms (unchanged)
README.md 105ms (unchanged)

valeri@win11-teslab MINGW64 /c/Exam/Automating Workflow with Git Hooks and CICD Integration (main)
$ git add .
warning: in the working copy of 'app.test.js', LF will be replaced by CRLF the next time Git touches it

valeri@win11-teslab MINGW64 /c/Exam/Automating Workflow with Git Hooks and CICD Integration (main)
$ git commit -m "modify app.test.js"
Prettier is runnig to check ...
Checking formatting...
All matched files use Prettier code style!
Prettier pass all and conitnue with commit!
[main cacc3a3] modify app.test.js
1 file changed, 1 insertion(+), 1 deletion(-)

$ git push -u origin main
Test is running ...

> automating-workflow-with-git-hooks-and-cicd-integration@1.0.0 test
> jest

FAIL ./app.test.js
● Test suite failed to run

    Jest encountered an unexpected token

    Jest failed to parse a file. This happens e.g. when your code or its dependencies use non-standard JavaScript syntax, or when Jest is not configured to support such syntax.

    Out of the box Jest supports Babel, which will be used to transform your files into valid JS based on your Babel configuration.

    By default "node_modules" folder is ignored by transformers.

    Here's what you can do:
     • If you are trying to use ECMAScript Modules, see https://jestjs.io/docs/ecmascript-modules for how to enable it.
     • If you are trying to use TypeScript, see https://jestjs.io/docs/getting-started#using-typescript
     • To have some of your "node_modules" files transformed, you can specify a custom "transformIgnorePatterns" in your config.
     • If you need a custom transformation, specify a "transform" option in your config.
     • If you simply want to mock your non-JS modules (e.g. binary assets) you can stub them out with the "moduleNameMapper" config option.

    You'll find more details and examples of these config options in the docs:
    https://jestjs.io/docs/configuration
    For information about custom transformations, see:
    https://jestjs.io/docs/code-transformation

    Details:

    C:\Exam\Automating Workflow with Git Hooks and CICD Integration\app.test.js:1
    import sum from "./app";
    ^^^^^^

    SyntaxError: Cannot use import statement outside a module

      at Runtime.createScriptFromCode (node_modules/jest-runtime/build/index.js:1316:40)

Test Suites: 1 failed, 1 total
Tests: 0 total
Snapshots: 0 total
Time: 0.843 s
Ran all test suites.
Tests failed and cannot push in remote repo!
error: failed to push some refs to 'github.com:bgatanasov/Automating-Workflow-with-Git-Hooks-and-CICD-Integration.git'

valeri@win11-teslab MINGW64 /c/Exam/Automating Workflow with Git Hooks and CICD Integration (main)
$ git push -u origin main
Test is running ...

> automating-workflow-with-git-hooks-and-cicd-integration@1.0.0 test
> jest

PASS ./app.test.js
√ adds 1 + 2 to equal 3 (8 ms)

Test Suites: 1 passed, 1 total
Tests: 1 passed, 1 total
Snapshots: 0 total
Time: 1.301 s
Ran all test suites.
All test passed and push is allowed to remote repo!
Enumerating objects: 30, done.
Counting objects: 100% (30/30), done.
Delta compression using up to 2 threads
Compressing objects: 100% (28/28), done.
Writing objects: 100% (30/30), 38.28 KiB | 1.20 MiB/s, done.
Total 30 (delta 11), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (11/11), done.
To github.com:bgatanasov/Automating-Workflow-with-Git-Hooks-and-CICD-Integration.git

- [new branch] main -> main
  branch 'main' set up to track 'origin/main'.
