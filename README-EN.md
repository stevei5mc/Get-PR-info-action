# Get PR info action
- **This action is used to obtain some related information about a PR.**

## **Language**
- **[简体中文](./README.md)**
- **English  <--**

## **Action Input**

|Input Name|Description|Default Value|
|:-:|:-:|:-:|
|repoName|The repository where the target PR is located|${{ github.repository }}|
|prId|The number of the target PR|${{ github.event.pull_request.number }}|
|token|GitHub token, which will default to the GitHub token. If you want to use your personal token (for locating other repositories, etc.), you can use it here.<br>If you are using a personal access token, it should have access to the `repo` scope.|${{ github.token }}|

## **Action Output**

|Output Name|Description|Notes|
|:-:|:-:|:-:|
|apiUrl|The API request link of the target Pull request||
|htmlUrl|The link of the target Pull request||
|prState|The state of the target Pull request||
|prLockedState|The locked state of the target Pull request||
|prDraftState|The draft state of the target Pull request||
|requestUser|The creator of the target Pull request||
|createdAt|The creation time of the target Pull request||
|updatedAt|The update time of the target Pull request||
|closedAt|The close time of the target Pull request|If the `prState` is `open`, no result will be returned|
|commits|The number of commits in the target Pull request||
|additions|The number of added lines in the target Pull request||
|deletions|The number of deleted lines in the target Pull request||
|changedFiles|The number of changed files in the target Pull request||
|headSha|The sha value of the head branch of the target Pull request||
|headRef|The ref name of the head branch of the target Pull request||
|headLabel|The label of the head branch of the target Pull request||
|headUserName|The username of the repository where the head branch of the target Pull request is located||
|headFullName|The full name of the repository where the head branch of the target Pull request is located||
|headRepoUrl|The link of the repository where the head branch of the target Pull request is located||
|baseSha|The sha value of the base branch of the target Pull request||
|baseRef|The ref name of the base branch of the target Pull request||
|baseLabel|The label of the base branch of the target Pull request||
|baseUserName|The username of the repository where the base branch of the target Pull request is located||
|baseFullName|The full name of the repository where the base branch of the target Pull request is located||
|baseRepoUrl|The link of the repository where the base branch of the target Pull request is located||
|prMergedState|The merge state of the target Pull request||
|prMergedBy|The user who merged the target Pull request|If the `prMergedState` is `false`, no result will be returned|

## **Usage examples**

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
        uses: stevei5mc/Get-PR-info-action@v1
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
        uses: stevei5mc/Get-PR-info-action@v1
        with:
            prId: ${{ inputs.PR_number }}
```