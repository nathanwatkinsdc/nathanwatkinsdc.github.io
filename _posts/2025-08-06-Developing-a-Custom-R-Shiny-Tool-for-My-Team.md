---
layout: default
title: Developing a Custom R Shiny Tool for My Team
date: 2025-08-06
thumbnail: /assets/images/shiny.png
description: How I used R Shiny to reduce the friction involved with being called back to the office in early 2025
---

# Making RTO a little more… Shiny

## 📋 Adapting to new reporting requirements
Federal agencies have always maintained records of employee attendance and work locations, but recent policy changes have introduced even more requirements. What was once a matter of “we’re all in the office” has evolved into a matrix of office days, telework schedules, AWS (flex day) arrangements, and various approved work locations 😵‍💫

In early 2025, my team and I found ourselves managing this complexity with a shared Word document, eventually graduating to an Excel spreadsheet, which quickly became unwieldy for this or that reason. Version conflicts, lost edits, and the general friction of email-based coordination were consuming valuable time that could be better spent on mission-critical work.
## 🗃️ The Excel problem
Here’s what we had in our Excel attendance tracking system:

- **Pay period tabs** with two-week cycles
- **Team member roster** with work schedules and AWS days
- **Daily attendance columns** for each business day
- **Reference codes** for various work locations and leave types
- **Color coding** for different attendance statuses

This approach was functional but had limitations: 

- **Concurrent editing conflicts** when multiple people updated simultaneously
- **Version control issues** with multiple copies floating around
- **Mobile accessibility challenges** for managers checking attendance on phones
- **Manual backup and recovery** processes
- **Limited audit trail** for compliance purposes

