
# GR_44

personal-data-vault/
├── .env
├── README.md
├── package.json
├── package-lock.json

├── client/
│   ├── public/
│   │   ├── index.html
│   │   └── manifest.json
│   ├── src/
│   │   ├── assets/
│   │   │   ├── logo.png
│   │   │   └── background.svg
│   │   ├── components/
│   │   │   ├── Navbar.jsx
│   │   │   ├── Sidebar.jsx
│   │   │   ├── ProfileCard.jsx
│   │   │   └── FileUpload.jsx
│   │   ├── pages/
│   │   │   ├── LoginPage.jsx
│   │   │   ├── RegisterPage.jsx
│   │   │   ├── Dashboard.jsx
│   │   │   ├── Vault.jsx
│   │   │   └── Settings.jsx
│   │   ├── services/
│   │   │   ├── api.js
│   │   │   ├── blockchain.js
│   │   │   ├── ipfsService.js
│   │   │   └── auth.js
│   │   ├── utils/
│   │   │   ├── encryption.js
│   │   │   ├── constants.js
│   │   │   └── validators.js
│   │   ├── App.js
│   │   ├── index.js
│   │   └── config.js
│   ├── tailwind.config.js
│   ├── postcss.config.js
│   ├── package.json
│   └── vite.config.js

├── mobile/
│   ├── lib/
│   │   ├── screens/
│   │   │   ├── login.dart
│   │   │   ├── register.dart
│   │   │   ├── dashboard.dart
│   │   │   └── vault.dart
│   │   ├── services/
│   │   │   ├── api_service.dart
│   │   │   ├── blockchain_service.dart
│   │   │   └── ipfs_service.dart
│   │   ├── widgets/
│   │   │   ├── input_field.dart
│   │   │   ├── button.dart
│   │   │   └── file_tile.dart
│   │   └── main.dart
│   ├── assets/
│   │   └── app_icon.png
│   └── pubspec.yaml

├── backend/
│   ├── controllers/
│   │   ├── authController.js
│   │   ├── fileController.js
│   │   └── accessController.js
│   ├── routes/
│   │   ├── authRoutes.js
│   │   ├── fileRoutes.js
│   │   └── accessRoutes.js
│   ├── services/
│   │   ├── ipfsService.js
│   │   ├── blockchainService.js
│   │   ├── zkpService.js
│   │   └── encryptionService.js
│   ├── middlewares/
│   │   ├── authMiddleware.js
│   │   └── errorHandler.js
│   ├── models/
│   │   ├── User.js
│   │   ├── File.js
│   │   └── AccessLog.js
│   ├── config/
│   │   ├── db.js
│   │   └── config.js
│   ├── app.js
│   ├── package.json
│   └── .env

├── contracts/
│   ├── IdentityManager.sol
│   ├── AccessControl.sol
│   ├── zkVerifier.sol
│   ├── build/
│   ├── migrations/
│   │   └── 1_deploy_contracts.js
│   ├── truffle-config.js
│   └── package.json

├── encryption/
│   ├── aes_encrypt.py
│   ├── ecc_keygen.py
│   ├── zkp_proof_generator.py
│   ├── requirements.txt
│   └── utils/
│       └── hash_utils.py

├── scripts/
│   ├── upload_to_ipfs.js
│   ├── grant_access.js
│   ├── generate_did.js
│   └── reset_demo_data.js