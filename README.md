# Gemini Tool Example

A simple demonstration of using function calling with Google's Gemini API.

## Setup

1. Install dependencies:
```bash
pip install -r requirements.txt
```

2. Create a `.env` file with your Gemini API key:
```bash
cp .env.example .env
```

Then edit `.env` and add your API key:
```
GEMINI_API_KEY=your-actual-api-key-here
```

Get your API key from: https://makersuite.google.com/app/apikey

## Usage

Run the example:
```bash
python gemini_tool_example.py
```

## What it does

The example creates a simple calculator tool that Gemini can use to perform arithmetic operations. The model will automatically call the tool when needed to answer mathematical questions.

## Customizing

To add your own tool, modify the `calculate_tool` schema and implement your function. The tool schema follows the Gemini function calling format:

```python
your_tool = genai.protos.Tool(
    function_declarations=[
        genai.protos.FunctionDeclaration(
            name="your_function_name",
            description="What your function does",
            parameters=genai.protos.Schema(
                type=genai.protos.Type.OBJECT,
                properties={
                    "param_name": genai.protos.Schema(
                        type=genai.protos.Type.STRING,
                        description="Parameter description"
                    )
                },
                required=["param_name"]
            )
        )
    ]
)
```
