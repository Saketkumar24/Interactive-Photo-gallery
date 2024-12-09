<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Interactive Photo Gallery</title>
        <link rel="stylesheet" href="styles.css">
    </head>
    <body>

        <!-- Gallery Section -->
        <section class="gallery">
            <div class="gallery-item">
                <img src="./Beach Paradise.jpeg" alt="Image 1"
                    class="gallery-image">
            </div>
            <div class="gallery-item">
                <img src="./Stylish Backpack.jpeg" alt="Image 2"
                    class="gallery-image">
            </div>
            <div class="gallery-item">
                <img src="./Urban Skyline.jpeg" alt="Image 3"
                    class="gallery-image">
            </div>
            <div class="gallery-item">
                <img src="./Serene Forest.jpeg" alt="Image 4"
                    class="gallery-image">
            </div>
            <div class="gallery-item">
                <img src="./Running Shoes.jpeg" alt="Image 5"
                    class="gallery-image">
            </div>
            <div class="gallery-item">
                <img src="./Mountain Landscape 1.jpeg" alt="Image 6"
                    class="gallery-image">
            </div>
            <div class="gallery-item">
                <img src="./Casual T-Shirt.jpeg" alt="Image 7"
                    class="gallery-image">
            </div>
        </section>

        <!-- Modal -->
        <div id="modal" class="modal">
            <span id="close" class="close">&times;</span>
            <img id="modal-image" class="modal-content" src>
            <div id="caption" class="caption"></div>
        </div>

        <script src="script.js"></script>
    </body>
</html>



/* General Reset */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  
  body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    background-color: #f4f4f4;
  }
  
  h1 {
    text-align: center;
    margin-bottom: 2rem;
    color: #333;
  }
  
  /* Gallery Layout */
  .gallery {
    background-color: rgb(218, 251, 251);
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 1rem;
    padding: 1rem;
  }
  
  .gallery-item {
    overflow: hidden;
    border-radius: 5px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }
  
  .gallery-image {
    width: 100%;
    height: auto;
    cursor: pointer;
    transition: transform 0.3s ease;
  }
  
  .gallery-image:hover {
    transform: scale(1.05);
  }
  
  /* Modal Styling */
  .modal {
    display: none;
    position: fixed;
    z-index: 1;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.8);
    justify-content: center;
    align-items: center;
  }
  
  .modal-content {
    max-width: 80%;
    max-height: 80%;
    margin: auto;
    border-radius: 8px;
  }
  
  .caption {
    text-align: center;
    padding: 10px;
    color: white;
    font-size: 1.2rem;
  }
  
  /* Close Button */
  .close {
    position: absolute;
    top: 15px;
    right: 35px;
    color: white;
    font-size: 40px;
    font-weight: bold;
    cursor: pointer;
  }
  
  .close:hover,
  .close:focus {
    color: #f44336;
    text-decoration: none;
    cursor: pointer;
  }




  // Get all gallery images
const galleryImages = document.querySelectorAll('.gallery-image');

// Get modal and its components
const modal = document.getElementById('modal');
const modalImage = document.getElementById('modal-image');
const caption = document.getElementById('caption');
const closeBtn = document.getElementById('close');

// When an image is clicked, open the modal and display the clicked image
galleryImages.forEach(image => {
  image.addEventListener('click', (e) => {
    modal.style.display = 'flex';
    modalImage.src = e.target.src; // Set the source of the modal image
    caption.textContent = e.target.alt; // Set the caption text to the image alt text
  });
});

// Close the modal when the close button is clicked
closeBtn.addEventListener('click', () => {
  modal.style.display = 'none';
});

// Close the modal if the user clicks outside the modal image
window.addEventListener('click', (e) => {
  if (e.target === modal) {
    modal.style.display = 'none';
  }
});
