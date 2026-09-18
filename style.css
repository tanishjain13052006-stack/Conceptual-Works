/**
 * Haute Joaillerie — Luxury Portfolio Interactions
 * Handles smooth staggered scroll reveals and micro-interactions
 */

document.addEventListener('DOMContentLoaded', () => {
  initCardScrollReveal();
  initDynamicEmeraldParallax();
});

/**
 * Staggered fade-up reveal for video cards using IntersectionObserver
 */
function initCardScrollReveal() {
  const cards = document.querySelectorAll('.video-card');
  if (!cards.length) return;

  const observerOptions = {
    root: null,
    rootMargin: '0px 0px -40px 0px',
    threshold: 0.12
  };

  const revealObserver = new IntersectionObserver((entries, observer) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        const card = entry.target;
        const index = Array.from(cards).indexOf(card);
        
        // Staggered reveal timing: 90ms offset per card
        const delay = (index % 3) * 90;
        
        setTimeout(() => {
          card.classList.add('revealed');
        }, delay);

        observer.unobserve(card);
      }
    });
  }, observerOptions);

  cards.forEach((card) => {
    revealObserver.observe(card);
  });
}

/**
 * Very gentle parallax on the emerald ambient glow orbs on desktop mouse movement
 */
function initDynamicEmeraldParallax() {
  // Only apply gentle parallax if desktop and pointer fine
  if (!window.matchMedia('(hover: hover) and (pointer: fine)').matches) {
    return;
  }

  const orbs = document.querySelectorAll('.glow-orb');
  if (!orbs.length) return;

  let ticking = false;
  let mouseX = 0;
  let mouseY = 0;

  window.addEventListener('mousemove', (e) => {
    mouseX = (e.clientX / window.innerWidth - 0.5) * 2; // -1 to 1
    mouseY = (e.clientY / window.innerHeight - 0.5) * 2; // -1 to 1

    if (!ticking) {
      window.requestAnimationFrame(() => {
        orbs.forEach((orb, i) => {
          const depth = (i + 1) * 14;
          const shiftX = mouseX * depth;
          const shiftY = mouseY * depth;
          orb.style.translate = `${shiftX}px ${shiftY}px`;
        });
        ticking = false;
      });
      ticking = true;
    }
  }, { passive: true });
}
