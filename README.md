
# 🎯 BugBounty Recon - Automated Reconnaissance Framework

![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Security](https://img.shields.io/badge/Security-Bug%20Bounty-red?style=for-the-badge)

**BugBounty Recon** is a web platform and automated framework designed to orchestrate reconnaissance pipelines for security audits and Bug Bounty programs. It seamlessly integrates the most popular community tools into a continuous workflow, all managed through an intuitive web interface.

<img width="1355" height="587" alt="Captura desde 2026-09-07 16-33-59" src="https://github.com/user-attachments/assets/cc198c4b-16be-4642-88ee-de738bc6dc11" />

---

## ✨ Key Features

*   **🖥️ Centralized Web Interface:** Launch scans, configure parameters, and review results comfortably from a unified dashboard.
*   **⚙️ Background Tasks:** Asynchronous execution of heavy scanning processes without blocking the user experience.
*   **🧩 Modular Architecture:**
    *   🔍 **Subdomain Enumeration:** Exhaustive discovery of the target's attack surface.
    *   🛡️ **WAF Detection:** Identification of Web Application Firewalls.
    *   🚪 **Port Scanning:** Integration with Nmap to discover exposed services.
    *   🌐 **Web Server Analysis:** Live endpoint checking and technology fingerprinting using HTTPX.
    *   🕷️ **Endpoint Discovery:** Extraction of hidden routes and parameters (Katana integration).
    *   ☢️ **Vulnerability Scanning:** Automated flaw hunting using Nuclei templates.
*   **🔔 Notification System:** Real-time alerts on new findings.
*   **🐳 100% Dockerized:** Fast, clean, and dependency-conflict-free deployment using Docker and Docker Compose.

---

## 📁 Project Structure

```text
bugbounty_reconv/
├── main.py                     # Web application entry point
├── tasks.py                    # Asynchronous task manager (background jobs)
├── docker-compose.yml          # Container orchestration
├── .env                        # Environment variables and secrets
├── certs/                      # SSL certificates for the web application
├── templates/                  # HTML views (Dashboard, Results, Settings, Login)
├── static/                     # Static files (CSS, JS, Favicon)
├── output/                     # Generated reports categorized by target and date
└── bugbounty_recon/            # Core Reconnaissance Engine
    ├── bugbounty_recon.py      # Main pipeline script
    ├── config/                 # JSON configurations for the scanner
    └── modules/                # Phase-specific modules (Nmap, Nuclei, Subdomains, etc.)
```

---

## 🚀 Installation & Deployment

The fastest and recommended way to deploy the platform is using Docker.

### Prerequisites
*   [Docker](https://docs.docker.com/get-docker/)
*   [Docker Compose](https://docs.docker.com/compose/install/)

### Setup Steps

1. **Clone the repository:**
   ```bash
   git clone https://github.com/rootzro/bugbounty_recon.git
   cd bugbounty_reconv
   ```

2. **Configure environment variables:**
   Edit the `.env` file in the root directory to set your secure credentials, API tokens (if used for subdomain enum), and database/messaging configurations.

3. **Spin up the services:**
   ```bash
   docker-compose up -d --build
   ```

4. **Access the platform:**
   Open your web browser and navigate to `https://localhost:8000` (or your configured port). Log in using your credentials.

---

## 💻 Usage

1. **Login:** Access the web platform using your secure account.
2. **Dashboard:** Enter the target domain you want to audit.
3. **Settings:** Toggle the modules you wish to run (e.g., skip port scanning, use specific Nuclei templates, run WAF detection).
4. **Results:** Once the background task finishes, head over to the results tab. Data is neatly organized into folders (e.g., `recon_target.com_date/`) dividing the findings into:
   *   `/subdomains/`
   *   `/ports/`
   *   `/vulnerabilities/`
   *   `/endpoints/`
   *   `/waf/`

---

## ⚠️ Disclaimer

This project was created **for educational and research purposes only**. The use of this tool to attack targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state, and federal laws. The developer assumes no liability and is not responsible for any misuse or damage caused by this program. Use it only on authorized Bug Bounty programs or your own systems.

---

## 🤝 Contributing

Contributions are always welcome! If you want to improve the recon engine, add new tools to the pipeline, or enhance the web UI:
1. Fork the Project.
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`).
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`).
4. Push to the Branch (`git push origin feature/AmazingFeature`).
5. Open a Pull Request.
