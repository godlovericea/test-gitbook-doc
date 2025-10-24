# Installation

Complete installation guide for setting up this test documentation.

## 🛠️ Installation Options

You have several options for working with this documentation:

### Option 1: View on GitBook (Recommended)

The easiest way is to view the documentation on GitBook:

1. Visit the GitBook site (URL will be provided after setup)
2. No installation required!
3. Search and AI features available

### Option 2: Local Development

For contributors or those who want to edit locally:

```bash
# Clone the repository
git clone https://github.com/godlovericea/test-gitbook-doc.git

# Navigate to the directory
cd test-gitbook-doc

# Edit with your favorite editor
code .
```

### Option 3: GitBook CLI (Advanced)

Install GitBook CLI for local preview:

```bash
# Install GitBook CLI globally
npm install -g gitbook-cli

# Initialize GitBook
cd test-gitbook-doc
gitbook install

# Serve locally
gitbook serve

# Build static site
gitbook build
```

The local server will be available at `http://localhost:4000`

## 📦 System Requirements

### For Viewing
- Any modern web browser
- Internet connection

### For Local Development
- Git 2.x or higher
- Text editor (VS Code, Sublime Text, etc.)
- Node.js 12+ (for GitBook CLI)

## 🔧 Configuration

### GitBook Configuration File

The `.gitbook.yaml` file controls GitBook behavior:

```yaml
root: ./

structure:
  readme: README.md
  summary: SUMMARY.md

redirects:
  previous: ./
```

### Directory Structure

```
test-gitbook-doc/
├── .gitbook.yaml      # GitBook configuration
├── README.md          # Home page (required)
├── SUMMARY.md         # Navigation menu (required)
├── getting-started/   # Getting started section
│   ├── quick-start.md
│   └── installation.md
├── guides/            # Guides section
│   ├── basic-guide.md
│   └── advanced-topics.md
└── api/               # API documentation
    ├── overview.md
    └── authentication.md
```

## ✅ Verification

After installation, verify everything works:

1. **Check Git**
   ```bash
   git --version
   ```

2. **Check Node.js** (if using CLI)
   ```bash
   node --version
   npm --version
   ```

3. **Test GitBook CLI** (if installed)
   ```bash
   gitbook --version
   ```

## 🐛 Troubleshooting

### Common Issues

#### Issue: GitBook CLI installation fails

**Solution:**
```bash
# Clear npm cache
npm cache clean --force

# Try installing again
npm install -g gitbook-cli
```

#### Issue: Port 4000 already in use

**Solution:**
```bash
# Use a different port
gitbook serve --port 4001
```

#### Issue: GitBook not detecting configuration

**Solution:**
- Ensure `.gitbook.yaml` is in the root directory
- Check YAML syntax (no tabs, proper indentation)
- Verify `README.md` and `SUMMARY.md` exist

## 📚 Additional Resources

- [GitBook Documentation](https://docs.gitbook.com/)
- [Markdown Guide](https://www.markdownguide.org/)
- [Git Basics](https://git-scm.com/book/en/v2)

---

**Next:** [Basic Guide](../guides/basic-guide.md) →

