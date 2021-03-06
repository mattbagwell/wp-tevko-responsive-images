This plugin tells WordPress to create three additional sizes for images you upload. Then it outputs special HTML (via a shortcode) that works with the Picturefill library to achieve responsive images in content.

### Usage
	
	Shortcode - 
    [responsive imageid="12" size1="0" size2="500" size3="1000"]

    PHP (use in template files) -

    <?php 
		$image = get_field('upload_image');
		$mappings = array(
            0 => 'small-img', // zero maps to default
            250 => 'large-img',
            1000 => 'full-width'
        );
	?>
	<span data-picture data-alt="<?php echo get_img_alt($image) ?>">
	   	<?php echo getPictureSrcs($image, $mappings) ?>
	   	<noscript> <?php echo wp_get_attachment_image($image, $mappings[2]) ?> </noscript>
	</span>

### Prereqs

Make sure your current theme has 

    'add_theme_support( 'post-thumbnails' );'

in the `functions.php` file.

### Tutorial

Here: http://css-tricks.com/hassle-free-responsive-images-for-wordpress