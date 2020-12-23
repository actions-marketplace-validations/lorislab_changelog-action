# changelog-action

Github action for [changelog](https://github.com/lorislab/changelog).

Create a release and close the version. 
```yaml
name: release
on:
  push:
    tags:
      - '**'
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1
      - name: Create release
        uses: lorislab/changelog-action@v1
        with:
          args: generate --create-release --close-version --file .github/changelog.yaml
        env:
          CHANGELOG_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
The optional changelog definition is in the `.github/changelog.yaml` file.
```yaml
sections:
  - title: Major changes
    labels: 
      - "release/super-fearure"
  - title: Complete changelog
    labels: 
      - "bug"
      - "enhancement"
template: |
  Descrition
  {{ range $section := .Sections }}{{ if $section.Items }}### {{ $section.GetTitle }}{{ range $item := $section.Items }}
  * [#{{ $item.GetID }}]({{ $item.GetURL }}) - {{ $item.GetTitle }}{{ end }}{{ end }}
  {{ end }}
```

Show changelog in the console
```yaml
- name: Show changelog
  id: example
  uses: lorislab/changelog-action@v1
  with:
    args: generate --console -v debug
  env:
    CHANGELOG_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
or only create a `Github` release
```yaml
- name: Show changelog
  id: example
  uses: lorislab/changelog-action@v1
  with:
    args: generate --create-release
  env:
    CHANGELOG_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```