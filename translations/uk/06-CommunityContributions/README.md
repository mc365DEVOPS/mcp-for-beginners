<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "7b4b9bfacd2926725e6f1cda82bc8ff5",
  "translation_date": "2025-07-17T12:53:41+00:00",
  "source_file": "06-CommunityContributions/README.md",
  "language_code": "uk"
}
-->
# Спільнота та внески

## Огляд

Цей урок присвячений тому, як взаємодіяти зі спільнотою MCP, робити внески в екосистему MCP та дотримуватися найкращих практик спільної розробки. Розуміння того, як брати участь у відкритих проектах MCP, є важливим для тих, хто хоче впливати на майбутнє цієї технології.

## Цілі навчання

Після проходження цього уроку ви зможете:
- Розуміти структуру спільноти та екосистеми MCP
- Ефективно брати участь у форумах та обговореннях спільноти MCP
- Робити внески у відкриті репозиторії MCP
- Створювати та ділитися власними інструментами та серверами MCP
- Дотримуватися найкращих практик розробки та співпраці в MCP
- Знаходити ресурси та фреймворки спільноти для розробки MCP

## Екосистема спільноти MCP

Екосистема MCP складається з різних компонентів і учасників, які працюють разом для розвитку протоколу.

### Основні компоненти спільноти

