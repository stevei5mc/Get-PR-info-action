# Get PR info action
- **这个 action 用于获取 pr 的一些相关的信息**

## **Language**
- **简体中文  <--**
- **[English](./README-EN.md)**

## **Action 的输入**

|输入名称|描述|默认值|
|:-:|:-:|:-:|
|repoName|目标PR所在的仓库|${{ github.repository }}|
|prId|目标PR的编号|${{ github.event.pull_request.number }}|
|token|GitHub token，这将默认为 GitHub token。如果您想使用您的个人令牌（用于定位其他存储库等）来使用的。<br>如果您使用的是个人访问 token，它应该可以访问 `repo` 范围。|${{ github.token }}|

## **Action 输出**

|输出名称|描述|备注|
|:-:|:-:|:-:|
|apiUrl|目标 Pull request 的api请求链接||
|htmlUrl|目标 Pull request的链接||
|prState|目标 Pull request 的状态||
|prLockedState|目标 Pull request 的锁定状态||
|prDraftState|目标 Pull request 的草案状态||
|requestUser|目标 Pull request 的发起人||
|createdAt|目标 Pull request 的创建时间||
|updatedAt|目标 Pull request 的更新时间||
|closedAt|目标 Pull request 的关闭时间|如果 `prState` 获取的状态为 `open` 将不会返回结果|
|commits|目标 Pull request 的提交数||
|additions|目标 Pull request 的增加行数||
|deletions|目标 Pull request 的删除行数||
|changedFiles|目标 Pull request 的文件改动数||
|headSha|目标 Pull request 的 head 分支的 sha 值||
|headRef|目标 Pull request 的 head 分支的 ref 名称||
|headLabel|目标 Pull request 的 head 分支的的标签||
|headUserName|目标 Pull request 的 head 分支所在的仓库的用户名||
|headFullName|目标 Pull request 的 head 分支所在的仓库的全名||
|headRepoUrl|目标 Pull request 的 head 分支所在的仓库的链接||
|baseSha|目标 Pull request 的 base 分支的 sha 值||
|baseRef|目标 Pull request 的 base 分支的 ref 名称||
|baseLabel|目标 Pull request 的 base 分支的的标签||
|baseUserName|目标 Pull request 的 base 分支所在的仓库的用户名||
|baseFullName|目标 Pull request 的 base 分支所在的仓库的全名||
|baseRepoUrl|目标 Pull request 的 base 分支所在的仓库的链接||
|prMergedState|目标 Pull request 的合并状态||
|prMergedBy|将目标 Pull request 合并的用户|如果 `prMergedState` 获取的状态为 `false` 将不会返回结果|

## **使用示例**

### **pull request**
```yml
on:
  pull_request:
    branches:
      - main

  test-action:
    runs-on: ubuntu-latest
    name: GitHub Actions Test
    steps:
      - name: Test Local Action 4 
        id: test-action-4
        uses: stevei5mc/Get-PR-info-action@main
```

### **workflow dispatch**

```yml
on:
  workflow_dispatch:
    PR_number:
        description: 'PR number'
        required: true

  test-action:
    runs-on: ubuntu-latest
    name: GitHub Actions Test
    steps:
      - name: Test Local Action 4 
        id: test-action-4
        uses: stevei5mc/Get-PR-info-action@main
        with:
            prId: ${{ inputs.PR_number }}
```