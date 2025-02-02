# aftFPDF

## Description
aftFPDF is a fork of [tFPDF](https://github.com/Setasign/tFPDF) that introduces additional features, including AcroForm support and transparency. It is designed to be 100% backward compatible with tFPDF, allowing for an effortless, drop-in replacement in existing projects.

## Features
- All features from tFPDF including UTF8 support for foreign language characters
- Create AcroForm with text fields, signature fields, checkboxes, and radio buttons.
- Control element transparency using *SetAlpha*.

## Requirements
- Compatible with PHP up to version 8.3+

## Usage

### Using AcroForm Fields

#### Adding Checkboxes

Use the `CheckboxField` function to add checkboxes to your PDF. The `$properties` array can include:
- `value`: Assign a value to differentiate checkboxes. Checkboxes with the same name become mutually exclusive.
- `checked`: Set to `true` to pre-check the checkbox.

```php
$pdf->CheckboxField('option1', 20, 140, 5, 5, array('value' => 'A', 'checked' => true));
$pdf->CheckboxField('option1', 20, 150, 5, 5, array('value' => 'B'));
$pdf->CheckboxField('option2', 20, 160, 5, 5, array('checked' => true)); // Independent checkbox
```

#### Adding Text Fields

Use the `TextField` function to add text input fields. The `$properties` array can include:
- `value`: The text displayed inside the field.
- `signature`: Set to `true` to make the field a signature field.
- `multiline`: Set to `true` to allow multiple lines of text.

```php
$pdf->TextField('fullname', 'John Doe', 20, 180, 60, 10);
$pdf->TextField('comments', '', 20, 200, 100, 30, array('multiline' => true));
$pdf->TextField('signature', '', 20, 250, 80, 20, array('signature' => true));
```

### Setting Transparency (>=v1.1.0)
You can use the `SetAlpha` function to control the transparency of elements in your PDF.

```php
require('aftFPDF.php');

$pdf = new aftFPDF();

$pdf->AddFont('DejaVuSans', '', 'DejaVuSans.ttf', true);
$pdf->SetFont('DejaVuSans');

$pdf->AddPage();

// Set an alpha value for the rectangle
$pdf->SetAlpha(0.5);
$pdf->Rect(20, 20, 50, 50, 'F');

// Set an 50% alpha value for the fill, but keep 100% for the stroke
$pdf->SetAlpha(0.5, 1);
$pdf->Rect(40, 40, 50, 50, 'DF');

// Also works with text
$pdf->SetFontSize(64);
$pdf->SetAlpha(0.5);
$pdf->SetTextColor(255, 0, 0);
$pdf->Text(45, 62, "Hello World");

$pdf->SetTextColor(0, 0, 255);
$pdf->Text(46, 63, "Hello World");

$pdf->Output('output.pdf', 'F');
```

## License
This project is licensed under the **GNU Lesser General Public License v3.0 (LGPL-3.0)**.
You are free to use, modify, and distribute this library under the terms of the LGPL-3.0 license.

## Support
If you encounter issues or have questions, feel free to contact me at [gabriel@gablem.com](mailto:gabriel@gablem.com).
