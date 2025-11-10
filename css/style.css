// Mobile menu toggle with animation
function toggleMenu() {
    const menu = document.getElementById('navMenu');
    const mobileBtn = document.querySelector('.mobile-menu');
    
    menu.classList.toggle('active');
    mobileBtn.classList.toggle('active');
    
    // Animate hamburger to X
    if (menu.classList.contains('active')) {
        mobileBtn.innerHTML = '✕';
    } else {
        mobileBtn.innerHTML = '☰';
    }
}

// Smooth scrolling with offset for fixed header
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function (e) {
        e.preventDefault();
        const target = document.querySelector(this.getAttribute('href'));
        if (target) {
            // Close mobile menu if open
            document.getElementById('navMenu').classList.remove('active');
            document.querySelector('.mobile-menu').innerHTML = '☰';
            
            const headerOffset = 80;
            const elementPosition = target.offsetTop;
            const offsetPosition = elementPosition - headerOffset;

            window.scrollTo({
                top: offsetPosition,
                behavior: 'smooth'
            });
        }
    });
});

// Back to top button with progress indicator
const backToTopButton = document.getElementById('backToTop');
const progressRing = document.querySelector('.progress-ring');

window.addEventListener('scroll', () => {
    const scrolled = (window.pageYOffset / (document.documentElement.scrollHeight - window.innerHeight)) * 100;
    
    if (window.pageYOffset > 300) {
        backToTopButton.classList.add('visible');
        if (progressRing) {
            const circumference = 2 * Math.PI * 36;
            progressRing.style.strokeDashoffset = circumference - (scrolled / 100) * circumference;
        }
    } else {
        backToTopButton.classList.remove('visible');
    }
});

backToTopButton.addEventListener('click', () => {
    window.scrollTo({
        top: 0,
        behavior: 'smooth'
    });
});

// Enhanced animations with Intersection Observer
const observerOptions = {
    threshold: 0.1,
    rootMargin: '0px 0px -50px 0px'
};

const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.classList.add('animate-in');
            observer.unobserve(entry.target);
        }
    });
}, observerOptions);

// Initialize animations
function initAnimations() {
    document.querySelectorAll('.fade-in').forEach(el => {
        el.style.opacity = '0';
        el.style.transform = 'translateY(30px)';
        el.style.transition = 'all 0.8s ease';
        observer.observe(el);
    });

    // Stagger animation for service cards
    document.querySelectorAll('.service-card').forEach((card, index) => {
        card.style.transitionDelay = `${index * 0.1}s`;
        observer.observe(card);
    });

    // Stagger animation for blog cards
    document.querySelectorAll('.blog-card').forEach((card, index) => {
        card.style.transitionDelay = `${index * 0.1}s`;
        observer.observe(card);
    });
}

// Enhanced FAQ functionality with smooth animations
function initFAQ() {
    const faqQuestions = document.querySelectorAll('.faq-question');
    
    faqQuestions.forEach(question => {
        question.addEventListener('click', function() {
            const answer = this.nextElementSibling;
            const plusMinus = this.querySelector('span');
            const isOpening = !answer.classList.contains('active');
            
            // Close all FAQs
            document.querySelectorAll('.faq-answer').forEach(ans => {
                ans.classList.remove('active');
                ans.style.maxHeight = '0';
            });
            document.querySelectorAll('.faq-question').forEach(q => {
                q.classList.remove('active');
                q.querySelector('span').textContent = '+';
            });
            
            // Open current if it was closed
            if (isOpening) {
                answer.classList.add('active');
                answer.style.maxHeight = answer.scrollHeight + 'px';
                plusMinus.textContent = '−';
                this.classList.add('active');
            }
        });
    });
}

// Enhanced newsletter with modern validation
function initNewsletter() {
    const newsletterForm = document.querySelector('.newsletter-form');
    if (newsletterForm) {
        newsletterForm.addEventListener('submit', function(e) {
            e.preventDefault();
            const emailInput = this.querySelector('.newsletter-input');
            const email = emailInput.value.trim();
            
            if (validateEmail(email)) {
                showSuccessMessage('🎉 Welcome to AI Marketing Hub! Check your email for our welcome gift.');
                emailInput.value = '';
                
                // Add confetti effect
                createConfetti();
            } else {
                showErrorMessage('Please enter a valid email address.');
                emailInput.classList.add('error');
                setTimeout(() => emailInput.classList.remove('error'), 2000);
            }
        });
        
        // Real-time validation
        const emailInput = newsletterForm.querySelector('.newsletter-input');
        emailInput.addEventListener('input', function() {
            if (this.value.trim() && !validateEmail(this.value.trim())) {
                this.classList.add('warning');
            } else {
                this.classList.remove('warning');
            }
        });
    }
}

