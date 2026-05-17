🧠 Agentic AI Product Intelligence System (Multi-Agent CrewAI Pipeline)

A production-style Agentic AI system designed and implemented as an AI/ML Engineer project to automate e-commerce product data extraction, structuring, and validation using a multi-agent architecture.

This system leverages CrewAI, LLMs, and Pydantic validation to transform unstructured HTML from e-commerce websites into clean, structured, and analytics-ready datasets.

🚀 Project Overview

This project implements a two-agent autonomous pipeline that performs end-to-end product intelligence extraction from raw web pages.

Instead of traditional scraping approaches relying on brittle CSS selectors, this system uses LLM-driven reasoning with strict schema validation to ensure structured and reliable outputs.

🏗️ Multi-Agent Architecture

The system consists of two specialized AI agents:

🤖 1. HTML Fetcher Agent

Responsibility:

Executes a deterministic scraping tool (html_scraper)
Fetches raw HTML content from product listing pages
Ensures no URL manipulation or hallucination

Key Characteristics:

Tool-driven execution only
No reasoning or transformation
Strict input enforcement
🧠 2. HTML Analyzer Agent

Responsibility:

Parses raw HTML content
Extracts structured product information
Converts unstructured DOM into normalized JSON

Extracted Fields:

Company / Brand
Product category
Model
Color
Price
Rating
Platform
Product URL

Key Characteristics:

LLM-based structured extraction
No hallucination policy
Strict JSON output enforcement
🔁 System Workflow
User Input (Product Queries)
        ↓
HTML Fetcher Agent (Tool Execution)
        ↓
Raw HTML Response
        ↓
HTML Analyzer Agent (LLM Parsing)
        ↓
Structured JSON Output
        ↓
Pydantic Validation Layer
        ↓
Data Flattening (Tabular Transformation)
        ↓
CSV Export / Analytics Layer
🧾 Data Schema (Pydantic Model)

All outputs are validated using strict Pydantic schemas to ensure consistency and reliability.

class Product(BaseModel):
    company: Optional[str]
    product: Optional[str]
    model: Optional[str]
    color: Optional[str]
    price: Optional[float]
    location: Optional[str]
    platform: Optional[str]
    title: Optional[str]
    rating: Optional[str]
    product_url: Optional[str]


class ProductList(BaseModel):
    products: List[Product]
⚙️ Core Pipeline Design
1. HTML Retrieval Layer
Controlled scraping via CrewAI tool
No LLM intervention
Deterministic execution
2. AI Extraction Layer
LLM-based structured parsing
Converts HTML → JSON objects
Handles multi-product pages
3. Validation Layer
Pydantic schema enforcement
Eliminates malformed outputs
Ensures data consistency
4. Transformation Layer
Nested JSON → tabular dataset
Pandas DataFrame conversion
CSV export for downstream use
📊 Output Format

Final structured dataset:

search_product	site	company	model	price	rating	title	product_url
mobile	amazon	Apple	iPhone 15 Pro	999	4.6	...	...
🧠 Engineering Highlights
🔹 Multi-Agent AI architecture (CrewAI)
🔹 Strict tool-based execution (no hallucinated URLs)
🔹 Schema-driven validation (Pydantic)
🔹 Cross-platform HTML compatibility
🔹 Robust JSON structuring from unstructured DOM
🔹 Production-ready data pipeline design
⚠️ Key Challenges Solved
1. HTML Noise Handling

Raw e-commerce HTML is highly unstructured and noisy. The system filters and structures content for LLM consumption.

2. LLM Hallucination Control

Strict prompting + schema validation prevents fabricated product data.

3. Cross-Site Variability

System is designed to work across different e-commerce platforms without hardcoded selectors.

4. Data Consistency

Pydantic ensures all outputs follow a consistent schema before storage.

📦 Tech Stack
Python 🐍
CrewAI 🤖 (Multi-Agent Framework)
Large Language Models (LLMs)
Pydantic (Schema Validation)
BeautifulSoup (HTML Processing)
Pandas (Data Transformation)
Requests (Web Fetching)
📁 Use Cases
E-commerce price intelligence
Product comparison engines
Market research automation
Competitive pricing analysis
Deal tracking systems
Structured product data pipelines
🚀 Future Improvements
Playwright-based dynamic rendering (anti-bot support)
Real-time product monitoring system
Multi-site normalization engine
Vector-based product deduplication
API deployment using FastAPI
Distributed scraping architecture
👨‍💻 Author

Designed and implemented as an AI Engineer project focused on Agentic AI systems, demonstrating practical application of multi-agent orchestration, structured extraction pipelines, and LLM-based automation for real-world e-commerce intelligence systems.
