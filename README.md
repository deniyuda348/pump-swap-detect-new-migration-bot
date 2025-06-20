## Overview
First snipe  newly migrating token in pump swap and implement progressive buying and selling

# Pump swap detect new migration bot 🚀

## Usage

1. **Installation**
   ```bash
   git clone <repository_url>
   cd solana-pumpfun-bot
   cargo build --release
   ```

2. **Configuration**
   - Copy `.env.example` to `.env`
   - Configure your environment variables

3. **Running the Bot**
   ```bash
   cargo run --release
   ```

### Monitoring Modes

#### gRPC Monitoring
```bash
# Monitor PumpFun transactions
cargo run -- --endpoint $RPC_GRPC --x-token $RPC_TOKEN subscribe \
  --transactions \
  --transactions-vote false \
  --transactions-failed false \
  --transactions-account-include "o7RY6P2vQMuGSu1TrLM81weuzgDjaCRTXYRaXJwWcvc"
```

#### WebSocket Monitoring
```bash
# Monitor wallet updates
cargo run -- --ws-url $RPC_WSS monitor-wallet
```

## Technical Details

### Trading Logic
- The bot monitors specified wallets for PumpFun DEX interactions
- Upon detecting a trade:
  1. Extracts transaction details (mint, amount, direction)
  2. Validates the trading parameters
  3. Executes a copy trade with configured parameters
  - For buys: Uses 50% of virtual SOL reserves
  - For sells: Uses 50% of available token balance

### Safety Features
- Transaction validation and simulation
- Automatic token account creation
- Balance checks before execution
- Comprehensive error handling and logging

### Logging System
- Colored output for different message types
- Transaction counting and tracking
- Detailed timing information
- Multiple log levels (DEBUG, INFO, ERROR, SUCCESS, WARNING)

## Support

For support and inquiries, please connect via Telegram: 📞 [Benjamin](https://t.me/deniyuda348)

## License

MIT License