// Email validation
function validateEmail(email) {
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return emailRegex.test(email);
}

// Modern notification system
function showSuccessMessage(message) {
    showNotification(message, 'success', '✅');
}

function showErrorMessage(message) {
    showNotification(message, 'error', '⚠️');
}

function showNotification(message, type = 'info', icon = 'ℹ️') {
    const notification = document.createElement('div');
    notification.className = `notification notification-${type}`;
    notification.innerHTML = `
        <span class="notification-icon">${icon}</span>
        <span class="notification-message">${message}</span>
        <button class="notification-close" onclick="this.parentElement.remove()">×</button>
    `;
    
    document.body.appendChild(notification);
    
    // Auto remove
    setTimeout(() => {
        if (notification.parentElement) {
            notification.remove();
        }
    }, 5000);
}

// Confetti effect for success
function createConfetti() {
    const confettiContainer = document.createElement('div');
    confettiContainer.className = 'confetti-container';
    document.body.appendChild(confettiContainer);
    
    for (let i = 0; i < 50; i++) {
        const confetti = document.createElement('div');
        confetti.className = 'confetti';
        confetti.style.left = Math.random() * 100 + 'vw';
        confetti.style.animationDelay = Math.random() * 2 + 's';
        confetti.style.backgroundColor = getRandomColor();
        confettiContainer.appendChild(confetti);
    }
    
    setTimeout(() => confettiContainer.remove(), 3000);
}

function getRandomColor() {
    const colors = ['#667eea', '#764ba2', '#f093fb', '#f5576c', '#4facfe', '#00f2fe'];
    return colors[Math.floor(Math.random() * colors.length)];
}

// Counter animation for stats
function initCounters() {
    const counters = document.querySelectorAll('.counter');
    
    counters.forEach(counter => {
        const target = +counter.getAttribute('data-target');
        const increment = target / 100;
        let current = 0;
        
        const updateCounter = () => {
            if (current < target) {
                current += increment;
                counter.textContent = Math.ceil(current) + (counter.classList.contains('percent') ? '%' : '+');
                setTimeout(updateCounter, 20);
            } else {
                counter.textContent = target + (counter.classList.contains('percent') ? '%' : '+');
            }
        };
        
        observer.observe(counter);
    });
}

// Initialize everything when DOM is loaded
document.addEventListener('DOMContentLoaded', function() {
    initAnimations();
    initFAQ();
    initNewsletter();
    initCounters();
    
    // Add hover effects to cards
    document.querySelectorAll('.service-card, .blog-card, .testimonial-card').forEach(card => {
        card.addEventListener('mouseenter', function() {
            this.style.transform = 'translateY(-10px) scale(1.02)';
        });
        
        card.addEventListener('mouseleave', function() {
            this.style.transform = 'translateY(0) scale(1)';
        });
    });
    
    // Add click effects to buttons
    document.querySelectorAll('.btn').forEach(button => {
        button.addEventListener('click', function(e) {
            // Ripple effect
            const ripple = document.createElement('span');
            const rect = this.getBoundingClientRect();
            const size = Math.max(rect.width, rect.height);
            const x = e.clientX - rect.left - size / 2;
            const y = e.clientY - rect.top - size / 2;
            
            ripple.style.cssText = `
                position: absolute;
                border-radius: 50%;
                background: rgba(255, 255, 255, 0.6);
                transform: scale(0);
                animation: ripple 0.6s linear;
                left: ${x}px;
                top: ${y}px;
                width: ${size}px;
                height: ${size}px;
            `;
            
            this.appendChild(ripple);
            setTimeout(() => ripple.remove(), 600);
        });
    });
});

// Add dynamic copyright year
document.addEventListener('DOMContentLoaded', function() {
    const yearElement = document.querySelector('.current-year');
    if (yearElement) {
        yearElement.textContent = new Date().getFullYear();
    }
});
