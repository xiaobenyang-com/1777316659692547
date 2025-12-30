# 苹果开发者文档搜索服务 Search Apple Docs

通过模型上下文协议（MCP）访问苹果官方开发者文档、框架、API及WWDC视频，支持AI驱动的自然语言查询，提供Swift/Objective-C代码示例和技术指南。
Access Apple's official developer documentation, frameworks, APIs, and WWDC videos through the Model Context Protocol (MCP), support AI driven natural language queries, and provide Swift/Objective-C code examples and technical guidelines.## 工具列表 Tool List

本MCP服务封装下列工具，可让模型通过标准化接口调用以下功能。 本MCP服务封装下列工具，可让模型通过标准化接口调用以下功能。

| 工具 Tool   | 描述 Description         |
|-------|--------------------|
| search_apple_docs | Search Apple Developer Documentation for APIs, frameworks, guides, and samples. Best for finding specific APIs, classes, or methods. For browsing sample code projects, use get_sample_code. For WWDC videos, use the dedicated WWDC tools (list_wwdc_videos, search_wwdc_content). |
| get_apple_doc_content | Get detailed content from a specific Apple Developer Documentation page. Use this after search_apple_docs to get full documentation. Supports enhanced analysis options for comprehensive API understanding. Best for: reading API details, understanding usage, checking availability. |
| list_technologies | Browse all Apple technologies and frameworks by category. Essential for discovering available frameworks and understanding Apple's technology ecosystem. Use this when: exploring what's available, finding framework identifiers for search_framework_symbols, checking beta status. |
| search_framework_symbols | Browse and search symbols within a specific Apple framework. Perfect for exploring framework APIs, finding all views/controllers/delegates in a framework, or discovering available types. Use after list_technologies to get framework identifiers. |
| get_related_apis | Analyze API relationships and discover related functionality. Shows inheritance, protocol conformances, and Apple's recommended alternatives. Essential for understanding how APIs work together. Use when: learning API hierarchy, finding protocol requirements, discovering related functionality. |
| resolve_references_batch | Deep dive into all types and APIs referenced in a documentation page. Resolves all mentioned types, methods, and properties to understand dependencies. Use when: analyzing complex APIs, understanding type requirements, exploring API ecosystems. |
| get_platform_compatibility | Check API availability across Apple platforms and OS versions. Shows minimum deployment targets, deprecations, and platform-specific features. Critical for cross-platform development. Use when: planning app requirements, checking API availability, finding platform alternatives. |
| find_similar_apis | Discover alternative and related APIs. Finds APIs with similar functionality, modern replacements for deprecated APIs, and platform-specific alternatives. Perfect when looking for better ways to implement functionality. |
| get_documentation_updates | Track latest Apple platform updates, new APIs, and changes. Shows WWDC announcements, framework updates, and release notes. Essential for staying current with Apple development. For detailed WWDC videos, use WWDC-specific tools. |
| get_technology_overviews | Access comprehensive guides and tutorials for Apple technologies. Includes getting started guides, architectural overviews, best practices, and implementation patterns. Perfect for learning new frameworks or understanding Apple's recommended approaches. |
| get_sample_code | Browse complete sample projects from Apple. Full working examples demonstrating best practices and implementation patterns. Different from search_apple_docs which returns code snippets. Use for learning by example. |
| list_wwdc_videos | Browse WWDC session videos with full offline access to transcripts and code. Shows all available sessions with filtering options. Use this to discover WWDC content, find sessions by topic, or identify videos with code examples. |
| search_wwdc_content | Full-text search across all WWDC video transcripts and code examples. Find specific discussions, API mentions, or implementation examples. More powerful than list_wwdc_videos for finding specific content. |
| get_wwdc_video | Access complete WWDC session content including full transcript, code examples, and resources. Use after finding videos with list_wwdc_videos or search_wwdc_content. Provides offline access to entire session content. |
| get_wwdc_code_examples | Browse all code examples from WWDC sessions. Perfect for finding implementation patterns, seeing new API usage, or learning by example. Each result includes the code and its session context. |
| browse_wwdc_topics | List all WWDC topic categories with their IDs. Essential first step before using list_wwdc_videos with topic filtering. Returns topic IDs like "swiftui-ui-frameworks" that can be used in other tools. |
| find_related_wwdc_videos | Discover WWDC sessions related to a specific video. Finds prerequisite sessions, follow-up content, and thematically similar talks. Essential for creating learning paths. |
| list_wwdc_years | List all available WWDC years with video counts and statistics. Shows which years have content available and how many videos each year contains. |


## 检查服务 ## Inspector

工具在线测试： [https://mcp.xiaobenyang.com/inspector/1777316659692547](https://mcp.xiaobenyang.com/inspector/1777316659692547)

Online Tool test [https://mcp.xiaobenyang.com/inspector/1777316659692547](https://mcp.xiaobenyang.com/inspector/1777316659692547)

## 服务配置 MCP Server Config


> #### 如何获取 XBY-APIKEY ？ How to get XBY-APIKEY ?
> 访问小笨羊科技网站 [https://xiaobenyang.com](https://xiaobenyang.com)，注册用户即可获得APIKEY
> Visit XiaoBenYang website [https://xiaobenyang.com](https://xiaobenyang.com), register and get the APIKEY.

### SSE
```json
{
  "mcpServers": {
    "苹果开发者文档搜索服务": {
      "headers": {
        "XBY-APIKEY": "<YOUR_XBY_APIKEY>"
      },
      "type": "sse",
      "url": "https://mcp.xiaobenyang.com/1777316659692547/sse"
    }
  }
}
```
### STREAMABLE HTTP
```json
{
  "mcpServers": {
    "苹果开发者文档搜索服务": {
      "headers": {
        "XBY-APIKEY": "<YOUR_XBY_APIKEY>"
      },
      "type": "streamable_http",
      "url": "https://mcp.xiaobenyang.com/1777316659692547/mcp"
    }
  }
}
```
### STDIO
```json
{
    "mcpServers": {
        "苹果开发者文档搜索服务": {
          "command": "npx",
          "args": [
            "-y",
            "xiaobenyang-mcp"
          ],
          "env": {
            "XBY_APIKEY": "<YOUR_XBY_APIKEY>",
            "mcpId": "1777316659692547",
          },
          "transport": "stdio"
        }
      }
}

```
