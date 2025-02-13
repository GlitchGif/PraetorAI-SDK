# PraetorAI - OpenAI Integration for Solana Blockchain

PraetorAI is an OpenAI Python SDK, designed to seamlessly integrate OpenAI's powerful models with Solana blockchain applications. This library enables on-chain AI-powered decision-making, data processing, and smart contract interactions using OpenAI models.

## Features
💡 Solana-Smart Contract AI – Use OpenAI models within Solana smart contracts for automated decision-making.
🚀 Optimized for Web3 – Interact with on-chain data and off-chain AI services efficiently.
🔄 Hybrid Compute – Combine blockchain transparency with AI-driven insights.
🔑 Secure API Key Handling – Uses Solana wallets & program-based authentication.
⚡ Fast Asynchronous API Calls – Powered by httpx, with async support.

## Installation
```sh
pip install praetorai
```

## Usage
### Basic AI Call from Solana
```python
import os
from praetorai import OpenAI
from solana.rpc.api import Client

# Initialize OpenAI client
client = OpenAI(api_key=os.getenv("OPENAI_API_KEY"))

# Initialize Solana client
solana_client = Client("https://api.mainnet-beta.solana.com")

# Fetch on-chain data
account_info = solana_client.get_account_info("SomeSolanaAddress")

# Generate AI insights based on blockchain data
chat_completion = client.chat.completions.create(
    messages=[
        {
            "role": "user",
            "content": f"Analyze this Solana account: {account_info}",
        }
    ],
    model="gpt-4o",
)

print(chat_completion.choices[0].message.content)
```

## AI-Powered Solana Smart Contracts
You can use OpenAI models within Solana smart contracts (via off-chain calls) to process data, generate insights, and automate interactions.

### Example: AI-Based NFT Metadata Generator
```python
metadata_prompt = "Generate a unique description for a Solana NFT with a cyberpunk theme."

response = client.chat.completions.create(
    model="gpt-4o",
    messages=[{"role": "user", "content": metadata_prompt}],
)

nft_metadata = response.choices[0].message.content
print(nft_metadata)
```

## Advanced Features
### Streaming AI Responses
Real-time AI processing for high-speed applications.
```python
stream = client.chat.completions.create(
    messages=[{"role": "user", "content": "Summarize this Solana transaction"}],
    model="gpt-4o",
    stream=True,
)

for chunk in stream:
    print(chunk.choices[0].delta.content or "", end="")
```

## Interacting with Smart Contracts
Use OpenAI’s models to interpret smart contract logs and transaction data:
```python
solana_tx_data = solana_client.get_transaction("SomeTransactionSignature")
ai_analysis = client.chat.completions.create(
    model="gpt-4o",
    messages=[{"role": "user", "content": f"Explain this Solana transaction: {solana_tx_data}"}],
)

print(ai_analysis.choices[0].message.content)
```

## Async Usage
PraetorAI supports async processing for faster AI queries.
```python
import asyncio
from praetorai import AsyncOpenAI

client = AsyncOpenAI()

async def main():
    chat_completion = await client.chat.completions.create(
        messages=[{"role": "user", "content": "Summarize the latest Solana transactions"}],
        model="gpt-4o",
    )
    print(chat_completion.choices[0].message.content)

asyncio.run(main())
```

## Roadmap
✅ OpenAI-Solana integration for AI-enhanced smart contracts
✅ AI-powered NFT metadata generation
✅ Transaction & blockchain data analysis via GPT models
🚀 Coming Soon: AI-powered on-chain oracles & autonomous trading bots

## Contributing
See CONTRIBUTING.md for how to contribute to the project.

