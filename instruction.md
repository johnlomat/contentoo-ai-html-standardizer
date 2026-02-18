# HTML Content Standardization Instructions

## Overview

This document provides systematic patterns and procedures for standardizing HTML content structure. These instructions are designed for AI assistants to follow when processing HTML files with structural issues.

## Table of Contents

- [Task Group A: Figure Tag Standardization](#task-group-a-figure-tag-standardization)
- [Task Group B: Table Tag Standardization](#task-group-b-table-tag-standardization)
- [Task Group C: Table of Contents (TOC) Standardization](#task-group-c-table-of-contents-toc-standardization)
  - [Extra TOC Task (Without Wrapper)](#extra-toc-task-without-wrapper)
- [Task Group D: FAQ Section Standardization](#task-group-d-faq-section-standardization)
- [Task Group E: Future Tasks](#task-group-e-future-tasks)
- [General Guidelines for AI Assistants](#general-guidelines-for-ai-assistants)

---

## Task Group A: Figure Tag Standardization

### Problem Pattern Recognition

When processing HTML files, identify these common structural issues with images:

- Empty `<figure>` tags containing placeholder content
- Real images placed outside their corresponding figure elements
- Duplicate caption text in separate paragraphs
- Placeholder paragraphs (e.g., "Alt text:", "Caption here.")

### Standard Transformation Pattern

**Pattern 1: Image with Caption (Before):**

```html
<div style="text-align: left">
  <img src="https://cdn.shopify.com/s/files/1/0657/0580/3913/files/3sixteen_e2366ee2-63b1-4042-8553-757e91f70394.jpg?v=1759115610" alt="Produkt side for Gentle Matter, et Klur hudpleieprodukt." style="margin-bottom: 16px; float: none" />
</div>
<p><em>Kilde: </em><a href="https://klur.co/">Klur</a></p>
<p>Alt text:&nbsp;</p>
```

**Corrected Structure (After):**

```html
<figure>
  <img class="border block--bordered" src="actual-image.jpg" alt="Description" />
  <figcaption><em>Kilde: </em><a href="https://klur.co/">Klur</a></figcaption>
</figure>
```

**Pattern 2: Image without Caption (Before):**

```html
<p><img src="https://cdn.shopify.com/example.jpg" alt="" /></p>
<p>Alt text: Screenshot showing the dashboard interface.</p>
```

**Corrected Structure (After):**

```html
<figure>
  <img class="border block--bordered" src="https://cdn.shopify.com/example.jpg" alt="Screenshot showing the dashboard interface." />
</figure>
```

**Note:** Only add `<figcaption>` if there is a separate caption paragraph (e.g., "Caption:", "Text:", "Source:") between the image and the alt text paragraph. If there's no caption paragraph, create a figure with only the img tag.

### Implementation Procedure

1. **Search for patterns**: Use grep/search to find "Caption here." or empty `<img src="/" />`
2. **Create todo list**: Track each instance that needs fixing
3. **Apply transformation systematically**:
   - Move the real image into the empty figure tag
   - **IMPORTANT**: Only add `<figcaption>` if there is a caption paragraph (e.g., "Caption:", "Text:", "Source:") between the image and alt text paragraph
   - If no caption paragraph exists, create figure with img only (no figcaption)
   - Replace placeholder figcaption with actual caption text (if caption exists)
   - Remove duplicate caption paragraph
   - Remove placeholder paragraphs (Alt text:, etc.)
   - Remove style attributes from img tags (keep class, src, alt)
   - Add `class="border block--bordered"` to all img tags
   - Preserve essential image attributes (class, src, alt)
   - Move alt text content from placeholder paragraph into img alt attribute
4. **Verify completion**: Confirm no placeholder content remains

### Quality Standards

- ✅ Semantic HTML5 compliance
- ✅ Accessibility improvements (proper figure/figcaption relationships)
- ✅ No content duplication
- ✅ Essential image attributes preserved (class, src, alt)
- ✅ Clean img tags without inline styling
- ✅ Standard styling classes applied (`class="border block--bordered"`)
- ✅ Source attributions maintained

---

## Task Group B: Table Tag Standardization

### Problem Pattern Recognition

When processing HTML files, identify these common structural issues with tables:

- Unnecessary `<p>` tags wrapping content inside table cells (`<th>` and `<td>`)
- Basic table structure without proper styling classes
- Missing semantic table formatting
- **IMPORTANT**: Tables often wrapped in `<div align="left">` or similar wrapper divs that must be removed

### Standard Transformation Pattern

**Broken Structure (Before):**

```html
<div align="left">
  <table>
    <thead>
      <tr>
        <th scope="col">
          <p>Plattform</p>
        </th>
        <th scope="col">
          <p>Styrker</p>
        </th>
        <th scope="col">
          <p>Best for</p>
        </th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>
          <p>TikTok</p>
        </td>
        <td>
          <p>Viral rekkevidde, unge publikum, UGC/video-native</p>
        </td>
        <td>
          <p>Visuelle produkter som skjønnhet, livsstil, DIY; tidlige oppdagelseskampanjer</p>
        </td>
      </tr>
      <tr>
        <td>
          <p>Meta</p>
        </td>
        <td>
          <p>Granulær målretting, retargeting, sosial tillit</p>
        </td>
        <td>
          <p>Retargeting, lookalikes, samfunnsbygging</p>
        </td>
      </tr>
      <tr>
        <td>
          <p>Google</p>
        </td>
        <td>
          <p>Intensjonsbasert søk, Shopping, sterk ROI</p>
        </td>
        <td>
          <p>Høy-intensjons kjøp</p>
        </td>
      </tr>
    </tbody>
  </table>
</div>
```

**Corrected Structure (After):**

```html
<div style="overflow-x: auto">
  <table class="tg" style="margin: 0 auto">
    <thead>
      <tr>
        <th scope="col" class="tg-wkkj" style="text-align: center">Plattform</th>
        <th scope="col" class="tg-wkkj" style="text-align: center">Styrker</th>
        <th scope="col" class="tg-wkkj" style="text-align: center">Best for</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td class="tg-wp8o">TikTok</td>
        <td class="tg-wp8o">Viral rekkevidde, unge publikum, UGC/video-native</td>
        <td class="tg-wp8o">Visuelle produkter som skjønnhet, livsstil, DIY; tidlige oppdagelseskampanjer</td>
      </tr>
      <tr>
        <td class="tg-wp8o">Meta</td>
        <td class="tg-wp8o">Granulær målretting, retargeting, sosial tillit</td>
        <td class="tg-wp8o">Retargeting, lookalikes, samfunnsbygging</td>
      </tr>
      <tr>
        <td class="tg-wp8o">Google</td>
        <td class="tg-wp8o">Intensjonsbasert søk, Shopping, sterk ROI</td>
        <td class="tg-wp8o">Høy-intensjons kjøp</td>
      </tr>
    </tbody>
  </table>
</div>
<p></p>
```

### Implementation Procedure

1. **Search for patterns**: Use grep/search to find `<p>` tags inside table cells
2. **Create todo list**: Track each table that needs `<p>` tag removal
3. **Add required CSS styles**: Insert the following CSS before the first table in the document:
   ```html
   <style type="text/css">
     .tg {
       border-collapse: collapse;
       border-spacing: 0;
     }
     .tg td {
       border-color: black;
       border-style: solid;
       border-width: 1px;
       overflow: hidden;
       padding: 9px 15px;
       word-break: normal;
     }
     .tg th {
       border-color: black;
       border-style: solid;
       border-width: 1px;
       font-weight: normal;
       overflow: hidden;
       padding: 9px 15px;
       word-break: normal;
     }
     .tg .tg-j53b {
       border-color: #000000;
       color: #15c;
       text-align: center;
       text-decoration: underline;
       vertical-align: top;
     }
     .tg .tg-wp8o {
       border-color: #000000;
       text-align: center;
       vertical-align: top;
     }
     .tg .tg-wkkj {
       background-color: #efefef;
       border-color: #000000;
       font-weight: bold;
       text-align: left;
       vertical-align: top;
     }
   </style>
   ```
4. **Apply transformation systematically**:
   - **CRITICAL**: Remove any wrapper divs (e.g., `<div align="left">`, `<div align="center">`) around the table element
   - Wrap each table in `<div style="overflow-x: auto">` for responsive horizontal scrolling
   - Remove `<p>` tags from all `<th>` and `<td>` elements
   - Add `class="tg" style="margin: 0 auto"` to table elements
   - Apply appropriate CSS classes to table cells (`tg-wkkj` for headers, `tg-wp8o` for data cells)
   - Add `style="text-align: center"` to all `<th>` elements in header rows
   - Add empty `<p></p>` tag immediately after each `</div>` closing tag (the overflow wrapper)
   - Preserve all other table attributes and styling
   - Maintain text content exactly as-is
5. **Verify completion**: Confirm no original wrapper divs around tables (like `<div align="left">`), each table is wrapped in `<div style="overflow-x: auto">`, no unnecessary `<p>` tags remain in tables, CSS styling is applied, and empty `<p></p>` tags are present after each overflow wrapper

### Quality Standards

- ✅ No original wrapper divs around table elements (like `<div align="left">`)
- ✅ Each table wrapped in `<div style="overflow-x: auto">` for responsive scrolling
- ✅ Clean table cell content without wrapper paragraphs
- ✅ Preserved table styling and CSS classes
- ✅ Maintained semantic table structure
- ✅ All text content preserved exactly
- ✅ Empty `<p></p>` tags added after each overflow wrapper `</div>`

---

## Task Group C: Table of Contents (TOC) Standardization

### Problem Pattern Recognition

When processing HTML files, identify these common structural issues with table of contents:

- Plain `<p>` and `<ul>` tags without proper styling wrapper
- Missing anchor links (`<a href="#id">`) in list items
- Inconsistent or missing ID attributes on heading tags (`<h2>`, `<h3>`)
- Non-sequential ID numbering that doesn't follow existing document structure

### Standard Transformation Pattern

**Broken Structure (Before):**

```html
<p>Main TOC</p>
<ul>
  <li>メンズアパレル製品の仕入れ先を選ぶ方法</li>
  <li>メンズアパレル製品のおすすめ卸売業者12選</li>
  <li>メンズアパレル製品の卸売業者は？</li>
  <li>メンズアパレル製品を卸売業者から購入するメリット</li>
  <li>品質保証のヒント</li>
  <li>卸売価格構造の理解</li>
  <li>カスタマイズとプライベートラベルの機会</li>
  <li>メンズファッションの仕入れに関するFAQ</li>
</ul>
```

**Corrected Structure (After):**

```html
<div class="marketing-block marketing-block--light marketing-block--padded">
  <p><strong>Table of contents</strong></p>
  <ul>
    <li><a href="#26">メンズアパレル製品の仕入れ先を選ぶ方法</a></li>
    <li><a href="#27">メンズアパレル製品のおすすめ卸売業者12選</a></li>
    <li><a href="#28">メンズアパレル製品の卸売業者は？</a></li>
    <li><a href="#29">メンズアパレル製品を卸売業者から購入するメリット</a></li>
    <li><a href="#30">品質保証のヒント</a></li>
    <li><a href="#31">卸売価格構造の理解</a></li>
    <li><a href="#32">カスタマイズとプライベートラベルの機会</a></li>
    <li><a href="#33">メンズファッションの仕入れに関するFAQ</a></li>
  </ul>
</div>
```

### Implementation Procedure

1. **Search for existing ID patterns**: Use grep to find all `id="[number]"` attributes in the document to identify the highest existing ID number
2. **Determine starting ID**: Continue numbering from the last used ID number (e.g., if highest is 25, start TOC items at 26)
3. **Apply TOC wrapper transformation**:
   - Wrap the TOC structure in `<div class="marketing-block marketing-block--light marketing-block--padded">`
   - Change heading to `<p><strong>Table of contents</strong></p>`
   - Add anchor links to each `<li>` item using sequential ID numbers
   - Format: `<li><a href="#[number]">Item text</a></li>`
4. **Update corresponding heading tags**: Add matching ID attributes to the related `<h2>` tags throughout the document
   - First TOC item links to first main section `<h2 id="26">`
   - Second TOC item links to second main section `<h2 id="27">`
   - Continue pattern for all TOC items
5. **Verify completion**: Confirm all TOC items have working anchor links and corresponding heading IDs

### Quality Standards

- ✅ Proper marketing block wrapper with standard classes
- ✅ Consistent "Table of contents" heading (not translated unless specified)
- ✅ Sequential ID numbering continuing from existing document structure
- ✅ All TOC items have functional anchor links
- ✅ All referenced headings have matching ID attributes
- ✅ Clean, clickable navigation structure
- ✅ Preserved original text content in list items

### Extra TOC Task (Without Wrapper)

For cases where a list already exists in the document and only needs anchor links added (no marketing block wrapper needed).

#### Problem Pattern Recognition

- Existing `<ol>` or `<ul>` lists that summarize sections but lack clickable navigation
- List items that correspond to `<h3>` or other subheadings without IDs
- No wrapper div needed - list structure should be preserved as-is

#### Standard Transformation Pattern

**Broken Structure (Before):**

```html
<ol>
  <li>Päätä, mistä podcast kertoo</li>
  <li>Määrittele podcastin tavoite ja tarkoitus</li>
  <li>Valitse formaatti</li>
  <li>Luo podcastille brändi</li>
</ol>
```

**Corrected Structure (After):**

```html
<ol>
  <li><a href="#6">Päätä, mistä podcast kertoo</a></li>
  <li><a href="#7">Määrittele podcastin tavoite ja tarkoitus</a></li>
  <li><a href="#8">Valitse formaatti</a></li>
  <li><a href="#9">Luo podcastille brändi</a></li>
</ol>
```

**Corresponding Heading Updates:**

```html
<h3 id="6"><strong>1. Päätä mistä podcastisi kertoo</strong></h3>
<h3 id="7"><strong>2. Määrittele podcastin tavoite ja tarkoitus</strong></h3>
<h3 id="8"><strong>3. Valitse formaatti</strong></h3>
<h3 id="9"><strong>4. Luo podcast-brändisi</strong></h3>
```

#### Implementation Procedure

1. **Search for existing ID patterns**: Use grep to find all `id="[number]"` attributes in the document to identify the highest existing ID number
2. **Determine starting ID**: Continue numbering from the last used ID number (e.g., if highest is 5, start list items at 6)
3. **Apply anchor link transformation** (NO wrapper needed):
   - Keep the existing `<ol>` or `<ul>` structure as-is
   - Add anchor links to each `<li>` item using sequential ID numbers
   - Format: `<li><a href="#[number]">Item text</a></li>`
4. **Update corresponding heading tags**: Add matching ID attributes to the related `<h3>` (or other) tags throughout the document
   - First list item links to first section heading `<h3 id="6">`
   - Second list item links to second section heading `<h3 id="7">`
   - Continue pattern for all list items
5. **Verify completion**: Confirm all list items have working anchor links and corresponding heading IDs

#### Quality Standards

- ✅ NO wrapper div added - existing list structure preserved
- ✅ Sequential ID numbering continuing from existing document structure
- ✅ All list items have functional anchor links
- ✅ All referenced headings have matching ID attributes
- ✅ Clean, clickable navigation structure
- ✅ Preserved original text content and list type (`<ol>` or `<ul>`)

---

## Task Group D: FAQ Section Standardization

### Problem Pattern Recognition

When processing HTML files, identify these common structural issues with FAQ sections:

- Plain FAQ sections without proper Schema.org markup
- Missing marketing block wrapper
- No structured data for SEO purposes
- Simple heading and paragraph structure without semantic FAQ markup

### Standard Transformation Pattern

**Broken Structure (Before):**

```html
<h2><strong>ECサイトと実店舗の比較に関するよくある質問</strong></h2>
<h3><strong>ECサイトは小売と見なされますか？</strong></h3>
<p>はい、ECサイトは小売の一形態と見なされます。小売は、最終消費者に商品やサービスを販売することと定義され、ECサイトはオンラインで商品やサービスを売買する小売の一形態です。</p>
<h3><strong>ECサイトは実店舗よりも優れていますか？</strong></h3>
<p>ECサイトは実店舗よりも優れています。オーバーヘッドコストが低く、リーチが広く、時間と労力が少なく、迅速な取引を促進し、より効率的なビジネスを運営するために自動化を活用します。</p>
```

**Corrected Structure (After):**

```html
<div class="marketing-block marketing-block--light marketing-block--padded">
  <div itemtype="https://schema.org/FAQPage" itemscope="">
    <h2><strong>ECサイトと実店舗の比較に関するよくある質問</strong></h2>
    <div itemtype="https://schema.org/Question" itemprop="mainEntity" itemscope="">
      <h3 itemprop="name"><strong>ECサイトは小売と見なされますか？</strong></h3>
      <div itemtype="https://schema.org/Answer" itemprop="acceptedAnswer" itemscope="">
        <div itemprop="text">
          <p>はい、ECサイトは小売の一形態と見なされます。小売は、最終消費者に商品やサービスを販売することと定義され、ECサイトはオンラインで商品やサービスを売買する小売の一形態です。</p>
        </div>
      </div>
    </div>
    <div itemtype="https://schema.org/Question" itemprop="mainEntity" itemscope="">
      <h3 itemprop="name"><strong>ECサイトは実店舗よりも優れていますか？</strong></h3>
      <div itemtype="https://schema.org/Answer" itemprop="acceptedAnswer" itemscope="">
        <div itemprop="text">
          <p>ECサイトは実店舗よりも優れています。オーバーヘッドコストが低く、リーチが広く、時間と労力が少なく、迅速な取引を促進し、より効率的なビジネスを運営するために自動化を活用します。</p>
        </div>
      </div>
    </div>
  </div>
</div>
```

### Implementation Procedure

1. **Search for FAQ patterns**: Use grep/search to find FAQ section headings (commonly containing "FAQ", "よくある質問", "Questions", etc.)
2. **Create todo list**: Track each FAQ section that needs transformation
3. **Apply FAQ wrapper transformation**:
   - Wrap entire FAQ section in `<div class="marketing-block marketing-block--light marketing-block--padded">`
   - Add FAQPage schema wrapper: `<div itemtype="https://schema.org/FAQPage" itemscope="">`
   - Keep the main FAQ heading (`<h2>`) as-is
   - Wrap each question-answer pair in Question schema markup
4. **Apply Question/Answer schema to each FAQ item**:
   - Wrap each Q&A pair in: `<div itemtype="https://schema.org/Question" itemprop="mainEntity" itemscope="">`
   - Add `itemprop="name"` to the question heading (`<h3>`)
   - Wrap answer content in: `<div itemtype="https://schema.org/Answer" itemprop="acceptedAnswer" itemscope="">`
   - Wrap answer text in: `<div itemprop="text">` containing the paragraph(s) or list elements
5. **Handle complex answers**: For answers with multiple paragraphs or lists (e.g., `<ol>`, `<ul>`), ensure all content stays within the `<div itemprop="text">` wrapper
6. **Verify completion**: Confirm all FAQ items have proper Schema.org markup and marketing block wrapper

### Quality Standards

- ✅ Proper marketing block wrapper with standard classes
- ✅ Valid Schema.org FAQPage structured data
- ✅ Each question wrapped with Question schema
- ✅ Each answer wrapped with Answer schema
- ✅ All text content preserved exactly
- ✅ Support for complex answers (multiple paragraphs, lists)
- ✅ Improved SEO with structured data markup
- ✅ Maintained heading hierarchy and text formatting

---

## Task Group E: [Future Tasks]

_Additional HTML standardization tasks can be added here_

### Example: Link Standardization

- Pattern recognition for broken links
- Systematic replacement procedures
- Quality standards for link structure

---

## General Guidelines for AI Assistants

### Workflow Pattern

1. **Analyze**: Read the HTML file and identify structural issues
2. **Plan**: Create a todo list to track all instances needing fixes
3. **Execute**: Apply transformations systematically using established patterns
4. **Verify**: Confirm all issues have been resolved and quality standards met

### Tool Selection for Efficient Processing

**CRITICAL: Always analyze the overall structure of ALL elements before deciding which tool to use.**

When processing multiple transformations, choose the appropriate tool based on:
1. **Number of instances**
2. **Structural consistency across ALL instances**

**Decision Process:**

1. **First: Analyze ALL instances** - Read through the document and examine the structure of every element that needs transformation
2. **Check for consistency** - Determine if all instances follow the same pattern or have structural variations
3. **Choose the appropriate tool** based on your analysis

**Single or Few Instances (1-3 items):**
- Use the **Edit tool** directly for individual transformations
- Suitable for unique cases or when each transformation requires different handling
- Example: Fixing 2-3 figure tags with different structures

**Multiple Similar Instances (4+ items with IDENTICAL structure):**
- Use the **Task tool** with the **general-purpose agent** for bulk operations
- **REQUIREMENT**: All instances must follow the exact same structural pattern
- Significantly faster than making individual Edit calls
- Agent can process all instances autonomously in parallel
- Example workflow:
  ```
  1. Analyze ALL elements (e.g., examine all 25 images)
  2. Confirm identical pattern across all instances
  3. Create clear transformation instructions for the agent
  4. Specify exact requirements and all locations
  5. Agent processes all transformations systematically
  6. Verify completion with single response
  ```

**Multiple Instances with MIXED structures (4+ items with variations):**
- Use the **Edit tool** for individual transformations
- **Example scenario**: 10 images where first 5 have captions, last 5 don't
- **Why manual approach**: Each requires different transformation pattern
- **Process**: Handle each instance individually based on its specific structure

**Benefits of Using Task Tool for Bulk Operations:**
- **Speed**: Processes multiple edits in one autonomous operation
- **Consistency**: Applies same pattern uniformly across all instances
- **Efficiency**: No back-and-forth for each individual edit
- **Scalability**: Works equally well for 5 items or 50 items

**When to Use Task Tool:**
- Figure tag standardization with 4+ images
- Table tag transformations across multiple tables
- Any repetitive pattern that appears multiple times
- Bulk removal of placeholder content

**Example Task Tool Usage:**
```
Task tool prompt for 25 images:
"Transform all 25 images in file X from pattern A to pattern B.
Requirements: [detailed list]
Locations: Line 37, 50, 64... [all locations]
Return confirmation when complete."
```

**Important Notes:**
- Always provide clear, detailed transformation requirements to the agent
- Specify exact line numbers or search patterns when possible
- Agent works autonomously - ensure instructions are complete
- Single response confirms all transformations completed

### Content Preservation Rules

**CRITICAL: Do not alter existing content, tag attributes, or tags unless specifically required for the transformation.**

- **Text Content**: Never modify the actual text content of paragraphs, headings, captions, etc.
- **Tag Attributes**: Preserve all existing attributes (class, style, src, alt, href, etc.)
- **HTML Tags**: Do not change existing tag types unless part of the specific transformation pattern
- **Styling**: Maintain all CSS classes and inline styles
- **Links**: Keep all href values and link text unchanged
- **Structure**: Only move/reorganize elements as defined in the transformation pattern

### Documentation Standards

- Always preserve existing content and styling
- Maintain semantic HTML5 compliance
- Ensure accessibility improvements
- Keep source attributions intact
- Follow established transformation patterns consistently

### Task Completion Criteria

- All placeholder content eliminated
- No content duplication
- Structural integrity maintained
- Quality standards checklist passed
