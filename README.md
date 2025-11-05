# Ethereum Improvement Proposals (EIPs)

> **_ATTENTION_**: The EIPs repository has recently [undergone](https://github.com/ethereum/EIPs/pull/7206) a separation of ERCs and EIPs. ERCs are now accessible at [https://github.com/ethereum/ercs](https://github.com/ethereum/ercs). All new ERCs and updates to existing ones must be directed at this new repository. The editors apologize for this inconvenience.

The goal of the EIP project is to standardize and provide high-quality documentation for Ethereum itself and conventions built upon it. This repository tracks past and ongoing improvements to Ethereum in the form of Ethereum Improvement Proposals (EIPs). [EIP-1](https://eips.ethereum.org/EIPS/eip-1) governs how EIPs are published.

The [status page](https://eips.ethereum.org/) tracks and lists EIPs, which can be divided into the following categories:

> **Note**: Each category serves a specific purpose in the Ethereum ecosystem and follows its own review process.

- [Core EIPs](https://eips.ethereum.org/core) are improvements to the Ethereum consensus protocol.
- [Networking EIPs](https://eips.ethereum.org/networking) specify the peer-to-peer networking layer of Ethereum.
- [Interface EIPs](https://eips.ethereum.org/interface) standardize interfaces to Ethereum, which determine how users and applications interact with the blockchain.
- [ERCs](https://eips.ethereum.org/erc) specify application layer standards, which determine how applications running on Ethereum can interact with each other.
- [Meta EIPs](https://eips.ethereum.org/meta) are miscellaneous improvements that nonetheless require some sort of consensus.
- [Informational EIPs](https://eips.ethereum.org/informational) are non-standard improvements that do not require any form of consensus.

**Before you write an EIP, ideas MUST be thoroughly discussed on [Ethereum Magicians](https://ethereum-magicians.org/) or [Ethereum Research](https://ethresear.ch/t/read-this-before-posting/8). Once consensus is reached, thoroughly read and review [EIP-1](https://eips.ethereum.org/EIPS/eip-1), which describes the EIP process.**

Please note that this repository is for documenting standards and not for help implementing them. These types of inquiries should be directed to the [Ethereum Stack Exchange](https://ethereum.stackexchange.com). For specific questions and concerns regarding EIPs, it's best to comment on the relevant discussion thread of the EIP denoted by the `discussions-to` tag in the EIP's preamble.

If you would like to become an EIP Editor, please read [EIP-5069](./EIPS/eip-5069.md).

### Referencing EIPs in Discussions

When discussing EIPs in forums, chat rooms, or social media, it's helpful to include a link to the canonical URL. This makes it easier for others to find and review the referenced proposal.

## Preferred Citation Format

The canonical URL for an EIP that has achieved draft status at any point is at <https://eips.ethereum.org/>. For example, the canonical URL for EIP-1 is <https://eips.ethereum.org/EIPS/eip-1>.

> **Tip**: Always use the canonical URL format when referencing EIPs in documentation, research papers, or technical articles.

Consider any document not published at <https://eips.ethereum.org/> as a working paper. Additionally, consider published EIPs with a status of "draft", "review", or "last call" to be incomplete drafts, and note that their specification is likely to be subject to change.

### Versioning

When citing EIPs, be aware that the content may change over time. For academic or formal citations, consider including the date of access or the commit hash if you need to reference a specific version.

When citing an EIP in academic or technical documentation, please use the canonical URL format for consistency and accessibility.

### Citation Examples

Here are some examples of how to cite EIPs:

**Academic Paper:**
```
Ethereum Improvement Proposal 1 (2024). Ethereum Improvement Proposals. 
Retrieved from https://eips.ethereum.org/EIPS/eip-1
```

**Technical Documentation:**
```
See EIP-1 (https://eips.ethereum.org/EIPS/eip-1) for more details on the EIP process.
```

**Markdown:**
```markdown
For more information, see [EIP-1](https://eips.ethereum.org/EIPS/eip-1).
```

### Citation Best Practices

- Always use the canonical URL from eips.ethereum.org
- Include the EIP number in your citation
- Link to the specific EIP rather than the general repository
- For draft EIPs, clearly indicate their status in your citation

## Validation and Automerging

All pull requests in this repository must pass automated checks before they can be automatically merged:

> **Note**: The validation process typically takes a few minutes. Please be patient while the checks complete.

- [eip-review-bot](https://github.com/ethereum/eip-review-bot/) determines when PRs can be automatically merged [^1]
- EIP-1 rules are enforced using [`eipw`](https://github.com/ethereum/eipw)[^2]
- HTML formatting and broken links are enforced using [HTMLProofer](https://github.com/gjtorikian/html-proofer)[^2]
- Spelling is enforced with [CodeSpell](https://github.com/codespell-project/codespell)[^2]
  - False positives sometimes occur. When this happens, please submit a PR editing [.codespell-whitelist](https://github.com/ethereum/EIPs/blob/master/config/.codespell-whitelist) and **ONLY** .codespell-whitelist
  - If you encounter a false positive, you can add the word to the whitelist following the existing format
- Markdown best practices are checked using [markdownlint](https://github.com/DavidAnson/markdownlint)[^2]

> **Important**: All automated checks must pass before a PR can be merged. Please ensure your changes comply with all validation rules.

[^1]: https://github.com/ethereum/EIPs/blob/master/.github/workflows/auto-review-bot.yml
[^2]: https://github.com/ethereum/EIPs/blob/master/.github/workflows/ci.yml

It is possible to run the EIP validator locally:

Make sure to add cargo's `bin` directory to your environment (typically `$HOME/.cargo/bin` in your `PATH` environment variable)

For Windows users, you may need to add the path to your system environment variables. For Linux and macOS users, you can add it to your shell profile (e.g., `~/.bashrc` or `~/.zshrc`).

```sh
cargo install eipw
eipw --config ./config/eipw.toml <INPUT FILE / DIRECTORY>
```

> **Tip**: Running the validator locally before submitting a PR can help catch issues early and speed up the review process.

### Validator Configuration

The validator uses a configuration file located at `./config/eipw.toml`. This file contains all the validation rules and settings. You can customize the validator behavior by modifying this configuration file.

### Common Validation Errors

Some common validation errors you might encounter:

- Missing required fields in EIP metadata
- Incorrect format for EIP numbers or titles
- Broken links or references
- Markdown formatting issues

### Running Validation on Specific Files

You can run the validator on specific files or directories:

```sh
eipw --config ./config/eipw.toml ./EIPS/eip-1.md
```

### Continuous Integration

The validator is also run automatically on all pull requests through GitHub Actions. This ensures all submissions meet the required standards before merging.

## Build the status page locally

### Install prerequisites

1. Open Terminal.

2. Check whether you have Ruby 3.1.4 installed. Later [versions are not supported](https://stackoverflow.com/questions/14351272/undefined-method-exists-for-fileclass-nomethoderror).

   ```sh
   ruby --version
   ```

3. If you don't have Ruby installed, install Ruby 3.1.4.

4. Install Bundler:

   ```sh
   gem install bundler
   ```

5. Install dependencies:

   ```sh
   bundle install
   ```

### Build your local Jekyll site

1. Bundle assets and start the server:

   ```sh
   bundle exec jekyll serve
   ```

2. Preview your local Jekyll site in your web browser at `http://localhost:4000`.

More information on Jekyll and GitHub Pages [here](https://docs.github.com/en/enterprise/2.14/user/articles/setting-up-your-github-pages-site-locally-with-jekyll).

### Troubleshooting

If you encounter issues while building the site locally, try:

- Checking your Ruby version matches the required version
- Ensuring all dependencies are installed correctly
- Clearing the Jekyll cache and rebuilding

## Contributing

We welcome contributions to improve the EIPs repository. Please ensure all pull requests follow the guidelines outlined in EIP-1 and pass all automated checks.

### Getting Started

If you're new to contributing to EIPs, here are some steps to get started:

1. Fork the repository
2. Create a new branch for your changes
3. Make your changes and test them locally
4. Submit a pull request with a clear description

### Code of Conduct

All contributors are expected to follow the project's code of conduct and maintain a respectful and inclusive environment.
