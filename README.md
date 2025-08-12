# Data Analyst Agent API

A powerful AI-powered data analysis API that can scrape, analyze, and visualize data from various sources using LLMs.

## 🚀 Live Demo

**API Endpoint**: [Your deployed URL here]

## ✨ Features

- **Multi-modal Data Processing**: Web scraping, PDF parsing, image OCR, audio processing
- **Intelligent Analysis**: Uses Gemini AI for natural language understanding and plan generation
- **Data Visualization**: Generates charts and plots with base64 encoding
- **Flexible Input**: Accepts text files with questions and data sources
- **JSON Responses**: Returns structured data in JSON format
- **Real-time Processing**: Answers within 3 minutes as required

## 🛠️ Technology Stack

- **Backend**: FastAPI (Python)
- **AI/LLM**: Google Gemini AI
- **Data Processing**: Pandas, NumPy, SciPy
- **Web Scraping**: BeautifulSoup4, Requests
- **Visualization**: Matplotlib, Seaborn, Plotly
- **Database**: DuckDB for SQL queries
- **Deployment**: Render/Vercel/Heroku ready

## 📋 API Usage

### Endpoint
```
POST https://your-api-url.com/api/
```

### Request Format
Send a text file with your analysis questions:

```bash
curl -X POST "https://your-api-url.com/api/" \
  -F "file=@question.txt"
```

### Example Question File
```
Scrape the list of highest grossing films from Wikipedia.
It is at the URL: https://en.wikipedia.org/wiki/List_of_highest-grossing_films

Answer the following questions and respond with a JSON array of strings:

1. How many $2 bn movies were released before 2020?
2. Which is the earliest film that grossed over $1.5 bn?
3. What's the correlation between the Rank and Peak?
4. Draw a scatterplot of Rank and Peak along with a dotted red regression line.
   Return as a base-64 encoded data URI.
```

### Response Format
```json
[
  "1",
  "Titanic",
  "0.485782",
  "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAA..."
]
```

## 🏗️ Architecture

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Client        │    │   FastAPI        │    │   Gemini AI     │
│   (Postman/    │───▶│   Application    │───▶│   LLM Engine    │
│   curl)        │    │                  │    │                 │
└─────────────────┘    └──────────────────┘    └─────────────────┘
                              │
                              ▼
                       ┌──────────────────┐
                       │   Data Tools     │
                       │   - Web Scraping │
                       │   - PDF Parsing  │
                       │   - Visualization│
                       │   - Analysis     │
                       └──────────────────┘
```

## 🚀 Quick Start

### Local Development

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/data-analyst-agent.git
cd data-analyst-agent
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

3. **Set environment variables**
```bash
cp env_example.txt .env
# Edit .env and add your GEMINI_API_KEY
```

4. **Run the server**
```bash
python start_server.py
```

5. **Test the API**
```bash
curl -X POST "http://localhost:8000/api/" \
  -F "file=@tests/sample_question.txt"
```

### Deployment

#### Render (Recommended)
1. Connect your GitHub repository to Render
2. Create a new Web Service
3. Set environment variables:
   - `GEMINI_API_KEY`: Your Gemini API key
   - `HOST`: 0.0.0.0
   - `PORT`: 10000
4. Deploy!

#### Vercel
1. Install Vercel CLI
2. Run `vercel --prod`
3. Set environment variables in Vercel dashboard

#### Heroku
1. Create Heroku app
2. Set environment variables
3. Deploy with `git push heroku main`

## 📊 Supported Data Sources

- **Web Scraping**: Wikipedia, news sites, data tables
- **PDF Documents**: Text extraction and analysis
- **Images**: OCR processing for text extraction
- **Audio Files**: Speech-to-text conversion
- **Structured Data**: CSV, JSON, SQL databases
- **APIs**: RESTful API data consumption

## 🔧 Configuration

### Environment Variables
- `GEMINI_API_KEY`: Your Google Gemini API key
- `HOST`: Server host (default: 0.0.0.0)
- `PORT`: Server port (default: 8000)
- `DEBUG`: Debug mode (default: false)

### API Endpoints
- `GET /`: Health check
- `GET /health`: Detailed health status
- `POST /api/`: Main analysis endpoint
- `GET /docs`: Interactive API documentation

## 🧪 Testing

Run the test suite:
```bash
python -m pytest tests/
```

Test with sample data:
```bash
python test_movie_api.py
```

## 📈 Performance

- **Response Time**: < 3 minutes (as per requirements)
- **Concurrent Requests**: Handles multiple simultaneous requests
- **Memory Usage**: Optimized for large datasets
- **Error Handling**: Robust error recovery and logging

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Google Gemini AI for LLM capabilities
- FastAPI for the web framework
- The open-source community for various data processing libraries

## 📞 Support

For questions or issues:
- Create an issue on GitHub
- Check the API documentation at `/docs`
- Review the test examples in the `tests/` directory

---

**Built with ❤️ for data analysis and AI-powered insights** 