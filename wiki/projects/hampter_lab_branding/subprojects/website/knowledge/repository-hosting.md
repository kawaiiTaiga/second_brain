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
- The TAIGA face runtime lives inside this same site at `/taiga/` instead of using a separate site deployment.
- If deployment and live content disagree, verify both the GitHub push and the Vercel production alias state.
