# JetFormBuilder Submit Icon Enhancer

A lightweight WordPress plugin that enhances JetFormBuilder's submit buttons by allowing users to add icons via custom CSS classes. This plugin dynamically injects icons into the submit buttons in the frontend based on the specified class.

## Features

- Allows form creators to specify an icon for each form's submit button using the "Additional CSS Class" field in Gutenberg.
- Supports [Font Awesome](https://fontawesome.com/) icons.
- Automatically aligns icons with button text for a clean and professional appearance.
- No external CSS dependencies – all styles are handled inline.

## How It Works

1. In Gutenberg, add a `Submit` block to your JetFormBuilder form.
2. In the block's settings (sidebar), find the "Additional CSS Class" field.
3. Add a class in the format `icon-fa-{icon-name}`. For example:
   - `icon-fa-paper-plane` for a paper plane icon.
   - `icon-fa-check` for a checkmark icon.
  ![image](https://github.com/user-attachments/assets/d43f1624-7c92-4851-8078-e72d19cabd77)

4. Save the form and view it on the frontend. The icon will appear before the button text.

## Installation

### Option 1: Add to functions.php
1. Open your WordPress theme's `functions.php` file.
2. Copy and paste the following snippet:

   ```php
   add_filter('the_content', 'my_custom_icon_in_jetform_button', 20);
   function my_custom_icon_in_jetform_button($content) {
       if (preg_match_all('/<button[^>]*class="[^"]*icon-fa-([a-z0-9-]+)/i', $content, $matches)) {
           foreach ($matches[1] as $icon_name) {
               $icon_class = 'fa-' . $icon_name;
               $regex = '/(<button\b[^>]*icon-fa-' . preg_quote($icon_name, '/') . '[^>]*>)(.*?)(<\/button>)/is';
               $replacement = '$1<i class="fa ' . $icon_class . '" style="margin-right:5px; vertical-align:middle;"></i>$2$3';
               $content = preg_replace($regex, $replacement, $content);
           }
       }
       return $content;
   }

### Option 2: Use a Plugin like Code Snippets
Install and activate the free plugin Code Snippets from the WordPress plugin repository.

1. In the WordPress admin panel, navigate to Snippets > Add New.
2. Give your snippet a name like "JetFormBuilder Submit Icon Enhancer."
3. Paste the following code into the snippet editor:
   
   ```php
   add_filter('the_content', 'my_custom_icon_in_jetform_button', 20);
   function my_custom_icon_in_jetform_button($content) {
       if (preg_match_all('/<button[^>]*class="[^"]*icon-fa-([a-z0-9-]+)/i', $content, $matches)) {
           foreach ($matches[1] as $icon_name) {
               $icon_class = 'fa-' . $icon_name;
               $regex = '/(<button\b[^>]*icon-fa-' . preg_quote($icon_name, '/') . '[^>]*>)(.*?)(<\/button>)/is';
               $replacement = '$1<i class="fa ' . $icon_class . '" style="margin-right:5px; vertical-align:middle;"></i>$2$3';
               $content = preg_replace($regex, $replacement, $content);
           }
       }
       return $content;
   }

4. Set the snippet to "Run Everywhere" and save it.
5. The functionality will now be active on your website.
   
## Usage

1. Add a `Submit` block to your form in JetFormBuilder.
2. Specify an icon using the "Additional CSS Class" field in the block settings. ![image](https://github.com/user-attachments/assets/d43f1624-7c92-4851-8078-e72d19cabd77)
3. Save and preview your form on the frontend to see the icon in action.

## Example

For a button with the text "Submit" and a paper plane icon:

1. Add the class `icon-fa-paper-plane` in the block settings.
2. The resulting button will display the paper plane icon aligned to the left of the "Submit" text.

   ```html
   <button class="jet-form-builder__action-button icon-fa-paper-plane">
     <i class="fa fa-paper-plane" style="margin-right:5px; vertical-align:middle;"></i> Submit
   </button>

## Popular Icons for Submit Buttons

Here is a list of 18 popular icons for submit buttons that you can use with this plugin. Simply add the corresponding class `icon-fa-{icon-name}` in the "Additional CSS Class" field of the Submit block.

| Icon Preview | Icon Name         | Font Awesome Class  |
|--------------|-------------------|---------------------|
| 📨           | Paper Plane       | `fa-paper-plane`    |
| 📩           | Envelope          | `fa-envelope`       |
| ✔️           | Check             | `fa-check`          |
| ❌           | Times             | `fa-times`          |
| ➕           | Plus              | `fa-plus`           |
| ➖           | Minus             | `fa-minus`          |
| ⭐           | Star              | `fa-star`           |
| ❤️           | Heart             | `fa-heart`          |
| 🔔           | Bell              | `fa-bell`           |
| 🔗           | Link              | `fa-link`           |
| 📤           | Upload            | `fa-upload`         |
| 🛒           | Cart              | `fa-shopping-cart`  |
| 🔒           | Lock              | `fa-lock`           |
| 🔓           | Unlock            | `fa-unlock`         |
| 📁           | Folder            | `fa-folder`         |
| 📂           | Open Folder       | `fa-folder-open`    |
| ➡️           | Arrow Right       | `fa-arrow-right`    |
| ⬅️           | Arrow Left        | `fa-arrow-left`     |

### Example

To use the **Paper Plane** icon for a Submit button:
1. Add the class `icon-fa-paper-plane` in the "Additional CSS Class" field.
2. The resulting button will display the icon 📨 aligned to the left of the button label.


## Compatibility
WordPress: Version 5.8 or higher.
JetFormBuilder: Version 2.0 or higher.
PHP: Version 7.4 or higher.
License
This snippet is open-source and licensed under the MIT License. See the LICENSE file for details.

## Acknowledgements
JetFormBuilder – For providing a robust form-building solution.
Font Awesome – For the icons.
