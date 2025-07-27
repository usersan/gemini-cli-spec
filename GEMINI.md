# Gemini CLI Spec-Driven Development

This project adapts the Kiro-style Spec-Driven Development methodology for use with the Gemini CLI. It provides a structured workflow for generating and managing software specifications.

## Project Context

### Project Steering
- Product overview: `.kiro/steering/product.md`
- Technology stack: `.kiro/steering/tech.md`
- Project structure: `.kiro/steering/structure.md`
- Custom steering docs for specialized contexts

### Active Specifications
- Current spec: Check `.kiro/specs/` for active specifications
- Use `gemini spec status [feature-name]` to check progress

## Development Guidelines
- Think in English, but generate responses in Japanese (思考は英語、回答の生成は日本語で行うように)

## Spec-Driven Development Workflow

### Phase 0: Steering Generation (Recommended)

#### Kiro Steering (`.kiro/steering/`)
```bash
gemini steering               # Intelligently create or update steering documents
gemini steering custom        # Create custom steering for specialized contexts
```

**Steering Management:**
- **`gemini steering`**: Unified command that intelligently detects existing files and handles them appropriately. Creates new files if needed, updates existing ones while preserving user customizations.

**Note**: For new features or empty projects, steering is recommended but not required. You can proceed directly to spec-requirements if needed.

### Phase 1: Specification Creation
```bash
gemini spec init [feature-name]           # Initialize spec structure only
gemini spec requirements [feature-name]   # Generate requirements → Review → Edit if needed
gemini spec design [feature-name]         # Generate technical design → Review → Edit if needed
gemini spec tasks [feature-name]          # Generate implementation tasks → Review → Edit if needed
```

### Phase 2: Progress Tracking
```bash
gemini spec status [feature-name]         # Check current progress and phases
```

## Spec-Driven Development Workflow

Kiro's spec-driven development follows a **3-phase approval workflow**:

### Phase 1: Requirements Generation & Approval
1. **Generate**: `gemini spec requirements [feature-name]` - Generate requirements document
2. **Review**: Human reviews `requirements.md` and edits if needed
3. **Approve**: Manually update `spec.json` to mark the requirements as approved.

### Phase 2: Design Generation & Approval
1. **Generate**: `gemini spec design [feature-name]`
2. **Approve**: Manually update `spec.json` to mark the design as approved.

### Phase 3: Tasks Generation & Approval
1. **Generate**: `gemini spec tasks [feature-name]`
2. **Approve**: Manually update `spec.json` to mark the tasks as approved.

### Implementation
Only after all three phases are approved can implementation begin.

**Key Principle**: Each phase requires explicit human approval before proceeding to the next phase, ensuring quality and accuracy throughout the development process.

## Development Rules

1. **Consider steering**: Run `gemini steering` before major development (optional for new features)
2. **Follow the 3-phase approval workflow**: Requirements → Design → Tasks → Implementation
3. **Approval required**: Each phase requires manual approval in `spec.json`.
4. **No skipping phases**: Design requires approved requirements; Tasks require approved design
5. **Update task status**: Mark tasks as completed when working on them
6. **Keep steering current**: Run `gemini steering` after significant changes
7. **Check spec compliance**: Use `gemini spec status` to verify alignment

## Automation

Automation in this Gemini CLI version relies on scripts and manual processes rather than hooks.

### Task Progress Tracking

When working on implementation:
1. **Manual tracking**: Update tasks.md checkboxes manually as you complete tasks
2. **Progress monitoring**: Use `gemini spec status` to view current completion status

## Getting Started

1. Initialize steering documents: `gemini steering`
2. Create your first spec: `gemini spec init [your-feature-name]`
3. Follow the workflow through requirements, design, and tasks

## Kiro Steering Details

Kiro-style steering provides persistent project knowledge through markdown files:

### Core Steering Documents
- **product.md**: Product overview, features, use cases, value proposition
- **tech.md**: Architecture, tech stack, dev environment, commands, ports
- **structure.md**: Directory organization, code patterns, naming conventions

### Custom Steering
Create specialized steering documents for:
- API standards
- Testing approaches
- Code style guidelines
- Security policies
- Database conventions
- Performance standards
- Deployment workflows

### Inclusion Modes
- **Always Included**: Loaded in every interaction (default)
- **Conditional**: Loaded for specific file patterns (e.g., `"*.test.js"`)
- **Manual**: Loaded on-demand with `#filename` reference

## Kiro Steering Configuration

### Current Steering Files
The `gemini steering` command manages these files automatically. Manual updates to this section reflect changes made through steering commands.

### Active Steering Files
- `product.md`: Always included - Product context and business objectives
- `tech.md`: Always included - Technology stack and architectural decisions  
- `structure.md`: Always included - File organization and code patterns

### Custom Steering Files
<!-- Added by gemini steering custom command -->
<!-- Example entries:
- `api-standards.md`: Conditional - `"src/api/**/*"`, `"**/*api*"` - API design guidelines
- `testing-approach.md`: Conditional - `"**/*.test.*"`, `"**/spec/**/*"` - Testing conventions
- `security-policies.md`: Manual - Security review guidelines (reference with @security-policies.md)
-->

### Usage Notes
- **Always files**: Automatically loaded in every interaction
- **Conditional files**: Loaded when working on matching file patterns
- **Manual files**: Reference explicitly with `@filename.md` syntax when needed
- **Updating**: Use `gemini steering` or `gemini steering custom` commands to modify this configuration