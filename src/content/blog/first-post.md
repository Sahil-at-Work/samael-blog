---
title: 'First post'
description: 'Lorem ipsum dolor sit amet'
pubDate: 'Jul 08 2022'
heroImage: '/blog-placeholder-3.jpg'
---

<style>
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); /* Adjust minmax for desired image size */
    gap: 15px; /* Adjust gap for spacing between images */
  }

  .gallery img {
    width: 100%;
    height: auto;
    border-radius: 5px; /* Optional: Add rounded corners */
    box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.1); /* Optional: Add a subtle shadow */
    transition: transform 0.3s ease-in-out; /* Optional: Add a hover effect */
  }

  .gallery img:hover {
    transform: scale(1.05); /* Optional: Slight zoom on hover */
  }
</style>

<div class="gallery">
  <img src="https://github.com/user-attachments/assets/1853dde1-dc20-44d3-87c9-832a91f4173b" alt="Image 1">
  <img src="https://github.com/user-attachments/assets/6d44208a-b213-4d6c-b64c-f4cff3037114" alt="Image 2">
  <img src="https://github.com/user-attachments/assets/4d860b50-56c8-4131-8b2a-ada36c085dd0" alt="Image 3">
  <img src="https://github.com/user-attachments/assets/5416b510-be87-43fa-ad4c-a17684aae453" alt="Image 4">
  <img src="https://github.com/user-attachments/assets/1adfac13-5ff5-415f-aa36-0e25336a2aa6" alt="Image 5">
  <img src="https://github.com/user-attachments/assets/92f0b17f-e3b2-4761-b6eb-a9fbeb106439" alt="Image 6">
  <img src="https://github.com/user-attachments/assets/cb0e79b7-66dc-40d3-994c-173d361afa7d" alt="Image 7">
</div>
