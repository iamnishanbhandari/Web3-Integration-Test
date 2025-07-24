## 🕒 1-Hour Coding Test Documentation
This documentation covers the implementation of Web3 functionality using Next.js/React and Node.js backend, focusing on functionality over UI design.

## 🛠 Tech Stack
- Frontend: Next.js/React 
- Backend: Node.js 18+
- Web3: ethers.js
- Authentication: NextAuth.js/React
- API: REST + WebSocket

## 🎯 Test Requirements & Completion Status

> **Important**: After completion, create a new branch with your name and push the code:
```bash
# Create and switch to your branch
git checkout -b firstname_lastname

# Add and commit your changes
git add .
git commit -m "Complete Web3 integration test"

# Push to your branch
git push origin firstname_lastname
```

### 1. Wallet Connectivity (5-10 mins) ✅
- [x] Implemented Web3 wallet connection using ethers.js
- [x] Added read functions for balance and status checks
- [x] Implemented proper error handling for connection failures
- [x] Added connection status indicators

### 2. Signature Verification (10 mins) ✅
- [x] Implemented EIP-191 message signing
- [x] Added EIP-712 typed data signing support
- [x] Added signature verification endpoints
- [x] Included error handling for invalid signatures

### 3. WebSocket Integration (10 mins) ✅
- [x] Set up WebSocket connection for real-time updates
- [x] Implemented event listeners for wallet events
- [x] Added reconnection logic
- [x] Included connection status monitoring

### 4. Security & Environment Setup (15 mins) ✅
- [x] Configured environment variables
- [x] Implemented security measures for dos/ddos attacks
- [x] Added authentication for Web3 endpoints
- [x] Secured sensitive data handling

### 5. Documentation & Testing (15 mins) ✅
- [x] Added API documentation
- [x] Included setup instructions
- [x] Created testing guidelines
- [x] Added security considerations

## 📋 Minimum Required Components

### Frontend Components
```typescript
// components/WalletConnect.tsx
/**
 * WalletConnect Component
 * Handles wallet connection and displays wallet status
 * 
 * @component
 * @example
 * return (
 *   <WalletConnect onConnect={handleConnect} />
 * )
 */
const WalletConnect: React.FC = () => {
  // State for wallet connection
  const [isConnected, setIsConnected] = useState(false);
  const [address, setAddress] = useState('');
  const [balance, setBalance] = useState('0');

  // ... implementation
};

// components/SignMessage.tsx
/**
 * SignMessage Component
 * Handles message signing and verification
 * 
 * @component
 * @param {string} message - Message to be signed
 */
const SignMessage: React.FC<{ message: string }> = ({ message }) => {
  // ... implementation
};

// components/WebSocketListener.tsx
/**
 * WebSocketListener Component
 * Manages WebSocket connection and real-time updates
 * 
 * @component
 * @param {string} url - WebSocket endpoint URL
 */
const WebSocketListener: React.FC<{ url: string }> = ({ url }) => {
  // ... implementation
};
```

### Backend Endpoints
```typescript
// pages/api/auth/[...nextauth].ts
/**
 * NextAuth Configuration
 * Handles authentication and session management
 */
export default NextAuth({
  // ... configuration
});

// pages/api/verify-signature.ts
/**
 * Signature Verification Endpoint
 * Verifies EIP-191 and EIP-712 signatures
 * 
 * @param {Request} req - HTTP request object
 * @param {Response} res - HTTP response object
 */
export default async function handler(req: NextApiRequest, res: NextApiResponse) {
  // ... implementation
}
```

### Required Fields
```typescript
// types/index.ts
interface WalletState {
  address: string;
  balance: string;
  network: string;
  isConnected: boolean;
}

interface SignatureRequest {
  message: string;
  address: string;
  signatureType: 'EIP191' | 'EIP712';
}

interface WebSocketMessage {
  type: 'WALLET_UPDATE' | 'TRANSACTION' | 'ERROR';
  payload: any;
}
```

## 🚀 Quick Start

### Prerequisites
```bash
Node.js >= 18.0
npm >= 6.14.0
```

### Project Setup
Choose either Next.js or Create React App:

#### Option 1: Next.js Setup
```bash
# Create Next.js app
npx create-next-app@latest your-project-name --typescript

# Navigate to project
cd your-project-name
```

#### Option 2: React Setup
```bash
# Create React app
npx create-react-app your-project-name --template typescript

# Navigate to project
cd your-project-name
```

### Environment Setup
```bash
# Create environment file
cp .env.example .env.local   # For Next.js
# OR
cp .env.example .env         # For React
```

### Environment Variables
```env
# Required environment variables
NEXT_PUBLIC_RPC_URL=your_rpc_url
NEXT_PUBLIC_CHAIN_ID=1
NEXTAUTH_SECRET=your_secret
NEXTAUTH_URL=http://localhost:3000

# Web3 Configuration
NEXT_PUBLIC_WEBSOCKET_URL=your_websocket_url
NEXT_PUBLIC_RATE_LIMIT=100

# Backend Configuration
DATABASE_URL=your_database_url
```

## 💻 Code Structure & Comments

### Required Code Comments
All code must include:
1. Function documentation
2. Parameter descriptions
3. Return value documentation
4. Usage examples
5. Error handling explanations

Example:
```typescript
/**
 * Connects to Web3 wallet and returns signer
 * 
 * @async
 * @function connectWallet
 * @param {boolean} [silentMode=false] - Whether to show user prompts
 * @returns {Promise<ethers.Signer>} Authenticated signer object
 * @throws {Error} When wallet connection fails
 * 
 * @example
 * try {
 *   const signer = await connectWallet();
 *   const address = await signer.getAddress();
 * } catch (error) {
 *   console.error('Wallet connection failed:', error);
 * }
 */
const connectWallet = async (silentMode = false): Promise<ethers.Signer> => {
  // Implementation...
};
```

## 🔒 Security Implementation

### DDoS Protection
```typescript
// middleware.ts
import { rateLimit } from 'express-rate-limit';
import { applyRateLimit } from './utils/rateLimiter';

export const config = {
  matcher: '/api/:path*',
};

export default function middleware(req: NextRequest) {
  // Apply rate limiting
  return applyRateLimit(req);
}
```

## ✅ Testing Requirements

### Unit Tests (Jest + React Testing Library)
```typescript
// __tests__/WalletConnect.test.tsx
describe('WalletConnect Component', () => {
  it('should connect to wallet', async () => {
    // Test implementation
  });
});
```

## 📝 Notes

- Focus on functionality over UI design
- Must include comprehensive code comments
- Implement proper error handling
- Follow js/ts best practises
- Security measures are implemented but should be reviewed for production use
- Additional features can be added based on requirements 

## 📝 Final Submission

1. **Code Organization**:
   - Maintain clear folder structure
   - Follow component-based architecture
   - Include comprehensive comments

2. **Documentation**:
   - Update README with setup instructions
   - Document any additional features
   - Include testing procedures

3. **Branch Creation and Submission**:
   ```bash
   # Create your branch
   git checkout -b firstname_lastname

   # Stage changes
   git add .

   # Commit with meaningful message
   git commit -m "Complete Web3 integration test with:
   - Wallet connectivity
   - Signature verification
   - WebSocket integration
   - Security measures
   - Documentation"

   # Push to your branch
   git push origin firstname_lastname
   ```

4. **Final Checklist**:
   - [ ] All requirements implemented
   - [ ] Code properly commented
   - [ ] Tests written and passing
   - [ ] Security measures in place
   - [ ] Branch created and pushed
   - [ ] Documentation complete 
