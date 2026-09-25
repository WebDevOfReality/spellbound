# 06: Hardware targets

| Target | Role | Notes |
|---|---|---|
| **School Chromebook / low-end laptop** | **Primary user target** | Browser only, weak CPU, 720p webcam. This is the bar that iteration 4 must pass. |
| **Phone (Android/iOS browser)** | User target | Selfie camera, the same data condition as FSboard and PopSign |
| **MSI Stealth 16 (`w3b-weavr`)** | Dev + training box | RTX 4070 Laptop 8 GB, Core Ultra 9 185H, 64 GB RAM. Trains the small models fast, and runs Ollama for the local coach LLM. |
| **heim** (home k3s server) | Optional hosting | Could host the static web app at `spellbound.heim` for family testing on the tailnet. It isn't needed, because the app is static. |

**Principle:** all inference that sees the camera runs **in the user's browser**. The servers host
static files and nothing else. So cost stays near zero and kids' video never leaves the device.
