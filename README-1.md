# QR Code Generator using Python

A beginner-friendly Python project that generates QR codes for text, website URLs and UPI payments using the `qrcode` library. Built as part of my MCA (Python Programming) practice work.

## Features

- **Text to QR**: converts any text you type into a QR code image
- **URL to QR**: validates that the link starts with `http://` or `https://` before generating
- **Custom QR**: control over version, error correction level, box size, border and background colour
- **UPI payment QR**: generates a QR from a UPI ID and name
- **UPI QR with fixed amount**: same as above, with the amount pre-filled

## Tech Stack

- Python 3
- [qrcode](https://pypi.org/project/qrcode/)
- [Pillow](https://pypi.org/project/pillow/)
- Jupyter Notebook

## Installation

```bash
git clone https://github.com/Arpit8755/qr-code-generator-python.git
cd qr-code-generator-python
pip install qrcode pillow
jupyter notebook
```

Then open `qr_code_generator.ipynb` and run the cells one by one.

## How It Works

**1. Basic QR code**
```python
import qrcode

data = input("Enter data to make QR: ")
qr = qrcode.make(data)
qr.save("qr_basic.png")
```

**2. URL QR with validation**
```python
url = input("Enter URL to make QR: ")
if url.startswith("http://") or url.startswith("https://"):
    qrcode.make(url).save("qr_url.png")
    print("QR code is ready")
else:
    print("INVALID")
```

**3. Customised QR code**
```python
qr = qrcode.QRCode(
    version=1,
    error_correction=qrcode.constants.ERROR_CORRECT_H,
    box_size=10,
    border=4,
)
qr.add_data(url)
qr.make()
image = qr.make_image(fill_color="black", back_color="red")
image.save("qr_custom.png")
```

**4. UPI QR with amount**
```python
upi_url = f"upi://pay?pa={upi_id}&pn={name}&am={amount}"
qrcode.make(upi_url).save("qr_upi.png")
```

## Sample Output

| URL QR | Custom Colour QR | UPI QR |
|:------:|:----------------:|:------:|
| ![URL QR](qr_url.png) | ![Custom QR](qr_custom.png) | ![UPI QR](qr_upi.png) |

## What I Learned

- Taking user input and validating it
- Using external Python libraries with `pip`
- Working with images using Pillow
- Building a UPI payment link and turning it into a QR code
- Handling errors (for example, a wrong class name in the library)

## Future Improvements

- Add a simple GUI using Tkinter
- Read text back from a QR image
- Add a logo in the centre of the QR code

## Author

**Arpit Mishra**
MCA, Invertis University, Bareilly

[GitHub](https://github.com/Arpit8755)
