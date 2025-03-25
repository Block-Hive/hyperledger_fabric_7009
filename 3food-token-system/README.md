# Food Token System using Hyperledger Fabric

This repository contains the **Food Token System** built using **Hyperledger Fabric**, allowing customers to redeem food tokens via QR codes.

## 📂 Download Project Folder

The project is too large for GitHub, so you can download it from the following cloud storage link:

🔗 **[Download Food Token System](YOUR_CLOUD_LINK_HERE)**

## 🚀 Getting Started

### 1️⃣ Prerequisites
Ensure you have the following installed:
- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Go](https://golang.org/dl/)
- [Node.js](https://nodejs.org/)
- [Hyperledger Fabric Binaries](https://hyperledger-fabric.readthedocs.io/en/latest/install.html)

### 2️⃣ Clone the Repository
```sh
git clone https://github.com/YOUR_GITHUB_USERNAME/food-token-system.git
cd food-token-system
```

### 3️⃣ Start the Hyperledger Fabric Network
```sh
cd blockchain
./startFabric.sh
```

### 4️⃣ Install Dependencies
```sh
cd webapp
pip install -r requirements.txt
```

### 5️⃣ Run the Web App
```sh
streamlit run app.py
```

## 🔑 Login Credentials

| User Type | Username | Password |
|-----------|----------|----------|
| **Vendor** | `admin` | `admin` |
| **Customer** | `Unique ID` | `Generated During Registration` |

## 📸 QR Code Scanning
- Customers generate QR codes during registration.
- Vendors scan QR codes using the WebRTC-based scanner.
- Token balance updates automatically.

## 🛠 Troubleshooting
**If the camera doesn't work:**
1. Allow browser permissions for the camera.
2. Run `pip install opencv-python-headless streamlit-webrtc av`.
3. Restart the Streamlit app.

## 📜 License
This project is licensed under the **MIT License**.

## 🤝 Contributing
Feel free to fork and submit pull requests!

---
**Made with ❤️ for secure food token transactions using blockchain!**
