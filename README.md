<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crimeson - Discord Role & Donation Platform</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Exo+2:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #ff3b30;
            --primary-dark: #cc0000;
            --primary-light: #ff6b60;
            --secondary: #0d0d0d;
            --accent: #8c0d05;
            --accent-light: #a82e26;
            --light: #f5f5f5;
            --dark: #0a0a0a;
            --gray: #1a1a1a;
            --gray-light: #2a2a2a;
            --success: #3ba55c;
            --warning: #f39c12;
            --text: #e6e6e6;
            --text-light: #b3b3b3;
            --shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
            --transition: all 0.3s ease;
            --transition-slow: all 0.5s ease;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background-color: var(--dark);
            color: var(--text);
            line-height: 1.6;
            overflow-x: hidden;
            font-family: 'Exo 2', sans-serif;
            background-image: 
                radial-gradient(circle at 10% 20%, rgba(255, 59, 48, 0.05) 0%, transparent 20%),
                radial-gradient(circle at 90% 80%, rgba(140, 13, 5, 0.05) 0%, transparent 20%),
                linear-gradient(to bottom, var(--dark), var(--secondary));
        }

        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }

        /* Header Styles */
        header {
            background-color: rgba(13, 13, 13, 0.95);
            box-shadow: var(--shadow);
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
            backdrop-filter: blur(10px);
            transition: var(--transition);
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 0;
        }

        .logo {
            font-size: 32px;
            font-weight: 900;
            color: var(--primary);
            display: flex;
            align-items: center;
            text-transform: uppercase;
            letter-spacing: 2px;
            font-family: 'Orbitron', sans-serif;
            text-shadow: 0 0 10px rgba(255, 59, 48, 0.5);
        }

        .logo i {
            margin-right: 12px;
            color: var(--accent);
            text-shadow: 0 0 15px rgba(255, 59, 48, 0.7);
        }

        nav ul {
            display: flex;
            list-style: none;
        }

        nav ul li {
            margin-left: 30px;
            position: relative;
        }

        nav ul li a {
            text-decoration: none;
            color: var(--text);
            font-weight: 500;
            transition: var(--transition);
            position: relative;
            font-size: 16px;
            padding: 5px 0;
        }

        nav ul li a:after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: linear-gradient(90deg, var(--primary), var(--accent));
            transition: var(--transition);
        }

        nav ul li a:hover {
            color: var(--primary);
        }

        nav ul li a:hover:after {
            width: 100%;
        }

        .nav-buttons {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .btn {
            padding: 12px 24px;
            border-radius: 6px;
            text-decoration: none;
            font-weight: 600;
            transition: var(--transition);
            display: inline-flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            text-align: center;
            position: relative;
            overflow: hidden;
            z-index: 1;
        }

        .btn:before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: var(--transition-slow);
            z-index: -1;
        }

        .btn:hover:before {
            left: 100%;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--primary), var(--accent));
            color: white;
            box-shadow: 0 4px 15px rgba(255, 59, 48, 0.3);
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(255, 59, 48, 0.4);
        }

        .btn-outline {
            border: 2px solid var(--primary);
            color: var(--primary);
            background: transparent;
        }

        .btn-outline:hover {
            background-color: var(--primary);
            color: white;
        }

        .btn-large {
            padding: 16px 32px;
            font-size: 18px;
        }

        .btn-discord {
            background: #5865f2;
            color: white;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .btn-discord:hover {
            background: #4752c4;
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(88, 101, 242, 0.4);
        }

        /* Hero Section */
        .hero {
            padding: 160px 0 100px;
            text-align: center;
            position: relative;
            overflow: hidden;
            min-height: 100vh;
            display: flex;
            align-items: center;
        }

        .hero-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                radial-gradient(circle at 20% 50%, rgba(255, 59, 48, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 80% 20%, rgba(140, 13, 5, 0.1) 0%, transparent 50%);
            z-index: -1;
        }

        .hero-content {
            max-width: 900px;
            margin: 0 auto;
            position: relative;
            z-index: 2;
        }

        .hero h1 {
            font-size: 4rem;
            margin-bottom: 24px;
            color: var(--text);
            text-shadow: 0 2px 10px rgba(0, 0, 0, 0.5);
            font-family: 'Orbitron', sans-serif;
            line-height: 1.2;
        }

        .hero h1 span {
            background: linear-gradient(135deg, var(--primary), var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: none;
        }

        .hero p {
            font-size: 1.3rem;
            max-width: 700px;
            margin: 0 auto 50px;
            color: var(--text-light);
            font-weight: 300;
        }

        .hero-buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 40px;
        }

        .floating-elements {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            overflow: hidden;
            z-index: 1;
        }

        .floating-element {
            position: absolute;
            background: rgba(255, 59, 48, 0.1);
            border-radius: 50%;
            animation: float 20s infinite linear;
        }

        .floating-element:nth-child(1) {
            width: 100px;
            height: 100px;
            top: 10%;
            left: 10%;
            animation-delay: 0s;
        }

        .floating-element:nth-child(2) {
            width: 150px;
            height: 150px;
            top: 60%;
            left: 80%;
            animation-delay: -5s;
        }

        .floating-element:nth-child(3) {
            width: 70px;
            height: 70px;
            top: 80%;
            left: 20%;
            animation-delay: -10s;
        }

        .floating-element:nth-child(4) {
            width: 120px;
            height: 120px;
            top: 30%;
            left: 70%;
            animation-delay: -15s;
        }

        @keyframes float {
            0% {
                transform: translateY(0) rotate(0deg);
            }
            50% {
                transform: translateY(-20px) rotate(180deg);
            }
            100% {
                transform: translateY(0) rotate(360deg);
            }
        }

        /* Discord Section */
        .discord {
            padding: 100px 0;
            background: linear-gradient(to bottom, var(--secondary), var(--dark));
        }

        .discord-container {
            display: flex;
            align-items: center;
            gap: 50px;
        }

        .discord-content {
            flex: 1;
        }

        .discord-visual {
            flex: 1;
            display: flex;
            justify-content: center;
        }

        .discord-steps {
            margin-top: 40px;
        }

        .discord-step {
            display: flex;
            align-items: flex-start;
            margin-bottom: 30px;
            padding: 20px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            border-left: 4px solid var(--primary);
        }

        .step-number {
            background: var(--primary);
            color: white;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            margin-right: 20px;
            flex-shrink: 0;
        }

        .step-content h4 {
            margin-bottom: 10px;
            font-size: 1.2rem;
        }

        .discord-graphic {
            width: 300px;
            height: 300px;
            background: linear-gradient(135deg, var(--gray), var(--dark));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            border: 2px solid #5865f2;
            box-shadow: 0 0 30px rgba(88, 101, 242, 0.3);
        }

        .discord-graphic:before {
            content: '';
            position: absolute;
            top: -10px;
            left: -10px;
            right: -10px;
            bottom: -10px;
            border-radius: 50%;
            background: linear-gradient(135deg, #5865f2, #4752c4);
            z-index: -1;
            opacity: 0.2;
        }

        .discord-graphic i {
            font-size: 5rem;
            color: #5865f2;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }

        /* Roles Section */
        .roles {
            padding: 100px 0;
            position: relative;
        }

        .section-title {
            text-align: center;
            margin-bottom: 80px;
        }

        .section-title h2 {
            font-size: 3rem;
            color: var(--text);
            margin-bottom: 20px;
            position: relative;
            display: inline-block;
            font-family: 'Orbitron', sans-serif;
        }

        .section-title h2:after {
            content: '';
            position: absolute;
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 4px;
            background: linear-gradient(90deg, var(--primary), var(--accent));
            border-radius: 2px;
        }

        .section-title p {
            color: var(--text-light);
            max-width: 700px;
            margin: 0 auto;
            font-size: 1.2rem;
            font-weight: 300;
        }

        .roles-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 40px;
        }

        .role-card {
            background: linear-gradient(145deg, var(--gray), var(--dark));
            border-radius: 12px;
            padding: 40px 30px;
            box-shadow: var(--shadow);
            transition: var(--transition);
            text-align: center;
            border: 1px solid rgba(255, 59, 48, 0.2);
            position: relative;
            overflow: hidden;
            z-index: 1;
        }

        .role-card:before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, var(--primary), var(--accent));
        }

        .role-card:after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(255, 59, 48, 0.05) 0%, transparent 50%);
            opacity: 0;
            transition: var(--transition);
            z-index: -1;
        }

        .role-card:hover {
            transform: translateY(-15px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.6);
            border-color: rgba(255, 59, 48, 0.4);
        }

        .role-card:hover:after {
            opacity: 1;
        }

        .role-icon {
            font-size: 4rem;
            margin-bottom: 25px;
            color: var(--primary);
            text-shadow: 0 0 15px rgba(255, 59, 48, 0.5);
        }

        .role-card h3 {
            margin-bottom: 15px;
            font-size: 2rem;
            color: var(--text);
            font-family: 'Orbitron', sans-serif;
        }

        .role-card .role-desc {
            color: var(--text-light);
            margin-bottom: 25px;
            font-size: 1rem;
        }

        .role-price {
            font-weight: bold;
            color: var(--primary);
            font-size: 2rem;
            margin: 25px 0;
            text-shadow: 0 0 10px rgba(255, 59, 48, 0.3);
        }

        .role-features {
            list-style: none;
            margin: 25px 0;
            text-align: left;
        }

        .role-features li {
            margin-bottom: 12px;
            padding-left: 30px;
            position: relative;
            transition: var(--transition);
        }

        .role-features li:hover {
            color: var(--primary-light);
            transform: translateX(5px);
        }

        .role-features li:before {
            content: '✓';
            position: absolute;
            left: 0;
            color: var(--success);
            font-weight: bold;
            font-size: 1.2rem;
        }

        .role-popular {
            position: absolute;
            top: 20px;
            right: -30px;
            background: linear-gradient(135deg, var(--primary), var(--accent));
            color: white;
            padding: 8px 40px;
            transform: rotate(45deg);
            font-weight: bold;
            font-size: 0.9rem;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
        }

        /* Products Section */
        .products {
            padding: 100px 0;
            background: linear-gradient(to bottom, var(--secondary), var(--dark));
            position: relative;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 30px;
        }

        .product-card {
            background: linear-gradient(145deg, var(--gray), var(--dark));
            border-radius: 12px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: var(--transition);
            border: 1px solid rgba(255, 59, 48, 0.2);
            position: relative;
        }

        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.5);
            border-color: rgba(255, 59, 48, 0.4);
        }

        .product-img {
            height: 200px;
            background: linear-gradient(45deg, var(--dark), var(--accent));
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        .product-img i {
            font-size: 5rem;
            color: rgba(255, 255, 255, 0.9);
            z-index: 2;
            text-shadow: 0 0 20px rgba(255, 59, 48, 0.5);
        }

        .product-img:after {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255, 255, 255, 0.1), transparent);
            transform: rotate(45deg);
            animation: shimmer 3s infinite;
        }

        @keyframes shimmer {
            0% { transform: rotate(45deg) translate(-50%, -50%); }
            100% { transform: rotate(45deg) translate(50%, 50%); }
        }

        .product-info {
            padding: 25px;
        }

        .product-info h3 {
            margin-bottom: 10px;
            font-size: 1.5rem;
            color: var(--text);
        }

        .product-info p {
            color: var(--text-light);
            margin-bottom: 20px;
            font-size: 0.95rem;
            line-height: 1.5;
        }

        .product-price {
            font-weight: bold;
            color: var(--primary);
            font-size: 1.5rem;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .product-btn {
            width: 100%;
            text-align: center;
            padding: 14px;
            font-size: 1.1rem;
        }

        /* Payment Section */
        .payment {
            padding: 100px 0;
            position: relative;
        }

        .payment-methods {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 25px;
            margin-top: 60px;
        }

        .payment-method {
            background: linear-gradient(145deg, var(--gray), var(--dark));
            padding: 25px;
            border-radius: 12px;
            box-shadow: var(--shadow);
            width: 160px;
            text-align: center;
            transition: var(--transition);
            border: 1px solid rgba(255, 59, 48, 0.2);
            position: relative;
        }

        .payment-method:hover {
            transform: translateY(-10px) scale(1.05);
            border-color: rgba(255, 59, 48, 0.4);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4);
        }

        .payment-icon {
            font-size: 3rem;
            margin-bottom: 15px;
            color: var(--primary);
        }

        /* Auth Section */
        .auth {
            padding: 100px 0;
            background: linear-gradient(to bottom, var(--secondary), var(--dark));
            position: relative;
        }

        .auth-container {
            max-width: 500px;
            margin: 0 auto;
            background: linear-gradient(145deg, var(--gray), var(--dark));
            padding: 50px 40px;
            border-radius: 12px;
            box-shadow: var(--shadow);
            border: 1px solid rgba(255, 59, 48, 0.2);
            position: relative;
            overflow: hidden;
        }

        .auth-container:before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, var(--primary), var(--accent));
        }

        .auth-tabs {
            display: flex;
            margin-bottom: 40px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        .auth-tab {
            flex: 1;
            text-align: center;
            padding: 15px;
            cursor: pointer;
            border-bottom: 3px solid transparent;
            transition: var(--transition);
            font-weight: 500;
            font-size: 1.1rem;
        }

        .auth-tab.active {
            border-bottom: 3px solid var(--primary);
            color: var(--primary);
            font-weight: 600;
        }

        .auth-form {
            display: none;
        }

        .auth-form.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .form-group {
            margin-bottom: 25px;
            position: relative;
        }

        .form-group label {
            display: block;
            margin-bottom: 10px;
            font-weight: 500;
            color: var(--text);
        }

        .form-group input {
            width: 100%;
            padding: 15px;
            background-color: rgba(13, 13, 13, 0.7);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 6px;
            font-size: 1rem;
            color: var(--text);
            transition: var(--transition);
        }

        .form-group input:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 2px rgba(255, 59, 48, 0.3);
        }

        .form-btn {
            width: 100%;
            padding: 15px;
            background: linear-gradient(135deg, var(--primary), var(--accent));
            color: white;
            border: none;
            border-radius: 6px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            margin-top: 10px;
        }

        .form-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(255, 59, 48, 0.4);
        }

        .auth-divider {
            text-align: center;
            margin: 30px 0;
            position: relative;
        }

        .auth-divider::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 0;
            right: 0;
            height: 1px;
            background-color: rgba(255, 255, 255, 0.1);
            z-index: 1;
        }

        .auth-divider span {
            background-color: var(--gray);
            padding: 0 20px;
            position: relative;
            z-index: 2;
            color: var(--text-light);
            font-size: 0.9rem;
        }

        .discord-auth {
            background-color: #5865f2;
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
            padding: 15px;
            border-radius: 6px;
            text-decoration: none;
            font-weight: 600;
            transition: var(--transition);
            font-size: 1.1rem;
        }

        .discord-auth:hover {
            background-color: #4752c4;
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(88, 101, 242, 0.4);
        }

        /* Footer */
        footer {
            background-color: var(--secondary);
            color: white;
            padding: 80px 0 30px;
            position: relative;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 50px;
            margin-bottom: 60px;
        }

        .footer-column h3 {
            font-size: 1.3rem;
            margin-bottom: 25px;
            color: var(--primary);
            font-family: 'Orbitron', sans-serif;
        }

        .footer-column p {
            color: #ccc;
            line-height: 1.6;
            margin-bottom: 20px;
        }

        .footer-column ul {
            list-style: none;
        }

        .footer-column ul li {
            margin-bottom: 12px;
        }

        .footer-column ul li a {
            color: #ccc;
            text-decoration: none;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .footer-column ul li a:hover {
            color: var(--primary);
            transform: translateX(5px);
        }

        .social-links {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .social-links a {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            background: var(--gray);
            border-radius: 50%;
            color: var(--text);
            transition: var(--transition);
        }

        .social-links a:hover {
            background: var(--primary);
            color: white;
            transform: translateY(-5px);
        }

        .copyright {
            text-align: center;
            padding-top: 30px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: #999;
            font-size: 0.9rem;
        }

        /* Scroll to top button */
        .scroll-top {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 50px;
            height: 50px;
            background: linear-gradient(135deg, var(--primary), var(--accent));
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: var(--transition);
            opacity: 0;
            visibility: hidden;
            z-index: 999;
            box-shadow: 0 4px 15px rgba(255, 59, 48, 0.4);
        }

        .scroll-top.active {
            opacity: 1;
            visibility: visible;
        }

        .scroll-top:hover {
            transform: translateY(-5px);
            box-shadow: 0 6px 20px rgba(255, 59, 48, 0.6);
        }

        /* Responsive Design */
        @media (max-width: 992px) {
            .hero h1 {
                font-size: 3.2rem;
            }
            
            .section-title h2 {
                font-size: 2.5rem;
            }

            .discord-container {
                flex-direction: column;
            }
        }

        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                text-align: center;
                padding: 15px 0;
            }

            nav ul {
                margin-top: 20px;
                flex-wrap: wrap;
                justify-content: center;
            }

            nav ul li {
                margin: 0 10px 10px;
            }

            .nav-buttons {
                margin-top: 20px;
            }

            .hero {
                padding: 140px 0 80px;
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .hero p {
                font-size: 1.1rem;
            }

            .hero-buttons {
                flex-direction: column;
                align-items: center;
                gap: 15px;
            }

            .roles-grid,
            .products-grid {
                grid-template-columns: 1fr;
            }

            .payment-methods {
                flex-direction: column;
                align-items: center;
            }

            .payment-method {
                width: 100%;
                max-width: 250px;
            }

            .footer-content {
                grid-template-columns: 1fr;
                gap: 40px;
            }
        }

        /* Animation classes */
        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: opacity 0.8s ease, transform 0.8s ease;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container">
            <div class="header-content">
                <div class="logo">
                    <i class="fas fa-fire"></i>
                    <span>Crimeson</span>
                </div>
                <nav>
                    <ul>
                        <li><a href="#home">Home</a></li>
                        <li><a href="#discord">Discord</a></li>
                        <li><a href="#roles">Roles</a></li>
                        <li><a href="#donations">Donations</a></li>
                        <li><a href="#payment">Payment</a></li>
                        <li><a href="#auth">Account</a></li>
                    </ul>
                </nav>
                <div class="nav-buttons">
                    <a href="#auth" class="btn btn-outline">Sign In</a>
                    <a href="#auth" class="btn btn-primary">Register</a>
                </div>
            </div>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="hero-bg"></div>
        <div class="floating-elements">
            <div class="floating-element"></div>
            <div class="floating-element"></div>
            <div class="floating-element"></div>
            <div class="floating-element"></div>
        </div>
        <div class="container">
            <div class="hero-content">
                <h1>Unlock Exclusive <span>Roles</span> & Support Our Community</h1>
                <p>Join the Crimeson elite with premium roles and donation packages. Get exclusive perks, early access to content, and help us build an amazing community.</p>
                <div class="hero-buttons">
                    <a href="#roles" class="btn btn-primary btn-large">Explore Roles</a>
                    <a href="#discord" class="btn btn-discord btn-large">
                        <i class="fab fa-discord"></i>
                        Join Our Discord
                    </a>
                </div>
            </div>
        </div>
    </section>

    <!-- Discord Section -->
    <section class="discord" id="discord">
        <div class="container">
            <div class="section-title">
                <h2>Join Our Discord Community</h2>
                <p>Connect with our community, get verified, and unlock exclusive content</p>
            </div>
            <div class="discord-container">
                <div class="discord-content">
                    <h3>Discord Verification Process</h3>
                    <p>Our white verification bot ensures a safe and authentic community by verifying all members before granting access to exclusive channels and features.</p>
                    
                    <div class="discord-steps">
                        <div class="discord-step">
                            <div class="step-number">1</div>
                            <div class="step-content">
                                <h4>Join Our Server</h4>
                                <p>Click the link below to join our Discord community.</p>
                            </div>
                        </div>
                        <div class="discord-step">
                            <div class="step-number">2</div>
                            <div class="step-content">
                                <h4>Complete Verification</h4>
                                <p>Follow the instructions from our verification bot to get verified.</p>
                            </div>
                        </div>
                        <div class="discord-step">
                            <div class="step-number">3</div>
                            <div class="step-content">
                                <h4>Access Exclusive Content</h4>
                                <p>Once verified, you'll gain access to member-only channels and features.</p>
                            </div>
                        </div>
                    </div>
                    
                    <a href="https://discord.gg/PTUS6TXTTj" class="btn btn-discord" target="_blank">
                        <i class="fab fa-discord"></i>
                        Join Discord Server
                    </a>
                </div>
                <div class="discord-visual">
                    <div class="discord-graphic">
                        <i class="fab fa-discord"></i>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Roles Section -->
    <section class="roles" id="roles">
        <div class="container">
            <div class="section-title">
                <h2>Exclusive Roles</h2>
                <p>Choose from our three premium role tiers, each with unique benefits and community recognition</p>
            </div>
            <div class="roles-grid">
                <div class="role-card fade-in">
                    <div class="role-icon">
                        <i class="fas fa-shield-alt"></i>
                    </div>
                    <h3>Guardian</h3>
                    <p class="role-desc">Basic support role with essential perks and community recognition</p>
                    <div class="role-price">$4.99</div>
                    <ul class="role-features">
                        <li>Special Discord role color</li>
                        <li>Access to #supporters channel</li>
                        <li>Early previews of new features</li>
                        <li>Custom emoji access</li>
                        <li>Priority support</li>
                        <li>Monthly community events</li>
                    </ul>
                    <a href="#payment" class="btn btn-primary">Get Role</a>
                </div>
                <div class="role-card fade-in">
                    <div class="role-popular">MOST POPULAR</div>
                    <div class="role-icon">
                        <i class="fas fa-crown"></i>
                    </div>
                    <h3>Noble</h3>
                    <p class="role-desc">Premium role with enhanced benefits and exclusive content access</p>
                    <div class="role-price">$9.99</div>
                    <ul class="role-features">
                        <li>All Guardian perks</li>
                        <li>Exclusive Noble badge</li>
                        <li>Access to VIP channels</li>
                        <li>Monthly Q&A with developers</li>
                        <li>Ability to suggest features</li>
                        <li>Custom title in server</li>
                        <li>Early access to beta features</li>
                    </ul>
                    <a href="#payment" class="btn btn-primary">Get Role</a>
                </div>
                <div class="role-card fade-in">
                    <div class="role-icon">
                        <i class="fas fa-dragon"></i>
                    </div>
                    <h3>Legend</h3>
                    <p class="role-desc">The ultimate role with all perks and maximum community influence</p>
                    <div class="role-price">$19.99</div>
                    <ul class="role-features">
                        <li>All Noble perks</li>
                        <li>Exclusive Legend badge</li>
                        <li>Personalized thank you video</li>
                        <li>Direct communication with team</li>
                        <li>Early access to all updates</li>
                        <li>Special role in community events</li>
                        <li>Physical merchandise discount</li>
                        <li>Name in credits</li>
                    </ul>
                    <a href="#payment" class="btn btn-primary">Get Role</a>
                </div>
            </div>
        </div>
    </section>

    <!-- Products Section -->
    <section class="products" id="donations">
        <div class="container">
            <div class="section-title">
                <h2>Donation Packages</h2>
                <p>Support our community and receive special rewards and recognition</p>
            </div>
            <div class="products-grid">
                <div class="product-card fade-in">
                    <div class="product-img">
                        <i class="fas fa-heart"></i>
                    </div>
                    <div class="product-info">
                        <h3>Supporter Pack</h3>
                        <p>Show your support with this basic donation package and get a special role color</p>
                        <div class="product-price">
                            <span>$2.99</span>
                        </div>
                        <a href="#payment" class="btn btn-primary product-btn">Donate Now</a>
                    </div>
                </div>
                <div class="product-card fade-in">
                    <div class="product-img">
                        <i class="fas fa-star"></i>
                    </div>
                    <div class="product-info">
                        <h3>Booster Pack</h3>
                        <p>Boost your support and get additional perks including custom emoji slots</p>
                        <div class="product-price">
                            <span>$7.99</span>
                        </div>
                        <a href="#payment" class="btn btn-primary product-btn">Donate Now</a>
                    </div>
                </div>
                <div class="product-card fade-in">
                    <div class="product-img">
                        <i class="fas fa-gem"></i>
                    </div>
                    <div class="product-info">
                        <h3>Premium Pack</h3>
                        <p>Premium donation package with exclusive rewards and priority in events</p>
                        <div class="product-price">
                            <span>$14.99</span>
                        </div>
                        <a href="#payment" class="btn btn-primary product-btn">Donate Now</a>
                    </div>
                </div>
                <div class="product-card fade-in">
                    <div class="product-img">
                        <i class="fas fa-award"></i>
                    </div>
                    <div class="product-info">
                        <h3>Ultimate Pack</h3>
                        <p>The ultimate donation package for our most dedicated supporters with all perks</p>
                        <div class="product-price">
                            <span>$29.99</span>
                        </div>
                        <a href="#payment" class="btn btn-primary product-btn">Donate Now</a>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Payment Section -->
    <section class="payment" id="payment">
        <div class="container">
            <div class="section-title">
                <h2>Payment Methods</h2>
                <p>We support all major payment options for your convenience</p>
            </div>
            <div class="payment-methods">
                <div class="payment-method">
                    <div class="payment-icon">
                        <i class="fas fa-credit-card"></i>
                    </div>
                    <h4>Credit Cards</h4>
                </div>
                <div class="payment-method">
                    <div class="payment-icon">
                        <i class="fab fa-paypal"></i>
                    </div>
                    <h4>PayPal</h4>
                </div>
                <div class="payment-method">
                    <div class="payment-icon">
                        <i class="fab fa-google-pay"></i>
                    </div>
                    <h4>Google Pay</h4>
                </div>
                <div class="payment-method">
                    <div class="payment-icon">
                        <i class="fab fa-apple-pay"></i>
                    </div>
                    <h4>Apple Pay</h4>
                </div>
                <div class="payment-method">
                    <div class="payment-icon">
                        <i class="fab fa-bitcoin"></i>
                    </div>
                    <h4>Cryptocurrency</h4>
                </div>
            </div>
        </div>
    </section>

    <!-- Auth Section -->
    <section class="auth" id="auth">
        <div class="container">
            <div class="section-title">
                <h2>Login / Register</h2>
                <p>Access your account using Discord or traditional email authentication</p>
            </div>
            <div class="auth-container">
                <div class="auth-tabs">
                    <div class="auth-tab active" data-tab="login">Login</div>
                    <div class="auth-tab" data-tab="register">Register</div>
                </div>
                <div class="auth-form active" id="login-form">
                    <div class="form-group">
                        <label for="login-email">Email</label>
                        <input type="email" id="login-email" placeholder="Enter your email">
                    </div>
                    <div class="form-group">
                        <label for="login-password">Password</label>
                        <input type="password" id="login-password" placeholder="Enter your password">
                    </div>
                    <button class="form-btn">Login</button>
                    <div class="auth-divider">
                        <span>Or continue with</span>
                    </div>
                    <a href="#" class="discord-auth">
                        <i class="fab fa-discord"></i>
                        Login with Discord
                    </a>
                </div>
                <div class="auth-form" id="register-form">
                    <div class="form-group">
                        <label for="register-name">Username</label>
                        <input type="text" id="register-name" placeholder="Choose a username">
                    </div>
                    <div class="form-group">
                        <label for="register-email">Email</label>
                        <input type="email" id="register-email" placeholder="Enter your email">
                    </div>
                    <div class="form-group">
                        <label for="register-password">Password</label>
                        <input type="password" id="register-password" placeholder="Create a password">
                    </div>
                    <button class="form-btn">Create Account</button>
                    <div class="auth-divider">
                        <span>Or continue with</span>
                    </div>
                    <a href="#" class="discord-auth">
                        <i class="fab fa-discord"></i>
                        Register with Discord
                    </a>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>Crimeson</h3>
                    <p>The premium role and donation platform with exclusive benefits for our community members. Join us today and unlock amazing perks!</p>
                    <div class="social-links">
                        <a href="https://discord.gg/PTUS6TXTTj" target="_blank"><i class="fab fa-discord"></i></a>
                        <a href="#"><i class="fab fa-twitter"></i></a>
                        <a href="#"><i class="fab fa-instagram"></i></a>
                        <a href="#"><i class="fab fa-youtube"></i></a>
                    </div>
                </div>
                <div class="footer-column">
                    <h3>Quick Links</h3>
                    <ul>
                        <li><a href="#home"><i class="fas fa-chevron-right"></i> Home</a></li>
                        <li><a href="#discord"><i class="fas fa-chevron-right"></i> Discord</a></li>
                        <li><a href="#roles"><i class="fas fa-chevron-right"></i> Roles</a></li>
                        <li><a href="#donations"><i class="fas fa-chevron-right"></i> Donations</a></li>
                        <li><a href="#payment"><i class="fas fa-chevron-right"></i> Payment</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Support</h3>
                    <ul>
                        <li><a href="#"><i class="fas fa-chevron-right"></i> FAQ</a></li>
                        <li><a href="#"><i class="fas fa-chevron-right"></i> Terms of Service</a></li>
                        <li><a href="#"><i class="fas fa-chevron-right"></i> Privacy Policy</a></li>
                        <li><a href="#"><i class="fas fa-chevron-right"></i> Contact Us</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Contact Info</h3>
                    <ul>
                        <li><a href="#"><i class="fas fa-envelope"></i> support@crimeson.com</a></li>
                        <li><a href="https://discord.gg/PTUS6TXTTj" target="_blank"><i class="fab fa-discord"></i> Join Our Discord</a></li>
                        <li><a href="#"><i class="fas fa-globe"></i> www.crimeson.com</a></li>
                    </ul>
                </div>
            </div>
            <div class="copyright">
                <p>&copy; 2023 Crimeson. All rights reserved. Designed with <i class="fas fa-heart" style="color: var(--primary);"></i> for the community</p>
            </div>
        </div>
    </footer>

    <!-- Scroll to top button -->
    <div class="scroll-top">
        <i class="fas fa-arrow-up"></i>
    </div>

    <script>
        // Auth Tabs Functionality
        const authTabs = document.querySelectorAll('.auth-tab');
        const authForms = document.querySelectorAll('.auth-form');

        authTabs.forEach(tab => {
            tab.addEventListener('click', () => {
                const targetTab = tab.getAttribute('data-tab');
                
                // Update active tab
                authTabs.forEach(t => t.classList.remove('active'));
                tab.classList.add('active');
                
                // Show corresponding form
                authForms.forEach(form => {
                    form.classList.remove('active');
                    if (form.id === `${targetTab}-form`) {
                        form.classList.add('active');
                    }
                });
            });
        });

        // Simple form validation
        const forms = document.querySelectorAll('.auth-form');
        forms.forEach(form => {
            form.addEventListener('submit', (e) => {
                e.preventDefault();
                alert('Form submission would be processed with backend validation.');
            });
        });

        // Discord authentication simulation
        const discordAuthButtons = document.querySelectorAll('.discord-auth');
        discordAuthButtons.forEach(button => {
            button.addEventListener('click', (e) => {
                e.preventDefault();
                alert('Discord OAuth authentication would be implemented here.');
            });
        });

        // Purchase buttons simulation
        const purchaseButtons = document.querySelectorAll('.btn-primary');
        purchaseButtons.forEach(button => {
            if (button.textContent.includes('Get Role') || button.textContent.includes('Donate Now')) {
                button.addEventListener('click', (e) => {
                    e.preventDefault();
                    alert('This would redirect to a payment processing page.');
                });
            }
        });

        // Scroll to top functionality
        const scrollTopBtn = document.querySelector('.scroll-top');
        
        window.addEventListener('scroll', () => {
            if (window.pageYOffset > 300) {
                scrollTopBtn.classList.add('active');
            } else {
                scrollTopBtn.classList.remove('active');
            }
        });
        
        scrollTopBtn.addEventListener('click', () => {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        });

        // Fade in animation on scroll
        const fadeElements = document.querySelectorAll('.fade-in');
        
        const fadeInOnScroll = () => {
            fadeElements.forEach(element => {
                const elementTop = element.getBoundingClientRect().top;
                const elementVisible = 150;
                
                if (elementTop < window.innerHeight - elementVisible) {
                    element.classList.add('visible');
                }
            });
        };
        
        window.addEventListener('scroll', fadeInOnScroll);
        // Initial check in case elements are already in view
        fadeInOnScroll();

        // Smooth scrolling for anchor links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                if (targetId === '#') return;
                
                const targetElement = document.querySelector(targetId);
                if (targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 80,
                        behavior: 'smooth'
                    });
                }
            });
        });

        // Header background on scroll
        window.addEventListener('scroll', () => {
            const header = document.querySelector('header');
            if (window.scrollY > 50) {
                header.style.backgroundColor = 'rgba(13, 13, 13, 0.98)';
                header.style.boxShadow = '0 5px 20px rgba(0, 0, 0, 0.5)';
            } else {
                header.style.backgroundColor = 'rgba(13, 13, 13, 0.95)';
                header.style.boxShadow = 'var(--shadow)';
            }
        });
    </script>
</body>
</html>
