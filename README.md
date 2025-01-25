# QR code decorated alredy

Generate Barcode & QR code from text feild on UI.

Type of QR code: Dynamic QR 
Languge: Python, HTML

This is a part of my thesis project. First time using flask that is framework of python

### QR Code Design Specification for the Project  

Here's the English translation of the QR Code Specification:

**QR Code Specification**

**1. Purpose**

Use QR Codes to record and track data within the organic milk product supply chain, reducing reliance on databases and server data retrieval.

**2. Embedded Data**

*   **Farmer QR Code**

    *   Tank ID: Raw milk tank ID (string)
    *   Production Date: Production date (ISO 8601 format, e.g., 2025-01-20)
    *   Farmer ID: Farmer ID (string)
    *   Destination Factory: Destination factory ID (string)
    *   Digital Signature: Digital signature to verify data authenticity (string)
*   **Factory QR Code**

    *   Lot ID: Product lot ID (string)
    *   Production Date: Production date (ISO 8601 format)
    *   Expiration Date: Expiration date (ISO 8601 format)
    *   Factory ID: Factory ID (string)
    *   Ingredients: Ingredient information (optional, list of strings)
    *   Digital Signature: Digital signature to verify data authenticity (string)
*   **Customer QR Code**

    *   Lot ID: Product lot ID (string)
    *   Product Name: Product name (string)
    *   URL: Link for more information (string, e.g., [https://example.com/product/LOT12345](https://example.com/product/LOT12345))

**3. QR Code Format**

*   Standard: QR Code (ISO/IEC 18004:2015)
*   Version:
    *   Farmer QR Code: Version 3-5 (26x26 to 37x37 cells)
    *   Factory QR Code: Version 5-10 (37x37 to 57x57 cells)
    *   Customer QR Code: Version 4-6 (33x33 to 41x41 cells)
*   Error Correction Level: Level H (High), supports logo insertion and protects against data corruption.
*   Encoding: UTF-8

**4. Example JSON Data Embedded in QR Code**

*   **Farmer QR Code**

    ```json
    {
      "tank_id": "TANK12345",
      "production_date": "2025-01-20",
      "farmer_id": "FARM67890",
      "destination_factory": "FACTORY123",
      "signature": "a1b2c3d4e5f6"
    }
    ```

*   **Factory QR Code**

    ```json
    {
      "lot_id": "LOT98765",
      "production_date": "2025-01-20",
      "expiration_date": "2025-06-20",
      "factory_id": "FACTORY123",
      "ingredients": ["raw_milk"],
      "signature": "z9y8x7w6v5u4"
    }
    ```

*   **Customer QR Code**

    ```json
    {
      "lot_id": "LOT98765",
      "product_name": "Organic Milk",
      "url": "https://example.com/product/LOT12345"
    }
    ```

**5. Front-End Requirements**

*   **QR Code Display:**
    *   Use Base64 encoded images (sent from the Back-End).
    *   Minimum display size: 200x200 pixels.
*   **Data Entry Forms:**
    *   Design forms to support fields according to each actor's data.
    *   Perform client-side validation before submitting data.

**6. Back-End Requirements**

*   **QR Code Generation:**
    *   Use libraries such as `qrcode` in Python.
    *   Support converting JSON to QR Code and returning it as Base64.
*   **Security:**
    *   Use digital signatures or encryption to prevent data forgery.
    *   Validate received data before processing.

**7. QR Code Testing**

Test scanning with various devices such as mobile phones and QR Code readers. Test under different lighting conditions and distances.

**8. Deployment**

Use in conjunction with a Blockchain system to store frequently changing data (Dynamic Data). Use an API server to provide QR Code creation and verification services.

**9. Information Displayed Upon User Scanning QR Code**

*   **Farmer:**
    *   Factory Name
    *   Address
    *   Production Date
    *   Certification File
*   **Factory:**
    *   Factory Name
    *   Address
    *   Pick up date
    *   Product Lot
    *   Certification
    *   Shipping Date
*   **Retailer:**
    *   Company Name
    *   Address
    *   Quality
*   **Logistic (Storage Information):**
    *   Company Name
    *   Sender's Name
    *   Temperature
    *   Quality Check


# Step to install:
Command Promt:
1.cd path folders
2.python -m venv venv หรือ python3 -m venv venv
3.venv\Scripts\activate
4.install: pip install Flask qrcode python-barcode 

Run file:
1.ดู (venv) ข้างหน้า
2.python app.py
3.เปิด http://127.0.0.1:5000/
