```http
# Connect Wallet
POST /api/wallet/connect
Body:
{
  "walletAddress": "0xYourWalletAddress",
  "signature": "signedMessage"
}
Response:
{
  "status": "success",
  "message": "Wallet connected",
  "wallet": "0xYourWalletAddress"
}

# Query Active Events
GET /api/events/active
Response:
{
  "events": [
    {
      "eventId": "evt123",
      "title": "Team A vs Team B",
      "startTime": "2025-11-01T12:00:00Z",
      "endTime": "2025-11-01T15:00:00Z",
      "options": ["Team A", "Team B", "Draw"]
    },
    {
      "eventId": "evt124",
      "title": "Election Prediction",
      "startTime": "2025-11-05T00:00:00Z",
      "endTime": "2025-11-07T23:59:59Z",
      "options": ["Candidate X", "Candidate Y"]
    }
  ]
}

# Query User Bets
GET /api/bets/user?walletAddress=0xYourWalletAddress
Response:
{
  "bets": [
    {
      "betId": "bet987",
      "eventId": "evt123",
      "option": "Team A",
      "amount": 50,
      "status": "pending"
    }
  ]
}

# Place Bet
POST /api/bets/place
Body:
{
  "walletAddress": "0xYourWalletAddress",
  "eventId": "evt123",
  "option": "Team A",
  "amount": 50
}
Response:
{
  "status": "success",
  "betId": "bet987",
  "message": "Bet placed successfully"
}

# Claim Rewards
POST /api/rewards/claim
Body:
{
  "walletAddress": "0xYourWalletAddress",
  "betId": "bet987"
}
Response:
{
  "status": "success",
  "rewards": 75,
  "token": "FluidX402",
  "message": "Rewards claimed successfully"
}

# Query Event Results
GET /api/events/results?eventId=evt123
Response:
{
  "eventId": "evt123",
  "winningOption": "Team A",
  "totalBets": 150,
  "totalRewardsDistributed": 200
}
