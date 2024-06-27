# Cappuccino - Jabona's Back-End Payment System

Welcome to the Cappuccino payment system, a back-end service for handling payments within the Jabaona housing renting platform.

## Table of Contents
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Endpoints](#endpoints)
- [Testing](#testing)
- [Contributing](#contributing)
- [License](#license)

## Features
- User-friendly payment API
- Integration with multiple payment gateways (Melat, Asan-Pardakht)
- Secure transaction handling
- Support for booking confirmations and receipts
- Error handling and logging

## Requirements
- Go 1.16 or later
- Access to Melat and Asan-Pardakht developer accounts and API keys

## Installation
1. **Clone the Repository:**
   ```sh
   git clone https://github.com/jabaona/cappuccino.git
   cd cappuccino
   ```

2. **Install Dependencies:**
   ```sh
   go mod tidy
   ```

## Configuration
1. **Environment Variables:**
   Create a `.env` file in the root directory and add the following configurations:
   ```sh
   PORT=8080
   Melat_API_KEY=your_Melat_api_key
   AP_CLIENT_ID=your_AP_client_id
   AP_SECRET=your_AP_secret
   ```

2. **Configuration File:**
   Alternatively, you can use a `config.yaml` file for configurations:
   ```yaml
   server:
     port: 8080
   stripe:
     apiKey: your_Melat_api_key
   paypal:
     clientId: your_AP_client_id
     secret: your_AP_secret
   ```

## Usage
1. **Run the Server:**
   ```sh
   go run main.go
   ```

2. **Build the Project:**
   ```sh
   go build -o cappuccino
   ./cappuccino
   ```

## Endpoints
### Payment
- **POST /api/payment/create**
  - Description: Create a new payment.
  - Request Body:
    ```json
    {
      "amount": 1000,
      "currency": "toman",
      "paymentMethod": "melat",
      "bookingId": "booking_123"
    }
    ```
  - Response:
    ```json
    {
      "status": "success",
      "paymentId": "payment_123",
      "message": "Payment created successfully."
    }
    ```

### Booking Confirmation
- **POST /api/payment/confirm**
  - Description: Confirm a booking after successful payment.
  - Request Body:
    ```json
    {
      "paymentId": "payment_123",
      "bookingId": "booking_123"
    }
    ```
  - Response:
    ```json
    {
      "status": "success",
      "message": "Booking confirmed."
    }
    ```

## Testing
1. **Run Unit Tests:**
   ```sh
   go test ./...
   ```

2. **Run Integration Tests:**
   Ensure that the payment gateways are set up correctly before running integration tests.
   ```sh
   go test -tags=integration ./...
   ```

## Contributing
We welcome contributions to improve Cappuccino. Please follow these steps:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes.
4. Commit your changes (`git commit -m 'Add some feature'`).
5. Push to the branch (`git push origin feature-branch`).
6. Open a pull request.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

---

**Maintainer:** [Raein](https://github.com/raeinsoltani)
