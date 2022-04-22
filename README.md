## Workflow

- User checks out new branch from staging:
  - `<feat | fix | cicd | etc>/<name-of-feature>`
  - eg `feat/cool-new-feature`
- When ready for a review, make a PR => staging
  - Will trigger `.github/workflows/main.yml`
- When approved, merge into staging
  - Should trigger a new staging build on vercel
- When ready for a release, can do two options:
    - Create a release branch:
    	- eg `releases/release-RC-2`
    	- release branch points to `main`, since Vercel production points to main
   - Merge directly into `main`
   - Both of these will trigger a release:
     - bump the app version of the next tag (NOTE this does not bump the `package.json` in main) accoridng to the commit history
       - If commits include a breaking change, a major version will be bumped (eg `1.x.x` => `2.x.x`)
       - If commits include <INSERT LIST HERE>, a minor version will be bumped (eg `x.1.x` => `x.2.x`)
       - If commits include <INSERT LIST HERE>, a patch version will be bumped (eg `x.x.1` => `x.x.2`)
     - Github users who worked on the changes will be notified
     - Commit history will be compiled to Release notes under the tag number and release name

- first change
- second change
- third change
- fourth change