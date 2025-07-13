def generate_github_readme():
    # User Inputs
    name = "Saddam Hossain"
    title = "Applied Mathematics Student | Data Science Enthusiast"
    about_me = """
    Passionate about leveraging **Machine Learning, Deep Learning, SQL, and Power BI** to solve real-world problems. 
    Strong mathematical background with a focus on data-driven decision-making. 
    Constantly learning and exploring new technologies in AI and data science.
    """
    skills = {
        "Programming": "Python, SQL",
        "Data Analysis": "Pandas, NumPy, Power BI, Excel",
        "Machine Learning": "Scikit-learn, TensorFlow, PyTorch",
        "Data Visualization": "Matplotlib, Seaborn, Power BI",
        "Database": "MySQL, PostgreSQL",
        "Tools": "Git, Jupyter Notebook, VS Code"
    }
    education = "BSc in Applied Mathematics (Your University Name)"
    projects_link = "https://github.com/yourusername?tab=repositories"
    contact = {
        "Email": "youremail@example.com",
        "LinkedIn": "https://linkedin.com/in/yourprofile",
        "Twitter/X": "https://twitter.com/yourhandle (optional)"
    }
    
    # Generate README content
    readme_content = f"""
# 👋 Hello, I'm {name}

### {title}

{about_me}

## 🛠️ Skills
"""
    # Add skills in a formatted way
    for category, items in skills.items():
        readme_content += f"- **{category}:** {items}\n"
    
    readme_content += f"""
## 🎓 Education
- {education}

## 🚀 Projects
Check out my projects [here]({projects_link})!

## 📫 Contact Me
"""
    # Add contact links
    for platform, link in contact.items():
        readme_content += f"- [{platform}]({link})\n"
    
    # Footer
    readme_content += """
---
⚡ **Fun Fact:** I love turning complex problems into simple, data-driven solutions!
"""
    
    # Save to README.md
    with open("README.md", "w", encoding="utf-8") as file:
        file.write(readme_content.strip())
    
    print("✅ README.md generated successfully!")

# Run the function
generate_github_readme()
