<template>
  <div class="about">
    <div class="introduction">
      <p>My name is Usama Ahmed Siddiquie (or colatz online).</p>
      <p>
        This site contains work I have done involving visual mediums. Scroll to
        start viewing my projects.
      </p>
    </div>
    <div class="contact">
      <h1>CONTACT</h1>
      <p><a href="#">sayhello@colatz.com</a></p>
      <p><a href="#">220usamaahmed on LinkedIn</a></p>
    </div>
  </div>
</template>

<script>
export default {
  mounted: function() {
    const observer = new IntersectionObserver(function (entries, observer) {
      entries.forEach(entry => {
        if (!entry.isIntersecting) {
          return;
        } else {
          entry.target.classList.add('show');
          observer.unobserve(entry.target);
        }
      });
    });
    
    observer.observe(document.querySelector('.introduction'));
    observer.observe(document.querySelector('.contact'));
  },
}
</script>


<style scoped lang="scss">
.about {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  padding: 120px 0;

  // background-color: pink;

  .introduction {
    grid-column: 2 / 6;
    opacity: 0;
    transition: opacity 240ms ease-in;

    p {
      color: black;
      margin-bottom: 12px;
      line-height: 1.8rem;
    }

    p:last-child {
      margin-bottom: 0;
    }
  }

  .contact {
    grid-column: 10 / -1;
    opacity: 0;
    transition: opacity 240ms ease-in;
    transition-delay: 240ms;

    h1 {
      color: #666666;
      font-size: 1rem;
      font-weight: 400;
      margin-bottom: 12px;
    }

    p {
      margin-bottom: 12px;
      letter-spacing: 1px;

      a {
        text-decoration: underline;
        color: black;
      }
    }
  }

  .show {
    opacity: 1;
  }
}

@media only screen and (max-width: 768px) {
  .about {
    padding: 60px 24px;

    .introduction {
      grid-column: 1 / -1;

    }

    .contact {
      display: none;
      margin-top: 60px;
      grid-column: 1 / -1;
    }
  }
}
</style>
