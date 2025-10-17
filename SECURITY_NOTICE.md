# Security Notice for Documentation Repository

## Educational Content Warning

This repository contains **educational documentation** that includes **examples of sensitive data patterns**. These examples are designed to teach developers what types of information should never be committed to real repositories.

## All Examples Are Placeholders

**IMPORTANT**: All credentials, API keys, tokens, and sensitive data shown in this repository are:

- ✅ **Placeholder values** (e.g., `sk_test_XXXXXXXXXXXXXXXXXXXXXXXX`)
- ✅ **Official example keys** (e.g., AWS's `AKIAIOSFODNN7EXAMPLE`)
- ✅ **Dummy/fake credentials** for illustration purposes
- ✅ **Educational examples** showing what NOT to do

**They are NOT**:
- ❌ Real, working credentials
- ❌ Valid API keys
- ❌ Actual secrets that need protection
- ❌ Security vulnerabilities

## Purpose of Examples

The examples in files like `docs/public-vs-private.md` serve to:

1. **Teach recognition** - Help developers identify what sensitive data looks like
2. **Show patterns** - Demonstrate common formats of credentials and secrets
3. **Illustrate risks** - Show what happens when secrets are committed
4. **Provide contrast** - Show proper vs. improper documentation practices

## Secret Scanning Alerts

If you receive secret scanning alerts for this repository:

### Expected Alerts (False Positives)

The following alerts are **expected and safe** in this educational context:

- **Stripe API keys**: Examples use test key format `sk_test_XXXXXXXXXXXXXXXXXXXXXXXX`
- **AWS credentials**: Using AWS's official example credentials ending in "EXAMPLE"
- **Generic tokens**: Placeholder patterns like `ghp_1234567890abcdef`
- **Database URLs**: Example connection strings with `user:password@localhost`
- **API keys**: Generic patterns for illustration

### Handling Alerts

1. **Review the file**: Check if it's in documentation/examples
2. **Verify it's a placeholder**: Look for "EXAMPLE", "XXXXXXX", "placeholder", "dummy"
3. **Check context**: Is it in a code comment explaining what NOT to do?
4. **If unsure**: Contact the repository maintainers

### Configuration Files

This repository includes:
- `.gitallowed` - Lists allowed educational examples
- `.gitleaksignore` - Configures GitLeaks to ignore educational content
- `.secretsignore` - Configures git-secrets to ignore teaching examples

## For Repository Maintainers

When adding new educational examples:

1. **Use obvious placeholders**:
   ```
   ✅ STRIPE_KEY=sk_test_XXXXXXXXXXXXXXXXXXXXXXXX
   ✅ AWS_KEY=AKIAIOSFODNN7EXAMPLE
   ❌ STRIPE_KEY=sk_test_4eC39HqLyjWDarjtT1zdp7dc (looks real)
   ```

2. **Add clear context**:
   ```markdown
   <!-- Educational Example - NOT REAL CREDENTIALS -->
   Example API key that should NEVER be committed:
   sk_test_XXXXXXXXXXXXXXXXXXXXXXXX
   ```

3. **Use official examples** when available:
   - AWS provides official example credentials
   - Stripe provides test mode key patterns
   - Use these instead of inventing new ones

4. **Update ignore files** if adding new patterns

## For Students/Learners

When using this repository to learn:

1. **Understand the examples** - These show what to avoid in YOUR projects
2. **Never use these patterns** - Don't copy-paste these into real projects
3. **Learn to recognize** - Train your eye to spot sensitive data
4. **Apply the lessons** - Use `.gitignore`, environment variables, and secret management in your own work

## Real Security Practices

This repository teaches that you should:

- ✅ Use environment variables for credentials
- ✅ Keep secrets out of version control
- ✅ Use `.gitignore` to prevent credential commits
- ✅ Use secret management services (AWS Secrets Manager, Vault, etc.)
- ✅ Scan your repositories for accidentally committed secrets
- ✅ Rotate credentials if exposed

## Reporting Real Security Issues

If you find an **actual security issue** in this repository (not an educational example):

- **Email**: security@example.com (replace with actual contact)
- **Don't**: Open a public GitHub issue
- **Do**: Follow responsible disclosure practices

## Questions?

If you're unsure whether something is an educational example or a real security issue:

1. Check the file location (docs/, examples/, whitepapers/)
2. Look for context comments
3. Verify against this SECURITY_NOTICE.md
4. When in doubt, contact the maintainers

## Summary

🎓 **This is an educational repository**
📚 **Examples teach what NOT to do**
🔒 **All credentials are fake/placeholders**
✅ **Secret scanning alerts are expected and safe**

---

**Last Updated**: October 17, 2025
**Maintained by**: Project Documentation Team
