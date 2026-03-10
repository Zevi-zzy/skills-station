当用户需要生成、更新或排版简历时，请使用此技能。此技能能够生成一个美观、专业且适合打印的 HTML 简历文件。

使用步骤：
1. **收集信息**：从用户的输入中提取简历的关键信息，包括：
    - **基本信息**：姓名、英文名（可选）、电话、邮箱、所在城市。
    - **教育经历**：学校名称、专业/学位、起止时间。
    - **技能专长**：按类别整理的技能点（例如：核心技能、工具、语言等）。
    - **工作经历**：公司名称、职位、起止时间、工作描述（包括关键成果数据）。
    - **项目经验**（可选，可合并在工作经历中）：项目名称、角色、描述、技术栈。
    - **证书奖项**（可选）。

2. **生成 HTML**：使用以下 HTML 模板，将提取的信息填充到对应的位置。
    - **注意**：保持 HTML 结构和 CSS 样式不变，仅替换内容部分。
    - **样式调整**：如果用户有特殊的颜色偏好，可以修改 `:root` 中的 `--primary-color` 和 `--sidebar-bg` 变量。

3. **输出文件**：将生成的 HTML 代码写入一个 `.html` 文件（例如 `resume.html`）。

4. **引导用户**：告知用户在浏览器中打开该文件，并使用 `Ctrl+P` (Windows) 或 `Cmd+P` (Mac) 打印并“另存为 PDF”。

---

