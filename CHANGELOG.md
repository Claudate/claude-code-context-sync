# Changelog

All notable changes to the Context Sync plugin will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.1] - 2025-12-11

### Fixed
- Fixed `/save-session` and `/resume-session` commands not executing properly
- Commands now correctly trigger the context-save and context-resume skills
- Changed command files from documentation to executable skill invocations

## [1.0.0] - 2025-12-10

### Added
- Initial release of Context Sync plugin
- `context-save` skill for saving session context
- `context-resume` skill for resuming previous sessions
- `/save-session` slash command
- `/resume-session` slash command
- Priority-based task tracking (🔴 High, 🟡 Medium, 🟢 Low)
- Automatic session file management
- Comprehensive documentation in README.md

### Features
- Save work context including tasks, files, and technical notes
- Resume sessions from any Claude Code window
- Smart task progress tracking
- Automatic cleanup of completed sessions

## [Unreleased]

### Planned
- Session search and filtering
- Export sessions to different formats
- Session templates
- Integration with project management tools
