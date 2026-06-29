document.addEventListener('DOMContentLoaded', () => {
  const toggle = document.querySelector('.navtoggle');
  const links = document.querySelector('.navlinks');
  if (toggle && links) {
    toggle.addEventListener('click', () => links.classList.toggle('open'));
  }

  const items = document.querySelectorAll('.reveal');
  if ('IntersectionObserver' in window && items.length) {
    const obs = new IntersectionObserver((entries) => {
      entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('in'); obs.unobserve(e.target); } });
    }, { threshold: 0.15 });
    items.forEach(i => obs.observe(i));
  } else {
    items.forEach(i => i.classList.add('in'));
  }
});
