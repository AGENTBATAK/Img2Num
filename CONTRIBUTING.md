# Contributing to Img2Num

Want to contribute to Img2Num? There are a few things you need to know.

We wrote a [contribution guide](https://img2num.dev/docs/contributing) to help you get started.

**A few important points:**

- **Add tests** with your PR — new features and bug fixes **must** include tests where appropriate. PRs without tests are unlikely to be approved.
- Follow the repository's coding style rules.
- Use the issue and PR templates when filing issues or submitting code. Your PR will be rejected if you don't.

If you're unsure what to change, [open a discussion](https://github.com/Ryan-Millard/Img2Num/discussions/new/choose) and someone will assist you.

## README Generation

The package README contains generated Node.js examples sourced from the canonical example applications in `example-apps/`.

When updating the ESM or CommonJS example applications, regenerate `packages/js/README.md` with:

```bash
pnpm readme:generate
```

The generated sections are marked with `BEGIN GENERATED` and `END GENERATED` comments. Do not edit the contents of those sections manually; update the canonical example source instead and regenerate the README.

All content outside these markers remains hand-written, including installation instructions, headings, explanations, browser examples, links, and package metadata. Generation replaces only the marked blocks and preserves the surrounding text. The output is ordinary fenced Markdown suitable for GitHub and npm.

To check synchronization without modifying any files:

```bash
pnpm readme:check
```

If the check fails, run `pnpm readme:generate` and commit the updated README alongside the source changes. CI runs the synchronization check and generator tests. The JavaScript release workflow checks before building, and the package's `prepublishOnly` hook checks before publishing from this repository. Keep the source examples and generator available when publishing; a copied package directory on its own cannot perform this check.

To add a generated example, add a uniquely named entry to `GENERATED_SECTIONS` in `scripts/generate-package-readme.mjs` with the repository-relative source path and code-fence language. Add matching `<!-- BEGIN GENERATED: name -->` and `<!-- END GENERATED: name -->` comments to `packages/js/README.md`, then regenerate. Use real runnable example files instead of duplicating code in the generator. Missing, reversed, duplicated, or nested markers cause generation to fail before writing the README.

The existing `.prettierignore` excludes README files so copied snippets stay faithful to their canonical sources. If enabling README formatting later, disable embedded code formatting for generated examples. The generator preserves the README's line endings and normalizes source line endings to match; Windows checkouts do not produce false synchronization failures.

To run the README generator tests:

```bash
pnpm readme:test
```

## Questions?

If you have questions or need help:
- Join our [Discord](https://discord.com/invite/BHjxcCqAnU)
- Check the [FAQ](https://img2num.dev/faq/) for answers to common questions.
- Open a [discussion](https://github.com/Ryan-Millard/Img2Num/discussions)
- Create an [issue](https://github.com/Ryan-Millard/Img2Num/issues)
- Check existing PRs for ideas

Thank you for improving Img2Num! 🎨🚀
