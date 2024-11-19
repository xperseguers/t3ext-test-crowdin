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
