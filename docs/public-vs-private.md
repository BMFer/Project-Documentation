# Public vs Private Documentation

## Overview

Understanding what information to share publicly versus keeping private is crucial for protecting your project, organization, and users while maintaining transparency. This guide helps you make informed decisions about documentation visibility.

## Table of Contents

- [Why This Matters](#why-this-matters)
- [Public Documentation](#public-documentation)
- [Private Documentation](#private-documentation)
- [Sensitive Information](#sensitive-information)
- [Security Considerations](#security-considerations)
- [Business Considerations](#business-considerations)
- [Decision Framework](#decision-framework)
- [GitHub Repository Settings](#github-repository-settings)
- [Best Practices](#best-practices)
- [Common Mistakes](#common-mistakes)
- [Transitioning Between Public and Private](#transitioning-between-public-and-private)

---

## Why This Matters

### Risks of Oversharing

**Security Risks**:
- Exposed credentials or API keys
- Revealed security vulnerabilities
- Disclosed internal infrastructure details
- Leaked authentication mechanisms

**Business Risks**:
- Competitive intelligence leakage
- Premature feature announcements
- Exposed business strategies
- Revealed customer information

**Legal Risks**:
- Privacy violations (GDPR, CCPA)
- Contract breaches (NDAs)
- Intellectual property exposure
- Compliance violations

### Benefits of Transparency

**For Open Source Projects**:
- Community trust and engagement
- Easier collaboration
- Faster bug discovery
- Knowledge sharing

**For All Projects**:
- Better documentation quality (public scrutiny)
- Reduced documentation duplication
- Improved onboarding
- Enhanced credibility

---

## Public Documentation

### What Should Be Public

#### ✅ Always Public

**Project Overview**:
- What the project does
- Why it exists
- Who it's for
- Key benefits and features
- General use cases

**Getting Started**:
- Installation instructions
- Basic configuration
- Quick start guides
- Prerequisites
- System requirements

**Usage Documentation**:
- Feature explanations
- API reference (for public APIs)
- Code examples
- Tutorials and guides
- Best practices

**Community Information**:
- Contributing guidelines
- Code of conduct
- License information
- Changelog
- Public roadmap (high-level)

**Support Resources**:
- FAQ
- Troubleshooting guides
- Community forums
- Issue templates
- Discussion guidelines

#### ✅ Often Public (Context-Dependent)

**Architecture Information**:
- High-level system design
- Technology stack overview
- Design patterns used
- Integration points (if public API)

**Development Processes**:
- Coding standards
- Testing approach
- Release process
- Documentation standards

**Project Management**:
- High-level roadmap
- Feature requests
- Bug reports (non-security)
- General milestones

### Public Documentation Examples

#### Public README.md
```markdown
# MyApp - Project Management Tool

A modern, collaborative project management application.

## Features
- Real-time collaboration
- Task management
- Team analytics
- Mobile apps

## Quick Start

### Installation
\`\`\`bash
npm install myapp
\`\`\`

### Basic Usage
\`\`\`javascript
const MyApp = require('myapp');
const app = new MyApp();
app.createProject('My First Project');
\`\`\`

## Documentation
Full documentation: https://docs.myapp.com

## Contributing
See [CONTRIBUTING.md](CONTRIBUTING.md)

## License
MIT
```

#### Public API Reference
```markdown
# Public API Reference

## Authentication
Use API keys for authentication. Get your key at https://myapp.com/api-keys

## Endpoints

### GET /api/v1/projects
List all projects for authenticated user.

**Request Headers**:
- `Authorization: Bearer YOUR_API_KEY`

**Response**:
\`\`\`json
{
  "projects": [
    {
      "id": "123",
      "name": "My Project",
      "created_at": "2025-01-01T00:00:00Z"
    }
  ]
}
\`\`\`

**Rate Limits**: 1000 requests/hour
```

#### Public Roadmap
```markdown
# Public Roadmap

## Vision
Become the leading collaborative project management platform.

## 2025 Goals

### Q1 2025
- [x] Mobile app launch
- [x] Real-time collaboration
- [ ] Advanced analytics (In Progress)

### Q2 2025
- Integration with Slack and Microsoft Teams
- Custom workflows
- Advanced reporting

### Later
- AI-powered insights
- Automation capabilities

*Note: This roadmap is subject to change based on user feedback and priorities.*
```

---

## Private Documentation

### What Should Stay Private

#### 🔒 Always Private

**Credentials and Secrets**:
- API keys and tokens
- Passwords and hashes
- Private keys and certificates
- Database connection strings
- OAuth client secrets
- Encryption keys
- Service account credentials

**Security Information**:
- Security vulnerabilities (until patched)
- Penetration test results
- Security audit reports
- Internal security procedures
- Incident response plans
- Disaster recovery plans

**Infrastructure Details**:
- Server IP addresses
- Internal network topology
- Database schemas with sensitive data
- Internal service URLs
- Backup locations
- Monitoring system details

**Business Sensitive**:
- Financial data
- Customer lists
- Pricing strategies
- Competitive analysis
- Contract terms
- Revenue/metrics
- Unannounced partnerships

**Personal Information**:
- Employee data
- Customer PII (Personally Identifiable Information)
- User analytics with identifiable data
- Internal communications
- Performance reviews

**Legal and Compliance**:
- Internal legal opinions
- Compliance documentation
- Audit trails with sensitive data
- Investigation reports
- Confidential agreements

#### 🔒 Usually Private (Context-Dependent)

**Detailed Architecture**:
- Internal service communication
- Database optimization details
- Caching strategies
- Load balancing configuration
- Failover mechanisms

**Development Details**:
- Sprint planning details
- Internal tool documentation
- Development environment configs
- Testing credentials
- Staging environment details

**Product Strategy**:
- Detailed feature specifications
- User research findings
- A/B test results
- Market research
- Competitive strategies

### Private Documentation Examples

#### Internal Architecture Document
```markdown
# Internal Architecture (CONFIDENTIAL)

## Infrastructure

### Production Environment
- Load Balancer: 10.0.1.10 (AWS ELB)
- App Servers: 10.0.2.10-13 (EC2 t3.large)
- Database: 10.0.3.10 (RDS PostgreSQL)
- Cache: 10.0.3.20 (ElastiCache Redis)

### Database Connection
\`\`\`
Host: prod-db.internal.myapp.com
User: app_user
Database: myapp_production
\`\`\`

### Security Groups
- SG-1234: Application tier
- SG-5678: Database tier

### Secrets Management
Secrets stored in AWS Secrets Manager:
- `prod/db/password`
- `prod/api/stripe_key`
- `prod/encryption/master_key`
```

#### Internal Runbook
```markdown
# Production Runbook (INTERNAL ONLY)

## Emergency Contacts
- On-call: PagerDuty rotation
- Database: db-team@internal.com
- Security: security@internal.com

## Database Failover Procedure
1. SSH to bastion: `ssh ops@bastion.internal.myapp.com`
2. Run failover script: `/opt/scripts/db-failover.sh`
3. Update DNS: [specific AWS console steps]
4. Notify in #incidents Slack channel

## Credentials
See 1Password vault: "Production Operations"
```

#### Customer Data Access Policy
```markdown
# Customer Data Access Policy (CONFIDENTIAL)

## Access Principles
- Minimum necessary access
- Just-in-time provisioning
- Audit all access
- Annual access reviews

## Who Can Access Customer Data
- Support engineers (with approval)
- Security team (incident response)
- Legal (with legal request)

## Access Procedure
1. Create ticket: [JIRA template]
2. Manager approval required
3. 72-hour time-bound access
4. All actions logged to security SIEM

## Compliance
This policy supports GDPR, CCPA, and SOC 2 requirements.
```

---

## Sensitive Information

### Categories of Sensitive Data

#### 1. Credentials
**What**: Anything used for authentication or authorization

**Examples**:
```bash
# NEVER COMMIT THESE
AWS_ACCESS_KEY_ID=AKIAIOSFODNN7EXAMPLE
AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
DATABASE_URL=postgresql://user:password@host:5432/db
STRIPE_SECRET_KEY=sk_live_51HqE...
ENCRYPTION_KEY=a3f8c9d2e1b4...
JWT_SECRET=my-super-secret-key
API_TOKEN=ghp_1234567890abcdef
```

**How to Handle**:
- ✅ Use environment variables
- ✅ Use secret management services (AWS Secrets Manager, HashiCorp Vault)
- ✅ Use `.env.example` with dummy values
- ✅ Add to `.gitignore`
- ❌ Never commit to Git
- ❌ Never include in documentation screenshots

#### 2. Internal URLs and Endpoints

**Private (Internal)**:
```
❌ https://admin.internal.myapp.com
❌ https://staging-db.myapp.internal
❌ http://10.0.1.50:8080/admin
❌ https://api.internal.myapp.com/debug
```

**Public (External)**:
```
✅ https://api.myapp.com
✅ https://docs.myapp.com
✅ https://www.myapp.com
```

#### 3. User Data

**Never Public**:
- Email addresses
- Phone numbers
- Physical addresses
- Payment information
- Social security numbers
- Medical information
- Behavioral analytics with PII

**Anonymized/Aggregated OK**:
```markdown
## User Statistics
- Total users: 10,000
- Active daily users: 3,500
- Average session length: 12 minutes

(No individual user data exposed)
```

#### 4. Business Metrics

**Private**:
```markdown
❌ Revenue: $1.2M MRR
❌ Churn rate: 3.5%
❌ Customer acquisition cost: $125
❌ Top 10 customers list
❌ Pricing negotiations with Partner X
```

**Public** (if you choose):
```markdown
✅ "Over 10,000 customers"
✅ "Trusted by Fortune 500 companies"
✅ "Processing millions of transactions monthly"
```

#### 5. Security Details

**Private**:
```markdown
❌ We use bcrypt with 12 rounds for password hashing
❌ Session tokens expire after 30 minutes
❌ Rate limiting: 100 req/min per IP
❌ Known vulnerability in authentication flow (pre-patch)
❌ Firewall rules for production servers
```

**Public** (General):
```markdown
✅ We use industry-standard encryption
✅ Sessions are securely managed
✅ Rate limiting protects against abuse
✅ Regular security audits performed
✅ Responsible disclosure program available
```

---

## Security Considerations

### .gitignore Best Practices

Create comprehensive `.gitignore`:

```bash
# Secrets and credentials
.env
.env.local
.env.*.local
*.pem
*.key
*.p12
*.pfx
config/secrets.yml
credentials.json

# System files
.DS_Store
Thumbs.db

# IDE files
.vscode/
.idea/
*.swp

# Dependencies
node_modules/
vendor/

# Build outputs
dist/
build/
*.log

# Database files
*.db
*.sqlite
*.sql

# Backup files
*.bak
*.tmp
~$*

# Environment specific
config/production.yml
config/local.yml
```

### Scanning for Secrets

**Pre-commit Hooks**:

Install `git-secrets`:
```bash
# Install
brew install git-secrets  # macOS
apt-get install git-secrets  # Linux

# Setup
git secrets --install
git secrets --register-aws
```

**GitHub Secret Scanning**:
- Automatically enabled for public repositories
- Available for private repos with GitHub Advanced Security
- Detects common secret patterns
- Notifies on detection

**Third-party Tools**:
- **TruffleHog**: Find secrets in Git history
- **GitGuardian**: Real-time secret detection
- **detect-secrets**: Yelp's secret scanner
- **gitleaks**: Fast secret scanner

**Example: Using TruffleHog**:
```bash
# Install
pip install truffleHog

# Scan repository
truffleHog --regex --entropy=False https://github.com/user/repo
```

### Secret Rotation

**If Secret is Exposed**:

1. **Immediate Actions**:
   - Revoke the compromised credential immediately
   - Generate new credential
   - Update all systems using it
   - Monitor for unauthorized access

2. **Remove from Git History**:
   ```bash
   # Using BFG Repo-Cleaner (recommended)
   bfg --replace-text passwords.txt repo.git
   git reflog expire --expire=now --all
   git gc --prune=now --aggressive

   # Push changes
   git push --force
   ```

3. **Notification**:
   - Notify security team
   - Document incident
   - Review access logs
   - Consider notifying affected users (if applicable)

### Environment Variables

**Instead of hardcoding**:
```javascript
// ❌ BAD
const apiKey = 'sk_live_51HqE2KLOp5...';

// ✅ GOOD
const apiKey = process.env.STRIPE_API_KEY;
```

**Document in README** (without actual values):
```markdown
## Environment Variables

Create a `.env` file:

\`\`\`bash
# API Keys
STRIPE_API_KEY=your_stripe_key_here
SENDGRID_API_KEY=your_sendgrid_key_here

# Database
DATABASE_URL=postgresql://user:password@localhost:5432/dbname

# Application
NODE_ENV=development
PORT=3000
\`\`\`

See `.env.example` for template.
```

**Provide .env.example**:
```bash
# .env.example - Safe to commit
STRIPE_API_KEY=sk_test_XXXXXXXXXXXXXXXXXXXXXXXX
SENDGRID_API_KEY=SG.XXXXXXXXXXXXXXXXXXXXXXXX
DATABASE_URL=postgresql://user:password@localhost:5432/myapp_dev
NODE_ENV=development
PORT=3000
```

---

## Business Considerations

### Competitive Intelligence

**What Competitors Can Learn from Public Docs**:
- Your technology stack
- Feature roadmap
- Customer base size
- Integration partners
- Pricing structure (if documented)
- Development velocity
- Team size (from commits)

**Protecting Competitive Advantage**:

**Public** (general):
```markdown
## Technology Stack
- Modern web technologies
- Cloud-based infrastructure
- Scalable architecture
```

**Private** (specific):
```markdown
## Technology Stack
- React 18.2 with Next.js 14
- Node.js 20 with Express
- PostgreSQL 15 with TimescaleDB
- Redis 7 for caching
- Deployed on AWS EKS with Fargate
- Using DataDog for monitoring
```

### Intellectual Property

**Patent-Pending Features**:
```markdown
# ❌ Don't document publicly before patent filing:
"We use a novel algorithm that combines X, Y, and Z
to achieve 10x performance improvement..."

# ✅ After patent filing or if not patenting:
"Advanced optimization techniques provide
significant performance improvements."
```

**Proprietary Algorithms**:
- Don't publish detailed implementations
- Provide high-level descriptions
- Document public APIs, not internal logic

### Partnership Considerations

**Before Public Announcement**:
```markdown
❌ "Upcoming integration with Microsoft Teams"
❌ "Partnership with Salesforce coming Q2"
```

**After Public Announcement**:
```markdown
✅ "Now integrates with Microsoft Teams"
✅ "Salesforce integration available"
```

**In Private Docs**:
```markdown
## Partner Integration Roadmap (CONFIDENTIAL)

Q1 2025:
- Finalize Microsoft Teams integration (under NDA)
- Begin Salesforce discussions

Q2 2025:
- Public launch of Teams integration
- Announce Salesforce partnership
```

### Customer Confidentiality

**Case Studies** - Get permission:
```markdown
# ❌ Without permission
"Acme Corp uses our platform to manage 10,000 projects
and has reduced costs by 30%."

# ✅ With permission (or anonymized)
"A Fortune 500 manufacturing company uses our platform
to manage thousands of projects, reducing costs by 30%."
```

**Customer Lists**:
- ❌ Never publish full customer lists without consent
- ✅ "Trusted by over 500 companies"
- ✅ Logo wall with permission
- ✅ Anonymous usage statistics

---

## Decision Framework

### The Decision Matrix

| Information Type | Public | Private | Depends On |
|-----------------|--------|---------|------------|
| Installation guide | ✅ | | |
| API reference (public API) | ✅ | | |
| Internal API docs | | ✅ | |
| High-level roadmap | ✅ | | |
| Detailed sprint plans | | ✅ | |
| Technology stack (general) | ✅ | | |
| Infrastructure details | | ✅ | |
| Bug reports (non-security) | ✅ | | Security impact |
| Security vulnerabilities | | ✅ | Until patched |
| User metrics (aggregated) | ✅ | | Business strategy |
| User data (individual) | | ✅ | |
| Contributing guidelines | ✅ | | |
| Internal processes | | ✅ | |
| License | ✅ | | |
| Customer contracts | | ✅ | |

### Questions to Ask

Before making documentation public, ask:

**Security**:
1. ❓ Could this help an attacker?
2. ❓ Does it reveal security mechanisms?
3. ❓ Does it contain credentials or secrets?
4. ❓ Could it expose infrastructure?

**Privacy**:
1. ❓ Does it contain personal information?
2. ❓ Could individuals be identified?
3. ❓ Does it comply with GDPR/CCPA?
4. ❓ Have affected parties consented?

**Business**:
1. ❓ Could this help competitors?
2. ❓ Does it reveal unannounced plans?
3. ❓ Does it expose financial data?
4. ❓ Could it violate NDAs or contracts?

**Legal**:
1. ❓ Is this protected by copyright/patent?
2. ❓ Does it contain proprietary information?
3. ❓ Could it create legal liability?
4. ❓ Does it meet compliance requirements?

**Practical**:
1. ❓ Will users benefit from this being public?
2. ❓ Could it improve community engagement?
3. ❓ Is there a reason to keep it private?
4. ❓ What's the worst case if it's public?

**If unsure**: Start private, make public later if appropriate.

---

## GitHub Repository Settings

### Repository Visibility

**Public Repository**:
```
Settings → General → Danger Zone → Change repository visibility
→ Make public
```

**Benefits**:
- Community contributions
- Free GitHub features (Actions, Pages)
- Increased visibility
- Open source collaboration

**Considerations**:
- Everything is visible
- Git history is public
- Issues/PRs are public
- Can't hide information selectively

**Private Repository**:
```
Settings → General → Danger Zone → Change repository visibility
→ Make private
```

**Benefits**:
- Control access
- Keep code confidential
- Selective sharing
- Internal collaboration

**Considerations**:
- Paid feature (for organizations)
- Less community engagement
- Limited external contributions

### Managing Access (Private Repos)

**Add Collaborators**:
```
Settings → Collaborators and teams → Add people
```

**Permission Levels**:
- **Read**: View and clone
- **Triage**: Read + manage issues/PRs
- **Write**: Triage + push to repo
- **Maintain**: Write + manage repo settings
- **Admin**: Full access

**Organization Teams**:
```
Organization → Teams → New team
→ Assign repositories and permissions
```

### Branch Protection

**Protect Sensitive Branches**:
```
Settings → Branches → Add branch protection rule
```

**Recommended Settings**:
- ✅ Require pull request reviews
- ✅ Require status checks to pass
- ✅ Require conversation resolution before merging
- ✅ Restrict who can push to matching branches
- ✅ Require signed commits

### GitHub Features by Repo Type

| Feature | Public | Private Free | Private Paid |
|---------|--------|--------------|--------------|
| Issues | ✅ | ✅ | ✅ |
| Pull Requests | ✅ | ✅ | ✅ |
| GitHub Pages | ✅ | ❌ | ✅ |
| GitHub Actions | ✅ (2000 min/mo) | ✅ (2000 min/mo) | ✅ (3000 min/mo) |
| Secret Scanning | ✅ | ❌ | ✅ |
| Dependency Scanning | ✅ | ❌ | ✅ |
| Code Owners | ✅ | ❌ | ✅ |

---

## Best Practices

### For Public Documentation

**Do**:
- ✅ Use `.env.example` for configuration templates
- ✅ Document public APIs thoroughly
- ✅ Provide clear contributing guidelines
- ✅ Include code of conduct
- ✅ Use issue templates
- ✅ Link to security policy
- ✅ Keep README concise and welcoming
- ✅ Respond to community feedback

**Don't**:
- ❌ Include real credentials (even expired ones)
- ❌ Publish security vulnerabilities before fixing
- ❌ Share customer data without permission
- ❌ Reveal internal infrastructure
- ❌ Document features before announcement
- ❌ Include personally identifiable information

### For Private Documentation

**Do**:
- ✅ Document internal processes thoroughly
- ✅ Include runbooks and troubleshooting
- ✅ Maintain access controls
- ✅ Regular review of who has access
- ✅ Use separate repositories for sensitive docs
- ✅ Encrypt sensitive documentation
- ✅ Audit access to private docs

**Don't**:
- ❌ Over-classify (don't make everything private)
- ❌ Share credentials in documentation
- ❌ Assume private means "don't document"
- ❌ Forget to update access when people leave
- ❌ Mix public and private content in same repo

### Dual Documentation Strategy

**Maintain Both**:

```
company-docs/
├── public-docs/          # Public repository
│   ├── README.md
│   ├── docs/
│   │   ├── getting-started.md
│   │   ├── api-reference.md
│   │   └── user-guide.md
│   └── examples/
│
└── internal-docs/        # Private repository
    ├── architecture/
    │   ├── infrastructure.md
    │   ├── database-schema.md
    │   └── security-setup.md
    ├── runbooks/
    │   ├── deployment.md
    │   ├── incident-response.md
    │   └── database-recovery.md
    └── processes/
        ├── onboarding.md
        ├── security-review.md
        └── release-checklist.md
```

**Cross-linking**:

In public docs:
```markdown
## Architecture

For a high-level overview, see our architecture decisions.

For detailed infrastructure documentation, see internal wiki.
(Internal team members: link to private docs)
```

### Documentation Reviews

**Before Publishing**:

1. **Automated Scanning**:
   ```bash
   # Scan for secrets
   truffleHog --regex --entropy=False .

   # Scan for email addresses
   grep -r '@company.com' .

   # Scan for IP addresses
   grep -rE '\b([0-9]{1,3}\.){3}[0-9]{1,3}\b' .
   ```

2. **Manual Review Checklist**:
   - [ ] No credentials or secrets
   - [ ] No internal URLs or IPs
   - [ ] No personal information
   - [ ] No unpublished features
   - [ ] No proprietary algorithms
   - [ ] No customer-specific information
   - [ ] Links work
   - [ ] Code examples tested
   - [ ] Screenshots don't reveal sensitive data

3. **Peer Review**:
   - Have another team member review
   - Security team review for sensitive topics
   - Legal review if needed

---

## Common Mistakes

### Mistake #1: Committing Secrets

**Problem**:
```bash
git commit -m "Add API integration"
# Accidentally committed .env file with real credentials
```

**Prevention**:
- Proper `.gitignore`
- Pre-commit hooks
- Secret scanning
- Code review

**Fix** (if caught immediately):
```bash
# Remove from last commit
git reset --soft HEAD~1
git reset HEAD .env
git commit -m "Add API integration"
```

**Fix** (if already pushed):
```bash
# Remove from history
bfg --delete-files .env
git push --force
# THEN: Rotate all exposed credentials immediately
```

### Mistake #2: Screenshots with Sensitive Data

**Problem**:
```markdown
## Dashboard Overview
![Dashboard](screenshot.png)
```

Screenshot shows:
- Real customer names
- Email addresses
- Internal URLs
- API keys in browser dev tools

**Prevention**:
- Use dummy/test data
- Blur sensitive information
- Use separate demo environment
- Review screenshots before committing

### Mistake #3: Detailed Error Messages

**Public Docs** (❌ Bad):
```markdown
## Troubleshooting

If you see error "Database connection failed":
- Check that PostgreSQL is running on db.internal.company.com:5432
- Verify username 'app_user' has correct permissions
- Ensure password matches value in Vault path 'prod/db/password'
```

**Public Docs** (✅ Good):
```markdown
## Troubleshooting

If you see "Database connection failed":
- Check database server is running
- Verify connection credentials
- Ensure user has correct permissions
- See configuration guide for setup details
```

### Mistake #4: Oversharing in Git History

**Problem**:
```bash
git log
# commit abc123
# "Update config with production database credentials"
```

Even if file is removed, commit message reveals sensitive info.

**Prevention**:
- Review commit messages
- Avoid mentioning sensitive details
- Use generic descriptions for security changes

### Mistake #5: Public Issue Tracker for Security

**Problem**:
```markdown
GitHub Issue #123
Title: "SQL Injection vulnerability in login endpoint"
Description: "The login endpoint doesn't sanitize input..."
```

**Prevention**:
- Use private security reporting
- GitHub Security Advisories
- Dedicated security email
- Bug bounty platform (if applicable)

**Proper Approach**:
```markdown
SECURITY.md:

## Reporting Security Vulnerabilities

Please do NOT report security vulnerabilities as GitHub issues.

Instead, email: security@company.com

Include:
- Description of vulnerability
- Steps to reproduce
- Potential impact
```

---

## Transitioning Between Public and Private

### Making a Private Repo Public

**Before Making Public**:

1. **Audit Git History**:
   ```bash
   # Search for common secret patterns
   git log -p | grep -i "password"
   git log -p | grep -i "api.key"
   git log -p | grep -i "secret"

   # Use automated tools
   truffleHog --regex --entropy=True .
   ```

2. **Review All Files**:
   ```bash
   # Check for sensitive files
   find . -name "*.env*"
   find . -name "*secret*"
   find . -name "*credential*"
   find . -name "config/*.yml"
   ```

3. **Clean Sensitive Data**:
   ```bash
   # Remove sensitive files from history
   bfg --delete-files sensitive-file.txt
   bfg --replace-text passwords.txt

   git reflog expire --expire=now --all
   git gc --prune=now --aggressive
   ```

4. **Update Documentation**:
   - Remove internal URLs
   - Remove employee names (if sensitive)
   - Remove customer references
   - Genericize examples

5. **Final Checklist**:
   - [ ] All secrets removed from history
   - [ ] .gitignore is comprehensive
   - [ ] README is public-friendly
   - [ ] No internal URLs or IPs
   - [ ] License added
   - [ ] Contributing guide added
   - [ ] Code of conduct added
   - [ ] Security policy added

6. **Make Public**:
   ```
   Settings → General → Danger Zone
   → Change repository visibility → Make public
   ```

### Making a Public Repo Private

**Reasons**:
- Security concerns discovered
- Business strategy change
- Proprietary development
- Privacy requirements

**Process**:

1. **Communicate Change**:
   ```markdown
   # Announcement
   We're transitioning this project to private development.

   Reason: [Brief explanation]

   Forks: Existing forks will remain available

   Questions: contact@company.com
   ```

2. **Export Public Issues/PRs** (if needed):
   ```bash
   # Use GitHub CLI
   gh issue list --state all --limit 1000 > issues.csv
   gh pr list --state all --limit 1000 > prs.csv
   ```

3. **Make Private**:
   ```
   Settings → General → Danger Zone
   → Change repository visibility → Make private
   ```

4. **Note**: Existing forks remain public!

**Handling Forks**:
- You cannot delete others' forks
- Contact fork owners if necessary
- Consider DMCA takedown only if truly necessary (legal implications)

---

## Summary Checklist

### Public Documentation ✅
- [ ] Installation and setup guides
- [ ] Public API documentation
- [ ] Usage examples
- [ ] Contributing guidelines
- [ ] License
- [ ] Code of conduct
- [ ] Security policy
- [ ] FAQ
- [ ] High-level roadmap
- [ ] Community resources

### Private Documentation 🔒
- [ ] Credentials and secrets
- [ ] Infrastructure details
- [ ] Security procedures
- [ ] Customer data
- [ ] Financial information
- [ ] Internal processes
- [ ] Detailed architecture
- [ ] Incident response plans
- [ ] Employee information
- [ ] Unannounced features

### Security Practices 🛡️
- [ ] Comprehensive .gitignore
- [ ] Secret scanning enabled
- [ ] Pre-commit hooks configured
- [ ] Environment variables for secrets
- [ ] .env.example provided
- [ ] Regular security audits
- [ ] Access reviews
- [ ] Incident response plan

---

## Resources

### Tools

**Secret Scanning**:
- [git-secrets](https://github.com/awslabs/git-secrets)
- [TruffleHog](https://github.com/trufflesecurity/truffleHog)
- [GitGuardian](https://www.gitguardian.com/)
- [detect-secrets](https://github.com/Yelp/detect-secrets)
- [gitleaks](https://github.com/gitleaks/gitleaks)

**Secret Management**:
- AWS Secrets Manager
- HashiCorp Vault
- Azure Key Vault
- Google Secret Manager
- 1Password Teams

**Documentation**:
- [GitHub Docs - Managing Security](https://docs.github.com/en/code-security)
- [OWASP - Secrets Management](https://owasp.org/www-community/vulnerabilities/Use_of_hard-coded_password)

### Further Reading

- [GitHub Security Best Practices](https://docs.github.com/en/code-security/getting-started/best-practices-for-preventing-data-leaks-in-your-organization)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [GDPR Compliance Guide](https://gdpr.eu/)
- [Open Source Security Foundation](https://openssf.org/)

---

**Last Updated**: October 17, 2025
**Version**: 1.0

**Classification**: Public
