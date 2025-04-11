<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Spider RnD</title>
    <style>
        :root {
            --primary-bg: #011B30;
            --secondary-bg: #04132A;
            --accent-blue: #5591EA;
            --text-primary: #ffffff;
            --text-secondary: #7A7A7A;
            --button-blue: #558dff;
            --card-bg: rgba(17, 34, 64, 0.3);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
        }
        
        body {
            background-color: var(--primary-bg);
            color: var(--text-primary);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }
        
        .sidebar {
            width: 200px;
            background-color: var(--secondary-bg);
            padding: 20px 0;
            display: flex;
            flex-direction: column;
            border-right: 1px solid rgba(255, 255, 255, 0.1);
            height: 100vh;
            position: fixed;
            left: 0;
            top: 0;
        }
        
        .logo-container {
            display: flex;
            align-items: center;
            padding: 0 20px 20px;
        }
        
        .logo {
            width: 36px;
            height: 36px;
            margin-right: 10px;
            border-radius: 4px;
        }
        
        .logo-text {
            font-size: 1.2rem;
            font-weight: 600;
            color: var(--accent-blue);
        }
        
        .nav-item {
            display: flex;
            align-items: center;
            padding: 12px 20px;
            color: var(--text-secondary);
            text-decoration: none;
            margin: 2px 0;
        }
        
        .nav-item.active {
            background-color: rgba(74, 136, 247, 0.1);
            color: var(--accent-blue);
            border-left: 3px solid var(--accent-blue);
        }
        
        .nav-icon {
            margin-right: 12px;
            width: 20px;
            height: 20px;
        }
        
        .main-content {
            margin-left: 200px;
            padding: 20px;
            flex: 1;
        }
        
        .search-container {
            display: flex;
            margin-bottom: 30px;
            justify-content: space-between;
        }
        
        .search-box {
            display: flex;
            align-items: center;
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 25px;
            padding: 8px 16px;
            width: 60%;
            max-width: 500px;
        }
        
        .search-input {
            background: transparent;
            border: none;
            color: var(--text-primary);
            font-size: 16px;
            outline: none;
            flex: 1;
            margin-left: 8px;
        }
        
        .search-icon {
            color: var(--text-secondary);
        }
        
        .add-project-btn {
            background-color: var(--button-blue);
            color: white;
            border: none;
            border-radius: 25px;
            padding: 10px 20px;
            font-size: 14px;
            font-weight: 500;
            cursor: pointer;
        }
        
        .page-header {
            font-size: 2.8rem;
            font-weight: 600;
            margin-bottom: 20px;
        }
        
        .top-nav {
            display: flex;
            margin-bottom: 40px;
            overflow-x: auto;
            white-space: nowrap;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            padding-bottom: 5px;
        }
        
        .nav-tab {
            padding: 12px 24px;
            margin-right: 10px;
            font-size: 16px;
            color: var(--text-secondary);
            cursor: pointer;
            position: relative;
        }
        
        .nav-tab.active {
            color: var(--text-primary);
        }
        
        .nav-tab.active::after {
            content: '';
            position: absolute;
            bottom: -6px;
            left: 0;
            right: 0;
            height: 2px;
            background-color: var(--accent-blue);
        }
        
        .section-header {
            font-size: 2rem;
            font-weight: 600;
            margin-bottom: 30px;
        }
        
        .table-header {
            display: grid;
            grid-template-columns: 280px 1fr 1fr;
            padding: 12px 20px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            color: var(--text-secondary);
            font-size: 14px;
        }
        
        .member-card {
            display: grid;
            grid-template-columns: 280px 1fr 1fr;
            padding: 12px 20px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.05);
            align-items: center;
        }
        
        .member-info {
            display: flex;
            align-items: center;
        }
        
        .member-avatar {
            width: 48px;
            height: 48px;
            border-radius: 50%;
            margin-right: 16px;
        }
        
        .member-name {
            font-weight: 500;
        }
        
        .tag {
            display: inline-block;
            padding: 4px 12px;
            background-color: rgba(74, 136, 247, 0.2);
            color: var(--accent-blue);
            border-radius: 20px;
            font-size: 12px;
            margin-right: 8px;
        }
        
        .project-info {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .project-text {
            font-size: 14px;
            color: var(--text-secondary);
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            flex: 1;
            padding-right: 15px;
        }
        
        .details-btn {
            background-color: rgba(255, 255, 255, 0.1);
            color: var(--text-secondary);
            border: none;
            border-radius: 20px;
            padding: 6px 16px;
            font-size: 12px;
            cursor: pointer;
            white-space: nowrap;
        }
        
        .footer {
            margin-top: auto;
            padding: 20px;
        }
        
        .footer-btn {
            display: flex;
            align-items: center;
            background: none;
            border: none;
            color: var(--text-secondary);
            cursor: pointer;
            padding: 8px 12px;
            margin-bottom: 8px;
            width: 100%;
            text-align: left;
        }
        
        .footer-icon {
            margin-right: 12px;
        }
    </style>
</head>
<body>
    <div class="sidebar">
        <div class="logo-container">
            <img src="/api/placeholder/36/36" alt="Spider RnD Logo" class="logo">
            <div class="logo-text">Spider RnD</div>
        </div>
        
        <a href="#" class="nav-item">
            <svg class="nav-icon" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <rect x="3" y="3" width="7" height="7" rx="1" stroke="currentColor" stroke-width="2"/>
                <rect x="3" y="14" width="7" height="7" rx="1" stroke="currentColor" stroke-width="2"/>
                <rect x="14" y="3" width="7" height="7" rx="1" stroke="currentColor" stroke-width="2"/>
                <rect x="14" y="14" width="7" height="7" rx="1" stroke="currentColor" stroke-width="2"/>
            </svg>
            Overview
        </a>
        
        <a href="#" class="nav-item">
            <svg class="nav-icon" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M3 21L12 4L21 21H3Z" stroke="currentColor" stroke-width="2"/>
            </svg>
            Projects
        </a>
        
        <a href="#" class="nav-item active">
            <svg class="nav-icon" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M17 21V19C17 17.9391 16.5786 16.9217 15.8284 16.1716C15.0783 15.4214 14.0609 15 13 15H5C3.93913 15 2.92172 15.4214 2.17157 16.1716C1.42143 16.9217 1 17.9391 1 19V21" stroke="currentColor" stroke-width="2"/>
                <circle cx="9" cy="7" r="4" stroke="currentColor" stroke-width="2"/>
                <path d="M23 21V19C22.9993 18.1137 22.7044 17.2528 22.1614 16.5523C21.6184 15.8519 20.8581 15.3516 20 15.13" stroke="currentColor" stroke-width="2"/>
                <path d="M16 3.13C16.8604 3.35031 17.623 3.85071 18.1676 4.55232C18.7122 5.25392 19.0078 6.11683 19.0078 7.005C19.0078 7.89318 18.7122 8.75608 18.1676 9.45769C17.623 10.1593 16.8604 10.6597 16 10.88" stroke="currentColor" stroke-width="2"/>
            </svg>
            Members
        </a>
        
        <a href="#" class="nav-item">
            <svg class="nav-icon" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="12" cy="12" r="10" stroke="currentColor" stroke-width="2"/>
                <path d="M12 6V12L16 14" stroke="currentColor" stroke-width="2"/>
            </svg>
            Help
        </a>
        
        <div class="footer">
            <button class="footer-btn">
                <svg class="footer-icon" width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M9 21H5C4.46957 21 3.96086 20.7893 3.58579 20.4142C3.21071 20.0391 3 19.5304 3 19V5C3 4.46957 3.21071 3.96086 3.58579 3.58579C3.96086 3.21071 4.46957 3 5 3H9" stroke="currentColor" stroke-width="2"/>
                    <path d="M16 17L21 12L16 7" stroke="currentColor" stroke-width="2"/>
                    <path d="M21 12H9" stroke="currentColor" stroke-width="2"/>
                </svg>
                Switch Organisation
            </button>
            
            <button class="footer-btn">
                <svg class="footer-icon" width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M12 17V12M12 12V7M12 12H17M12 12H7" stroke="currentColor" stroke-width="2"/>
                    <circle cx="12" cy="12" r="10" stroke="currentColor" stroke-width="2"/>
                </svg>
                Switch Appearance
            </button>
            
            <button class="footer-btn">
                <svg class="footer-icon" width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M4 6H20M4 12H20M4 18H20" stroke="currentColor" stroke-width="2"/>
                </svg>
                More
            </button>
        </div>
    </div>
    
    <div class="main-content">
        <div class="search-container">
            <div class="search-box">
                <svg class="search-icon" width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M21 21L15.8033 15.8033M15.8033 15.8033C17.1605 14.4461 18 12.5711 18 10.5C18 6.35786 14.6421 3 10.5 3C6.35786 3 3 6.35786 3 10.5C3 14.6421 6.35786 18 10.5 18C12.5711 18 14.4461 17.1605 15.8033 15.8033Z" stroke="currentColor" stroke-width="2"/>
                </svg>
                <input type="text" class="search-input" placeholder="Search a members, organisations, etc ...">
            </div>
            
            <button class="add-project-btn">Add a project</button>
        </div>
        
        <h1 class="page-header">Members</h1>
        
        <div class="top-nav">
            <div class="nav-tab">EXCOMMS</div>
            <div class="nav-tab active">UI UX</div>
            <div class="nav-tab">Devops</div>
            <div class="nav-tab">Blockchain</div>
            <div class="nav-tab">ML</div>
            <div class="nav-tab">Cybersecurity</div>
        </div>
        
        <h2 class="section-header">UI UX</h2>
        
        <div class="table-header">
            <div>Member</div>
            <div>Domains</div>
            <div>Projects</div>
        </div>
        
        <!-- Member 1 -->
        <div class="member-card">
            <div class="member-info">
                <img src="/api/placeholder/48/48" alt="Sanjay Sriram" class="member-avatar">
                <div class="member-name">Sanjay Sriram</div>
            </div>
            <div>
                <span class="tag">UI UX</span>
            </div>
            <div class="project-info">
                <div class="project-text">Lorem Ipsum, Lorem Ipsum...</div>
                <button class="details-btn">See details</button>
            </div>
        </div>
        
        <!-- Member 2 -->
        <div class="member-card">
            <div class="member-info">
                <img src="/api/placeholder/48/48" alt="Sanjay Sriram" class="member-avatar">
                <div class="member-name">Sanjay Sriram</div>
            </div>
            <div>
                <span class="tag">Web Dev</span>
            </div>
            <div class="project-info">
                <div class="project-text">Lorem Ipsum, Lorem Ipsum...</div>
                <button class="details-btn">See details</button>
            </div>
        </div>
        
        <!-- Member 3 -->
        <div class="member-card">
            <div class="member-info">
                <img src="/api/placeholder/48/48" alt="Sanjay Sriram" class="member-avatar">
                <div class="member-name">Sanjay Sriram</div>
            </div>
            <div>
                <span class="tag">UI UX</span>
            </div>
            <div class="project-info">
                <div class="project-text">Lorem Ipsum, Lorem Ipsum...</div>
                <button class="details-btn">See details</button>
            </div>
        </div>
        
        <!-- Member 4 -->
        <div class="member-card">
            <div class="member-info">
                <img src="/api/placeholder/48/48" alt="Sanjay Sriram" class="member-avatar">
                <div class="member-name">Sanjay Sriram</div>
            </div>
            <div>
                <span class="tag">Web Dev</span>
                <span class="tag">UI UX</span>
            </div>
            <div class="project-info">
                <div class="project-text">Lorem Ipsum, Lorem Ipsum...</div>
                <button class="details-btn">See details</button>
            </div>
        </div>
        
        <!-- Member 5 -->
        <div class="member-card">
            <div class="member-info">
                <img src="/api/placeholder/48/48" alt="Sanjay Sriram" class="member-avatar">
                <div class="member-name">Sanjay Sriram</div>
            </div>
            <div>
                <span class="tag">Web Dev</span>
            </div>
            <div class="project-info">
                <div class="project-text">Lorem Ipsum, Lorem Ipsum...</div>
                <button class="details-btn">See details</button>
            </div>
        </div>
    </div>
</body>
</html>
