# GoDoc-Canonical

**GoDoc-Canonical** is a professional standard for writing idiomatic, high-quality Go documentation. This skill ensures that your package comments aren't just "notes," but a structured API manual that renders perfectly on [pkg.go.dev](https://www.google.com/search?q=https://pkg.go.dev).

## 🚀 Why Use This?

In Go, documentation is treated as a first-class citizen. Poorly formatted comments lead to broken layouts in `godoc` and confusion for end-users. This standard enforces the "Go Way":

* **Discoverability:** Consistent naming makes documentation easy to search.
* **Verification:** Encourages testable examples that never go out of date.
* **Aesthetics:** Leverages `gofmt` to ensure clean, professional rendering.

## 🛠 How to Apply the Skill

### 1. The Naming Rule

Every exported identifier must have a comment starting with its own name.

```go
// Good
// Authorize checks the user credentials.
func Authorize() { ... }

// Bad
// This function checks the user credentials.
func Authorize() { ... }

```

### 2. Format with `gofmt`

The `gofmt` tool is the source of truth. It handles the alignment and spacing of your comments. Before pushing code, always run:

```bash
go fmt ./...

```

### 3. Use the `SKILL.md`

For a deep dive into package documentation, pre-formatted blocks, and deprecation notices, refer to the [SKILL.md](https://www.google.com/search?q=./SKILL.md) file in this repository.

## 📋 Quick Checklist

| Task | Requirement |
| --- | --- |
| **Package Doc** | Starts with `// Package [name] ...` |
| **Identifiers** | Start with the identifier's name |
| **Formatting** | Use 2-space indentation for code snippets |
| **Examples** | Included in `_test.go` with `// Output:` |

---

> "Good documentation is as important as good code." — The Go Authors
