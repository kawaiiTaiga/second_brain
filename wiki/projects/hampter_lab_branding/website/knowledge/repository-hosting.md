# Repository Hosting

## GitHub

- Owner: `kawaiiTaiga`
- Repository: `hampter-lab`
- Default branch: `main`
- Remote name: `origin`
- Repository URL: <https://github.com/kawaiiTaiga/hampter-lab>
- Clone URL: `https://github.com/kawaiiTaiga/hampter-lab.git`

## Deployment

- Platform: `Vercel`
- Production URL: <https://hampterlab.vercel.app>
- Vercel project name: `hampter_lab`
- GitHub pushes to `origin/main` are expected to trigger redeploys
- Manual production deploys have also been performed with `npx vercel --prod --yes`

## Operational Notes

- The website is the current public HAMPTER LAB brand surface.
- The TAIGA face runtime lives inside this same site at `/makes/taiga_face/` instead of using a separate site deployment.
- If deployment and live content disagree, verify both the GitHub push and the Vercel production alias state.
- `hampter-lab` is the showcase repository, not the source-of-truth repository for every underlying project experiment.
- Project repos such as `https://github.com/kawaiiTaiga/taiga` may exist separately and should not be treated as automatic website updates.
- Default deployment path is `git push` to `origin/main`; do not pair every push with a manual Vercel production deploy.
- Use manual `npx vercel --prod --yes` only when Git-triggered production deployment fails, the alias is stale, or production content does not match the latest pushed commit.
- Repeated duplicate deploys are operationally unnecessary and consume Vercel usage limits faster.

