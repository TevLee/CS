# Github 레포지토리로 push 할때 오류
```
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
원인 : github에서 레파지토리 생성할 때, README.md 파일을 생성했기 때문.(혹은 깃헙에서 직접 다른 파일을 생성)
해결 : 
(1) git pull origin {해당 repo명 또는 branch명}
(2) git pull origin {해당 repo명 또는 branch명} --allow-unrelated-history
  - commit 히스토리가 서로 연관성이 없어 push가 거절된 것이므로

** (1) 방법으로 해결..