### HTML 模板代码

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{NAME}}_简历</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+SC:wght@300;400;500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-color: #2c58a0; /* 主色调：深蓝色 */
            --accent-color: #f4f7fa; /* 辅助背景色 */
            --text-main: #2c3e50; /* 主要文字颜色 */
            --text-secondary: #596c80; /* 次要文字颜色 */
            --highlight-color: #000000; /* 高亮文字颜色 */
            --border-color: #e6e9ed; /* 边框颜色 */
            --sidebar-width: 210px; /* 侧边栏宽度 */
            --sidebar-bg: linear-gradient(160deg, #1a2a44 0%, #244275 100%); /* 侧边栏背景 */
            --sidebar-text: #ffffff; /* 侧边栏文字颜色 */
            --sidebar-text-muted: rgba(255, 255, 255, 0.75); /* 侧边栏次要文字颜色 */
        }

        @page {
            size: A4;
            margin: 0;
        }

        body {
            font-family: "Noto Sans SC", -apple-system, BlinkMacSystemFont, "PingFang SC", "Microsoft YaHei", "Helvetica Neue", Helvetica, Arial, sans-serif;
            line-height: 1.4;
            color: var(--text-main);
            background-color: #e9ecef;
            margin: 0;
            padding: 20px 0;
            font-size: 13px;
            -webkit-font-smoothing: antialiased;
            display: flex;
            justify-content: center;
        }

        .resume-container {
            display: flex;
            width: 210mm;
            min-height: 297mm;
            background: #fff;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }

        @media print {
            body {
                background: white;
                padding: 0;
                display: block;
            }
            .resume-container {
                width: 100%;
                min-height: 100vh;
                box-shadow: none;
                margin: 0;
            }
            * {
                -webkit-print-color-adjust: exact !important;
                print-color-adjust: exact !important;
            }
        }

        /* Left Sidebar */
        .sidebar {
            width: var(--sidebar-width);
            background: var(--sidebar-bg);
            color: var(--sidebar-text);
            padding: 25px 18px;
            flex-shrink: 0;
            display: flex;
            flex-direction: column;
        }

        .profile-section {
            text-align: left;
            margin-bottom: 25px;
        }

        .name-box h1 {
            font-size: 28px;
            margin: 0 0 8px 0;
            font-weight: 700;
            letter-spacing: 1px;
            color: #fff;
            line-height: 1.2;
        }

        .name-box h2 {
            font-size: 13px;
            margin: 0;
            font-weight: 500;
            color: #fff;
            background: rgba(255,255,255,0.15);
            display: inline-block;
            padding: 4px 10px;
            border-radius: 4px;
            line-height: 1.4;
        }

        .sidebar-section {
            margin-bottom: 20px;
        }

        .sidebar-title {
            font-size: 13.5px;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            margin-bottom: 10px;
            border-bottom: 1px solid rgba(255,255,255,0.2);
            padding-bottom: 5px;
            color: #fff;
            font-weight: 700;
            opacity: 0.9;
        }

        /* Contact Info */
        .contact-list {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .contact-item {
            display: flex;
            align-items: flex-start;
            gap: 10px;
            font-size: 12.5px;
            color: var(--sidebar-text-muted);
            line-height: 1.4;
        }

        .contact-item svg {
            width: 14px;
            height: 14px;
            fill: #fff;
            opacity: 0.8;
            margin-top: 2px;
        }

        /* Sidebar Lists */
        .edu-item {
            margin-bottom: 16px;
        }

        .edu-school {
            font-weight: 700;
            font-size: 13.5px;
            color: #fff;
            margin-bottom: 3px;
            display: block;
        }

        .edu-meta {
            font-size: 12px;
            color: var(--sidebar-text-muted);
            margin-bottom: 2px;
            display: block;
        }

        .skill-category {
            margin-bottom: 16px;
        }

        .skill-cat-title {
            font-size: 12px;
            color: #a8c5ff; 
            font-weight: 700;
            margin-bottom: 6px;
            display: block;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .skill-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 6px;
        }

        .sidebar-tag {
            font-size: 11px;
            background: rgba(255,255,255,0.12);
            padding: 3px 6px;
            border-radius: 4px;
            color: #f0f0f0;
            line-height: 1.3;
        }

        /* Right Content */
        .main-content {
            flex-grow: 1;
            padding: 25px 30px;
            background-color: #fff;
        }

        .content-section {
            margin-bottom: 0px;
        }

        .content-title {
            font-size: 16px;
            color: var(--primary-color);
            border-bottom: 2px solid #eee;
            padding-bottom: 6px;
            margin-bottom: 15px;
            font-weight: 700;
            display: flex;
            align-items: center;
            gap: 10px;
            letter-spacing: 0.5px;
        }

        .content-title svg {
            width: 18px;
            height: 18px;
            fill: var(--primary-color);
        }

        /* Experience Timeline */
        .experience-item {
            position: relative;
            padding-left: 20px;
            margin-bottom: 18px;
            border-left: 2px solid #e6e9ed;
        }

        .experience-item:last-child {
            border-left: 2px solid #e6e9ed;
            padding-left: 20px;
            margin-bottom: 0;
            padding-bottom: 5px; 
        }
        
        .experience-item::before {
            content: '';
            position: absolute;
            left: -6px;
            top: 4px;
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background: #fff;
            border: 3px solid var(--primary-color);
            box-shadow: 0 0 0 3px #fff;
        }

        .job-header {
            display: flex;
            justify-content: space-between;
            align-items: baseline;
            margin-bottom: 4px;
        }

        .company {
            font-size: 16px;
            font-weight: 700;
            color: #1a2a44;
        }

        .job-period {
            font-size: 12.5px;
            color: #888;
            font-weight: 500;
        }

        .role-name {
            font-size: 13.5px;
            font-weight: 600;
            color: var(--primary-color);
            margin-bottom: 4px;
            display: block;
        }

        .job-desc ul {
            margin: 0;
            padding-left: 16px;
        }

        .job-desc li {
            margin-bottom: 3px;
            color: #444;
            font-size: 13px;
            text-align: justify;
            line-height: 1.45;
        }

        .key-result {
            font-weight: 700;
            color: #000;
        }

        .tech-stack-row {
            margin-top: 6px;
            display: flex;
            flex-wrap: wrap;
            gap: 6px;
        }

        .tech-badge {
            font-size: 10.5px;
            color: var(--primary-color);
            background-color: #ecf3ff;
            padding: 2px 8px;
            border-radius: 10px;
            font-weight: 600;
            border: 1px solid rgba(44, 88, 160, 0.1);
        }
    </style>
</head>
<body>
    <div class="resume-container">
        <!-- Left Sidebar -->
        <aside class="sidebar">
            <div class="profile-section">
                <div class="name-box">
                    <h1>{{NAME}}</h1>
                    <h2>{{ENGLISH_NAME}}</h2>
                </div>
            </div>

            <div class="sidebar-section">
                <div class="sidebar-title">联系方式</div>
                <div class="contact-list">
                    <div class="contact-item">
                        <svg viewBox="0 0 24 24"><path d="M6.62 10.79c1.44 2.83 3.76 5.14 6.59 6.59l2.2-2.2c.27-.27.67-.36 1.02-.24 1.12.37 2.33.57 3.57.57.55 0 1 .45 1 1V20c0 .55-.45 1-1 1-9.39 0-17-7.61-17-17 0-.55.45-1 1-1h3.5c.55 0 1 .45 1 1 0 1.25.2 2.45.57 3.57.11.35.03.74-.25 1.02l-2.2 2.2z"/></svg>
                        <span>{{PHONE}}</span>
                    </div>
                    <div class="contact-item">
                        <svg viewBox="0 0 24 24"><path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/></svg>
                        <span>{{EMAIL}}</span>
                    </div>
                    <div class="contact-item">
                        <svg viewBox="0 0 24 24"><path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"/></svg>
                        <span>{{LOCATION}}</span>
                    </div>
                </div>
            </div>

            <div class="sidebar-section">
                <div class="sidebar-title">教育经历</div>
                <!-- 循环渲染教育经历 -->
                {{#EDUCATION_LIST}}
                <div class="edu-item">
                    <div class="edu-school">{{SCHOOL}}</div>
                    <div class="edu-meta">{{DEGREE_MAJOR}}</div>
                    <div class="edu-meta">{{YEAR}}</div>
                </div>
                {{/EDUCATION_LIST}}
            </div>

            <div class="sidebar-section">
                <div class="sidebar-title">技能专长</div>
                
                <!-- 循环渲染技能分类 -->
                {{#SKILL_CATEGORIES}}
                <div class="skill-category">
                    <span class="skill-cat-title">{{CATEGORY_NAME}}</span>
                    <div class="skill-tags">
                        {{#SKILLS}}
                        <span class="sidebar-tag">{{.}}</span>
                        {{/SKILLS}}
                    </div>
                </div>
                {{/SKILL_CATEGORIES}}
            </div>

            <div class="sidebar-section">
                <div class="sidebar-title">资质证书</div>
                <div class="skill-tags">
                    {{#CERTIFICATES}}
                    <span class="sidebar-tag">{{.}}</span>
                    {{/CERTIFICATES}}
                </div>
            </div>
        </aside>

        <!-- Main Content -->
        <main class="main-content">
            <section class="content-section">
                <div class="content-title">
                    <svg viewBox="0 0 24 24"><path d="M20 6h-4V4c0-1.11-.89-2-2-2h-4c-1.11 0-2 .89-2 2v2H4c-1.11 0-1.99.89-1.99 2L2 19c0 1.11.89 2 2 2h16c1.11 0 2-.89 2-2V8c0-1.11-.89-2-2-2zm-6 0h-4V4h4v2z"/></svg>
                    工作经历
                </div>

                <!-- 循环渲染工作经历 -->
                {{#WORK_EXPERIENCE}}
                <div class="experience-item">
                    <div class="job-header">
                        <span class="company">{{COMPANY}}</span>
                        <span class="job-period">{{PERIOD}}</span>
                    </div>
                    <div class="role-name">{{ROLE}}</div>
                    <div class="job-desc">
                        <ul>
                            {{#ACHIEVEMENTS}}
                            <li>{{.}}</li>
                            {{/ACHIEVEMENTS}}
                        </ul>
                    </div>
                </div>
                {{/WORK_EXPERIENCE}}

            </section>
        </main>
    </div>
</body>
</html>
```
