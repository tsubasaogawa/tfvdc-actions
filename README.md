# tfvdc-actions

![Sample](https://user-images.githubusercontent.com/7788821/220005307-7edffee7-5d0f-4418-a24b-d1cd819fe276.png)

A simple gh-actions to make sure that the variable contains a description

## Features

- Warning if a variable block has not `description` field.
- Comment to pull request using [reviewdog](https://github.com/reviewdog/reviewdog).

## Usage

```yaml
    - uses: tsubasaogawa/tfvdc-actions@v1
      with:
        input_path: ${{ github.workspace }}
        result_path: ${{ github.workspace }}/tfvdc.out
    - name: Run reviewdog
      env:
        REVIEWDOG_GITHUB_API_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      run: |
        cd ${{ github.workspace }}
        cat ${{ github.workspace }}/tfvdc.out | reviewdog -reporter=github-pr-review -f=golint
```

[Sample yaml file](https://github.com/tsubasaogawa/tfvdc-actions/blob/ae1a2233fc93ad821b0297db00e2fe2210ca04ed/.github/workflows/tfvdc.yml)

## Inputs

| Name        | Description                                             | Default     |
| ----------- | ------------------------------------------------------- | ----------- |
| input_path  | Input directory path contains Terraform variable blocks | .           |
| result_path | Result file path                                        | ~/tfvdc.out |

## Links

- <https://github.com/tsubasaogawa/terraform-variable-description-coverage>
