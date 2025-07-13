<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GitHub Profile README Generator</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            color: #333;
            background-color: #f5f5f5;
        }
        h1 {
            color: #0366d6;
            text-align: center;
        }
        .container {
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }
        .form-group {
            margin-bottom: 15px;
        }
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        input, textarea, select {
            width: 100%;
            padding: 8px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-family: inherit;
        }
        textarea {
            min-height: 100px;
            resize: vertical;
        }
        button {
            background: #0366d6;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
        }
        button:hover {
            background: #0056b3;
        }
        #output {
            margin-top: 20px;
            padding: 15px;
            background: #f8f9fa;
            border: 1px solid #ddd;
            border-radius: 4px;
            white-space: pre-wrap;
            font-family: monospace;
        }
        .skill-item {
            display: flex;
            margin-bottom: 10px;
        }
        .skill-item input {
            flex: 1;
            margin-right: 10px;
        }
        .remove-skill {
            background: #dc3545;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>GitHub Profile README Generator</h1>
        
        <div class="form-group">
            <label for="name">Your Name</label>
            <input type="text" id="name" placeholder="Saddam Hossain">
        </div>
        
        <div class="form-group">
            <label for="title">Professional Title</label>
            <input type="text" id="title" placeholder="Applied Mathematics Student | Data Science Enthusiast">
        </div>
        
        <div class="form-group">
            <label for="about">About You</label>
            <textarea id="about" placeholder="Passionate about Machine Learning, Deep Learning, SQL, and Power BI..."></textarea>
        </div>
        
        <div class="form-group">
            <label>Skills</label>
            <div id="skills-container">
                <div class="skill-item">
                    <input type="text" placeholder="Category (e.g., Programming)" class="skill-category">
                    <input type="text" placeholder="Skills (e.g., Python, SQL)" class="skill-items">
                    <button type="button" class="remove-skill">×</button>
                </div>
            </div>
            <button type="button" id="add-skill">+ Add Skill</button>
        </div>
        
        <div class="form-group">
            <label for="education">Education</label>
            <input type="text" id="education" placeholder="BSc in Applied Mathematics">
        </div>
        
        <div class="form-group">
            <label for="projects">Projects Link</label>
            <input type="text" id="projects" placeholder="https://github.com/yourusername?tab=repositories">
        </div>
        
        <div class="form-group">
            <label>Contact Info</label>
            <div id="contact-container">
                <div class="skill-item">
                    <input type="text" placeholder="Platform (e.g., Email)" class="contact-platform">
                    <input type="text" placeholder="Link/Info (e.g., you@example.com)" class="contact-link">
                    <button type="button" class="remove-contact">×</button>
                </div>
            </div>
            <button type="button" id="add-contact">+ Add Contact</button>
        </div>
        
        <button type="button" id="generate">Generate README</button>
        
        <div class="form-group">
            <label for="output">Your GitHub README.md</label>
            <textarea id="output" readonly></textarea>
        </div>
    </div>

    <script>
        // Add new skill row
        document.getElementById('add-skill').addEventListener('click', function() {
            const div = document.createElement('div');
            div.className = 'skill-item';
            div.innerHTML = `
                <input type="text" placeholder="Category (e.g., Programming)" class="skill-category">
                <input type="text" placeholder="Skills (e.g., Python, SQL)" class="skill-items">
                <button type="button" class="remove-skill">×</button>
            `;
            document.getElementById('skills-container').appendChild(div);
            addRemoveListeners();
        });

        // Add new contact row
        document.getElementById('add-contact').addEventListener('click', function() {
            const div = document.createElement('div');
            div.className = 'skill-item';
            div.innerHTML = `
                <input type="text" placeholder="Platform (e.g., Email)" class="contact-platform">
                <input type="text" placeholder="Link/Info (e.g., you@example.com)" class="contact-link">
                <button type="button" class="remove-contact">×</button>
            `;
            document.getElementById('contact-container').appendChild(div);
            addRemoveListeners();
        });

        // Add event listeners to remove buttons
        function addRemoveListeners() {
            document.querySelectorAll('.remove-skill').forEach(btn => {
                btn.addEventListener('click', function() {
                    this.parentElement.remove();
                });
            });
            document.querySelectorAll('.remove-contact').forEach(btn => {
                btn.addEventListener('click', function() {
                    this.parentElement.remove();
                });
            });
        }

        // Initial setup
        addRemoveListeners();

        // Generate README
        document.getElementById('generate').addEventListener('click', function() {
            const name = document.getElementById('name').value || 'Your Name';
            const title = document.getElementById('title').value || 'Your Title';
            const about = document.getElementById('about').value || 'A short bio about yourself...';
            const education = document.getElementById('education').value || 'Your education background';
            const projects = document.getElementById('projects').value || 'https://github.com/yourusername';

            // Process skills
            let skillsMarkdown = '';
            document.querySelectorAll('.skill-item').forEach(item => {
                const category = item.querySelector('.skill-category')?.value;
                const items = item.querySelector('.skill-items')?.value;
                if (category && items) {
                    skillsMarkdown += `- **${category}:** ${items}\n`;
                }
            });

            // Process contacts
            let contactsMarkdown = '';
            document.querySelectorAll('.skill-item').forEach(item => {
                const platform = item.querySelector('.contact-platform')?.value;
                const link = item.querySelector('.contact-link')?.value;
                if (platform && link) {
                    if (link.startsWith('http') || link.includes('@')) {
                        contactsMarkdown += `- [${platform}](${link})\n`;
                    } else {
                        contactsMarkdown += `- **${platform}:** ${link}\n`;
                    }
                }
            });

            // Generate the README content
            const readmeContent = `# 👋 Hello, I'm ${name}

### ${title}

${about}

## 🛠️ Skills
${skillsMarkdown || 'Add your skills above'}

## 🎓 Education
- ${education}

## 🚀 Projects
Check out my projects [here](${projects})!

## 📫 Contact Me
${contactsMarkdown || 'Add your contact info above'}

---
⚡ **Fun Fact:** I love turning complex problems into simple solutions!
`;

            document.getElementById('output').value = readmeContent;
        });
    </script>
</body>
</html>
