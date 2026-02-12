---
name: GoDoc-Canonical
description: A standard for writing idiomatic Go documentation that ensures comments are clear, concise, and perfectly rendered by the godoc tool.
---

# Go Documentation Standard 

This document outlines the standard for writing idiomatic, "canonical" Go documentation. High-quality Go documentation is not just about comments; it is about how those comments are parsed by the `godoc` tool and rendered on [pkg.go.dev](https://pkg.go.dev).

## 1. The Core Principle

**Documentation is for the user, not the maintainer.**
Go documentation should focus on *what* an identifier does and *how* to use it, rather than *how* it is implemented internally.

## 2. Package Documentation

Every package must have a package comment.

* **Location:** Immediately preceding the `package` clause.
* **Style:** Start with "Package [name] ..."
* **Content:** Provide a high-level overview of the package's purpose and its main entry points.
* **Large Packages:** If the documentation is extensive, place it in a file named `doc.go` containing only the package comment and the package clause.

```go
// Package archive provides access to various archive formats.
package archive

```

## 3. Formatting Rules

The `godoc` tool uses a simple, minimalist parser. Avoid Markdown (except for modern `go doc` versions which support limited features).

* **Paragraphs:** Separate paragraphs with a single empty line.
* **Pre-formatted Text:** Indent lines (usually by two spaces or a tab) to render them as fixed-width code blocks.
* **Headers:** A line consisting of a single sentence starting with an uppercase letter and containing no end punctuation can be treated as a section header.
* **Links:** URLs in the text are automatically converted into HTML links.

### Automated Formatting with `gofmt`

- The `gofmt` tool is not just for code; it is the official formatter for your documentation comments. Using it ensures your docs adhere to the canonical visual style.

Comment Indentation: `gofmt` will automatically adjust the indentation of your comments to match the code block they describe.

- HTML Conversion: It ensures that your "pre-formatted" blocks (indented text) are preserved correctly so that tools like godoc render them as <pre> tags.

- Consistency: Running `gofmt -s` (simplify) can occasionally clean up redundant comment structures, ensuring the documentation remains "Gofmt-clean."

- Pro Tip: Always run `go fmt ./...` before committing. If your doc comments look "off" in your IDE, gofmt is the authoritative source for how they should be spaced.

## 4. Documenting Identifiers (Functions, Types, Vars)

* **Direct Attachment:** Comments must immediately precede the declaration with no empty lines in between.
* **The Naming Rule:** Every doc comment must start with the name of the identifier being documented. This makes it easy to grep and provides a consistent rhythm.

```go
// Read reads up to len(p) bytes into p.
func (f *File) Read(p []byte) (n int, err error)

// User represents a system account.
type User struct { ... }

```

## 5. Writing Style

* **Be Concise:** Avoid "This function..." or "The purpose of this type is...". Jump straight to the action.
* **Use Third Person:** Use "Returns", "Reads", "Executes" instead of "Return" or "Read".
* **Deprecation:** To deprecate an identifier, start a paragraph with "Deprecated: " followed by a suggestion for an alternative.

```go
// Title returns a copy of the string s with all Unicode letters that begin words
// mapped to their Unicode title case.
//
// Deprecated: Use golang.org/x/text/cases instead.
func Title(s string) string

```

### The doc.go Pattern

If you are starting a new project or a complex sub-package, don’t clutter your main logic file. Use the skill’s advice to create a doc.go file. 
This serves as the "Readme" that appears at the very top of your package documentation on pkg.go.dev.




## 6. Examples

The best form of documentation is a working example.

* **Location:** Place examples in a file ending in `_test.go` (e.g., `example_test.go`).
* **Naming:** Functions should be named `Example`, `ExampleIdentifier`, or `ExampleIdentifier_suffix`.
* **Output:** Include an "Output:" comment at the end of the function. The Go test runner will execute the example and verify the output.

```go
func ExampleHello() {
    fmt.Println("hello")
    // Output: hello
}

```

## 7. Best Practices & Checklist

* [ ] Does every exported identifier have a comment?
* [ ] Do all comments start with the name of the identifier?
* [ ] Are code snippets in comments indented?
* [ ] Is the package comment present and descriptive?
* [ ] Are complex behaviors illustrated with `Example` functions?

---

*Refer to the official [Go Blog: Go Doc](https://go.dev/blog/godoc) for the foundational philosophy behind these standards.*

