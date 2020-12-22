# changelog-action

Changelog github action

Show changelog
```yaml
- name: Show changelog
  id: example
  uses: lorislab/changelog-action@v0.1.0
  with:
    args: generate --console -v debug
  env:
    CHANGELOG_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

Create a release
```yaml
- name: Show changelog
  id: example
  uses: lorislab/changelog-action@v0.1.0
  with:
    args: generate --create-release
  env:
    CHANGELOG_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

Create a release and close the version
```yaml
- name: Show changelog
  id: example
  uses: lorislab/changelog-action@v0.1.0
  with:
    args: generate --create-release --close-version
  env:
    CHANGELOG_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```