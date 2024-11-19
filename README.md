# Test Crowdin

This is a test project to test the integration of this pseudo-TYPO3 extension into Crowdin.

Some notes about the structure of translation files in this extension. The extension is
holding both the original English language files and the French and German translations.
To do so, the English language files are stored in the `Resources/Private/Language` directory
as `locallang.xlf` and `locallang_db.xlf` files. The French and German translation files are
stored in **the same directory**, prefixed with the language code, as `fr.locallang.xlf` and
`fr.locallang_db.xlf`, respectively as `de.locallang.xlf` and `de.locallang_db.xlf` files.

At that point, we want to integrate the extension into Crowdin and make sure that the
existing translations are correctly imported into Crowdin, then removed from the extension
repository so that the translations are managed in Crowdin and only the English language
files are kept in the extension repository.

## GitHub Integration

The configuration steps are originally described in the
[Crowdin documentation](https://support.crowdin.com/github-integration/) but have been
adapted to the TYPO3 extension development workflow.

### Step 1: Create a Crowdin Configuration File

Within your TYPO3 extension repository, create a `.crowdin.yml` file at root with the
following content:

```yaml
"preserve_hierarchy": true
"files": [
  {
    "source": "/Resources/Private/Language/*.xlf",
    "translation": "/%original_path%/%two_letters_code%.%original_file_name%",
    "ignore": [
      "/**/%two_letters_code%.%original_file_name%"
    ]
  }
]
```

### Step 2: Set Up the Project in Crowdin

Get in touch with the team in the TYPO3 Slack channel `#typo3-translations` with the
following information:

1. Extension name
2. Your email address for an invitation to Crowdin, so you will get the correct role for
   your project.

Once done, you will receive an email invitation to join the Crowdin project for your
extension.

### Step 3: Configure the GitHub Integration

In the Crowdin project settings, go to the Integrations tab and click on the button
"Browse Integrations", then choose "GitHub". Follow the instructions to connect your
GitHub repository to Crowdin.

Once installed, the Integrations tab will show the GitHub integration with a button
to "Set Up Integration". Click on it and choose the mode "Source and translation files mode".

At this point, Crowdin will request additional permissions to access your repository.
You should accept the default permissions and click on the "Authorize crowdin" button.

Then follow the instructions to configure the integration:

1. Select the repository from the list of your GitHub repositories.
2. Select the branch to use for synchronization (usually `main` or `master`).
   - When ticking the branch, Crowdin will suggest a "Service Branch Name"
     `l10n_main` (or `l10n_master`), which is the branch where Crowdin will push
     the translations. You can keep the default value.
3. Click the pencil icon next to the Service Branch Name to edit configuration.
4. When asked for the Configuration file name, change it from `crowdin.yml` to
   `.crowdin.yml` and click "Continue". This will effectively use the configuration
   we created in step 1 and ensure that everything is properly configured for your
   TYPO3 extension.
5. Click the "Save" button to save the configuration.
6. Back to the main GitHub integration page, you should see a circled checkmark next
   to the Service Branch Name, indicating that the integration is correctly set up.
7. Ensure the checkbox "One-time translation import after the branch is connected" is
   ticked.
8. Do not tick the checkbox "Push Sources" as the sources are already in the repository
   and changes are managed within the extension repository **and not in Crowdin**.
9. Click the "Save" button to save the configuration of the integration. 