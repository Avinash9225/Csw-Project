<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Personal Portfolio Website</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/bootstrap/5.3.0/css/bootstrap.min.css" rel="stylesheet">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-color: #f86f06;
            --secondary-color: #feb305;
            --accent-color: #06cef1;
            --dark-bg: #042331;
            --card-bg: #1e293b;
            --text-light: #f1f5f9;
            --text-muted: #94a3b8;
            --gradient: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: var(--dark-bg);
            color: var(--text-light);
            overflow-x: hidden;
        }

      
        .bg-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: linear-gradient(-45deg, #0f172a, #1e293b, #374151, #1e293b);
            background-size: 400% 400%;
            animation: gradientShift 15s ease infinite;
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

      
        .particle {
            position: absolute;
            background: var(--accent-color);
            border-radius: 50%;
            opacity: 0.1;
            animation: float 6s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(180deg); }
        }

        .navbar {
            backdrop-filter: blur(20px);
            background: rgba(15, 23, 42, 0.8);
            border-bottom: 1px solid rgba(148, 163, 184, 0.1);
            transition: all 0.3s ease;
        }

        .navbar-brand {
            font-weight: 700;
            font-size: 1.5rem;
            background: var(--gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .nav-link {
            color: var(--text-light) !important;
            font-weight: 500;
            position: relative;
            transition: all 0.3s ease;
        }

        .nav-link:hover {
            color: var(--accent-color) !important;
            transform: translateY(-2px);
        }

        .nav-link::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: 0;
            left: 50%;
            background: var(--gradient);
            transition: all 0.3s ease;
        }

        .nav-link:hover::after {
            width: 100%;
            left: 0;
        }

        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            position: relative;
            overflow: hidden;
        }

        .hero-content {
            z-index: 2;
        }

        .hero-title {
            font-size: clamp(2.5rem, 8vw, 4.5rem);
            font-weight: 700;
            margin-bottom: 1rem;
            background: var(--gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: slideInUp 1s ease;
        }

        .hero-subtitle {
            font-size: 1.5rem;
            color: var(--text-muted);
            margin-bottom: 2rem;
            animation: slideInUp 1s ease 0.2s both;
        }

        .hero-description {
            font-size: 1.1rem;
            line-height: 1.6;
            margin-bottom: 3rem;
            animation: slideInUp 1s ease 0.4s both;
        }

        @keyframes slideInUp {
            from {
                opacity: 0;
                transform: translateY(50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .btn-gradient {
            background: var(--gradient);
            border: none;
            padding: 12px 30px;
            border-radius: 50px;
            font-weight: 600;
            text-decoration: none;
            color: white;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            animation: slideInUp 1s ease 0.6s both;
        }

        .btn-gradient::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.5s;
        }

        .btn-gradient:hover::before {
            left: 100%;
        }

        .btn-gradient:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(99, 102, 241, 0.3);
            color: white;
        }

        .btn-outline {
            border: 2px solid var(--accent-color);
            color: var(--accent-color);
            padding: 10px 28px;
            border-radius: 50px;
            background: transparent;
            transition: all 0.3s ease;
            animation: slideInUp 1s ease 0.8s both;
        }

        .btn-outline:hover {
            background: var(--accent-color);
            color: var(--dark-bg);
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(6, 182, 212, 0.3);
        }

    
        .card-modern {
            background: var(--card-bg);
            border-radius: 20px;
            border: 1px solid rgba(148, 163, 184, 0.1);
            transition: all 0.3s ease;
            overflow: hidden;
            position: relative;
        }

        .card-modern::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: var(--gradient);
            transform: scaleX(0);
            transition: transform 0.3s ease;
        }

        .card-modern:hover::before {
            transform: scaleX(1);
        }

        .card-modern:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
            border-color: rgba(99, 102, 241, 0.3);
        }

       
        .skill-item {
            background: rgba(99, 102, 241, 0.1);
            border: 1px solid rgba(99, 102, 241, 0.3);
            border-radius: 50px;
            padding: 8px 20px;
            margin: 5px;
            display: inline-block;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .skill-item:hover {
            background: rgba(99, 102, 241, 0.2);
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(99, 102, 241, 0.3);
        }

      
        .project-card {
            position: relative;
            overflow: hidden;
            border-radius: 15px;
            cursor: pointer;
        }

        .project-image {
            width: 100%;
            height: 200px;
            background: var(--gradient);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            color: white;
            transition: all 0.3s ease;
        }

        .project-overlay {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0, 0, 0, 0.8);
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            transition: all 0.3s ease;
        }

        .project-card:hover .project-overlay {
            opacity: 1;
        }

        .project-card:hover .project-image {
            transform: scale(1.1);
        }

        
        .form-control {
            background: rgba(30, 41, 59, 0.8);
            border: 1px solid rgba(148, 163, 184, 0.2);
            border-radius: 10px;
            color: var(--text-light);
            padding: 12px 16px;
            transition: all 0.3s ease;
        }

        .form-control:focus {
            background: rgba(30, 41, 59, 1);
            border-color: var(--primary-color);
            box-shadow: 0 0 0 0.2rem rgba(99, 102, 241, 0.25);
            color: var(--text-light);
        }

        .form-control::placeholder {
            color: var(--text-muted);
        }


        .section {
            padding: 100px 0;
            position: relative;
        }

        .section-title {
            font-size: 2.5rem;
            font-weight: 700;
            text-align: center;
            margin-bottom: 3rem;
            background: var(--gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .footer {
            background: rgba(15, 23, 42, 0.9);
            border-top: 1px solid rgba(148, 163, 184, 0.1);
            padding: 50px 0 30px;
        }

        .social-icon {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 50px;
            height: 50px;
            background: var(--card-bg);
            border-radius: 50%;
            color: var(--text-light);
            font-size: 1.2rem;
            text-decoration: none;
            margin: 0 10px;
            transition: all 0.3s ease;
        }

        .social-icon:hover {
            background: var(--gradient);
            color: white;
            transform: translateY(-5px);
        }

        @media (max-width: 768px) {
            .hero-title {
                font-size: 2.5rem;
            }
            
            .hero-subtitle {
                font-size: 1.2rem;
            }
            
            .section {
                padding: 60px 0;
            }
            
            .section-title {
                font-size: 2rem;
            }
        }

        .fade-in {
            animation: fadeIn 1s ease;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
    </style>
</head>
<body>
    
    <div class="bg-animation"></div>

    
    <nav class="navbar navbar-expand-lg fixed-top">
        <div class="container">
            <a class="navbar-brand" href="#home">Avinash Mahapatra</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav ms-auto">
                    <li class="nav-item">
                        <a class="nav-link" href="#home">Home</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#about">About</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#skills">Skills</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#projects">Projects</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#contact">Contact</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>

    
    <section id="home" class="hero">
        <div class="container">
            <div class="row align-items-center">
                <div class="col-lg-6">
                    <div class="hero-content">
                        <h1 class="hero-title">Avinash Mahapatra</h1>
                        <p class="hero-subtitle">Computer Science Major</p>
                        <p class="hero-description">
                            SOA University student passionate about software development and problem-solving. 
                            Currently pursuing Computer Science and exploring various technologies 
                            to build innovative solutions and contribute to the tech community.
                        </p>
                        <div class="d-flex flex-wrap gap-3">
                            <a href="#projects" class="btn btn-gradient">
                                <i class="fas fa-rocket me-2"></i>View My Work
                            </a>
                            <a href="#contact" class="btn btn-outline">
                                <i class="fas fa-envelope me-2"></i>Get In Touch
                            </a>
                        </div>
                    </div>
                </div>
                <div class="col-lg-6">
                    <div class="text-center">
                        <div style="width: 300px; height: 300px; background: var(--gradient); border-radius: 50%; margin: 0 auto; display: flex; align-items: center; justify-content: center; font-size: 8rem; animation: pulse 2s ease-in-out infinite;">
                            <i class="fas fa-code" style="color: white;"></i>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

  
    <section id="about" class="section">
        <div class="container">
            <h2 class="section-title">About Me</h2>
            <div class="row">
                <div class="col-lg-8 mx-auto">
                    <div class="card-modern p-5 fade-in">
                        <p class="lead text-center mb-4">
                            I'm a passionate Computer Science Major at SOA University with a keen interest 
                            in software development and emerging technologies.
                        </p>
                        <p class="text-center">
                            Currently in my 2nd year, I'm building a strong foundation in programming 
                            languages and development frameworks. My academic journey has introduced me 
                            to various aspects of computer science, from algorithms and data structures 
                            to web development and software engineering principles. I enjoy tackling 
                            challenging problems and am always eager to learn new technologies and 
                            contribute to meaningful projects.
                        </p>
                        <div class="text-center mt-4">
                            <a href="#" class="btn btn-gradient">
                                <i class="fas fa-download me-2"></i>Download Resume
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

   
    <section id="skills" class="section">
        <div class="container">
            <h2 class="section-title">Skills & Technologies</h2>
            <div class="row">
                <div class="col-lg-10 mx-auto">
                    <div class="card-modern p-5 fade-in">
                        <div class="row">
                            <div class="col-md-6 mb-4">
                                <h4 class="mb-3">Frontend Development</h4>
                                <div>
                                    <span class="skill-item">React</span>
                                    <span class="skill-item">HTML5</span>
                                    <span class="skill-item">CSS3</span>
                                    <span class="skill-item">JavaScript</span>
                                    <span class="skill-item">TypeScript</span>
                                </div>
                            </div>
                            <div class="col-md-6 mb-4">
                                <h4 class="mb-3">Backend Development</h4>
                                <div>
                                    <span class="skill-item">Java</span>
                                    <span class="skill-item">Python</span>
                                    <span class="skill-item">C++</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>


    <section id="projects" class="section">
        <div class="container">
            <h2 class="section-title">University Projects</h2>
            <div class="row g-4">
                <div class="col-lg-4 col-md-6">
                    <div class="card-modern fade-in">
                        <div class="project-card">
                            <div class="project-image">
                                <i class="fas fa-calculator"></i>
                            </div>
                            <div class="project-overlay">
                                <div class="text-center">
                                    <a href="#" class="btn btn-gradient me-2">
                                        <i class="fas fa-eye"></i> View
                                    </a>
                                    <a href="#" class="btn btn-outline">
                                        <i class="fab fa-github"></i> Code
                                    </a>
                                </div>
                            </div>
                        </div>
                        <div class="p-4">
                            <h5 class="mb-3">Scientific Calculator</h5>
                            <p class="text-muted">
                                A comprehensive scientific calculator built with Java Swing for Data Structures 
                                course. Features advanced mathematical operations, expression parsing, and 
                                history functionality using stack and queue implementations.
                            </p>
                            <div>
                                <span class="skill-item">Java</span>
                                <span class="skill-item">Swing</span>
                                <span class="skill-item">Data Structures</span>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="col-lg-4 col-md-6">
                    <div class="card-modern fade-in">
                        <div class="project-card">
                            <div class="project-image">
                                <i class="fas fa-gamepad"></i>
                            </div>
                            <div class="project-overlay">
                                <div class="text-center">
                                    <a href="#" class="btn btn-gradient me-2">
                                        <i class="fas fa-eye"></i> View
                                    </a>
                                    <a href="#" class="btn btn-outline">
                                        <i class="fab fa-github"></i> Code
                                    </a>
                                </div>
                            </div>
                        </div>
                        <div class="p-4">
                            <h5 class="mb-3">Snake Game</h5>
                            <p class="text-muted">
                                Classic Snake game implementation using Python and Pygame for Object-Oriented 
                                Programming course. Features score tracking, increasing difficulty levels, 
                                and collision detection with clean OOP design patterns.
                            </p>
                            <div>
                                <span class="skill-item">Python</span>
                                <span class="skill-item">Pygame</span>
                                <span class="skill-item">OOP</span>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="col-lg-4 col-md-6">
                    <div class="card-modern fade-in">
                        <div class="project-card">
                            <div class="project-image">
                                <i class="fas fa-search"></i>
                            </div>
                            <div class="project-overlay">
                                <div class="text-center">
                                    <a href="#" class="btn btn-gradient me-2">
                                        <i class="fas fa-eye"></i> View
                                    </a>
                                    <a href="#" class="btn btn-outline">
                                        <i class="fab fa-github"></i> Code
                                    </a>
                                </div>
                            </div>
                        </div>
                        <div class="p-4">
                            <h5 class="mb-3">Sorting Visualizer</h5>
                            <p class="text-muted">
                                Interactive web application that visualizes various sorting algorithms 
                                including Bubble Sort, Quick Sort, and Merge Sort. Built with HTML, CSS, 
                                and JavaScript for Algorithms course project.
                            </p>
                            <div>
                                <span class="skill-item">HTML</span>
                                <span class="skill-item">CSS</span>
                                <span class="skill-item">JavaScript</span>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="col-lg-4 col-md-6">
                    <div class="card-modern fade-in">
                        <div class="project-card">
                            <div class="project-image">
                                <i class="fas fa-database"></i>
                            </div>
                            <div class="project-overlay">
                                <div class="text-center">
                                    <a href="#" class="btn btn-gradient me-2">
                                        <i class="fas fa-eye"></i> View
                                    </a>
                                    <a href="#" class="btn btn-outline">
                                        <i class="fab fa-github"></i> Code
                                    </a>
                                </div>
                            </div>
                        </div>
                        <div class="p-4">
                            <h5 class="mb-3">Student Management System</h5>
                            <p class="text-muted">
                                Console-based student record management system built with C++ for 
                                Programming Fundamentals course. Features CRUD operations, file handling, 
                                and data validation with structured programming approach.
                            </p>
                            <div>
                                <span class="skill-item">C++</span>
                                <span class="skill-item">File I/O</span>
                                <span class="skill-item">Data Management</span>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="col-lg-4 col-md-6">
                    <div class="card-modern fade-in">
                        <div class="project-card">
                            <div class="project-image">
                                <i class="fas fa-globe"></i>
                            </div>
                            <div class="project-overlay">
                                <div class="text-center">
                                    <a href="#" class="btn btn-gradient me-2">
                                        <i class="fas fa-eye"></i> View
                                    </a>
                                    <a href="#" class="btn btn-outline">
                                        <i class="fab fa-github"></i> Code
                                    </a>
                                </div>
                            </div>
                        </div>
                        <div class="p-4">
                            <h5 class="mb-3">Personal Portfolio Website</h5>
                            <p class="text-muted">
                                Responsive personal portfolio website built with React for Web Development 
                                course. Features modern design, interactive components, and responsive 
                                layout showcasing academic projects and skills.
                            </p>
                            <div>
                                <span class="skill-item">React</span>
                                <span class="skill-item">CSS3</span>
                                <span class="skill-item">Responsive Design</span>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="col-lg-4 col-md-6">
                    <div class="card-modern fade-in">
                        <div class="project-card">
                            <div class="project-image">
                                <i class="fas fa-code-branch"></i>
                            </div>
                            <div class="project-overlay">
                                <div class="text-center">
                                    <a href="#" class="btn btn-gradient me-2">
                                        <i class="fas fa-eye"></i> View
                                    </a>
                                    <a href="#" class="btn btn-outline">
                                        <i class="fab fa-github"></i> Code
                                    </a>
                                </div>
                            </div>
                        </div>
                        <div class="p-4">
                            <h5 class="mb-3">Binary Search Tree Visualizer</h5>
                            <p class="text-muted">
                                Interactive visualization tool for Binary Search Tree operations including 
                                insertion, deletion, and traversal. Built with Python and Tkinter for 
                                Advanced Data Structures course with step-by-step animation.
                            </p>
                            <div>
                                <span class="skill-item">Python</span>
                                <span class="skill-item">Tkinter</span>
                                <span class="skill-item">Algorithms</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    
    <section id="contact" class="section">
        <div class="container">
            <h2 class="section-title">Get In Touch</h2>
            <div class="row">
                <div class="col-lg-8 mx-auto">
                    <div class="card-modern p-5 fade-in">
                        <p class="text-center mb-4 lead">
                            Let's discuss your next project or just say hello!
                        </p>
                        <form id="contactForm">
                            <div class="row">
                                <div class="col-md-6 mb-3">
                                    <input type="text" class="form-control" placeholder="Your Name" required>
                                </div>
                                <div class="col-md-6 mb-3">
                                    <input type="email" class="form-control" placeholder="Your Email" required>
                                </div>
                            </div>
                            <div class="mb-3">
                                <input type="text" class="form-control" placeholder="Subject">
                            </div>
                            <div class="mb-4">
                                <textarea class="form-control" rows="5" placeholder="Your Message" required></textarea>
                            </div>
                            <div class="text-center">
                                <button type="submit" class="btn btn-gradient">
                                    <i class="fas fa-paper-plane me-2"></i>Send Message
                                </button>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </section>

    
    <footer class="footer">
        <div class="container">
            <div class="row">
                <div class="col-lg-8 mx-auto text-center">
                    <h5 class="mb-4">Connect With Me</h5>
                    <div class="mb-4">
                        <a href="#" class="social-icon">
                            <i class="fab fa-linkedin"></i>
                        </a>
                        <a href="#" class="social-icon">
                            <i class="fab fa-github"></i>
                        </a>
                        <a href="#" class="social-icon">
                            <i class="fab fa-twitter"></i>
                        </a>
                        <a href="#" class="social-icon">
                            <i class="fas fa-envelope"></i>
                        </a>
                    </div>
                    <p class="text-muted">
                        &copy; 2025 Avinash Mahapatra. All rights reserved.
                    </p>
                </div>
            </div>
        </div>
    </footer>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/bootstrap/5.3.0/js/bootstrap.bundle.min.js"></script>
    <script>
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        
        window.addEventListener('scroll', function() {
            const navbar = document.querySelector('.navbar');
            if (window.scrollY > 50) {
                navbar.style.background = 'rgba(15, 23, 42, 0.95)';
            } else {
                navbar.style.background = 'rgba(15, 23, 42, 0.8)';
            }
        });

       
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver(function(entries) {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.animation = 'fadeIn 1s ease forwards';
                }
            });
        }, observerOptions);

        document.querySelectorAll('.fade-in').forEach(el => {
            el.style.opacity = '0';
            observer.observe(el);
        });

      
        document.getElementById('contactForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
           
            const button = this.querySelector('button[type="submit"]');
            const originalText = button.innerHTML;
            button.innerHTML = '<i class="fas fa-check me-2"></i>Message Sent!';
            button.style.background = 'linear-gradient(135deg, #10b981, #059669)';
            
          
            setTimeout(() => {
                this.reset();
                button.innerHTML = originalText;
                button.style.background = '';
            }, 3000);
        });

        
        function createParticle() {
            const particle = document.createElement('div');
            particle.className = 'particle';
            particle.style.left = Math.random() * 100 + '%';
            particle.style.top = Math.random() * 100 + '%';
            particle.style.width = Math.random() * 6 + 2 + 'px';
            particle.style.height = particle.style.width;
            particle.style.animationDelay = Math.random() * 2 + 's';
            particle.style.animationDuration = (Math.random() * 3 + 3) + 's';
            
            document.body.appendChild(particle);
            
            setTimeout(() => {
                particle.remove();
            }, 6000);
        }

        
        setInterval(createParticle, 2000);

       
        const heroIcon = document.querySelector('.hero i');
        if (heroIcon) {
            setInterval(() => {
                heroIcon.style.transform = 'scale(1.1)';
                setTimeout(() => {
                    heroIcon.style.transform = 'scale(1)';
                }, 1000);
            }, 3000);
        }

        
        document.querySelectorAll('.skill-item').forEach(skill => {
            skill.addEventListener('mouseenter', function() {
                this.style.transform = 'translateY(-3px) scale(1.05)';
            });
            
            skill.addEventListener('mouseleave', function() {
                this.style.transform = 'translateY(0) scale(1)';
            });
        });

       
        document.querySelectorAll('.project-card').forEach(card => {
            card.addEventListener('mouseenter', function() {
                const overlay = this.querySelector('.project-overlay');
                const image = this.querySelector('.project-image');
                overlay.style.opacity = '1';
                image.style.transform = 'scale(1.1)';
            });
            
            card.addEventListener('mouseleave', function() {
                const overlay = this.querySelector('.project-overlay');
                const image = this.querySelector('.project-image');
                overlay.style.opacity = '0';
                image.style.transform = 'scale(1)';
            });
        });

        
        function typeWriter(element, text, speed = 100) {
            let i = 0;
            element.innerHTML = '';
            function type() {
                if (i < text.length) {
                    element.innerHTML += text.charAt(i);
                    i++;
                    setTimeout(type, speed);
                }
            }
            type();
        }

        window.addEventListener('load', function() {
            const subtitle = document.querySelector('.hero-subtitle');
            const originalText = subtitle.textContent;
            setTimeout(() => {
                typeWriter(subtitle, originalText, 150);
            }, 1500);
        });

        window.addEventListener('scroll', function() {
            const scrolled = window.pageYOffset;
            const hero = document.querySelector('.hero');
            const rate = scrolled * -0.5;
            
            if (hero) {
                hero.style.transform = `translateY(${rate}px)`;
            }
        });
    </script>
</body>
</html>
