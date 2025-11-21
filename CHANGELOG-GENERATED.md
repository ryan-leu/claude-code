# Changelog - Recent Fixes

## 🐛 Bug Fixes

- **#50**: [BUG] Cross-project hook inheritance executes sibling project hooks inappropriately ([bug, has repro, platform:macos, area:tools])
- **#48**: Claude Code executes wrong project hooks in multi-project workspace ([bug, has repro, platform:macos, area:tools])
- **#37**: Invalid JSON Encoding in API Request Body ([bug, duplicate, area:core, platform:macos, area:api])
- **#32**: Calling MCP tool create-spec-doc freezes in Cursor AI + GPT-5 ([bug, area:mcp, area:ide, external])
- **#25**: Missing Tool Result Block for Tool Use ID toolu_01GUUUdR6TqtrqKTprMSuLqc ([bug, duplicate, area:core, platform:macos, area:api])
- **#22**: [BUG] Search/Grep tool is BROKEN ([bug, has repro, area:tools])
- **#21**: Invalid JSON Encoding Error During API Request ([bug, duplicate, area:core, platform:macos, area:api])
- **#15**: [BUG] Hard to trace changes in releases ([bug])
- **#13**: Agent Command Autocomplete Regression in v72 ([bug, has repro, platform:macos, area:tui])
- **#12**: [BUG] PowerLevel10k terminal theme causes Claude Code timeout and parsing failures due to ANSI escape sequence contamination ([bug, has repro, area:core, platform:macos, area:tui])

## 📚 Documentation

- **#39**: [DOCS] Slash command frontmatter table is misformatted ([documentation])
- **#30**: [Docs] Undocumented `statusline` configuration feature ([documentation, area:tui])
- **#23**: [Documentation] Claude Code release notes for v1.0.71 is not informative. Need more detailed notes. ([documentation, enhancement])

## 🔄 Duplicates

- **#37**: Invalid JSON Encoding in API Request Body ([bug, duplicate, area:core, platform:macos, area:api])
- **#25**: Missing Tool Result Block for Tool Use ID toolu_01GUUUdR6TqtrqKTprMSuLqc ([bug, duplicate, area:core, platform:macos, area:api])
- **#21**: Invalid JSON Encoding Error During API Request ([bug, duplicate, area:core, platform:macos, area:api])

## 🎨 Enhancements

- **#27**: Task color proposal - orange/ginger instead of blue. ([enhancement, area:tui])

## 📊 Statistics

### Overview
- **Total Closed Issues**: 14
- **Bug Fixes**: 10
- **Documentation**: 3
- **Enhancements**: 1
- **Duplicates**: 3

### Distribution by Platform

| Platform | Count |
|----------|-------|
| platform:macos | 8 |
| Other/Unspecified | 6 |

### Distribution by Area

| Area | Count |
|------|-------|
| area:tools | 3 |
| area:core | 3 |
| area:api | 3 |
| area:tui | 3 |
| area:mcp | 1 |
| area:ide | 1 |
| Other/Unspecified | 4 |

### Cross-Platform Impact
Issues affecting multiple platforms or having broader ecosystem impact:
- **#50, #48**: Cross-project hook inheritance issues affecting Python/Node.js multi-language workspaces
- **#12**: Terminal theme compatibility affecting all macOS terminal users
- **#32**: External tool integration issues with Cursor AI
- **#37, #25, #21**: API encoding issues causing widespread request failures

### Resolution Patterns
- **Hook Management**: 2 issues resolved related to project-type detection and hook execution
- **API Encoding**: 3 duplicate issues identified and consolidated around JSON encoding problems
- **Terminal Compatibility**: Multiple issues around terminal integration and display
- **Documentation Gaps**: 3 issues highlighting need for better documentation coverage