We had the skills to overcome these limitations on the team, so why not go for it?!
## 🛤️ R Shiny was the way
As RTO was introduced, so were budget cuts, so whatever solution we came up with couldn’t cost any money. I decided to pitch a solution using [R Shiny](https://shiny.posit.co/)—a powerful framework for creating web applications with R offering several advantages:
### Technical advantages
- **Open source** with no licensing costs
- **Government-friendly** with extensive federal adoption
- **Rapid development** cycle for iterative improvements
- **Familiar R ecosystem** already used for data analysis at my organization
- **Self-hosted** for complete data control
### User experience benefits
- **Browser-based access** from any device including organization phones
- **Real-time collaboration** without version conflicts
- **Familiar interface** mimicking Excel functionality
- **Mobile responsive** design for on-the-go access
- **Integrated reference materials** with built-in help

## 📸 Screenshots of our R Shiny tool
Having developed an R Shiny dashboard or two before, it didn’t take too long to whip something up. With anonymized (and slightly silly) names, here’s what my coworkers and I see in our browsers when we want to log where we’ll be working on a given day:

<img src="/assets/images/screenshot-1.png" alt="Screenshot of main R Shiny window" style="width:80%; max-width:700px;">

Users interact with the window by entering for a given day where they’ll be working. Blank means default location, which is in the office. Other values include AWS (flex day), LOC1 (non-office location 1), etc. Users can check the other codes by navigating through the left-hand menu:

<img src="/assets/images/screenshot-2.png" alt="Screenshot of R Shiny window" style="width:80%; max-width:700px;">

Users can also check their colleagues’ work schedules to see when their flex days are, i.e., when they are regularly out of the office (e.g., every second Friday) by navigating the left-hand menu as well: 

<img src="/assets/images/screenshot-3.png" alt="Screenshot of R Shiny window" style="width:80%; max-width:700px;">

## Developing your own R Shiny tool like mine
If you want to implement a similar solution, here’s how to get started:
### Prerequisites

```r
# Install R, RStudio, and then the required packages below:
install.packages(c(
  "shiny", "DT", "shinydashboard", 
  "shinyWidgets", "jsonlite", "DBI", 
  "RSQLite", "pool"
))
```

### Quick setup and customization

```bash
# Clone the repository
git clone https://github.com/nathanwatkinsdc/rto-attendance.git
cd rto-attendance

# Set up the database
Rscript scripts/setup_database.R

# Run the application
Rscript -e "shiny::runApp()"
```

The application will open in your default browser at `http://localhost:3838`. Now you can customize for your different organizational needs using the modular setup:

- **Team data** in `data/team_data.csv`
- **Reason codes** in `database/seed_data.sql`
- **Pay periods** automatically generated or manually configured
- **Styling** through CSS customization in `www/custom.css`
## Production deployment using Shiny Server
To deploy in your organization, you’ll need to use Shiny Server, which provides enterprise-grade hosting with proper authentication, logging, and scalability. It may be best to get IT involved, but either way, you’ll need a server with certain specs like: 

**Server Specifications:**
- Ubuntu 20.04+ or CentOS 8+ (recommended)
- 4GB RAM minimum (8GB+ for larger teams)
- 2 CPU cores minimum
- 50GB storage (includes logs and backups)

**Network Requirements:**
- Internal network access for team members
- Optional: secure external access through VPN
- SSL certificate for HTTPS (Let's Encrypt recommended)

### Installation Process
Assuming admin rights, you can install the server and deploy the application. 

**1. Server Setup**

```bash
# Install R and system dependencies
sudo apt update
sudo apt install -y r-base r-base-dev libcurl4-openssl-dev \
  libssl-dev libxml2-dev postgresql postgresql-contrib nginx

# Install Shiny Server
wget https://download3.rstudio.org/ubuntu-18.04/x86_64/shiny-server-1.5.20.1002-amd64.deb
sudo dpkg -i shiny-server-1.5.20.1002-amd64.deb
```

**2. Application Deployment**

```bash
# Deploy application
sudo cp -r attendance-tracking /srv/shiny-server/
sudo chown -R shiny:shiny /srv/shiny-server/attendance-tracking

# Install R dependencies
sudo R -e "install.packages(c('shiny', 'DT', 'shinydashboard', 'shinyWidgets', 'jsonlite',
'DBI', 'RPostgreSQL', 'pool'), repos='https://cran.rstudio.com/')"
```

**3. Database Configuration**

For production use, PostgreSQL provides better performance and reliability:

```bash
# Create database and user
sudo -u postgres createdb attendance_prod
sudo -u postgres createuser -P app_user

# Apply schema
psql -U app_user -d attendance_prod -f database/schema.sql
psql -U app_user -d attendance_prod -f database/seed_data.sql
```

**4. SSL and Security Setup**

```bash
# Install Let's Encrypt
sudo apt install certbot python3-certbot-nginx

# Obtain SSL certificate
sudo certbot --nginx -d your-domain.organization.gov

# Configure Nginx reverse proxy
sudo nano /etc/nginx/sites-available/attendance-tracking
```

### Security and operational considerations
Federal deployment requires attention to several security aspects, so, again, you’ll want to consult IT wherever you work. These aspects include authentication integration, data protection, and network security.

As for operational considerations, here’s some code to help with **monitoring and maintenance**

```bash
# Setup log rotation
sudo logrotate -f /etc/logrotate.d/shiny-server

# Monitor application health
curl -f http://localhost:3838/attendance-tracking/health

# Database backup automation
sudo crontab -e
# 0 2 * * * /scripts/backup_database.sh
```

### 🧑‍🏫 Lessons learned
1. **User training and support:** there are several ways to support users. I like using wikis with screenshots. You can also have training sessions and integrate existing help desks. You can introduce change management processes for feature updates.
2. **Technical insights:** it’s definitely best to start simple. Basic functionality first, then more advanced features. 
3. **Organizational insights:** keeping the interface familiar reduced the need for training. Developing the tool with scalability in mind made it easy to apply to multiple organizational units.
4. **Compliance benefits:** change histories and required reports are all automated. Robust data protection means all backup and recovery requirements are met.

## 🏁 Conclusion: innovation in government is possible (if practical)
Open-source tools are a great solution for teams facing operational challenges (e.g., federal teams). To find the source code, documentation, and deployment guides for my open-source tool, check out my [GitHub](https://github.com/nathanwatkinsdc/rto-attendance). 

## Conclusion: Practical Innovation in Government
This project demonstrates how teams under constraints can leverage open-source tools to solve real operational challenges. By building on familiar interfaces while adding modern collaboration capabilities, we created a solution that improves both efficiency and compliance.

The complete source code, documentation, and deployment guides are available in our GitHub repository, enabling other federal teams to adapt this solution for their specific needs. The investment in learning these technologies pays dividends not only in immediate operational improvements but also in building internal technical capabilities for future challenges.

For federal IT professionals considering similar projects, the combination of R Shiny's rapid development capabilities and robust deployment options provides an attractive alternative to expensive commercial solutions or lengthy procurement processes. The key is starting with a clear understanding of user needs and building iteratively toward a production-ready solution.

_In this post, I refer to an attendance tracking application used at the organization where I work. The tool shared on my GitHub is not this tool but rather a similar tool that I developed on my own and in my personal time in a similar fashion using open-source tools. This post does

---
## Resources

- **GitHub Repository**: [attendance-tracking](https://github.com/your-org/attendance-tracking)
- **Deployment Guide**: [docs/deployment.md](https://claude.ai/chat/docs/deployment.md)
- **User Documentation**: [docs/user_guide.md](https://claude.ai/chat/docs/user_guide.md)
- **R Shiny Resources**: [shiny.rstudio.com](https://shiny.rstudio.com/)
- **Federal R Community**: [gsa.github.io/federal-source-code](https://gsa.github.io/federal-source-code)
