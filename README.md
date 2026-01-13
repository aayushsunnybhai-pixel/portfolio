    <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aayush Tripathi — Marketing Strategist</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=Inter:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --black: #000000;
            --white: #FFFFFF;
            --gray: #9C9C9C;
            --light-gray: #F5F5F5;
            --accent: #FFD700;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Space Grotesk', 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            background: var(--white);
            color: var(--black);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Custom Cursor - Desktop Only */
        @media (min-width: 1024px) {
            .cursor {
                width: 20px;
                height: 20px;
                border: 2px solid var(--black);
                border-radius: 50%;
                position: fixed;
                pointer-events: none;
                z-index: 9999;
                transition: all 0.15s ease;
                transform: translate(-50%, -50%);
                mix-blend-mode: difference;
            }

            .cursor-follower {
                width: 40px;
                height: 40px;
                border: 1px solid var(--gray);
                border-radius: 50%;
                position: fixed;
                pointer-events: none;
                z-index: 9998;
                transition: all 0.3s ease;
                transform: translate(-50%, -50%);
                mix-blend-mode: difference;
            }
        }

        @media (max-width: 1023px) {
            .cursor, .cursor-follower {
                display: none;
            }
        }

        /* Mobile Menu Toggle */
        .menu-toggle {
            display: none;
            flex-direction: column;
            gap: 6px;
            cursor: pointer;
            z-index: 1001;
        }

        .menu-toggle span {
            width: 30px;
            height: 3px;
            background: var(--white);
            transition: all 0.3s ease;
        }

        nav.scrolled .menu-toggle span {
            background: var(--black);
        }

        .menu-toggle.active span:nth-child(1) {
            transform: rotate(45deg) translate(8px, 8px);
        }

        .menu-toggle.active span:nth-child(2) {
            opacity: 0;
        }

        .menu-toggle.active span:nth-child(3) {
            transform: rotate(-45deg) translate(8px, -8px);
        }

        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            padding: 2rem 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 1000;
            transition: all 0.5s cubic-bezier(0.19, 1, 0.22, 1);
            mix-blend-mode: difference;
        }

        nav.scrolled {
            padding: 1rem 5%;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            mix-blend-mode: normal;
            box-shadow: 0 2px 20px rgba(0,0,0,0.05);
        }

        .logo {
            font-size: 1.3rem;
            font-weight: 700;
            letter-spacing: -0.03em;
            color: var(--white);
            transition: color 0.3s ease;
            cursor: pointer;
        }

        nav.scrolled .logo {
            color: var(--black);
        }

        .nav-links {
            display: flex;
            gap: 3rem;
            list-style: none;
        }

        .nav-links a {
            color: var(--white);
            text-decoration: none;
            font-weight: 500;
            font-size: 0.9rem;
            letter-spacing: 0.05em;
            text-transform: uppercase;
            transition: all 0.3s ease;
            position: relative;
        }

        nav.scrolled .nav-links a {
            color: var(--black);
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: currentColor;
            transition: width 0.3s ease;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        /* Mobile Navigation */
        @media (max-width: 768px) {
            .menu-toggle {
                display: flex;
            }

            .nav-links {
                position: fixed;
                top: 0;
                right: -100%;
                height: 100vh;
                width: 70%;
                max-width: 300px;
                background: var(--black);
                flex-direction: column;
                padding: 6rem 2rem;
                gap: 2rem;
                transition: right 0.4s cubic-bezier(0.19, 1, 0.22, 1);
                box-shadow: -5px 0 20px rgba(0,0,0,0.3);
            }

            .nav-links.active {
                right: 0;
            }

            .nav-links a {
                color: var(--white) !important;
                font-size: 1.2rem;
            }

            nav {
                padding: 1.5rem 5%;
            }

            nav.scrolled {
                padding: 1rem 5%;
            }
        }

        /* Hero Section - Mobile Optimized */
        .hero {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            position: relative;
            overflow: hidden;
            background: linear-gradient(135deg, #000000 0%, #1a1a1a 100%);
            padding: 8rem 5% 4rem;
        }

        .hero::before {
            content: '';
            position: absolute;
            width: 150%;
            height: 150%;
            background: 
                radial-gradient(circle at 20% 50%, rgba(255,215,0,0.1) 0%, transparent 50%),
                radial-gradient(circle at 80% 50%, rgba(255,255,255,0.05) 0%, transparent 50%),
                repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(255,255,255,0.03) 2px, rgba(255,255,255,0.03) 4px);
            animation: heroBackground 20s linear infinite;
        }

        @keyframes heroBackground {
            0% { transform: translate(0, 0) rotate(0deg); }
            100% { transform: translate(50px, 50px) rotate(360deg); }
        }

        .hero-content {
            position: relative;
            z-index: 2;
            text-align: center;
            max-width: 1200px;
        }

        .hero-image-wrapper {
            width: 180px;
            height: 180px;
            border-radius: 50%;
            overflow: hidden;
            margin: 0 auto 3rem;
            border: 4px solid var(--white);
            opacity: 0;
            transform: scale(0.8);
            animation: fadeInScale 1s ease 0.2s forwards;
            position: relative;
        }

        @media (max-width: 768px) {
            .hero-image-wrapper {
                width: 150px;
                height: 150px;
            }
        }

        .hero-image-wrapper::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255,255,255,0.1), transparent);
            animation: shimmer 3s infinite;
        }

        @keyframes shimmer {
            0% { transform: translateX(-100%) translateY(-100%) rotate(45deg); }
            100% { transform: translateX(100%) translateY(100%) rotate(45deg); }
        }

        .hero-image {
            width: 100%;
            height: 100%;
            object-fit: cover;
            filter: grayscale(100%) contrast(1.3) brightness(1.1);
            transition: all 0.5s ease;
        }

        .hero-image:hover {
            filter: grayscale(0%) contrast(1.1) brightness(1);
            transform: scale(1.1);
        }

        @keyframes fadeInScale {
            to {
                opacity: 1;
                transform: scale(1);
            }
        }

        .hero-label {
            font-size: 0.85rem;
            letter-spacing: 0.2em;
            text-transform: uppercase;
            color: var(--gray);
            margin-bottom: 2rem;
            opacity: 0;
            animation: fadeInUp 1s ease 0.4s forwards;
        }

        .hero-title {
            font-size: clamp(3rem, 12vw, 12rem);
            font-weight: 700;
            line-height: 0.85;
            letter-spacing: -0.04em;
            margin-bottom: 1rem;
            color: var(--white);
            opacity: 0;
            animation: fadeInUp 1s ease 0.6s forwards;
        }

        .hero-title .outline {
            color: transparent;
            -webkit-text-stroke: 2px var(--white);
            text-stroke: 2px var(--white);
        }

        .hero-subtitle {
            font-size: clamp(1.2rem, 3.5vw, 3rem);
            font-weight: 300;
            color: var(--gray);
            margin-bottom: 2rem;
            opacity: 0;
            animation: fadeInUp 1s ease 0.8s forwards;
        }

        .hero-description {
            max-width: 700px;
            font-size: clamp(1rem, 2vw, 1.1rem);
            line-height: 1.8;
            color: var(--gray);
            margin: 0 auto;
            opacity: 0;
            animation: fadeInUp 1s ease 1s forwards;
            padding: 0 1rem;
        }

        .scroll-indicator {
            position: absolute;
            bottom: 3rem;
            left: 50%;
            transform: translateX(-50%);
            color: var(--white);
            font-size: 0.8rem;
            letter-spacing: 0.2em;
            text-transform: uppercase;
            opacity: 0;
            animation: fadeInUp 1s ease 1.2s forwards, bounce 2s ease-in-out 2s infinite;
            cursor: pointer;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes bounce {
            0%, 100% { transform: translateX(-50%) translateY(0); }
            50% { transform: translateX(-50%) translateY(10px); }
        }

        /* Interactive Floating Action Button */
        .fab {
            position: fixed;
            bottom: 2rem;
            right: 2rem;
            width: 60px;
            height: 60px;
            background: var(--accent);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            z-index: 999;
            box-shadow: 0 4px 20px rgba(255,215,0,0.4);
            transition: all 0.3s ease;
            font-size: 1.5rem;
        }

        .fab:hover {
            transform: scale(1.1) rotate(90deg);
            box-shadow: 0 6px 30px rgba(255,215,0,0.6);
        }

        .fab-menu {
            position: fixed;
            bottom: 5rem;
            right: 2rem;
            background: var(--white);
            border-radius: 15px;
            padding: 1rem;
            box-shadow: 0 10px 40px rgba(0,0,0,0.2);
            opacity: 0;
            visibility: hidden;
            transform: translateY(20px);
            transition: all 0.3s ease;
            z-index: 998;
        }

        .fab-menu.active {
            opacity: 1;
            visibility: visible;
            transform: translateY(0);
        }

        .fab-menu-item {
            display: flex;
            align-items: center;
            gap: 1rem;
            padding: 1rem;
            cursor: pointer;
            border-radius: 10px;
            transition: all 0.3s ease;
            white-space: nowrap;
        }

        .fab-menu-item:hover {
            background: var(--light-gray);
            transform: translateX(5px);
        }

        /* Marquee - Mobile Optimized */
        .marquee {
            padding: 3rem 0;
            background: var(--black);
            color: var(--white);
            overflow: hidden;
            position: relative;
        }

        .marquee-content {
            display: flex;
            animation: marqueeScroll 40s linear infinite;
            white-space: nowrap;
        }

        .marquee-content:hover {
            animation-play-state: paused;
        }

        .marquee-item {
            font-size: clamp(1.5rem, 4vw, 4rem);
            font-weight: 700;
            padding: 0 2rem;
            display: flex;
            align-items: center;
            gap: 2rem;
        }

        .marquee-item::after {
            content: '•';
            font-size: 2rem;
        }

        @keyframes marqueeScroll {
            0% { transform: translateX(0); }
            100% { transform: translateX(-50%); }
        }

        /* Section Styling - Mobile Optimized */
        .section {
            padding: clamp(4rem, 10vw, 10rem) 5%;
            position: relative;
        }

        .section-header {
            margin-bottom: clamp(4rem, 8vw, 8rem);
        }

        .section-number {
            font-size: clamp(0.85rem, 1.5vw, 1rem);
            letter-spacing: 0.2em;
            color: var(--gray);
            margin-bottom: 1rem;
            text-transform: uppercase;
        }

        .section-title {
            font-size: clamp(2.5rem, 8vw, 8rem);
            font-weight: 700;
            line-height: 0.9;
            margin-bottom: 2rem;
            letter-spacing: -0.03em;
        }

        .section-description {
            font-size: clamp(1rem, 2vw, 1.3rem);
            color: var(--gray);
            max-width: 700px;
            line-height: 1.7;
        }

        /* Projects Grid - Fully Responsive */
        .projects-grid {
            display: grid;
            gap: clamp(4rem, 6vw, 8rem) clamp(2rem, 4vw, 4rem);
        }

        .project-card {
            display: grid;
            grid-template-columns: 1fr;
            gap: 2rem;
            opacity: 0;
            transform: translateY(100px);
            transition: all 1s cubic-bezier(0.19, 1, 0.22, 1);
        }

        @media (min-width: 768px) {
            .project-card {
                grid-template-columns: 1fr 1.2fr;
                gap: 4rem;
                align-items: center;
            }

            .project-card:nth-child(even) {
                grid-template-columns: 1.2fr 1fr;
            }

            .project-card:nth-child(even) .project-content {
                order: -1;
            }
        }

        .project-card.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* Animated Project Visuals - Touch Optimized */
        .project-visual {
            position: relative;
            aspect-ratio: 4/3;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            overflow: hidden;
            cursor: pointer;
            border-radius: 20px;
            transition: transform 0.3s ease;
            touch-action: manipulation;
        }

        .project-visual:active {
            transform: scale(0.98);
        }

        @media (min-width: 1024px) {
            .project-visual:hover {
                transform: scale(1.02);
            }
        }

        .project-visual.visual-1 {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }

        .project-visual.visual-2 {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
        }

        .project-visual.visual-3 {
            background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
        }

        .project-visual.visual-4 {
            background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);
        }

        .project-number {
            position: absolute;
            top: 1rem;
            right: 1rem;
            font-size: clamp(4rem, 10vw, 8rem);
            font-weight: 700;
            color: rgba(255,255,255,0.2);
            line-height: 1;
            z-index: 1;
        }

        /* Chart Animation */
        .chart-animation {
            position: absolute;
            bottom: 15%;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: clamp(0.8rem, 2vw, 1.5rem);
            align-items: flex-end;
            height: 60%;
        }

        .chart-bar {
            width: clamp(30px, 5vw, 50px);
            background: rgba(255,255,255,0.9);
            border-radius: 8px 8px 0 0;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
            animation: barGrow 2s ease-in-out infinite;
        }

        .chart-bar:nth-child(1) { animation-delay: 0s; height: 40%; }
        .chart-bar:nth-child(2) { animation-delay: 0.2s; height: 65%; }
        .chart-bar:nth-child(3) { animation-delay: 0.4s; height: 85%; }
        .chart-bar:nth-child(4) { animation-delay: 0.6s; height: 55%; }
        .chart-bar:nth-child(5) { animation-delay: 0.8s; height: 95%; }

        @keyframes barGrow {
            0%, 100% { transform: scaleY(0.95); }
            50% { transform: scaleY(1.05); }
        }

        /* Process/Gear Animation */
        .process-animation {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 70%;
            height: 70%;
        }

        .gear {
            position: absolute;
            border: clamp(4px, 1vw, 8px) solid rgba(255,255,255,0.9);
            border-radius: 50%;
        }

        .gear::before, .gear::after {
            content: '';
            position: absolute;
            background: rgba(255,255,255,0.9);
        }

        .gear-1 {
            width: clamp(100px, 20vw, 150px);
            height: clamp(100px, 20vw, 150px);
            top: 20%;
            left: 20%;
            animation: rotateGear 4s linear infinite;
        }

        .gear-1::before {
            width: clamp(20px, 4vw, 30px);
            height: 100%;
            left: 50%;
            transform: translateX(-50%);
        }

        .gear-1::after {
            height: clamp(20px, 4vw, 30px);
            width: 100%;
            top: 50%;
            transform: translateY(-50%);
        }

        .gear-2 {
            width: clamp(80px, 16vw, 120px);
            height: clamp(80px, 16vw, 120px);
            bottom: 20%;
            right: 20%;
            animation: rotateGearReverse 3s linear infinite;
        }

        .gear-2::before {
            width: clamp(16px, 3vw, 25px);
            height: 100%;
            left: 50%;
            transform: translateX(-50%);
        }

        .gear-2::after {
            height: clamp(16px, 3vw, 25px);
            width: 100%;
            top: 50%;
            transform: translateY(-50%);
        }

        @keyframes rotateGear {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        @keyframes rotateGearReverse {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(-360deg); }
        }

        /* Network Animation */
        .network-animation {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 80%;
            height: 80%;
        }

        .network-node {
            position: absolute;
            width: clamp(50px, 8vw, 70px);
            height: clamp(50px, 8vw, 70px);
            background: rgba(255,255,255,0.9);
            border-radius: 50%;
            box-shadow: 0 0 30px rgba(255,255,255,0.5);
            animation: nodePulse 2s ease-in-out infinite;
        }

        .network-node:nth-child(1) { top: 10%; left: 50%; transform: translateX(-50%); animation-delay: 0s; }
        .network-node:nth-child(2) { top: 40%; right: 10%; animation-delay: 0.4s; }
        .network-node:nth-child(3) { bottom: 10%; left: 50%; transform: translateX(-50%); animation-delay: 0.8s; }
        .network-node:nth-child(4) { top: 40%; left: 10%; animation-delay: 1.2s; }

        @keyframes nodePulse {
            0%, 100% { transform: scale(1); opacity: 0.8; }
            50% { transform: scale(1.1); opacity: 1; }
        }

        /* Documents Animation */
        .documents-animation {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 80%;
            height: 80%;
        }

        .document {
            position: absolute;
            width: clamp(60px, 10vw, 80px);
            height: clamp(75px, 12vw, 100px);
            background: rgba(255,255,255,0.9);
            border-radius: 8px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.2);
            animation: documentFloat 4s ease-in-out infinite;
        }

        .document::before {
            content: '';
            position: absolute;
            top: 15px;
            left: 15px;
            right: 15px;
            height: 3px;
            background: rgba(0,0,0,0.2);
            border-radius: 2px;
        }

        .document:nth-child(1) { top: 20%; left: 10%; animation-delay: 0s; }
        .document:nth-child(2) { top: 20%; right: 10%; animation-delay: 0.5s; }
        .document:nth-child(3) { bottom: 20%; left: 20%; animation-delay: 1s; }
        .document:nth-child(4) { bottom: 20%; right: 20%; animation-delay: 1.5s; }
        .document:nth-child(5) { top: 50%; left: 50%; transform: translate(-50%, -50%); animation-delay: 2s; }

        @keyframes documentFloat {
            0%, 100% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(5deg); }
        }

        .project-content {
            padding: 1rem 0;
        }

        .project-tag {
            display: inline-block;
            padding: 0.5rem 1.5rem;
            background: var(--black);
            color: var(--white);
            font-size: clamp(0.75rem, 1.5vw, 0.8rem);
            letter-spacing: 0.1em;
            text-transform: uppercase;
            margin-bottom: 1.5rem;
            transition: all 0.3s ease;
        }

        .project-title {
            font-size: clamp(1.8rem, 4vw, 3rem);
            font-weight: 700;
            margin-bottom: 1rem;
            letter-spacing: -0.02em;
            line-height: 1.1;
        }

        .project-description {
            font-size: clamp(1rem, 2vw, 1.1rem);
            color: var(--gray);
            line-height: 1.7;
            margin-bottom: 1.5rem;
        }

        .project-metrics {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .metric {
            display: flex;
            flex-direction: column;
        }

        .metric-value {
            font-size: clamp(2rem, 4vw, 2.5rem);
            font-weight: 700;
            line-height: 1;
            margin-bottom: 0.5rem;
        }

        .metric-label {
            font-size: clamp(0.8rem, 1.5vw, 0.9rem);
            color: var(--gray);
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }

        /* Comprehensive Timeline Section */
        .timeline-section {
            background: var(--black);
            color: var(--white);
            padding: clamp(6rem, 10vw, 10rem) 5%;
            position: relative;
            overflow: hidden;
        }

        .timeline-container {
            max-width: 1200px;
            margin: 0 auto;
        }

        .timeline-track {
            position: relative;
            padding: 3rem 0;
        }

        .timeline-line {
            position: absolute;
            left: 30px;
            top: 0;
            bottom: 0;
            width: 3px;
            background: linear-gradient(180deg, transparent 0%, var(--accent) 10%, var(--accent) 90%, transparent 100%);
        }

        @media (min-width: 768px) {
            .timeline-line {
                left: 50%;
                transform: translateX(-50%);
            }
        }

        .timeline-entry {
            position: relative;
            margin-bottom: 4rem;
            opacity: 0;
            transform: translateY(50px);
            transition: all 0.6s cubic-bezier(0.19, 1, 0.22, 1);
        }

        .timeline-entry.visible {
            opacity: 1;
            transform: translateY(0);
        }

        @media (min-width: 768px) {
            .timeline-entry:nth-child(odd) .timeline-content {
                margin-left: 0;
                margin-right: calc(50% + 3rem);
                text-align: right;
            }

            .timeline-entry:nth-child(even) .timeline-content {
                margin-left: calc(50% + 3rem);
                margin-right: 0;
                text-align: left;
            }
        }

        .timeline-dot {
            position: absolute;
            left: 21px;
            top: 0;
            width: 20px;
            height: 20px;
            background: var(--accent);
            border: 4px solid var(--black);
            border-radius: 50%;
            z-index: 2;
            box-shadow: 0 0 20px var(--accent);
            animation: dotPulse 2s ease-in-out infinite;
        }

        @media (min-width: 768px) {
            .timeline-dot {
                left: 50%;
                transform: translateX(-50%);
            }
        }

        @keyframes dotPulse {
            0%, 100% { transform: scale(1); box-shadow: 0 0 20px var(--accent); }
            50% { transform: scale(1.2); box-shadow: 0 0 30px var(--accent); }
        }

        .timeline-content {
            background: rgba(255,255,255,0.05);
            padding: 2rem;
            border-radius: 15px;
            margin-left: 4rem;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255,255,255,0.1);
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .timeline-content:hover {
            background: rgba(255,255,255,0.08);
            border-color: var(--accent);
            transform: translateY(-5px);
            box-shadow: 0 10px 40px rgba(255,215,0,0.2);
        }

        @media (max-width: 767px) {
            .timeline-content {
                margin-left: 4rem;
                margin-right: 0;
            }
        }

        .timeline-date {
            font-size: clamp(1.2rem, 2vw, 1.5rem);
            font-weight: 700;
            color: var(--accent);
            margin-bottom: 0.5rem;
        }

        .timeline-location {
            font-size: clamp(0.85rem, 1.5vw, 0.95rem);
            color: var(--gray);
            margin-bottom: 1rem;
            text-transform: uppercase;
            letter-spacing: 0.1em;
        }

        .timeline-role {
            font-size: clamp(1.3rem, 2.5vw, 1.8rem);
            font-weight: 600;
            margin-bottom: 0.5rem;
            color: var(--white);
        }

        .timeline-company {
            font-size: clamp(1rem, 1.8vw, 1.2rem);
            color: var(--gray);
            margin-bottom: 1rem;
            font-style: italic;
        }

        .timeline-description {
            font-size: clamp(0.95rem, 1.6vw, 1.05rem);
            line-height: 1.7;
            color: rgba(255,255,255,0.8);
        }

        .timeline-highlights {
            margin-top: 1rem;
            padding-top: 1rem;
            border-top: 1px solid rgba(255,255,255,0.1);
        }

        .timeline-highlight {
            display: flex;
            align-items: start;
            gap: 0.5rem;
            margin-bottom: 0.5rem;
            font-size: clamp(0.9rem, 1.5vw, 1rem);
            line-height: 1.6;
        }

        .timeline-highlight::before {
            content: '▸';
            color: var(--accent);
            font-weight: bold;
            flex-shrink: 0;
        }

        /* Interactive World Map Styling */
        .world-map-wrapper {
            margin-bottom: 6rem;
        }

        .map-title {
            font-size: clamp(2rem, 5vw, 3rem);
            font-weight: 700;
            text-align: center;
            margin-bottom: 1rem;
            color: var(--white);
        }

        .map-subtitle {
            text-align: center;
            color: var(--gray);
            font-size: clamp(1rem, 2vw, 1.2rem);
            margin-bottom: 3rem;
        }

        .world-map-container {
            position: relative;
            max-width: 1400px;
            margin: 0 auto;
            background: rgba(255,255,255,0.02);
            border-radius: 20px;
            padding: 3rem;
            border: 1px solid rgba(255,255,255,0.1);
            min-height: 600px;
        }

        @media (max-width: 768px) {
            .world-map-container {
                padding: 2rem 1rem;
                min-height: 400px;
            }
        }

        .world-map-svg {
            width: 100%;
            height: 100%;
            opacity: 0.6;
        }

        .map-continents path {
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .map-continents path:hover {
            fill: rgba(255,215,0,0.1);
            stroke: var(--accent);
            stroke-width: 2;
        }

        .connection-line {
            animation: dashFlow 20s linear infinite;
        }

        @keyframes dashFlow {
            to { stroke-dashoffset: -1000; }
        }

        /* Location Markers */
        .map-markers {
            position: absolute;
            top: 3rem;
            left: 3rem;
            right: 3rem;
            bottom: 3rem;
            pointer-events: none;
        }

        @media (max-width: 768px) {
            .map-markers {
                top: 2rem;
                left: 1rem;
                right: 1rem;
                bottom: 2rem;
            }
        }

        .location-marker {
            position: absolute;
            pointer-events: all;
            cursor: pointer;
            z-index: 10;
        }

        .marker-pulse {
            position: absolute;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: var(--accent);
            opacity: 0.6;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            animation: markerPulse 2s ease-out infinite;
        }

        @keyframes markerPulse {
            0% {
                transform: translate(-50%, -50%) scale(0.5);
                opacity: 0.8;
            }
            100% {
                transform: translate(-50%, -50%) scale(2);
                opacity: 0;
            }
        }

        .marker-dot {
            position: absolute;
            width: 16px;
            height: 16px;
            background: var(--accent);
            border: 3px solid var(--black);
            border-radius: 50%;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            box-shadow: 0 0 20px var(--accent);
            transition: all 0.3s ease;
            animation: markerBounce 1s ease-in-out infinite;
        }

        @keyframes markerBounce {
            0%, 100% { transform: translate(-50%, -50%) scale(1); }
            50% { transform: translate(-50%, -50%) scale(1.2); }
        }

        .location-marker:hover .marker-dot {
            transform: translate(-50%, -50%) scale(1.4);
            box-shadow: 0 0 30px var(--accent);
        }

        /* Current location special styling */
        .marker-current .marker-dot {
            background: #FF4444;
            box-shadow: 0 0 20px #FF4444;
            animation: currentBlink 1.5s ease-in-out infinite;
        }

        .marker-current .pulse-current {
            background: #FF4444;
        }

        @keyframes currentBlink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.6; }
        }

        .dot-current {
            background: #FF4444 !important;
            box-shadow: 0 0 20px #FF4444 !important;
        }

        /* Location Popup */
        .location-popup {
            position: absolute;
            bottom: 100%;
            left: 50%;
            transform: translateX(-50%) translateY(-10px) scale(0.8);
            background: var(--white);
            color: var(--black);
            padding: 1.5rem;
            border-radius: 15px;
            min-width: clamp(250px, 30vw, 320px);
            box-shadow: 0 15px 50px rgba(0,0,0,0.4);
            opacity: 0;
            visibility: hidden;
            transition: all 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            z-index: 100;
            margin-bottom: 15px;
        }

        .location-popup::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 0;
            height: 0;
            border-left: 10px solid transparent;
            border-right: 10px solid transparent;
            border-top: 10px solid var(--white);
        }

        .location-marker:hover .location-popup,
        .location-marker.active .location-popup {
            opacity: 1;
            visibility: visible;
            transform: translateX(-50%) translateY(-10px) scale(1);
        }

        @media (max-width: 768px) {
            .location-popup {
                position: fixed;
                bottom: 20px;
                left: 20px;
                right: 20px;
                transform: translateY(100px);
                min-width: auto;
                max-width: calc(100vw - 40px);
            }

            .location-popup::after {
                display: none;
            }

            .location-marker.active .location-popup {
                transform: translateY(0);
            }
        }

        .popup-header {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin-bottom: 0.75rem;
            flex-wrap: wrap;
        }

        .popup-flag {
            font-size: 1.5rem;
        }

        .popup-title {
            font-size: 1.3rem;
            font-weight: 700;
        }

        .popup-badge {
            background: #FF4444;
            color: var(--white);
            padding: 0.25rem 0.75rem;
            border-radius: 20px;
            font-size: 0.7rem;
            font-weight: 700;
            letter-spacing: 0.1em;
            animation: badgePulse 2s ease-in-out infinite;
        }

        @keyframes badgePulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        .popup-date {
            font-size: 0.9rem;
            color: var(--accent);
            font-weight: 600;
            margin-bottom: 0.5rem;
        }

        .popup-role {
            font-size: 1.1rem;
            font-weight: 600;
            margin-bottom: 0.25rem;
            color: var(--black);
        }

        .popup-company {
            font-size: 0.95rem;
            color: var(--gray);
            margin-bottom: 0.75rem;
            font-style: italic;
        }

        .popup-description {
            font-size: 0.95rem;
            line-height: 1.6;
            color: #666;
        }

        .popup-highlights {
            margin-top: 0.75rem;
            padding-top: 0.75rem;
            border-top: 1px solid rgba(0,0,0,0.1);
        }

        .popup-highlights div {
            font-size: 0.9rem;
            line-height: 1.8;
            color: #666;
        }

        /* Map Legend */
        .map-legend {
            display: flex;
            justify-content: center;
            gap: 2rem;
            flex-wrap: wrap;
            margin-top: 2rem;
            padding: 1.5rem;
            background: rgba(255,255,255,0.05);
            border-radius: 15px;
        }

        .legend-item {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            font-size: 0.9rem;
            color: var(--gray);
        }

        .legend-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            border: 2px solid var(--black);
        }

        /* Color coding for different markers */
        .marker-india-general .marker-dot {
            background: #FFD700;
            box-shadow: 0 0 20px #FFD700;
        }

        .marker-chennai-1 .marker-dot {
            background: #667eea;
            box-shadow: 0 0 20px #667eea;
        }

        .marker-chennai-2 .marker-dot {
            background: #667eea;
            box-shadow: 0 0 20px #667eea;
        }

        .marker-paris .marker-dot {
            background: #FFD700;
            box-shadow: 0 0 20px #FFD700;
        }

        .marker-bangalore .marker-dot {
            background: #f093fb;
            box-shadow: 0 0 20px #f093fb;
        }

        .marker-saskatoon-1 .marker-dot {
            background: #43e97b;
            box-shadow: 0 0 20px #43e97b;
        }

        /* Responsive adjustments */
        @media (max-width: 768px) {
            .marker-dot {
                width: 14px;
                height: 14px;
            }

            .marker-pulse {
                width: 35px;
                height: 35px;
            }

            .map-legend {
                gap: 1rem;
                font-size: 0.85rem;
            }
        }

        /* Stats Section - Mobile Optimized */
        .stats-section {
            background: var(--light-gray);
            padding: clamp(4rem, 8vw, 8rem) 5%;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: clamp(2rem, 4vw, 4rem);
            max-width: 1200px;
            margin: 0 auto;
        }

        .stat-item {
            text-align: center;
            padding: clamp(2rem, 4vw, 3rem);
            background: var(--white);
            border-radius: 15px;
            transition: all 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            box-shadow: 0 5px 20px rgba(0,0,0,0.05);
            cursor: pointer;
        }

        .stat-item:hover, .stat-item:active {
            transform: translateY(-15px) scale(1.05);
            box-shadow: 0 15px 50px rgba(0,0,0,0.15);
        }

        .stat-number {
            font-size: clamp(3rem, 8vw, 5rem);
            font-weight: 700;
            line-height: 1;
            margin-bottom: 1rem;
            background: linear-gradient(135deg, var(--black) 0%, var(--gray) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .stat-label {
            font-size: clamp(0.9rem, 1.5vw, 1rem);
            color: var(--gray);
            letter-spacing: 0.05em;
        }

        /* Contact Section - Mobile Optimized */
        .contact-section {
            background: var(--black);
            color: var(--white);
            padding: clamp(8rem, 12vw, 12rem) 5%;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .contact-section::before {
            content: '';
            position: absolute;
            width: 500px;
            height: 500px;
            background: radial-gradient(circle, rgba(255,215,0,0.1) 0%, transparent 70%);
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            animation: contactGlow 4s ease-in-out infinite;
        }

        @keyframes contactGlow {
            0%, 100% { transform: translate(-50%, -50%) scale(1); opacity: 0.5; }
            50% { transform: translate(-50%, -50%) scale(1.2); opacity: 0.8; }
        }

        .contact-title {
            font-size: clamp(2.5rem, 8vw, 7rem);
            font-weight: 700;
            line-height: 1.1;
            margin-bottom: 3rem;
            letter-spacing: -0.03em;
            position: relative;
            z-index: 2;
        }

        .contact-email {
            font-size: clamp(1.2rem, 3.5vw, 3rem);
            font-weight: 600;
            color: var(--white);
            text-decoration: none;
            display: inline-block;
            border-bottom: 3px solid var(--white);
            padding-bottom: 0.5rem;
            transition: all 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            position: relative;
            z-index: 2;
            word-break: break-all;
        }

        .contact-email:hover, .contact-email:active {
            color: var(--accent);
            border-color: var(--accent);
            transform: translateY(-10px);
            text-shadow: 0 10px 30px rgba(255,215,0,0.5);
        }

        .social-links {
            display: flex;
            gap: clamp(1.5rem, 3vw, 3rem);
            justify-content: center;
            margin-top: 4rem;
            position: relative;
            z-index: 2;
            flex-wrap: wrap;
        }

        .social-links a {
            color: var(--gray);
            text-decoration: none;
            font-size: clamp(0.9rem, 1.5vw, 1rem);
            letter-spacing: 0.1em;
            text-transform: uppercase;
            transition: all 0.3s ease;
            position: relative;
        }

        .social-links a::before {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--accent);
            transition: width 0.3s ease;
        }

        .social-links a:hover::before {
            width: 100%;
        }

        .social-links a:hover, .social-links a:active {
            color: var(--accent);
        }

        /* Footer - Mobile Optimized */
        footer {
            padding: clamp(2rem, 3vw, 3rem) 5%;
            background: var(--black);
            color: var(--white);
            display: flex;
            flex-direction: column;
            gap: 1rem;
            align-items: center;
            text-align: center;
            border-top: 1px solid rgba(255,255,255,0.1);
        }

        @media (min-width: 768px) {
            footer {
                flex-direction: row;
                justify-content: space-between;
                text-align: left;
            }
        }

        footer a {
            color: var(--gray);
            text-decoration: none;
            transition: all 0.3s ease;
        }

        footer a:hover, footer a:active {
            color: var(--accent);
            transform: translateY(-3px);
        }

        /* Loading Animation */
        .page-loader {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--black);
            z-index: 10000;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            gap: 2rem;
            transition: opacity 0.5s ease, visibility 0.5s ease;
        }

        .page-loader.hidden {
            opacity: 0;
            visibility: hidden;
        }

        .loader-text {
            font-size: clamp(1.5rem, 3vw, 2rem);
            font-weight: 700;
            color: var(--white);
            letter-spacing: 0.1em;
            animation: loaderPulse 1.5s ease-in-out infinite;
        }

        .loader-bar {
            width: clamp(150px, 40vw, 200px);
            height: 4px;
            background: rgba(255,255,255,0.2);
            border-radius: 2px;
            overflow: hidden;
        }

        .loader-progress {
            height: 100%;
            background: var(--accent);
            animation: loaderProgress 2s ease-in-out;
        }

        @keyframes loaderPulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.5; }
        }

        @keyframes loaderProgress {
            0% { width: 0; }
            100% { width: 100%; }
        }

        /* Scroll Progress Bar */
        .scroll-progress {
            position: fixed;
            top: 0;
            left: 0;
            height: 3px;
            background: linear-gradient(90deg, var(--accent) 0%, #FFA500 100%);
            z-index: 10001;
            transition: width 0.1s ease;
        }

        /* Mobile Touch Feedback */
        @media (max-width: 1023px) {
            .project-visual:active,
            .stat-item:active,
            .timeline-content:active {
                transform: scale(0.98);
            }
        }
    </style>
</head>
<body>
    <!-- Page Loader -->
    <div class="page-loader">
        <div class="loader-text">AAYUSH TRIPATHI</div>
        <div class="loader-bar">
            <div class="loader-progress"></div>
        </div>
    </div>

    <!-- Scroll Progress Bar -->
    <div class="scroll-progress"></div>

    <!-- Custom Cursor -->
    <div class="cursor"></div>
    <div class="cursor-follower"></div>

    <!-- Navigation -->
    <nav id="nav">
        <div class="logo" onclick="window.scrollTo({top: 0, behavior: 'smooth'})">AT</div>
        <div class="menu-toggle" onclick="toggleMenu()">
            <span></span>
            <span></span>
            <span></span>
        </div>
        <ul class="nav-links" id="navLinks">
            <li><a href="#work" onclick="closeMenu()">Work</a></li>
            <li><a href="#timeline" onclick="closeMenu()">Timeline</a></li>
            <li><a href="#contact" onclick="closeMenu()">Contact</a></li>
        </ul>
    </nav>

    <!-- Floating Action Button -->
    <div class="fab" onclick="toggleFabMenu()">⚡</div>
    <div class="fab-menu" id="fabMenu">
        <div class="fab-menu-item" onclick="scrollToSection('work')">
            <span>📊</span> View Work
        </div>
        <div class="fab-menu-item" onclick="scrollToSection('timeline')">
            <span>🗺️</span> See Journey
        </div>
        <div class="fab-menu-item" onclick="scrollToSection('contact')">
            <span>✉️</span> Get in Touch
        </div>
        <div class="fab-menu-item" onclick="window.open('https://www.linkedin.com/in/iamaayushtripathi/', '_blank')">
            <span>💼</span> LinkedIn
        </div>
    </div>

    <!-- Hero Section -->
    <section class="hero">
        <div class="hero-content">
            <div class="hero-image-wrapper">
                <img src="https://i.ibb.co/HVyswLz/image.png" alt="Aayush Tripathi" class="hero-image">
            </div>
            <div class="hero-label">Marketing Strategist</div>
            <h1 class="hero-title">
                AAYUSH<br>
                <span class="outline">TRIPATHI</span>
            </h1>
            <h2 class="hero-subtitle">Campaign Orchestration. Growth Systems.</h2>
            <p class="hero-description">
                Engineering precision meets creative marketing. I build operations that transform chaos into competitive advantage—where systematic thinking creates campaigns that scale.
            </p>
        </div>
        <div class="scroll-indicator" onclick="scrollToSection('work')">Scroll to explore ↓</div>
    </section>

    <!-- Marquee -->
    <div class="marquee">
        <div class="marquee-content">
            <span class="marquee-item">CAMPAIGN ORCHESTRATION</span>
            <span class="marquee-item">PROCESS ARCHITECTURE</span>
            <span class="marquee-item">GROWTH SYSTEMS</span>
            <span class="marquee-item">OPERATIONAL EXCELLENCE</span>
            <span class="marquee-item">CAMPAIGN ORCHESTRATION</span>
            <span class="marquee-item">PROCESS ARCHITECTURE</span>
            <span class="marquee-item">GROWTH SYSTEMS</span>
            <span class="marquee-item">OPERATIONAL EXCELLENCE</span>
        </div>
    </div>

    <!-- Work Section -->
    <section id="work" class="section">
        <div class="section-header">
            <div class="section-number">01 — Selected Work</div>
            <h2 class="section-title">Projects That<br>Built Systems</h2>
            <p class="section-description">
                Each project represents a transformation from operational chaos to competitive advantage. Not just campaigns—infrastructure that outlasts tenure.
            </p>
        </div>

        <div class="projects-grid">
            <!-- Project 1 -->
            <div class="project-card">
                <div class="project-visual visual-1">
                    <div class="project-number">01</div>
                    <div class="chart-animation">
                        <div class="chart-bar"></div>
                        <div class="chart-bar"></div>
                        <div class="chart-bar"></div>
                        <div class="chart-bar"></div>
                        <div class="chart-bar"></div>
                    </div>
                </div>
                <div class="project-content">
                    <span class="project-tag">Product Launch</span>
                    <h3 class="project-title">Q3 Security Analytics Launch</h3>
                    <p class="project-description">
                        Orchestrated ADVANIX's largest product launch—a security analytics platform module. Coordinated 8-week campaign across multiple channels, managing cross-functional team of 12 stakeholders.
                    </p>
                    <div class="project-metrics">
                        <div class="metric">
                            <div class="metric-value">0</div>
                            <div class="metric-label">Missed Deadlines</div>
                        </div>
                        <div class="metric">
                            <div class="metric-value">8</div>
                            <div class="metric-label">Week Campaign</div>
                        </div>
                        <div class="metric">
                            <div class="metric-value">12</div>
                            <div class="metric-label">Stakeholders</div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Project 2 -->
            <div class="project-card">
                <div class="project-visual visual-2">
                    <div class="project-number">02</div>
                    <div class="process-animation">
                        <div class="gear gear-1"></div>
                        <div class="gear gear-2"></div>
                    </div>
                </div>
                <div class="project-content">
                    <span class="project-tag">Operations</span>
                    <h3 class="project-title">Marketing Operations System</h3>
                    <p class="project-description">
                        Transformed fragmented campaign execution into standardized system. Reduced creative review cycles from 5 days to 3. Doubled quarterly campaign capacity without adding headcount.
                    </p>
                    <div class="project-metrics">
                        <div class="metric">
                            <div class="metric-value">40%</div>
                            <div class="metric-label">Faster Cycles</div>
                        </div>
                        <div class="metric">
                            <div class="metric-value">20%</div>
                            <div class="metric-label">Cost Efficiency</div>
                        </div>
                        <div class="metric">
                            <div class="metric-value">12+</div>
                            <div class="metric-label">Campaigns/Quarter</div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Project 3 -->
            <div class="project-card">
                <div class="project-visual visual-3">
                    <div class="project-number">03</div>
                    <div class="network-animation">
                        <div class="network-node"></div>
                        <div class="network-node"></div>
                        <div class="network-node"></div>
                        <div class="network-node"></div>
                    </div>
                </div>
                <div class="project-content">
                    <span class="project-tag">Partnership</span>
                    <h3 class="project-title">Agency Relationship Reset</h3>
                    <p class="project-description">
                        Diagnosed failing creative agency relationship through analysis of 15 projects. Transformed satisfaction from 4/10 to 8/10. Saved agency partnership on verge of cancellation.
                    </p>
                    <div class="project-metrics">
                        <div class="metric">
                            <div class="metric-value">100%</div>
                            <div class="metric-label">Satisfaction Gain</div>
                        </div>
                        <div class="metric">
                            <div class="metric-value">15</div>
                            <div class="metric-label">Projects Analyzed</div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Project 4 -->
            <div class="project-card">
                <div class="project-visual visual-4">
                    <div class="project-number">04</div>
                    <div class="documents-animation">
                        <div class="document"></div>
                        <div class="document"></div>
                        <div class="document"></div>
                        <div class="document"></div>
                        <div class="document"></div>
                    </div>
                </div>
                <div class="project-content">
                    <span class="project-tag">Sales Enablement</span>
                    <h3 class="project-title">Sales Asset Library</h3>
                    <p class="project-description">
                        Built comprehensive asset system—20+ materials. Interviewed top performers to understand needs. Reduced sales cycle time by 15%.
                    </p>
                    <div class="project-metrics">
                        <div class="metric">
                            <div class="metric-value">15%</div>
                            <div class="metric-label">Faster Cycles</div>
                        </div>
                        <div class="metric">
                            <div class="metric-value">20+</div>
                            <div class="metric-label">Assets Created</div>
                        </div>
                        <div class="metric">
                            <div class="metric-value">25%</div>
                            <div class="metric-label">Better Conversion</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Stats Section -->
    <section class="stats-section">
        <div class="stats-grid">
            <div class="stat-item">
                <div class="stat-number">40%</div>
                <div class="stat-label">Faster Review Cycles</div>
            </div>
            <div class="stat-item">
                <div class="stat-number">12+</div>
                <div class="stat-label">Campaigns Per Quarter</div>
            </div>
            <div class="stat-item">
                <div class="stat-number">20%</div>
                <div class="stat-label">Cost Efficiency Gain</div>
            </div>
            <div class="stat-item">
                <div class="stat-number">0</div>
                <div class="stat-label">Missed Deadlines</div>
            </div>
        </div>
    </section>

    <!-- Comprehensive Timeline Section -->
    <section id="timeline" class="timeline-section">
        <div class="section-header">
            <div class="section-number">02 — Journey</div>
            <h2 class="section-title">My Complete<br>Timeline</h2>
            <p class="section-description" style="color: var(--gray);">
                From education to multi-industry experience—each chapter builds on systematic thinking and operational excellence.
            </p>
        </div>

        <!-- Interactive World Map -->
        <div class="world-map-wrapper">
            <h3 class="map-title">🌍 Global Journey Map</h3>
            <p class="map-subtitle">Click on the glowing markers to explore my journey across continents</p>
            
            <div class="world-map-container">
                <svg class="world-map-svg" viewBox="0 0 1000 500" xmlns="http://www.w3.org/2000/svg">
                    <!-- World Map Continents -->
                    <g class="map-continents">
                        <!-- North America -->
                        <path d="M 80,120 Q 120,80 160,100 L 200,110 Q 240,105 270,130 L 290,160 Q 300,180 290,200 L 270,220 Q 250,230 230,220 L 200,210 Q 170,200 150,180 L 120,160 Q 90,140 80,120 Z" fill="rgba(255,255,255,0.1)" stroke="rgba(255,255,255,0.4)" stroke-width="1"/>
                        
                        <!-- South America -->
                        <path d="M 220,250 Q 240,240 255,250 L 270,280 Q 280,320 270,360 Q 260,390 245,405 L 230,395 Q 220,360 215,320 L 210,280 Q 215,260 220,250 Z" fill="rgba(255,255,255,0.1)" stroke="rgba(255,255,255,0.4)" stroke-width="1"/>
                        
                        <!-- Europe -->
                        <path d="M 480,110 Q 510,100 540,105 L 570,120 Q 590,135 580,150 L 560,160 Q 540,155 520,145 L 500,130 Q 480,120 480,110 Z" fill="rgba(255,255,255,0.1)" stroke="rgba(255,255,255,0.4)" stroke-width="1"/>
                        
                        <!-- Africa -->
                        <path d="M 500,180 Q 530,170 560,180 L 580,220 Q 590,260 580,300 Q 570,340 550,360 L 520,350 Q 500,320 490,280 L 485,240 Q 490,200 500,180 Z" fill="rgba(255,255,255,0.1)" stroke="rgba(255,255,255,0.4)" stroke-width="1"/>
                        
                        <!-- Asia -->
                        <path d="M 620,120 Q 670,110 720,125 L 770,140 Q 820,155 840,180 L 830,220 Q 810,240 780,235 L 740,225 Q 700,210 670,195 L 640,170 Q 620,145 620,120 Z" fill="rgba(255,255,255,0.1)" stroke="rgba(255,255,255,0.4)" stroke-width="1"/>
                        
                        <!-- Australia -->
                        <path d="M 780,360 Q 820,350 860,365 L 880,390 Q 890,420 870,440 L 830,435 Q 800,420 780,400 L 775,380 Q 775,370 780,360 Z" fill="rgba(255,255,255,0.1)" stroke="rgba(255,255,255,0.4)" stroke-width="1"/>
                        
                        <!-- Connection Lines between locations -->
                        <line class="connection-line" x1="750" y1="250" x2="500" y2="130" stroke="rgba(255,215,0,0.3)" stroke-width="2" stroke-dasharray="5,5"/>
                        <line class="connection-line" x1="500" y1="130" x2="710" y2="250" stroke="rgba(255,215,0,0.3)" stroke-width="2" stroke-dasharray="5,5"/>
                        <line class="connection-line" x1="710" y1="250" x2="180" y2="140" stroke="rgba(255,215,0,0.3)" stroke-width="2" stroke-dasharray="5,5"/>
                    </g>
                </svg>
                
                <!-- Interactive Location Markers -->
                <div class="map-markers">
                    <!-- India - Multiple locations -->
                    <div class="location-marker marker-india-general" data-location="india-edu" style="top: 38%; left: 75%;">
                        <div class="marker-pulse"></div>
                        <div class="marker-dot"></div>
                        <div class="location-popup">
                            <div class="popup-header">
                                <span class="popup-flag">🇮🇳</span>
                                <span class="popup-title">India</span>
                            </div>
                            <div class="popup-date">2017 - 2021</div>
                            <div class="popup-role">Bachelor of Engineering - Aerospace</div>
                            <div class="popup-company">University Education</div>
                            <div class="popup-description">
                                Built foundation in engineering principles and systematic problem-solving. Started journey in operations and systems thinking.
                            </div>
                        </div>
                    </div>

                    <!-- Chennai, India - Vugha -->
                    <div class="location-marker marker-chennai-1" data-location="chennai-vugha" style="top: 42%; left: 73%;">
                        <div class="marker-pulse"></div>
                        <div class="marker-dot"></div>
                        <div class="location-popup">
                            <div class="popup-header">
                                <span class="popup-flag">🇮🇳</span>
                                <span class="popup-title">Chennai, India</span>
                            </div>
                            <div class="popup-date">Sep - Dec 2020</div>
                            <div class="popup-role">Business Development Manager</div>
                            <div class="popup-company">Vugha Technologies (Internship)</div>
                            <div class="popup-highlights">
                                <div>✓ Identified 50+ potential clients</div>
                                <div>✓ Increased engagement by 11%</div>
                                <div>✓ Expanded client base by 15%</div>
                            </div>
                        </div>
                    </div>

                    <!-- Chennai, India - Garuda -->
                    <div class="location-marker marker-chennai-2" data-location="chennai-garuda" style="top: 41%; left: 71%;">
                        <div class="marker-pulse"></div>
                        <div class="marker-dot"></div>
                        <div class="location-popup">
                            <div class="popup-header">
                                <span class="popup-flag">🇮🇳</span>
                                <span class="popup-title">Chennai, India</span>
                            </div>
                            <div class="popup-date">Jan - Dec 2021</div>
                            <div class="popup-role">Process Engineer</div>
                            <div class="popup-company">Garuda Aerospace</div>
                            <div class="popup-highlights">
                                <div>✓ Reduced defects by 2.3%</div>
                                <div>✓ Improved cycle time by 7%</div>
                                <div>✓ Enhanced efficiency by 5%</div>
                            </div>
                        </div>
                    </div>

                    <!-- Paris, France -->
                    <div class="location-marker marker-paris" data-location="paris" style="top: 26%; left: 50%;">
                        <div class="marker-pulse"></div>
                        <div class="marker-dot"></div>
                        <div class="location-popup">
                            <div class="popup-header">
                                <span class="popup-flag">🇫🇷</span>
                                <span class="popup-title">Paris, France</span>
                            </div>
                            <div class="popup-date">2019</div>
                            <div class="popup-role">Exchange Program</div>
                            <div class="popup-company">Aerospace Engineering</div>
                            <div class="popup-description">
                                Managed cross-functional projects in international environment. Developed cultural adaptability and global collaboration skills.
                            </div>
                        </div>
                    </div>

                    <!-- Bangalore, India -->
                    <div class="location-marker marker-bangalore" data-location="bangalore" style="top: 43%; left: 71.5%;">
                        <div class="marker-pulse"></div>
                        <div class="marker-dot"></div>
                        <div class="location-popup">
                            <div class="popup-header">
                                <span class="popup-flag">🇮🇳</span>
                                <span class="popup-title">Bangalore, India</span>
                            </div>
                            <div class="popup-date">Oct 2021 - Nov 2022</div>
                            <div class="popup-role">Marketing Coordinator</div>
                            <div class="popup-company">ADVANIX IT Solutions</div>
                            <div class="popup-highlights">
                                <div>✓ 12+ campaigns quarterly</div>
                                <div>✓ 40% faster review cycles</div>
                                <div>✓ 20% efficiency improvement</div>
                                <div>✓ Zero missed deadlines</div>
                            </div>
                        </div>
                    </div>

                    <!-- Saskatoon, Canada - No Frills -->
                    <div class="location-marker marker-saskatoon-1" data-location="saskatoon-nofrills" style="top: 24%; left: 18%;">
                        <div class="marker-pulse"></div>
                        <div class="marker-dot"></div>
                        <div class="location-popup">
                            <div class="popup-header">
                                <span class="popup-flag">🇨🇦</span>
                                <span class="popup-title">Saskatoon, Canada</span>
                            </div>
                            <div class="popup-date">Jan 2023 - Feb 2025</div>
                            <div class="popup-role">Produce Supervisor</div>
                            <div class="popup-company">No Frills (Loblaw)</div>
                            <div class="popup-highlights">
                                <div>✓ Led team of 10+ employees</div>
                                <div>✓ Reduced waste by 10%</div>
                                <div>✓ Six Sigma implementation</div>
                            </div>
                        </div>
                    </div>

                    <!-- Saskatoon, Canada - Current -->
                    <div class="location-marker marker-saskatoon-2 marker-current" data-location="saskatoon-current" style="top: 23%; left: 18%;">
                        <div class="marker-pulse pulse-current"></div>
                        <div class="marker-dot dot-current"></div>
                        <div class="location-popup">
                            <div class="popup-header">
                                <span class="popup-flag">🇨🇦</span>
                                <span class="popup-title">Saskatoon, Canada</span>
                                <span class="popup-badge">CURRENT</span>
                            </div>
                            <div class="popup-date">Feb 2025 - Present</div>
                            <div class="popup-role">Inventory & SAP Operations Manager</div>
                            <div class="popup-company">Loblaw Companies Limited</div>
                            <div class="popup-highlights">
                                <div>✓ Reduced KPI from 75% to 13%</div>
                                <div>✓ Optimized picklists 60%</div>
                                <div>✓ SAP system management</div>
                                <div>✓ Master's degree in progress</div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Map Legend -->
                <div class="map-legend">
                    <div class="legend-item">
                        <div class="legend-dot" style="background: #FFD700;"></div>
                        <span>Education</span>
                    </div>
                    <div class="legend-item">
                        <div class="legend-dot" style="background: #667eea;"></div>
                        <span>Early Career</span>
                    </div>
                    <div class="legend-item">
                        <div class="legend-dot" style="background: #f093fb;"></div>
                        <span>Marketing</span>
                    </div>
                    <div class="legend-item">
                        <div class="legend-dot" style="background: #43e97b;"></div>
                        <span>Operations</span>
                    </div>
                    <div class="legend-item">
                        <div class="legend-dot dot-current"></div>
                        <span>Current Role</span>
                    </div>
                </div>
            </div>
        </div>

        <div class="timeline-container">
            <div class="timeline-track">
                <div class="timeline-line"></div>

                <!-- Education: Bachelor's Degree -->
                <div class="timeline-entry">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-date">2017 - 2021</div>
                        <div class="timeline-location">📍 India</div>
                        <div class="timeline-role">Bachelor of Engineering - Aerospace</div>
                        <div class="timeline-company">University</div>
                        <div class="timeline-description">
                            Built foundation in engineering principles and systematic problem-solving. Completed exchange program in Paris, developing cross-cultural collaboration skills.
                        </div>
                    </div>
                </div>

                <!-- Exchange Program -->
                <div class="timeline-entry">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-date">2019</div>
                        <div class="timeline-location">📍 Paris, France</div>
                        <div class="timeline-role">Exchange Program</div>
                        <div class="timeline-company">Aerospace Engineering</div>
                        <div class="timeline-description">
                            Managed cross-functional projects in international environment. Developed cultural adaptability and communication skills essential for global business operations.
                        </div>
                    </div>
                </div>

                <!-- Vugha Technologies -->
                <div class="timeline-entry">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-date">Sep 2020 - Dec 2020</div>
                        <div class="timeline-location">📍 Chennai, India</div>
                        <div class="timeline-role">Business Development Manager (Intern)</div>
                        <div class="timeline-company">Vugha Technologies</div>
                        <div class="timeline-highlights">
                            <div class="timeline-highlight">Identified 50+ potential clients through market trend analysis</div>
                            <div class="timeline-highlight">Increased product engagement by 11% using data-driven strategies</div>
                            <div class="timeline-highlight">Expanded client base by 15% leveraging Six Sigma methodologies</div>
                        </div>
                    </div>
                </div>

                <!-- Garuda Aerospace -->
                <div class="timeline-entry">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-date">Jan 2021 - Dec 2021</div>
                        <div class="timeline-location">📍 Chennai, India</div>
                        <div class="timeline-role">Process Engineer</div>
                        <div class="timeline-company">Garuda Aerospace Private Limited</div>
                        <div class="timeline-highlights">
                            <div class="timeline-highlight">Reduced defect rates by 2.3% through APQP implementation</div>
                            <div class="timeline-highlight">Improved manufacturing cycle times by 7% with robotic welding</div>
                            <div class="timeline-highlight">Increased process efficiency by 5% via Lean Manufacturing</div>
                            <div class="timeline-highlight">Enhanced operational reliability by 4.6% through predictive maintenance</div>
                        </div>
                    </div>
                </div>

                <!-- ADVANIX IT Solutions -->
                <div class="timeline-entry">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-date">Oct 2021 - Nov 2022</div>
                        <div class="timeline-location">📍 Bangalore, India</div>
                        <div class="timeline-role">Marketing Coordinator</div>
                        <div class="timeline-company">ADVANIX IT Solutions</div>
                        <div class="timeline-highlights">
                            <div class="timeline-highlight">Executed 12+ marketing campaigns quarterly across multiple channels</div>
                            <div class="timeline-highlight">Reduced creative review cycles from 5 days to 3 days (40% improvement)</div>
                            <div class="timeline-highlight">Improved campaign efficiency by 20% through post-mortem analysis</div>
                            <div class="timeline-highlight">Developed campaign execution playbook adopted across team</div>
                            <div class="timeline-highlight">Coordinated largest product launch with zero missed deadlines</div>
                        </div>
                    </div>
                </div>

                <!-- No Frills -->
                <div class="timeline-entry">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-date">Jan 2023 - Feb 2025</div>
                        <div class="timeline-location">📍 Saskatoon, Canada</div>
                        <div class="timeline-role">Produce Supervisor</div>
                        <div class="timeline-company">No Frills (Loblaw Companies)</div>
                        <div class="timeline-highlights">
                            <div class="timeline-highlight">Supervised and mentored team of 10+ employees</div>
                            <div class="timeline-highlight">Reduced waste by 10% through JIT stocking and SAP ERP forecasting</div>
                            <div class="timeline-highlight">Implemented Six Sigma continuous improvement projects</div>
                            <div class="timeline-highlight">Ensured compliance with OSHA safety standards and food safety regulations</div>
                        </div>
                    </div>
                </div>

                <!-- Current: Loblaw -->
                <div class="timeline-entry">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-date">Feb 2025 - Present</div>
                        <div class="timeline-location">📍 Saskatoon, Canada</div>
                        <div class="timeline-role">Inventory & SAP Operations Manager</div>
                        <div class="timeline-company">Loblaw Companies Limited (MacNeil's Your Independent Grocer)</div>
                        <div class="timeline-highlights">
                            <div class="timeline-highlight">Reduced "hole match" KPI from 47-75% to 13-17% (surpassing 24% standard)</div>
                            <div class="timeline-highlight">Lowered daily picklist volumes from 25-28 pages to 10-15 pages</div>
                            <div class="timeline-highlight">Applied data-driven cycle counting for improved inventory confidence</div>
                            <div class="timeline-highlight">Managed SAP receiving, procurement, and replenishment functions</div>
                            <div class="timeline-highlight">Led structured floor walks integrated with system audits</div>
                        </div>
                    </div>
                </div>

                <!-- Master's Degree -->
                <div class="timeline-entry">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-date">2023 - Present</div>
                        <div class="timeline-location">📍 Saskatoon, Canada</div>
                        <div class="timeline-role">Master's Degree Program</div>
                        <div class="timeline-company">Graduate Studies</div>
                        <div class="timeline-description">
                            Pursuing advanced education while applying operational excellence principles across retail operations. Proving systematic thinking transfers across industries and domains.
                        </div>
                    </div>
                </div>

            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="contact-section">
        <h2 class="contact-title">Let's Build<br>Something Together</h2>
        <a href="mailto:iaayushtripathi@gmail.com" class="contact-email">iaayushtripathi@gmail.com</a>
        
        <div class="social-links">
            <a href="https://www.linkedin.com/in/iamaayushtripathi/" target="_blank">LinkedIn</a>
            <span style="color: var(--gray);">·</span>
            <a href="mailto:iaayushtripathi@gmail.com">Email</a>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div>© 2026 Aayush Tripathi</div>
        <div style="color: var(--gray);">Marketing Strategist · Saskatoon, SK</div>
        <a href="#" onclick="window.scrollTo({top: 0, behavior: 'smooth'}); return false;">Back to top ↑</a>
    </footer>

    <script>
        // Page Loader
        window.addEventListener('load', () => {
            setTimeout(() => {
                document.querySelector('.page-loader').classList.add('hidden');
            }, 2000);
        });

        // Mobile Menu Toggle
        function toggleMenu() {
            const navLinks = document.getElementById('navLinks');
            const menuToggle = document.querySelector('.menu-toggle');
            navLinks.classList.toggle('active');
            menuToggle.classList.toggle('active');
        }

        function closeMenu() {
            const navLinks = document.getElementById('navLinks');
            const menuToggle = document.querySelector('.menu-toggle');
            navLinks.classList.remove('active');
            menuToggle.classList.remove('active');
        }

        // Close menu when clicking outside
        document.addEventListener('click', (e) => {
            const navLinks = document.getElementById('navLinks');
            const menuToggle = document.querySelector('.menu-toggle');
            if (!navLinks.contains(e.target) && !menuToggle.contains(e.target)) {
                closeMenu();
            }
        });

        // Custom Cursor (Desktop Only)
        if (window.innerWidth >= 1024) {
            const cursor = document.querySelector('.cursor');
            const cursorFollower = document.querySelector('.cursor-follower');

            let mouseX = 0, mouseY = 0;
            let cursorX = 0, cursorY = 0;
            let followerX = 0, followerY = 0;

            document.addEventListener('mousemove', (e) => {
                mouseX = e.clientX;
                mouseY = e.clientY;
            });

            function animateCursor() {
                cursorX += (mouseX - cursorX) * 0.9;
                cursorY += (mouseY - cursorY) * 0.9;
                followerX += (mouseX - followerX) * 0.1;
                followerY += (mouseY - followerY) * 0.1;

                cursor.style.left = cursorX + 'px';
                cursor.style.top = cursorY + 'px';
                cursorFollower.style.left = followerX + 'px';
                cursorFollower.style.top = followerY + 'px';

                requestAnimationFrame(animateCursor);
            }
            animateCursor();

            // Cursor hover effect
            const hoverElements = document.querySelectorAll('a, button, .project-card, .timeline-content, .stat-item, .fab');
            hoverElements.forEach(el => {
                el.addEventListener('mouseenter', () => {
                    cursor.style.width = '40px';
                    cursor.style.height = '40px';
                    cursor.style.background = 'rgba(255,215,0,0.5)';
                    cursorFollower.style.width = '60px';
                    cursorFollower.style.height = '60px';
                });
                el.addEventListener('mouseleave', () => {
                    cursor.style.width = '20px';
                    cursor.style.height = '20px';
                    cursor.style.background = 'none';
                    cursorFollower.style.width = '40px';
                    cursorFollower.style.height = '40px';
                });
            });
        }

        // Navigation scroll effect
        const nav = document.getElementById('nav');
        let lastScroll = 0;

        window.addEventListener('scroll', () => {
            const currentScroll = window.pageYOffset;
            
            if (currentScroll > 100) {
                nav.classList.add('scrolled');
            } else {
                nav.classList.remove('scrolled');
            }
            
            lastScroll = currentScroll;
        });

        // Smooth scroll helper
        function scrollToSection(id) {
            const element = document.getElementById(id);
            if (element) {
                element.scrollIntoView({ behavior: 'smooth', block: 'start' });
            }
            closeFabMenu();
            closeMenu();
        }

        // Smooth scroll for navigation
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth', block: 'start' });
                }
            });
        });

        // FAB Menu Toggle
        function toggleFabMenu() {
            const fabMenu = document.getElementById('fabMenu');
            fabMenu.classList.toggle('active');
        }

        function closeFabMenu() {
            const fabMenu = document.getElementById('fabMenu');
            fabMenu.classList.remove('active');
        }

        // Close FAB menu when clicking outside
        document.addEventListener('click', (e) => {
            const fab = document.querySelector('.fab');
            const fabMenu = document.getElementById('fabMenu');
            if (!fab.contains(e.target) && !fabMenu.contains(e.target)) {
                closeFabMenu();
            }
        });

        // Scroll reveal animations
        const observerOptions = {
            threshold: 0.15,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        document.querySelectorAll('.project-card, .timeline-entry').forEach(el => observer.observe(el));

        // Parallax effect for hero (Desktop Only)
        if (window.innerWidth >= 768) {
            window.addEventListener('scroll', () => {
                const scrolled = window.pageYOffset;
                const hero = document.querySelector('.hero');
                if (hero && scrolled < window.innerHeight) {
                    const heroContent = hero.querySelector('.hero-content');
                    heroContent.style.transform = `translateY(${scrolled * 0.3}px)`;
                    heroContent.style.opacity = 1 - (scrolled / window.innerHeight) * 0.5;
                }
            });
        }

        // Stats counter animation
        const statNumbers = document.querySelectorAll('.stat-number');
        const statsObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    const target = entry.target;
                    const finalValue = target.textContent;
                    const isPercentage = finalValue.includes('%');
                    const isPlus = finalValue.includes('+');
                    const numericValue = parseInt(finalValue.replace(/[^\d]/g, ''));
                    
                    if (!isNaN(numericValue)) {
                        let current = 0;
                        const increment = numericValue / 60;
                        const timer = setInterval(() => {
                            current += increment;
                            if (current >= numericValue) {
                                current = numericValue;
                                clearInterval(timer);
                            }
                            target.textContent = Math.floor(current) + (isPercentage ? '%' : '') + (isPlus ? '+' : '');
                        }, 25);
                    }
                    
                    statsObserver.unobserve(target);
                }
            });
        }, { threshold: 0.5 });

        statNumbers.forEach(stat => statsObserver.observe(stat));

        // Timeline entry hover effect (Desktop only)
        if (window.innerWidth >= 1024) {
            const timelineEntries = document.querySelectorAll('.timeline-content');
            timelineEntries.forEach(entry => {
                entry.addEventListener('click', function() {
                    this.style.transform = 'scale(1.02)';
                    setTimeout(() => {
                        this.style.transform = '';
                    }, 300);
                });
            });
        }

        // Scroll Progress Bar
        const scrollProgress = document.querySelector('.scroll-progress');
        window.addEventListener('scroll', () => {
            const windowHeight = document.documentElement.scrollHeight - document.documentElement.clientHeight;
            const scrolled = (window.pageYOffset / windowHeight) * 100;
            scrollProgress.style.width = scrolled + '%';
        });

        // Add keyboard navigation (Desktop only)
        if (window.innerWidth >= 768) {
            document.addEventListener('keydown', (e) => {
                if (e.key === 'ArrowDown') {
                    window.scrollBy({ top: 100, behavior: 'smooth' });
                } else if (e.key === 'ArrowUp') {
                    window.scrollBy({ top: -100, behavior: 'smooth' });
                } else if (e.key === 'Home') {
                    window.scrollTo({ top: 0, behavior: 'smooth' });
                } else if (e.key === 'End') {
                    window.scrollTo({ top: document.body.scrollHeight, behavior: 'smooth' });
                }
            });
        }

        // Project visual 3D tilt effect (Desktop only)
        if (window.innerWidth >= 1024) {
            const projectCards = document.querySelectorAll('.project-card');
            projectCards.forEach(card => {
                const visual = card.querySelector('.project-visual');
                
                card.addEventListener('mousemove', (e) => {
                    const rect = visual.getBoundingClientRect();
                    const x = e.clientX - rect.left;
                    const y = e.clientY - rect.top;
                    const centerX = rect.width / 2;
                    const centerY = rect.height / 2;
                    const rotateX = (y - centerY) / 15;
                    const rotateY = (centerX - x) / 15;
                    
                    visual.style.transform = `perspective(1000px) rotateX(${rotateX}deg) rotateY(${rotateY}deg) scale(1.02)`;
                });
                
                card.addEventListener('mouseleave', () => {
                    visual.style.transform = 'perspective(1000px) rotateX(0) rotateY(0) scale(1)';
                });
            });
        }

        // Touch feedback for mobile
        if ('ontouchstart' in window) {
            const touchElements = document.querySelectorAll('.project-visual, .stat-item, .timeline-content');
            touchElements.forEach(el => {
                el.addEventListener('touchstart', function() {
                    this.style.transform = 'scale(0.98)';
                });
                el.addEventListener('touchend', function() {
                    this.style.transform = '';
                });
            });
        }

        // Prevent mobile bounce scroll
        let lastTouchY = 0;
        document.addEventListener('touchmove', (e) => {
            const touchY = e.touches[0].clientY;
            const touchYDelta = touchY - lastTouchY;
            lastTouchY = touchY;

            if (document.body.scrollTop === 0 && touchYDelta > 0) {
                e.preventDefault();
            }
        }, { passive: false });

        // Console Easter Egg
        console.log('%c👋 Welcome to my portfolio!', 'font-size: 20px; color: #FFD700; font-weight: bold;');
        console.log('%cBuilt with passion, precision, and a lot of coffee ☕', 'font-size: 14px; color: #9C9C9C;');
        console.log('%cInterested in working together? Let\'s chat!', 'font-size: 14px; color: #000;');
        console.log('%ciaayushtripathi@gmail.com', 'font-size: 14px; color: #FFD700; font-weight: bold;');

        // Performance optimization: Debounce scroll events
        function debounce(func, wait) {
            let timeout;
            return function executedFunction(...args) {
                const later = () => {
                    clearTimeout(timeout);
                    func(...args);
                };
                clearTimeout(timeout);
                timeout = setTimeout(later, wait);
            };
        }

        // Lazy load animations on mobile for better performance
        if (window.innerWidth <= 768) {
            const animations = document.querySelectorAll('.chart-bar, .gear, .network-node, .document');
            animations.forEach(anim => {
                anim.style.animationPlayState = 'paused';
            });

            const animObserver = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        const anims = entry.target.querySelectorAll('.chart-bar, .gear, .network-node, .document');
                        anims.forEach(anim => {
                            anim.style.animationPlayState = 'running';
                        });
                    }
                });
            }, { threshold: 0.3 });

            document.querySelectorAll('.project-visual').forEach(visual => {
                animObserver.observe(visual);
            });
        }

        // Add haptic feedback for mobile interactions (if supported)
        if ('vibrate' in navigator) {
            const clickableElements = document.querySelectorAll('a, button, .project-card, .stat-item, .fab');
            clickableElements.forEach(el => {
                el.addEventListener('touchstart', () => {
                    navigator.vibrate(10);
                });
            });
        }

        // Responsive font size adjustment
        function adjustFontSizes() {
            const width = window.innerWidth;
            if (width < 375) {
                document.documentElement.style.fontSize = '14px';
            } else {
                document.documentElement.style.fontSize = '16px';
            }
        }

        adjustFontSizes();
        window.addEventListener('resize', debounce(adjustFontSizes, 250));

        // Interactive Map Markers
        const locationMarkers = document.querySelectorAll('.location-marker');
        
        locationMarkers.forEach(marker => {
            // Desktop: hover to show
            if (window.innerWidth >= 768) {
                marker.addEventListener('mouseenter', function() {
                    // Close all other popups
                    locationMarkers.forEach(m => m.classList.remove('active'));
                    // Open this one
                    this.classList.add('active');
                });

                marker.addEventListener('mouseleave', function() {
                    this.classList.remove('active');
                });
            } 
            // Mobile: tap to toggle
            else {
                marker.addEventListener('click', function(e) {
                    e.stopPropagation();
                    const isActive = this.classList.contains('active');
                    
                    // Close all popups
                    locationMarkers.forEach(m => m.classList.remove('active'));
                    
                    // Toggle this one
                    if (!isActive) {
                        this.classList.add('active');
                    }
                });
            }
        });

        // Close popups when clicking outside (mobile)
        document.addEventListener('click', function(e) {
            if (!e.target.closest('.location-marker')) {
                locationMarkers.forEach(m => m.classList.remove('active'));
            }
        });

        // Map continent hover effects
        const continents = document.querySelectorAll('.map-continents path');
        continents.forEach(continent => {
            continent.addEventListener('mouseenter', function() {
                this.style.fill = 'rgba(255,215,0,0.15)';
                this.style.stroke = 'var(--accent)';
                this.style.strokeWidth = '2';
            });
            
            continent.addEventListener('mouseleave', function() {
                this.style.fill = 'rgba(255,255,255,0.1)';
                this.style.stroke = 'rgba(255,255,255,0.4)';
                this.style.strokeWidth = '1';
            });
        });

        // Animate markers on scroll into view
        const mapContainer = document.querySelector('.world-map-container');
        const mapObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    locationMarkers.forEach((marker, index) => {
                        setTimeout(() => {
                            marker.style.opacity = '0';
                            marker.style.transform = 'scale(0)';
                            setTimeout(() => {
                                marker.style.transition = 'all 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55)';
                                marker.style.opacity = '1';
                                marker.style.transform = 'scale(1)';
                            }, 50);
                        }, index * 200);
                    });
                    mapObserver.unobserve(entry.target);
                }
            });
        }, { threshold: 0.3 });

        if (mapContainer) {
            mapObserver.observe(mapContainer);
        }

        // Add touch feedback for map markers on mobile
        if ('ontouchstart' in window) {
            locationMarkers.forEach(marker => {
                marker.addEventListener('touchstart', function() {
                    this.style.transform = 'scale(1.1)';
                    if ('vibrate' in navigator) {
                        navigator.vibrate(10);
                    }
                });
                
                marker.addEventListener('touchend', function() {
                    setTimeout(() => {
                        this.style.transform = 'scale(1)';
                    }, 100);
                });
            });
        }

        // Intersection Observer for timeline staggered animations
        const timelineEntries = document.querySelectorAll('.timeline-entry');
        const timelineObserver = new IntersectionObserver((entries) => {
            entries.forEach((entry, index) => {
                if (entry.isIntersecting) {
                    setTimeout(() => {
                        entry.target.style.opacity = '1';
                        entry.target.style.transform = 'translateY(0)';
                    }, index * 100);
                }
            });
        }, { threshold: 0.2 });

        timelineEntries.forEach(item => {
            timelineObserver.observe(item);
        });

        // Screen orientation change handler
        window.addEventListener('orientationchange', () => {
            setTimeout(() => {
                window.scrollTo(window.scrollX, window.scrollY);
            }, 100);
        });

        // Accessibility: Skip to content
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Tab' && e.shiftKey === false) {
                const firstFocusable = document.querySelector('a, button');
                if (document.activeElement === document.body && firstFocusable) {
                    e.preventDefault();
                    firstFocusable.focus();
                }
            }
        });
    </script>
</body>
</html>
