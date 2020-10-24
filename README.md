# google-chat-action

Sample

```yaml
name: Sample Testing
on: [push]

jobs:
  my_job:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout
      uses: actions/checkout@v2
    - run: echo "::set-output name=sha8::$(echo ${GITHUB_SHA} | cut -c1-8)"
      id: slug
    - name: Chat Setup
      uses: DTherHtun/google-chat-action@v0.7
      with:
        project: ${{ github.repository }}
        commit: ${{ steps.slug.outputs.sha8 }}
        branch: ${{ github.ref }}
        status: ${{ job.status }}
        actionid: ${{ github.repository }}/runs/${{ github.run_id }}
        webhook: "https://chat.googleapis.com/v1/spaces/AAAAzPcAy4s/messages?key=AIzaSyDdI0hCZtE6vySjMm-WEfRq3CPzqKqqsHI&token=MmdzluicdrdkyUAV_QwB6BzlLcIhbfrwNzxVrEllaec%3D&threadKey=git-commit"


```