1. **Основні підтримувачі протоколу**: офіційна [GitHub організація Model Context Protocol](https://github.com/modelcontextprotocol) підтримує основні специфікації MCP та референсні реалізації
2. **Розробники інструментів**: окремі особи та команди, які створюють інструменти та сервери MCP
3. **Провайдери інтеграцій**: компанії, що інтегрують MCP у свої продукти та сервіси
4. **Кінцеві користувачі**: розробники та організації, які використовують MCP у своїх додатках
5. **Внесники**: члени спільноти, які роблять внески у код, документацію або інші ресурси

### Ресурси спільноти

#### Офіційні канали

- [MCP GitHub організація](https://github.com/modelcontextprotocol)
- [Документація MCP](https://modelcontextprotocol.io/)
- [Специфікація MCP](https://modelcontextprotocol.io/docs/specification)
- [GitHub Discussions](https://github.com/orgs/modelcontextprotocol/discussions)
- [Репозиторій прикладів та серверів MCP](https://github.com/modelcontextprotocol/servers)

#### Ресурси, створені спільнотою

- [Клієнти MCP](https://modelcontextprotocol.io/clients) – список клієнтів, які підтримують інтеграції MCP
- [Сервери MCP спільноти](https://github.com/modelcontextprotocol/servers?tab=readme-ov-file#-community-servers) – зростаючий список серверів MCP, розроблених спільнотою
- [Awesome MCP Servers](https://github.com/wong2/awesome-mcp-servers) – кураторський список серверів MCP
- [PulseMCP](https://www.pulsemcp.com/) – хаб спільноти та розсилка для пошуку ресурсів MCP
- [Discord сервер](https://discord.gg/jHEGxQu2a5) – спілкування з розробниками MCP
- SDK реалізації для різних мов
- Блоги та навчальні матеріали

## Внесок у MCP

### Типи внесків

Екосистема MCP вітає різні типи внесків:

1. **Внески у код**:
   - Покращення основного протоколу
   - Виправлення помилок
   - Реалізації інструментів та серверів
   - Бібліотеки клієнтів/серверів на різних мовах

2. **Документація**:
   - Покращення існуючої документації
   - Створення навчальних матеріалів та посібників
   - Переклад документації
   - Створення прикладів та демонстраційних додатків

3. **Підтримка спільноти**:
   - Відповіді на питання на форумах та в обговореннях
   - Тестування та звітування про проблеми
   - Організація подій спільноти
   - Наставництво нових учасників

### Процес внеску: Основний протокол

Щоб зробити внесок у основний протокол MCP або офіційні реалізації, дотримуйтесь принципів із [офіційних рекомендацій щодо внесків](https://github.com/modelcontextprotocol/modelcontextprotocol/blob/main/CONTRIBUTING.md):

1. **Простота та мінімалізм**: Специфікація MCP встановлює високі вимоги до додавання нових концепцій. Легше додати щось у специфікацію, ніж видалити.

2. **Конкретний підхід**: Зміни у специфікації мають базуватися на конкретних проблемах реалізації, а не на спекулятивних ідеях.

3. **Етапи пропозиції**:
   - Визначення: дослідити проблему, підтвердити, що інші користувачі MCP мають подібну проблему
   - Прототипування: створити приклад рішення та показати його практичне застосування
   - Написання: на основі прототипу написати пропозицію до специфікації

### Налаштування середовища розробки

```bash
# Fork the repository
git clone https://github.com/YOUR-USERNAME/modelcontextprotocol.git
cd modelcontextprotocol

# Install dependencies
npm install

# For schema changes, validate and generate schema.json:
npm run check:schema:ts
npm run generate:schema

# For documentation changes
npm run check:docs
npm run format

# Preview documentation locally (optional):
npm run serve:docs
```

### Приклад: Внесок виправлення помилки

```javascript
// Original code with bug in the typescript-sdk
export function validateResource(resource: unknown): resource is MCPResource {
  if (!resource || typeof resource !== 'object') {
    return false;
  }
  
  // Bug: Missing property validation
  // Current implementation:
  const hasName = 'name' in resource;
  const hasSchema = 'schema' in resource;
  
  return hasName && hasSchema;
}

// Fixed implementation in a contribution
export function validateResource(resource: unknown): resource is MCPResource {
  if (!resource || typeof resource !== 'object') {
    return false;
  }
  
  // Improved validation
  const hasName = 'name' in resource && typeof (resource as MCPResource).name === 'string';
  const hasSchema = 'schema' in resource && typeof (resource as MCPResource).schema === 'object';
  const hasDescription = !('description' in resource) || typeof (resource as MCPResource).description === 'string';
  
  return hasName && hasSchema && hasDescription;
}
```

### Приклад: Внесок нового інструменту до стандартної бібліотеки

```python
# Example contribution: A CSV data processing tool for the MCP standard library

from mcp_tools import Tool, ToolRequest, ToolResponse, ToolExecutionException
import pandas as pd
import io
import json
from typing import Dict, Any, List, Optional

class CsvProcessingTool(Tool):
    """
    Tool for processing and analyzing CSV data.
    
    This tool allows models to extract information from CSV files,
    run basic analysis, and convert data between formats.
    """
    
    def get_name(self):
        return "csvProcessor"
        
    def get_description(self):
        return "Processes and analyzes CSV data"
    
    def get_schema(self):
        return {
            "type": "object",
            "properties": {
                "csvData": {
                    "type": "string", 
                    "description": "CSV data as a string"
                },
                "csvUrl": {
                    "type": "string",
                    "description": "URL to a CSV file (alternative to csvData)"
                },
                "operation": {
                    "type": "string",
                    "enum": ["summary", "filter", "transform", "convert"],
                    "description": "Operation to perform on the CSV data"
                },
                "filterColumn": {
                    "type": "string",
                    "description": "Column to filter by (for filter operation)"
                },
                "filterValue": {
                    "type": "string",
                    "description": "Value to filter for (for filter operation)"
                },
                "outputFormat": {
                    "type": "string",
                    "enum": ["json", "csv", "markdown"],
                    "default": "json",
                    "description": "Output format for the processed data"
                }
            },
            "oneOf": [
                {"required": ["csvData", "operation"]},
                {"required": ["csvUrl", "operation"]}
            ]
        }
    
    async def execute_async(self, request: ToolRequest) -> ToolResponse:
        try:
            # Extract parameters
            operation = request.parameters.get("operation")
            output_format = request.parameters.get("outputFormat", "json")
            
            # Get CSV data from either direct data or URL
            df = await self._get_dataframe(request)
            
            # Process based on requested operation
            result = {}
            
            if operation == "summary":
                result = self._generate_summary(df)
            elif operation == "filter":
                column = request.parameters.get("filterColumn")
                value = request.parameters.get("filterValue")
                if not column:
                    raise ToolExecutionException("filterColumn is required for filter operation")
                result = self._filter_data(df, column, value)
            elif operation == "transform":
                result = self._transform_data(df, request.parameters)
            elif operation == "convert":
                result = self._convert_format(df, output_format)
            else:
                raise ToolExecutionException(f"Unknown operation: {operation}")
            
            return ToolResponse(result=result)
        
        except Exception as e:
            raise ToolExecutionException(f"CSV processing failed: {str(e)}")
    
    async def _get_dataframe(self, request: ToolRequest) -> pd.DataFrame:
        """Gets a pandas DataFrame from either CSV data or URL"""
        if "csvData" in request.parameters:
            csv_data = request.parameters.get("csvData")
            return pd.read_csv(io.StringIO(csv_data))
        elif "csvUrl" in request.parameters:
            csv_url = request.parameters.get("csvUrl")
            return pd.read_csv(csv_url)
        else:
            raise ToolExecutionException("Either csvData or csvUrl must be provided")
    
    def _generate_summary(self, df: pd.DataFrame) -> Dict[str, Any]:
        """Generates a summary of the CSV data"""
        return {
            "columns": df.columns.tolist(),
            "rowCount": len(df),
            "columnCount": len(df.columns),
            "numericColumns": df.select_dtypes(include=['number']).columns.tolist(),
            "categoricalColumns": df.select_dtypes(include=['object']).columns.tolist(),
            "sampleRows": json.loads(df.head(5).to_json(orient="records")),
            "statistics": json.loads(df.describe().to_json())
        }
    
    def _filter_data(self, df: pd.DataFrame, column: str, value: str) -> Dict[str, Any]:
        """Filters the DataFrame by a column value"""
        if column not in df.columns:
            raise ToolExecutionException(f"Column '{column}' not found")
            
        filtered_df = df[df[column].astype(str).str.contains(value)]
        
        return {
            "originalRowCount": len(df),
            "filteredRowCount": len(filtered_df),
            "data": json.loads(filtered_df.to_json(orient="records"))
        }
    
    def _transform_data(self, df: pd.DataFrame, params: Dict[str, Any]) -> Dict[str, Any]:
        """Transforms the data based on parameters"""
        # Implementation would include various transformations
        return {
            "status": "success",
            "message": "Transformation applied"
        }
    
    def _convert_format(self, df: pd.DataFrame, format: str) -> Dict[str, Any]:
        """Converts the DataFrame to different formats"""
        if format == "json":
            return {
                "data": json.loads(df.to_json(orient="records")),
                "format": "json"
            }
        elif format == "csv":
            return {
                "data": df.to_csv(index=False),
                "format": "csv"
            }
        elif format == "markdown":
            return {
                "data": df.to_markdown(),
                "format": "markdown"
            }
        else:
            raise ToolExecutionException(f"Unsupported output format: {format}")
```

### Рекомендації щодо внесків

Щоб зробити успішний внесок у проекти MCP:

1. **Починайте з малого**: починайте з документації, виправлень помилок або невеликих покращень
2. **Дотримуйтесь стилю коду**: дотримуйтесь стилю коду та конвенцій проекту
3. **Пишіть тести**: додавайте юніт-тести для своїх змін
4. **Документуйте свою роботу**: додавайте чітку документацію для нових функцій або змін
5. **Надсилайте цільові PR**: тримайте pull request сфокусованими на одній проблемі або функції
6. **Взаємодійте з відгуками**: будьте відкриті до зворотного зв’язку щодо ваших внесків

### Приклад робочого процесу внеску

```bash
# Clone the repository
git clone https://github.com/modelcontextprotocol/typescript-sdk.git
cd typescript-sdk

# Create a new branch for your contribution
git checkout -b feature/my-contribution

# Make your changes
# ...

# Run tests to ensure your changes don't break existing functionality
npm test

# Commit your changes with a descriptive message
git commit -am "Fix validation in resource handler"

# Push your branch to your fork
git push origin feature/my-contribution

# Create a pull request from your branch to the main repository
# Then engage with feedback and iterate on your PR as needed
```

## Створення та поширення серверів MCP

Один із найцінніших способів зробити внесок у екосистему MCP — створювати та ділитися власними серверами MCP. Спільнота вже розробила сотні серверів для різних сервісів і випадків використання.

### Фреймворки для розробки серверів MCP

Існує кілька фреймворків, які спрощують розробку серверів MCP:

1. **Офіційні SDK**:
   - [TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk)
   - [Python SDK](https://github.com/modelcontextprotocol/python-sdk)
   - [C# SDK](https://github.com/modelcontextprotocol/csharp-sdk)
   - [Go SDK](https://github.com/modelcontextprotocol/go-sdk)
   - [Java SDK](https://github.com/modelcontextprotocol/java-sdk)
   - [Kotlin SDK](https://github.com/modelcontextprotocol/kotlin-sdk)

2. **Фреймворки спільноти**:
   - [MCP-Framework](https://mcp-framework.com/) – створення серверів MCP з елегантністю та швидкістю на TypeScript
   - [MCP Declarative Java SDK](https://github.com/codeboyzhou/mcp-declarative-java-sdk) – сервери MCP на Java з анотаціями
   - [Quarkus MCP Server SDK](https://github.com/quarkiverse/quarkus-mcp-server) – Java фреймворк для серверів MCP
   - [Next.js MCP Server Template](https://github.com/vercel-labs/mcp-for-next.js) – стартовий проект Next.js для серверів MCP

### Розробка інструментів для спільного використання

#### Приклад .NET: створення пакету інструментів для спільного використання

```csharp
// Create a new .NET library project
// dotnet new classlib -n McpFinanceTools

using Microsoft.Mcp.Tools;
using System.Threading.Tasks;
using System.Net.Http;
using System.Text.Json;

namespace McpFinanceTools
{
    // Stock quote tool
    public class StockQuoteTool : IMcpTool
    {
        private readonly HttpClient _httpClient;
        
        public StockQuoteTool(HttpClient httpClient = null)
        {
            _httpClient = httpClient ?? new HttpClient();
        }
        
        public string Name => "stockQuote";
        public string Description => "Gets current stock quotes for specified symbols";
        
        public object GetSchema()
        {
            return new {
                type = "object",
                properties = new {
                    symbol = new { 
                        type = "string",
                        description = "Stock symbol (e.g., MSFT, AAPL)" 
                    },
                    includeHistory = new { 
                        type = "boolean",
                        description = "Whether to include historical data",
                        default = false
                    }
                },
                required = new[] { "symbol" }
            };
        }
        
        public async Task<ToolResponse> ExecuteAsync(ToolRequest request)
        {
            // Extract parameters
            string symbol = request.Parameters.GetProperty("symbol").GetString();
            bool includeHistory = false;
            
            if (request.Parameters.TryGetProperty("includeHistory", out var historyProp))
            {
                includeHistory = historyProp.GetBoolean();
            }
            
            // Call external API (example)
            var quoteResult = await GetStockQuoteAsync(symbol);
            
            // Add historical data if requested
            if (includeHistory)
            {
                var historyData = await GetStockHistoryAsync(symbol);
                quoteResult.Add("history", historyData);
            }
            
            // Return formatted result
            return new ToolResponse {
                Result = JsonSerializer.SerializeToElement(quoteResult)
            };
        }
        
        private async Task<Dictionary<string, object>> GetStockQuoteAsync(string symbol)
        {
            // Implementation would call a real stock API
            // This is a simplified example
            return new Dictionary<string, object>
            {
                ["symbol"] = symbol,
                ["price"] = 123.45,
                ["change"] = 2.5,
                ["percentChange"] = 1.2,
                ["lastUpdated"] = DateTime.UtcNow
            };
        }
        
        private async Task<object> GetStockHistoryAsync(string symbol)
        {
            // Implementation would get historical data
            // Simplified example
            return new[]
            {
                new { date = DateTime.Now.AddDays(-7).Date, price = 120.25 },
                new { date = DateTime.Now.AddDays(-6).Date, price = 122.50 },
                new { date = DateTime.Now.AddDays(-5).Date, price = 121.75 }
                // More historical data...
            };
        }
    }
}

// Create package and publish to NuGet
// dotnet pack -c Release
// dotnet nuget push bin/Release/McpFinanceTools.1.0.0.nupkg -s https://api.nuget.org/v3/index.json -k YOUR_API_KEY
```

#### Приклад Java: створення Maven пакету для інструментів

```java
// pom.xml configuration for a shareable MCP tool package
<!-- 
<project>
    <groupId>com.example</groupId>
    <artifactId>mcp-weather-tools</artifactId>
    <version>1.0.0</version>
    
    <dependencies>
        <dependency>
            <groupId>com.mcp</groupId>
            <artifactId>mcp-server</artifactId>
            <version>1.0.0</version>
        </dependency>
    </dependencies>
    
    <distributionManagement>
        <repository>
            <id>github</id>
            <name>GitHub Packages</name>
            <url>https://maven.pkg.github.com/username/mcp-weather-tools</url>
        </repository>
    </distributionManagement>
</project>
-->

package com.example.mcp.weather;

import com.mcp.tools.Tool;
import com.mcp.tools.ToolRequest;
import com.mcp.tools.ToolResponse;
import com.mcp.tools.ToolExecutionException;

import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;
import java.net.URI;
import java.util.HashMap;
import java.util.Map;

public class WeatherForecastTool implements Tool {
    private final HttpClient httpClient;
    private final String apiKey;
    
    public WeatherForecastTool(String apiKey) {
        this.httpClient = HttpClient.newHttpClient();
        this.apiKey = apiKey;
    }
    
    @Override
    public String getName() {
        return "weatherForecast";
    }
    
    @Override
    public String getDescription() {
        return "Gets weather forecast for a specified location";
    }
    
    @Override
    public Object getSchema() {
        Map<String, Object> schema = new HashMap<>();
        // Schema definition...
        return schema;
    }
    
    @Override
    public ToolResponse execute(ToolRequest request) {
        try {
            String location = request.getParameters().get("location").asText();
            int days = request.getParameters().has("days") ? 
                request.getParameters().get("days").asInt() : 3;
            
            // Call weather API
            Map<String, Object> forecast = getForecast(location, days);
            
            // Build response
            return new ToolResponse.Builder()
                .setResult(forecast)
                .build();
        } catch (Exception ex) {
            throw new ToolExecutionException("Weather forecast failed: " + ex.getMessage(), ex);
        }
    }
    
    private Map<String, Object> getForecast(String location, int days) {
        // Implementation would call weather API
        // Simplified example
        Map<String, Object> result = new HashMap<>();
        // Add forecast data...
        return result;
    }
}

// Build and publish using Maven
// mvn clean package
// mvn deploy
```

#### Приклад Python: публікація пакету на PyPI

```python
# Directory structure for a PyPI package:
# mcp_nlp_tools/
# ├── LICENSE
# ├── README.md
# ├── setup.py
# ├── mcp_nlp_tools/
# │   ├── __init__.py
# │   ├── sentiment_tool.py
# │   └── translation_tool.py

# Example setup.py
"""
from setuptools import setup, find_packages

setup(
    name="mcp_nlp_tools",
    version="0.1.0",
    packages=find_packages(),
    install_requires=[
        "mcp_server>=1.0.0",
        "transformers>=4.0.0",
        "torch>=1.8.0"
    ],
    author="Your Name",
    author_email="your.email@example.com",
    description="MCP tools for natural language processing tasks",
    long_description=open("README.md").read(),
    long_description_content_type="text/markdown",
    url="https://github.com/username/mcp_nlp_tools",
    classifiers=[
        "Programming Language :: Python :: 3",
        "License :: OSI Approved :: MIT License",
        "Operating System :: OS Independent",
    ],
    python_requires=">=3.8",
)
"""

# Example NLP tool implementation (sentiment_tool.py)
from mcp_tools import Tool, ToolRequest, ToolResponse, ToolExecutionException
from transformers import pipeline
import torch

class SentimentAnalysisTool(Tool):
    """MCP tool for sentiment analysis of text"""
    
    def __init__(self, model_name="distilbert-base-uncased-finetuned-sst-2-english"):
        # Load the sentiment analysis model
        self.sentiment_analyzer = pipeline("sentiment-analysis", model=model_name)
    
    def get_name(self):
        return "sentimentAnalysis"
        
    def get_description(self):
        return "Analyzes the sentiment of text, classifying it as positive or negative"
    
    def get_schema(self):
        return {
            "type": "object",
            "properties": {
                "text": {
                    "type": "string", 
                    "description": "The text to analyze for sentiment"
                },
                "includeScore": {
                    "type": "boolean",
                    "description": "Whether to include confidence scores",
                    "default": True
                }
            },
            "required": ["text"]
        }
    
    async def execute_async(self, request: ToolRequest) -> ToolResponse:
        try:
            # Extract parameters
            text = request.parameters.get("text")
            include_score = request.parameters.get("includeScore", True)
            
            # Analyze sentiment
            sentiment_result = self.sentiment_analyzer(text)[0]
            
            # Format result
            result = {
                "sentiment": sentiment_result["label"],
                "text": text
            }
            
            if include_score:
                result["score"] = sentiment_result["score"]
            
            # Return result
            return ToolResponse(result=result)
            
        except Exception as e:
            raise ToolExecutionException(f"Sentiment analysis failed: {str(e)}")

# To publish:
# python setup.py sdist bdist_wheel
# python -m twine upload dist/*
```

### Рекомендації щодо поширення

При поширенні інструментів MCP у спільноті:

1. **Повна документація**:
   - Документуйте призначення, використання та приклади
   - Пояснюйте параметри та значення, що повертаються
   - Документуйте зовнішні залежності

2. **Обробка помилок**:
   - Реалізуйте надійну обробку помилок
   - Надавайте корисні повідомлення про помилки
   - Коректно обробляйте крайні випадки

3. **Продуктивність**:
   - Оптимізуйте швидкість та використання ресурсів
   - Використовуйте кешування, коли це доречно
   - Плануйте масштабованість

4. **Безпека**:
   - Використовуйте безпечні API ключі та автентифікацію
   - Перевіряйте та очищуйте вхідні дані
   - Впроваджуйте обмеження частоти запитів до зовнішніх API

5. **Тестування**:
   - Забезпечте повне покриття тестами
   - Тестуйте з різними типами вхідних даних та крайніми випадками
   - Документуйте процедури тестування

## Співпраця у спільноті та найкращі практики

Ефективна співпраця — ключ до процвітання екосистеми MCP.

### Канали комунікації

- GitHub Issues та Discussions
- Microsoft Tech Community
- Discord та Slack канали
- Stack Overflow (теги: `model-context-protocol` або `mcp`)

### Перегляд коду

Під час перегляду внесків у MCP звертайте увагу на:

1. **Зрозумілість**: чи код зрозумілий і добре документований?
2. **Коректність**: чи працює він як очікується?
3. **Послідовність**: чи дотримується він конвенцій проекту?
4. **Повнота**: чи включені тести та документація?
5. **Безпека**: чи немає проблем із безпекою?

### Сумісність версій

При розробці для MCP:

1. **Версії протоколу**: дотримуйтесь версії протоколу MCP, яку підтримує ваш інструмент
2. **Сумісність клієнтів**: враховуйте зворотну сумісність
3. **Сумісність серверів**: дотримуйтесь рекомендацій щодо реалізації серверів
4. **Значні зміни**: чітко документуйте будь-які несумісні зміни

## Приклад спільнотного проекту: Реєстр інструментів MCP

Важливим внеском у спільноту може бути розробка публічного реєстру інструментів MCP.

```python
# Example schema for a community tool registry API

from fastapi import FastAPI, HTTPException, Depends
from pydantic import BaseModel, Field, HttpUrl
from typing import List, Optional
import datetime
import uuid

# Models for the tool registry
class ToolSchema(BaseModel):
    """JSON Schema for a tool"""
    type: str
    properties: dict
    required: List[str] = []

class ToolRegistration(BaseModel):
    """Information for registering a tool"""
    name: str = Field(..., description="Unique name for the tool")
    description: str = Field(..., description="Description of what the tool does")
    version: str = Field(..., description="Semantic version of the tool")
    schema: ToolSchema = Field(..., description="JSON Schema for tool parameters")
    author: str = Field(..., description="Author of the tool")
    repository: Optional[HttpUrl] = Field(None, description="Repository URL")
    documentation: Optional[HttpUrl] = Field(None, description="Documentation URL")
    package: Optional[HttpUrl] = Field(None, description="Package URL")
    tags: List[str] = Field(default_factory=list, description="Tags for categorization")
    examples: List[dict] = Field(default_factory=list, description="Example usage")

class Tool(ToolRegistration):
    """Tool with registry metadata"""
    id: uuid.UUID = Field(default_factory=uuid.uuid4)
    created_at: datetime.datetime = Field(default_factory=datetime.datetime.now)
    updated_at: datetime.datetime = Field(default_factory=datetime.datetime.now)
    downloads: int = Field(default=0)
    rating: float = Field(default=0.0)
    ratings_count: int = Field(default=0)

# FastAPI application for the registry
app = FastAPI(title="MCP Tool Registry")

# In-memory database for this example
tools_db = {}

@app.post("/tools", response_model=Tool)
async def register_tool(tool: ToolRegistration):
    """Register a new tool in the registry"""
    if tool.name in tools_db:
        raise HTTPException(status_code=400, detail=f"Tool '{tool.name}' already exists")
    
    new_tool = Tool(**tool.dict())
    tools_db[tool.name] = new_tool
    return new_tool

@app.get("/tools", response_model=List[Tool])
async def list_tools(tag: Optional[str] = None):
    """List all registered tools, optionally filtered by tag"""
    if tag:
        return [tool for tool in tools_db.values() if tag in tool.tags]
    return list(tools_db.values())

@app.get("/tools/{tool_name}", response_model=Tool)
async def get_tool(tool_name: str):
    """Get information about a specific tool"""
    if tool_name not in tools_db:
        raise HTTPException(status_code=404, detail=f"Tool '{tool_name}' not found")
    return tools_db[tool_name]

@app.delete("/tools/{tool_name}")
async def delete_tool(tool_name: str):
    """Delete a tool from the registry"""
    if tool_name not in tools_db:
        raise HTTPException(status_code=404, detail=f"Tool '{tool_name}' not found")
    del tools_db[tool_name]
    return {"message": f"Tool '{tool_name}' deleted"}
```

## Основні висновки

- Спільнота MCP різноманітна і вітає різні типи внесків
- Внески можуть охоплювати від покращень основного протоколу до створення власних інструментів
- Дотримання рекомендацій щодо внесків підвищує шанси на прийняття вашого PR
- Створення та поширення інструментів MCP — цінний спосіб розвивати екосистему
- Співпраця у спільноті є необхідною для зростання та вдосконалення MCP

## Вправа

1. Визначте область в екосистемі MCP, де ви могли б зробити внесок, враховуючи свої навички та інтереси
2. Форкніть репозиторій MCP та налаштуйте локальне середовище розробки
3. Створіть невелике покращення, виправлення помилки або інструмент, який буде корисним для спільноти
4. Документуйте свій внесок з відповідними тестами та документацією
5. Надішліть pull request у відповідний репозиторій

## Додаткові ресурси

- [Проекти спільноти MCP](https://github.com/topics/model-context-protocol)


---

Далі: [Уроки з раннього впровадження](../07-LessonsfromEarlyAdoption/README.md)

**Відмова від відповідальності**:  
Цей документ було перекладено за допомогою сервісу автоматичного перекладу [Co-op Translator](https://github.com/Azure/co-op-translator). Хоча ми прагнемо до точності, будь ласка, майте на увазі, що автоматичні переклади можуть містити помилки або неточності. Оригінальний документ рідною мовою слід вважати авторитетним джерелом. Для критично важливої інформації рекомендується звертатися до професійного людського перекладу. Ми не несемо відповідальності за будь-які непорозуміння або неправильні тлумачення, що виникли внаслідок використання цього перекладу.