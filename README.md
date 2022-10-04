# aftFPDF
** This repository is the official one for cloning aftFPDF releases.

On top of tFPDF features, aftFPDF implements AcroForm support to generate forms within PDF files.

aftFPDF offers two new functions, TextField and CheckboxField, to create text and signature fields, checkboxes and radio buttons.

You should make the 'unifont' folder writeable (CHMOD 755 or 644). Although this
is not essential, it allows caching of the font metrics the first time a font is used,
making subsequent uses much faster.

All aftFPDF requires is a .ttf TrueType font file. The file should be placed in the
'unifont' directory. Optionally, you can also define the path to your system fonts e.g. 'C:\Windows\Font'
(see the example ex.php file) and reference TrueType fonts in this directory.

## Usage

Notice that aftFPDF is not name-spaced. You can extend the class this way:

```php 
namespace your\namespace;
    
class Document extends \aftFPDF
```

or create an instance this way:

```php 
$pdf = new \aftFPDF();
```
