---
categories: ['Website Development']
tags: ['PHP', 'SEO']
title: 'How to create SEO friendly URL in PHP'
---

> 📄 This write-up is hosted on Notion.  
> 👉 [Click here to view the full article](https://0xkaran.notion.site/Anthem-22783fa810768027b664df6f97f59669?source=copy_link)

---

## 🔄 Auto-Redirect Notice

This repository automatically redirects to the original article hosted on Notion.

If you're not redirected automatically, [click here](https://0xkaran.notion.site/Anthem-22783fa810768027b664df6f97f59669?source=copy_link).

### 🧠 About the Writeup

In this tutorial, we will create a PHP function that converts a string into an SEO-friendly URL. The result is a URL with:

- All lowercase characters  
- No special characters  
- Hyphens instead of spaces/underscores  
- Clean and readable URLs  

### 🧩 Sample Function

```php
function seoFriendlyUrl($string) {
  $string = strtolower($string);
  $string = preg_replace('/[^a-z0-9_\s-]/', '', $string);
  $string = preg_replace('/[\s_]+/', '-', $string);
  return $string;
}
