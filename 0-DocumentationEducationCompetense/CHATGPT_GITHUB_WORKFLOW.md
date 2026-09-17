# ChatGPT ↔ GitHub workflow for GMVA

This guide records the reusable workflow used to give ChatGPT access to the GMVA repository through a separate GitHub identity and then manage issue/branch/PR-based work.

## 1. Connect the GMVA GitHub identity

1. In ChatGPT, open **Settings → Plugins → GitHub**.
2. Under connected accounts, choose **Connect another account**.
3. Sign in to GitHub as **`tlindi`** and complete the requested authorization.
4. Give this ChatGPT connection the nickname **GMVA** so it can be distinguished from other GitHub connections.
5. Install/authorize **ChatGPT Codex Connector** for the `tlindi` GitHub account.
6. In the GitHub authorization/repository-access settings, grant the connector access to **`tlindi/Generic-model-of-value-addition`**.

The relationship is:

```text
ChatGPT
  └─ GitHub plugin / connection: "GMVA"
       └─ GitHub identity: tlindi
            └─ ChatGPT Codex Connector authorization
                 └─ repository access: tlindi/Generic-model-of-value-addition
```

The ChatGPT nickname selects the intended connected account; GitHub remains the authority for what that identity and connector may access.

## 2. Verify repository access

Before making changes, ask ChatGPT to use the **GMVA** GitHub connection and inspect `tlindi/Generic-model-of-value-addition`.

Verify that it can:

- identify the repository and default branch;
- read repository files;
- see repository issues and pull requests; and
- perform the required GitHub write actions.

If the repository is not visible, first check the GitHub connector's repository authorization rather than creating a different connection.

## 3. Use issue → branch → PR for implementation

For the GMVA Pages work, the concrete sequence was:

1. Create evaluation issue **#1**, defining the three-page GitHub Pages goal and evaluation criteria.
2. Create a dedicated implementation branch from `main`.
3. Add the three-page site under `/docs`.
4. Open implementation PR **#2** from that branch to `main`, linked to issue #1.
5. Leave the PR open for evaluation rather than merging immediately.

This separates the question **“is this the right implementation?”** from the act of merging it.

## 4. Evaluate and revise the same PR

The first HTML implementation was factually/content-wise correct, but its presentation was too conventional compared with the VIEPS three-page concept images.

The revised design requirement became:

> Recreate the VIEPS color mixed-media/zine visual language as real responsive HTML and CSS, not as flattened generated page images.

That means using magazine/zine composition, asymmetrical layouts, large typography, strong hierarchy, diagrams, explanatory blocks, annotations, callouts, equation cards, visual flows, contrasting panels and mixed-media character while preserving GMVA terminology and semantic HTML.

### Important Git rule

A pull request follows its **head branch**. To revise an existing PR, commit/push the new work to that same branch:

```text
issue #1
   ↓ defines/evaluates
implementation branch
   ↓ is the head branch of
PR #2
   ↓ automatically shows every new commit on that branch
```

Do **not** open a replacement PR merely because the design changed. Create a new PR only when a genuinely separate change or branch is intended.

## 5. Reuse this workflow

For similar work:

1. Select the correct named GitHub connection in ChatGPT.
2. Verify repository visibility and write access.
3. Open an issue describing the evaluation target and acceptance criteria.
4. Create one branch for the implementation.
5. Open one PR linked to the issue.
6. Review the result.
7. Iterate by committing to the same PR branch.
8. Merge only after the evaluation is accepted.

The account connection controls **which GitHub identity ChatGPT acts through**; GitHub authorization controls **which repositories that connection can reach**; the issue records **what is being evaluated**; the branch contains **the evolving implementation**; and the PR is the persistent **review boundary** for that branch.
