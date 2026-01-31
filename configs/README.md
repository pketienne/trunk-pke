# Configuration Notes

## markdownlint (.markdownlint.json)

**MD060 disabled**: dprint cannot handle multi-byte (Unicode) characters correctly when formatting tables with column alignment.

**Note**: Prettier cannot address most markdownlint rules - they are complementary tools, not interchangeable.

## dprint (dprint.json)

Uses a custom fork ([pketienne/dprint-plugin-markdown](https://github.com/pketienne/dprint-plugin-markdown)) that adds `autoLinkBareUrls` for MD034 (bare URL) support.
