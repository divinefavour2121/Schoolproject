<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ScoreSheet - Academic Management System</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #3498db;
            --primary-dark: #2980b9;
            --secondary: #2c3e50;
            --accent: #27ae60;
            --accent-dark: #219653;
            --light: #f8f9fa;
            --dark: #1a2530;
            --gray: #7f8c8d;
            --light-gray: #e1e5eb;
            --danger: #e74c3c;
            --success: #2ecc71;
            --warning: #f39c12;
            --admin-blue: #1e3a8a;
            --admin-blue-light: #3b82f6;
        }

        body {
            background: linear-gradient(135deg, #1e5799, #207cca, #2989d8, #1e5799);
            color: #333;
            line-height: 1.6;
            min-height: 100vh;
            overflow-x: hidden;
        }

        .page-container {
            display: none;
            min-height: 100vh;
            animation: fadeIn 0.5s ease;
        }

        .active-page {
            display: block;
        }

        /* Header Styles */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 40px;
            background: rgba(0, 0, 0, 0.2);
        }

        .logo {
            display: flex;
            align-items: center;
        }

        .logo i {
            font-size: 32px;
            color: white;
            margin-right: 15px;
        }

        .logo-text h1 {
            font-size: 24px;
            font-weight: 700;
            color: white;
            letter-spacing: 0.5px;
        }

        .logo-text p {
            color: rgba(255, 255, 255, 0.8);
            font-size: 14px;
        }

        .nav-links {
            display: flex;
            gap: 15px;
        }

        .nav-btn {
            background: rgba(255, 255, 255, 0.15);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 50px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 8px;
            font-size: 15px;
        }

        .nav-btn:hover {
            background: rgba(255, 255, 255, 0.25);
            transform: translateY(-3px);
        }

        .nav-btn i {
            font-size: 16px;
        }

        /* Homepage Styles */
        .home-container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }

        .hero {
            display: flex;
            align-items: center;
            margin: 40px 0 60px;
            gap: 50px;
        }

        .hero-content {
            flex: 1;
            color: white;
        }

        .hero-content h2 {
            font-size: 42px;
            margin-bottom: 20px;
            line-height: 1.2;
        }

        .hero-content p {
            font-size: 18px;
            margin-bottom: 30px;
            opacity: 0.9;
            max-width: 600px;
        }

        .hero-image {
            flex: 1;
            display: flex;
            justify-content: center;
        }

        .hero-image img {
            max-width: 100%;
            border-radius: 15px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
        }

        .cta-buttons {
            display: flex;
            gap: 20px;
            margin-top: 30px;
        }

        .cta-btn {
            padding: 14px 30px;
            border-radius: 50px;
            font-size: 16px;
            font-weight: 600;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .cta-btn-primary {
            background: var(--accent);
            color: white;
            box-shadow: 0 8px 15px rgba(39, 174, 96, 0.3);
        }

        .cta-btn-primary:hover {
            background: var(--accent-dark);
            transform: translateY(-3px);
            box-shadow: 0 12px 20px rgba(39, 174, 96, 0.4);
        }

        .cta-btn-secondary {
            background: rgba(255, 255, 255, 0.15);
            color: white;
            backdrop-filter: blur(5px);
        }

        .cta-btn-secondary:hover {
            background: rgba(255, 255, 255, 0.25);
            transform: translateY(-3px);
        }

        /* Login Cards */
        .section-title {
            text-align: center;
            margin-bottom: 50px;
            color: white;
        }

        .section-title h2 {
            font-size: 32px;
            margin-bottom: 15px;
            position: relative;
            display: inline-block;
        }

        .section-title h2:after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 4px;
            background: var(--accent);
            border-radius: 2px;
        }

        .section-title p {
            font-size: 17px;
            max-width: 700px;
            margin: 20px auto 0;
            opacity: 0.9;
        }

        .cards {
            display: flex;
            flex-wrap: wrap;
            gap: 30px;
            margin-bottom: 60px;
            justify-content: center;
        }

        .card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            padding: 35px;
            width: 100%;
            max-width: 450px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
            border: 1px solid rgba(255, 255, 255, 0.15);
            transition: all 0.3s ease;
        }

        .card:hover {
            transform: translateY(-10px);
            background: rgba(255, 255, 255, 0.15);
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
        }

        .card-icon {
            width: 90px;
            height: 90px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.15);
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 25px;
            font-size: 36px;
            color: white;
        }

        .card h3 {
            font-size: 24px;
            margin-bottom: 20px;
            color: white;
        }

        .card p {
            color: rgba(255, 255, 255, 0.85);
            margin-bottom: 30px;
            font-size: 16px;
        }

        .card-btn {
            display: inline-block;
            padding: 12px 30px;
            background: var(--primary);
            color: white;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            font-size: 16px;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .card-btn:hover {
            background: var(--primary-dark);
            transform: translateY(-3px);
            box-shadow: 0 8px 15px rgba(52, 152, 219, 0.3);
        }

        /* Features Section */
        .features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 25px;
            margin-bottom: 60px;
        }

        .feature {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.15);
            transition: all 0.3s ease;
        }

        .feature:hover {
            transform: translateY(-5px);
            background: rgba(255, 255, 255, 0.15);
        }

        .feature i {
            font-size: 40px;
            color: var(--accent);
            margin-bottom: 20px;
        }

        .feature h3 {
            font-size: 20px;
            color: white;
            margin-bottom: 15px;
        }

        .feature p {
            color: rgba(255, 255, 255, 0.85);
            font-size: 15px;
        }

        /* Footer */
        footer {
            background: rgba(0, 0, 0, 0.2);
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            margin-top: 40px;
            color: rgba(255, 255, 255, 0.8);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .footer-links {
            display: flex;
            justify-content: center;
            gap: 25px;
            margin: 15px 0;
            flex-wrap: wrap;
        }

        .footer-links a {
            color: rgba(255, 255, 255, 0.8);
            text-decoration: none;
            transition: all 0.3s ease;
        }

        .footer-links a:hover {
            color: white;
            text-decoration: underline;
        }

        .copyright {
            margin-top: 15px;
            font-size: 14px;
        }

        /* Login Pages */
        .login-container {
            display: flex;
            max-width: 1100px;
            width: 100%;
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
            margin: 40px auto;
        }

        .left-panel {
            flex: 1;
            background: linear-gradient(to bottom right, var(--secondary), var(--dark));
            color: white;
            padding: 50px 40px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        .admin-graphic {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0.08;
            background:
                radial-gradient(circle at 20% 30%, rgba(52, 152, 219, 0.3) 0%, transparent 40%),
                radial-gradient(circle at 80% 70%, rgba(46, 204, 113, 0.3) 0%, transparent 40%);
        }

        .login-logo {
            text-align: center;
            margin-bottom: 40px;
            position: relative;
            z-index: 2;
        }

        .login-logo i {
            font-size: 48px;
            color: var(--primary);
            margin-bottom: 15px;
            background: rgba(255, 255, 255, 0.1);
            width: 90px;
            height: 90px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 20px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }

        .login-logo h1 {
            font-size: 28px;
            font-weight: 700;
            color: #fff;
            letter-spacing: 0.5px;
            margin-bottom: 10px;
        }

        .login-logo p {
            color: rgba(255, 255, 255, 0.7);
            font-size: 16px;
        }

        .features {
            margin-top: 40px;
            position: relative;
            z-index: 2;
        }

        .feature-item {
            display: flex;
            align-items: center;
            margin-bottom: 25px;
            padding: 15px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            border-left: 3px solid var(--primary);
            transition: all 0.3s ease;
        }

        .feature-item:hover {
            background: rgba(255, 255, 255, 0.1);
            transform: translateX(5px);
        }

        .feature-item i {
            font-size: 22px;
            color: var(--primary);
            margin-right: 15px;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.1);
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .feature-item div {
            color: #ecf0f1;
            font-size: 15px;
        }

        .right-panel {
            flex: 1;
            padding: 50px 40px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            background: #f8fafc;
        }

        .welcome {
            margin-bottom: 40px;
            text-align: center;
        }

        .welcome h2 {
            font-size: 28px;
            margin-bottom: 15px;
            color: var(--secondary);
            position: relative;
            display: inline-block;
            padding-bottom: 15px;
        }

        .welcome h2:after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 60px;
            height: 4px;
            background: var(--primary);
            border-radius: 2px;
        }

        .welcome p {
            color: var(--gray);
            font-size: 17px;
            margin-top: 15px;
        }

        .form-group {
            margin-bottom: 25px;
            position: relative;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--secondary);
            font-size: 15px;
        }

        .input-with-icon {
            position: relative;
        }

        .input-with-icon i {
            position: absolute;
            left: 15px;
            top: 50%;
            transform: translateY(-50%);
            color: var(--gray);
            font-size: 18px;
        }

        .form-control {
            width: 100%;
            padding: 15px 15px 15px 50px;
            border: 2px solid var(--light-gray);
            border-radius: 10px;
            font-size: 16px;
            transition: all 0.3s ease;
            background: white;
        }

        .form-control:focus {
            border-color: var(--primary);
            outline: none;
            box-shadow: 0 0 0 4px rgba(52, 152, 219, 0.2);
        }

        .btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 15px 20px;
            font-size: 17px;
            font-weight: 600;
            border-radius: 10px;
            cursor: pointer;
            width: 100%;
            transition: all 0.3s ease;
            box-shadow: 0 6px 12px rgba(52, 152, 219, 0.25);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .btn:hover {
            background: var(--primary-dark);
            transform: translateY(-3px);
            box-shadow: 0 8px 15px rgba(52, 152, 219, 0.3);
        }

        .btn:active {
            transform: translateY(-1px);
        }

        .login-link {
            text-align: center;
            margin-top: 25px;
            color: var(--gray);
            font-size: 15px;
        }

        .login-link a {
            color: var(--primary);
            text-decoration: none;
            font-weight: 600;
            transition: color 0.3s ease;
        }

        .login-link a:hover {
            color: var(--primary-dark);
            text-decoration: underline;
        }

        .copyright {
            text-align: center;
            margin-top: 30px;
            color: var(--gray);
            font-size: 14px;
            border-top: 1px solid var(--light-gray);
            padding-top: 20px;
        }

        .security-info {
            background: #e3f2fd;
            border-radius: 10px;
            padding: 15px;
            margin-top: 20px;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .security-info i {
            color: var(--primary);
            font-size: 18px;
            min-width: 30px;
        }

        .security-info p {
            color: var(--secondary);
            font-size: 14px;
        }

        /* Level and Semester Selector */
        .level-selector {
            display: flex;
            gap: 15px;
            margin-bottom: 25px;
            flex-wrap: wrap;
        }

        .level-card {
            flex: 1;
            min-width: 150px;
            background: white;
            border-radius: 10px;
            padding: 20px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            border: 2px solid var(--light-gray);
        }

        .level-card:hover,
        .level-card.active {
            border-color: var(--primary);
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(52, 152, 219, 0.2);
        }

        .level-card i {
            font-size: 36px;
            color: var(--primary);
            margin-bottom: 10px;
        }

        .level-card h3 {
            color: var(--secondary);
            margin-bottom: 5px;
        }

        .semester-selector {
            display: flex;
            gap: 15px;
            margin-bottom: 25px;
        }

        .semester-card {
            flex: 1;
            background: white;
            border-radius: 10px;
            padding: 20px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            border: 2px solid var(--light-gray);
        }

        .semester-card:hover,
        .semester-card.active {
            border-color: var(--accent);
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(39, 174, 96, 0.2);
        }

        .semester-card i {
            font-size: 36px;
            color: var(--accent);
            margin-bottom: 10px;
        }

        .semester-card h3 {
            color: var(--secondary);
            margin-bottom: 5px;
        }

        /* Dashboard Styles */
        .dashboard-container {
            display: flex;
            min-height: calc(100vh - 80px);
            max-width: 1600px;
            margin: 0 auto;
        }

        /* Sidebar Styles */
        .sidebar {
            width: 250px;
            background: linear-gradient(to bottom, var(--primary), var(--primary-dark));
            color: white;
            padding: 20px 0;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
            position: relative;
            z-index: 100;
        }

        .dashboard-logo {
            text-align: center;
            padding: 20px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            margin-bottom: 20px;
        }

        .dashboard-logo i {
            font-size: 32px;
            color: #fff;
            margin-bottom: 10px;
        }

        .dashboard-logo h1 {
            font-size: 20px;
            font-weight: 600;
            letter-spacing: 0.5px;
        }

        .user-info {
            text-align: center;
            padding: 20px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        .user-info img {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid rgba(255, 255, 255, 0.2);
            margin-bottom: 15px;
        }

        .user-info h2 {
            font-size: 18px;
            margin-bottom: 5px;
        }

        .user-info p {
            font-size: 14px;
            opacity: 0.8;
        }

        .nav-links-dash {
            padding: 20px 0;
        }

  