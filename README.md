# DbProof with Prisma Migrate

An example of [DbProof](https://dbproof.dev/prisma) checking Prisma migrations against production’s schema and statistics.

- `prisma/` is a small app: invoices, where `dueDate` is optional.
- [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml) stands in for production. It applies the migrations to a Postgres in the job, fills it with 200,000 invoices, every 300th without a due date, and captures it with [`dbproof/capture-action`](https://github.com/marketplace/actions/dbproof-capture).
- The workflows DbProof’s setup pull request added check every pull request that changes `prisma/migrations`, with [`dbproof/check-action`](https://github.com/marketplace/actions/dbproof-check).

See the pull requests for checks in action. The [blog post](https://dbproof.dev/blog/prisma-not-null-migration) explains the `SET NOT NULL` case.
