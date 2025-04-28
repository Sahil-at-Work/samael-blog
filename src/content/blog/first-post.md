---
title: 'First post'
description: 'Lorem ipsum dolor sit amet'
pubDate: 'Jul 08 2022'
heroImage: '/blog-placeholder-3.jpg'
---

<style>
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 15px;
  }

  .gallery img {
    width: 100%;
    height: auto;
    border-radius: 5px;
    box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.1);
    cursor: pointer; /* Indicate that the images are clickable */
  }

  /* Styles for the image viewer overlay */
  .image-viewer {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.9);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000; /* Ensure it's on top of everything */
    opacity: 0;
    visibility: hidden;
    transition: opacity 0.3s ease-in-out, visibility 0s linear 0.3s;
  }

  .image-viewer.open {
    opacity: 1;
    visibility: visible;
    transition: opacity 0.3s ease-in-out;
  }

  .image-viewer-content {
    max-width: 90%;
    max-height: 90%;
    position: relative;
  }

  .image-viewer-content img {
    display: block;
    width: auto;
    max-height: 90vh; /* Ensure image fits within viewport */
    box-shadow: none;
    border-radius: 0;
  }

  .close-button, .prev-button, .next-button {
    position: absolute;
    top: 20px;
    color: white;
    font-size: 1.5em;
    cursor: pointer;
    background: none;
    border: none;
    padding: 10px;
    opacity: 0.7;
    transition: opacity 0.2s ease-in-out;
  }

  .close-button:hover, .prev-button:hover, .next-button:hover {
    opacity: 1;
  }

  .close-button {
    right: 20px;
  }

  .prev-button {
    left: 20px;
    top: 50%;
    transform: translateY(-50%);
  }

  .next-button {
    right: 20px;
    top: 50%;
    transform: translateY(-50%);
  }
</style>

<div class="gallery">
  <img src="https://github.com/user-attachments/assets/1853dde1-dc20-44d3-87c9-832a91f4173b" alt="Image 1" data-index="0">
  <img src="https://github.com/user-attachments/assets/6d44208a-b213-4d6c-b64c-f4cff3037114" alt="Image 2" data-index="1">
  <img src="https://github.com/user-attachments/assets/4d860b50-56c8-4131-8b2a-ada36c085dd0" alt="Image 3" data-index="2">
  <img src="https://github.com/user-attachments/assets/5416b510-be87-43fa-ad4c-a17684aae453" alt="Image 4" data-index="3">
  <img src="https://github.com/user-attachments/assets/1adfac13-5ff5-415f-aa36-0e25336a2aa6" alt="Image 5" data-index="4">
  <img src="https://github.com/user-attachments/assets/92f0b17f-e3b2-4761-b6eb-a9fbeb106439" alt="Image 6" data-index="5">
  <img src="https://github.com/user-attachments/assets/cb0e79b7-66dc-40d3-994c-173d361afa7d" alt="Image 7" data-index="6">
</div>

<div class="image-viewer">
  <div class="image-viewer-content">
    <button class="close-button">&times;</button>
    <button class="prev-button">&lt;</button>
    <img src="" alt="Full Image">
    <button class="next-button">&gt;</button>
  </div>
</div>

<script>
  const galleryImages = document.querySelectorAll('.gallery img');
  const imageViewer = document.querySelector('.image-viewer');
  const viewerImage = imageViewer.querySelector('img');
  const closeButton = imageViewer.querySelector('.close-button');
  const prevButton = imageViewer.querySelector('.prev-button');
  const nextButton = imageViewer.querySelector('.next-button');
  let currentIndex = 0;
  const imageUrls = Array.from(galleryImages).map(img => img.src);

  function openImageViewer(index) {
    currentIndex = index;
    viewerImage.src = imageUrls[currentIndex];
    imageViewer.classList.add('open');
  }

  function closeImageViewer() {
    imageViewer.classList.remove('open');
  }

  function showPreviousImage() {
    currentIndex = (currentIndex - 1 + imageUrls.length) % imageUrls.length;
    viewerImage.src = imageUrls[currentIndex];
  }

  function showNextImage() {
    currentIndex = (currentIndex + 1) % imageUrls.length;
    viewerImage.src = imageUrls[currentIndex];
  }

  galleryImages.forEach((img, index) => {
    img.addEventListener('click', () => {
      openImageViewer(index);
    });
  });

  closeButton.addEventListener('click', closeImageViewer);
  prevButton.addEventListener('click', showPreviousImage);
  nextButton.addEventListener('click', showNextImage);

  // Close viewer on outside click
  imageViewer.addEventListener('click', function(event) {
    if (event.target === imageViewer) {
      closeImageViewer();
    }
  });

  // Keyboard navigation
  document.addEventListener('keydown', function(event) {
    if (!imageViewer.classList.contains('open')) return;
    if (event.key === 'Escape') {
      closeImageViewer();
    } else if (event.key === 'ArrowLeft') {
      showPreviousImage();
    } else if (event.key === 'ArrowRight') {
      showNextImage();
    }
  });
</script>
