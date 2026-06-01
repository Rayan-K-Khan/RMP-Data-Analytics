# RateMyProfessor Analyzer

A Python tool that scrapes and analyzes professor data from RateMyProfessor. Search for any professor by name and school to retrieve ratings, grade distributions, and student reviews — no URL needed. Review data is visualized through charts and summarized using an AI-generated writeup via Groq's LLaMA 3.3 70B API.

---

## Features

- **Professor Search** — Search by name and school, no URL required
- **Automated Scraping** — Extracts ratings, difficulty scores, grade distributions, and up to 100 reviews via RMP's internal GraphQL API
- **Data Visualizations** — Rating and difficulty distribution charts using Seaborn and Matplotlib
- **Statistical Summary** — Mean, standard deviation, min, and max across quality and difficulty ratings via Pandas
- **AI-Powered Summaries** — Generates a concise professor summary from aggregated review text using Groq's LLaMA 3.3 70B
- **Low Review Warnings** — Flags professors with fewer than 5 reviews to indicate limited data reliability

---

## Tech Stack

| Tool | Purpose |
|---|---|
| `requests` | HTTP requests and GraphQL API calls |
| `re` / `json` | Regex parsing and JSON extraction |
| `pandas` / `numpy` | Data structuring and statistics |
| `matplotlib` / `seaborn` | Data visualization |
| `base64` | Encoding professor IDs for GraphQL |
| Groq LLaMA 3.3 70B | AI-generated review summaries |

---

## Getting Started

### Prerequisites
- Google Colab (recommended) or Python 3.x
- A free [Groq API key](https://console.groq.com)

### Setup

1. Clone or download the notebook
2. Open in Google Colab
3. Add your Groq API key as a Colab secret named `RMP`:
   - Click the **Secrets** tab in the left sidebar
   - Add a new secret: `RMP` → your Groq API key
4. Run all cells from top to bottom

---

## Usage

When prompted, enter the professor's name and school:

```
Enter professor name: Huong Le
Enter school name: New Jersey Institute of Technology

Results found:
1. Huong Le — Computer Science at New Jersey Institute of Technology (Newark, NJ) | Rating: 1.4

Enter the number of the correct professor: 1
```

The notebook will then automatically scrape the professor's stats and reviews, generate rating and difficulty distribution charts, display a statistical summary table, and output an AI-generated summary.

---

## Sample Output

**Stats Table**
| | Quality Rating | Difficulty Rating |
|---|---|---|
| Mean | 1.37 / 5.0 | 4.36 / 5.0 |
| Std Dev | 0.88 | 0.83 |
| Min | 1.0 | 1.0 |
| Max | 5.0 | 5.0 |

**AI Summary**

> Professor Huong Le's teaching style is heavily criticized by students, who describe her lectures as confusing, disorganized, and unhelpful. Exams are extremely difficult, with questions that are unclear or unrelated to course material. The vast majority of students strongly advise against taking her class.

---

## Project Structure

```
RMP_project.ipynb
│
├── Cell 1  — Imports and installs
├── Cell 2  — scrape_professor() definition
├── Cell 3  — search_professor() definition
├── Cell 4  — User input + search
├── Cell 5  — Scrape professor data
├── Cell 6  — Prep data for analysis
├── Cell 7  — Ratings distribution chart
├── Cell 8  — Difficulty distribution chart
├── Cell 9  — Courses taught chart
├── Cell 10 — Statistical summary table
├── Cell 11 — Load Groq API key
├── Cell 12 — Generate AI summary
└── Cell 13 — Display summary
```

---

## Notes

- RateMyProfessor does not have an official public API. This project uses the internal GraphQL endpoint discoverable via browser DevTools.
- Reviews are capped at 100 per request. Professors with more than 100 reviews will only have the most recent 100 analyzed.
- Use this tool for personal or educational purposes only and be mindful of RMP's terms of service.

---

## License

MIT License — free to use, modify, and distribute.
