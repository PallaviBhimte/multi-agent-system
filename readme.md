# 🔬 ResearchMind - Multi-Agent AI Research System

ResearchMind is a Multi-Agent AI Research System built using LangChain, OpenAI, Tavily Search, BeautifulSoup, and Streamlit.

The system simulates a team of specialized AI agents collaborating together to perform end-to-end research on any topic.

Instead of relying on a single LLM call, the workflow is divided into multiple specialized agents:

1. Search Agent → Finds recent and reliable information from the web.
2. Reader Agent → Scrapes and extracts deeper content from selected sources.
3. Writer Chain → Generates a structured research report.
4. Critic Chain → Reviews and evaluates the report quality.

The final result is a research report along with constructive AI-generated feedback.

---

# 🎥 Demo

[Watch Demo Video](https://drive.google.com/file/d/13isTtgD2P7IzFYV0pMnLivd3tEvIifHY/view?usp=share_link)

---

# 🛠️ Tech Stack

### LLM & Agents

* LangChain
* OpenAI GPT-4o-mini

### Search

* Tavily Search API

### Scraping

* Requests
* BeautifulSoup

### UI

* Streamlit

### Environment Management

* Python Dotenv

### Utilities

* Rich
* Pandas
* Tiktoken


---

# 🚀 Features

* Multi-Agent Architecture
* Tavily Web Search Integration
* Web Scraping using BeautifulSoup
* LangChain Agents
* LCEL Chains
* OpenAI GPT-4o-mini
* Research Report Generation
* AI Critic & Evaluation Agent
* Interactive Streamlit UI
* Download Research Reports

---

# 🏗️ Architecture

```text
User Query
    │
    ▼
Search Agent
(Tavily Search)
    │
    ▼
Reader Agent
(BeautifulSoup Scraper)
    │
    ▼
Writer Chain
(Research Report Generation)
    │
    ▼
Critic Chain
(Report Evaluation)
    │
    ▼
Final Report + Feedback
```

---

# 📂 Project Structure

```text
.
├── agents.py
├── app.py
├── pipeline.py
├── tools.py
├── requirements.txt
└── README.md
```

---

# 📄 File Descriptions

## tools.py

Contains all external tools used by the agents.

### web_search()

Uses Tavily Search API to:

* Search the internet
* Retrieve recent information
* Return titles, URLs, and snippets

### scrape_url()

Uses:

* Requests
* BeautifulSoup

to scrape webpage content and clean unnecessary HTML elements.

---

## agents.py

Contains all AI agents and chains.

### Search Agent

Responsible for finding relevant information using:

```python
web_search()
```

### Reader Agent

Responsible for scraping deeper content using:

```python
scrape_url()
```

### Writer Chain

Uses:

* ChatPromptTemplate
* GPT-4o-mini
* StrOutputParser

to generate a structured research report.

### Critic Chain

Evaluates the generated report and provides:

* Score
* Strengths
* Areas for Improvement
* Verdict

---

## pipeline.py

Main orchestration layer.

Runs the complete research workflow:

```text
Search Agent
    ↓
Reader Agent
    ↓
Writer Chain
    ↓
Critic Chain
```

Maintains pipeline state and passes outputs between agents.

---

## app.py

Streamlit frontend.

Provides:

* User Interface
* Progress Tracking
* Agent Status Display
* Report Rendering
* Critic Feedback
* Report Download Option

---

# ⚙️ Setup Instructions

## 1. Clone Repository

```bash
git clone https://github.com/YOUR_USERNAME/researchmind.git

cd researchmind
```

---

## 2. Install Python

Recommended Version:

```text
Python 3.11+
```

Verify:

```bash
python3.11 --version
```

---

## 3. Create Virtual Environment

```bash
python3.11 -m venv .venv
```

Activate:

### Mac/Linux

```bash
source .venv/bin/activate
```

### Windows

```bash
.venv\Scripts\activate
```

Verify:

```bash
which python
```

Expected:

```text
.../.venv/bin/python
```

---

## 4. Install Dependencies

```bash
pip install -r requirements.txt
```

or

```bash
uv pip install -r requirements.txt
```

---

## 5. Create Environment Variables

Create a file named:

```text
.env
```

Add:

```env
OPENAI_API_KEY=your_openai_api_key
TAVILY_API_KEY=your_tavily_api_key
```

---

# ▶️ Running the Application

## Streamlit UI

```bash
streamlit run app.py
```
---

## Terminal Version

Run the pipeline directly:

```bash
python pipeline.py
```

Example:

```text
Enter a Research Topic:

What is the impact of war on the Stock Market?
```
---

# 📊 Sample Output

## Research Report

```text
 Enter a Research Topic: 
What is the impact of war on the stock market?

 =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  = 
Step 1 - search agent is working...
==================================================

 search result Here are some recent and reliable sources discussing the impact of war on the stock market:

1. **The impact of the Russian-Ukraine war on the stock market**
   - **URL**: [Read more](https://www.tandfonline.com/doi/full/10.1080/00036846.2023.2188168)
   - **Snippet**: This article discusses how the war has led to sanctions on Russia, increasing geopolitical tension and fear in stock markets, and examines the broader implications for global financial stability.

2. **The Impact of War on the Stock Markets—What Investors Need To Know**
   - **URL**: [Read more](https://www.investopedia.com/the-impact-of-war-on-the-stock-markets-what-investors-need-to-know-11918505)
   - **Snippet**: This piece highlights that historical data shows major geopolitical events often do not have a lasting negative impact on U.S. stocks, despite initial volatility. It covers various global conflicts and their effects on market performance.

3. **How Does War Impact Equity Markets?**
   - **URL**: [Read more](https://www.alliancebernstein.com/corporate/en/insights/investment-insights/how-does-war-impact-equity-markets.html)
   - **Snippet**: This article analyzes how geopolitical shocks have historically influenced financial markets, noting that the context of the event (e.g., economic conditions) plays a significant role in market reactions.

4. **Expected impact of war on the stock market**
   - **URL**: [Read more](https://www.researchgate.net/figure/Expected-impact-of-war-on-the-stock-market_tbl1_253064520)
   - **Snippet**: This research discusses how both conflictive and cooperative events can influence the development of equities, providing insights into market behavior during wartime.

5. **What Happens to the Stock Market in Times of War?**
   - **URL**: [Read more](https://blog.commonwealth.com/independent-market-observer/what-happens-to-the-stock-market-in-times-of-war)
   - **Snippet**: This blog post examines the immediate reactions of capital markets to rising tensions, illustrating how fear and uncertainty can lead to sharp declines in stock prices.

These sources provide a comprehensive overview of how wars and geopolitical tensions can affect stock markets, including historical perspectives and current analyses.

 =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  = 
Step 2 - Reader agent is scraping top resources...
==================================================

 scraped content: 
  The article titled **"The Impact of War on the Stock Markets—What Investors Need To Know"** from Investopedia provides a comprehensive overview of how wars affect stock markets. Here are the key points extracted from the content:

### Key Takeaways:
- **Short-term Sell-offs**: Wars often lead to immediate sell-offs in the stock market due to heightened uncertainty and fear among investors.
- **Market Recovery**: Historically, markets tend to recover as situations stabilize, demonstrating resilience in the face of geopolitical crises.
- **Sector Performance**: Defense and energy stocks typically perform well during wartime due to increased demand for military and energy resources.
- **Historical Context**: Major geopolitical events usually do not have a lasting negative impact on U.S. stocks, as evidenced by past market behaviors.
- **Investor Behavior**: During conflicts, investors often shift their portfolios towards safer assets like gold and bonds, reflecting a flight to safety.

### Market Dynamics:
- The article discusses how global conflicts, such as Russia's invasion of Ukraine and the U.S. war in Iran, influence market sentiment and create short-term volatility.
- The concept of the "war puzzle" is introduced, indicating that market reactions can vary based on whether a conflict is anticipated or comes as a surprise.

### Conclusion:
The article emphasizes that while wars can create immediate challenges for investors, the stock market has historically shown a capacity to rebound, highlighting the importance of a long-term investment perspective during periods of geopolitical instability.

For further details, you can read the full article [here](https://www.investopedia.com/the-impact-of-war-on-the-stock-markets-what-investors-need-to-know-11918505).

 =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  = 
Step 3 - Writer is drafting the report...
==================================================

 Final Report: 
 # Research Report: The Impact of War on the Stock Market

## Introduction

The relationship between war and the stock market is a complex and multifaceted issue that has garnered significant attention from investors, economists, and policymakers alike. Wars and geopolitical tensions can create immediate volatility in financial markets, influencing investor behavior and market dynamics. This report aims to explore the impact of war on the stock market, drawing insights from recent research and historical data to provide a comprehensive understanding of this phenomenon.

## Key Findings

### 1. Short-term Volatility and Market Reactions

One of the most immediate effects of war on the stock market is the occurrence of short-term sell-offs. As geopolitical tensions escalate, investors often react with fear and uncertainty, leading to a rapid decline in stock prices. For instance, the onset of the Russian-Ukraine war resulted in significant market fluctuations, as investors grappled with the implications of sanctions and increased geopolitical risk. Historical data indicates that such sell-offs are common during the initial stages of conflict, as seen in various global conflicts, including the Gulf War and the U.S. invasion of Iraq. However, these declines are often temporary, with markets typically rebounding as the situation stabilizes and investors reassess the long-term implications of the conflict.

### 2. Sector Performance and Investment Shifts

Wars tend to create distinct patterns in sector performance within the stock market. Notably, defense and energy sectors often experience increased demand during wartime, leading to a rise in stock prices for companies operating in these industries. For example, defense contractors may see a surge in contracts and revenue as governments ramp up military spending. Conversely, sectors such as travel and tourism may suffer due to heightened uncertainty and reduced consumer confidence. Additionally, during periods of conflict, investors frequently shift their portfolios towards safer assets, such as gold and government bonds, reflecting a flight to safety. This behavior underscores the importance of understanding sector dynamics and investor psychology during wartime.

### 3. Historical Resilience of Markets

Despite the immediate volatility associated with wars, historical evidence suggests that major geopolitical events do not have a lasting negative impact on stock markets, particularly in the United States. Research indicates that, over time, markets tend to recover and even thrive following conflicts. This phenomenon, often referred to as the "war puzzle," highlights the resilience of financial markets in the face of adversity. For instance, after the initial shock of the September 11 attacks, the U.S. stock market rebounded within a relatively short period. This resilience can be attributed to various factors, including economic fundamentals, government interventions, and the inherent adaptability of markets to changing conditions.

## Conclusion

The impact of war on the stock market is characterized by short-term volatility, sector-specific performance shifts, and a historical trend of market resilience. While wars can create immediate challenges for investors, the stock market has demonstrated a capacity to recover over time, emphasizing the importance of a long-term investment perspective. Understanding the dynamics of market reactions during conflicts can help investors navigate the complexities of geopolitical tensions and make informed decisions in uncertain times.

## Sources

1. The impact of the Russian-Ukraine war on the stock market - [Read more](https://www.tandfonline.com/doi/full/10.1080/00036846.2023.2188168)
2. The Impact of War on the Stock Markets—What Investors Need To Know - [Read more](https://www.investopedia.com/the-impact-of-war-on-the-stock-markets-what-investors-need-to-know-11918505)
3. How Does War Impact Equity Markets? - [Read more](https://www.alliancebernstein.com/corporate/en/insights/investment-insights/how-does-war-impact-equity-markets.html)
4. Expected impact of war on the stock market - [Read more](https://www.researchgate.net/figure/Expected-impact-of-war-on-the-stock-market_tbl1_253064520)
5. What Happens to the Stock Market in Times of War? - [Read more](https://blog.commonwealth.com/independent-market-observer/what-happens-to-the-stock-market-in-times-of-war)

 =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  =  = 
Step 4 - Critic is reviewing the report...
==================================================

 Critic Report: 
 Score: 6/10

Strengths:
- The report provides a clear structure, with distinct sections that outline key findings related to the impact of war on the stock market.
- It effectively highlights the short-term volatility and sector-specific performance shifts, which are critical aspects of the relationship between war and market behavior.
- The inclusion of historical examples, such as the Gulf War and the September 11 attacks, adds credibility and context to the analysis.

Areas to Improve:
- The report lacks quantitative data or specific metrics to support the claims made, which would strengthen the arguments and provide a more robust analysis.
- There is insufficient discussion on the long-term implications of war on different markets outside the U.S., limiting the scope of the findings.
- The sources listed are not critically evaluated or integrated into the report, which diminishes the academic rigor and depth of the research.
- The conclusion could benefit from a more nuanced discussion on the potential exceptions to the observed trends, as well as the role of external factors influencing market behavior during conflicts.

One line verdict:
While the report outlines key trends in the impact of war on the stock market, it lacks depth and empirical support, limiting its overall effectiveness.
```
---

# 👩‍💻 Author

- Pallavi Bhimte 
- Data & ML Engineer
- Melbourne, Australia
