GIT SECRETS test
================


Adding a new password pattern:
git secrets --add 'MyPASSWORD[0-9]+'

Listing current patterns in **this** repository:
git secrets --list
```
secrets.patterns MyPASSWORD[0-9]+
```

Using as git pre-hook:
git secrets --install
```
✓ Installed commit-msg hook to .git/hooks/commit-msg
✓ Installed pre-commit hook to .git/hooks/pre-commit
✓ Installed prepare-commit-msg hook to .git/hooks/prepare-commit-msg
```

Example of output when detects any password pattern in the code:

```
git commit -m "update: trying error again"
index.js:1:const password=process.env.USER_PASSWORD || 'MyPASSWORD666';

[ERROR] Matched one or more prohibited patterns

Possible mitigations:
- Mark false positives as allowed using: git config --add secrets.allowed ...
- Mark false positives as allowed by adding regular expressions to .gitallowed at repository's root directory
- List your configured patterns: git config --get-all secrets.patterns
- List your configured allowed patterns: git config --get-all secrets.allowed
- List your configured allowed patterns in .gitallowed at repository's root directory
- Use --no-verify if this is a one-time false positive
```

Even more interesting:

Detecting password pattern in git history:
git secrets --scan-history

