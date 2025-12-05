# 📚 EPUB Translator

A web-based application that translates EPUB books while preserving all original formatting, structure, and metadata.

## ✨ Features

- **Complete EPUB Translation**: Translates all XHTML/HTML content within EPUB files
- **Format Preservation**: Maintains original formatting, indentation, and XML structure
- **Multi-Language Support**: Supports 13 languages including Slovak, Czech, English, Spanish, French, German, Italian, Portuguese, Russian, Japanese, Chinese, Korean, and Arabic
- **Attribute Translation**: Translates image alt text, titles, aria-labels, and placeholders
- **Smart Content Handling**: Skips code blocks, scripts, and style tags
- **Browser-Based**: No installation required - runs entirely in your browser
- **Privacy-Focused**: All processing happens client-side (except translation API calls)

## 🛠️ Technical Details

### Technologies Used
- **React 18**: UI framework
- **JSZip**: EPUB extraction and repacking
- **Anthropic Claude API**: AI-powered translation
- **Vanilla CSS**: Production-ready styling (no frameworks)

### How It Works

1. **Extraction**: The EPUB file is unzipped using JSZip
2. **Content Detection**: All `.xhtml` and `.html` files are identified
3. **Translation**: Each file's text content is translated using Claude API
4. **Preservation**: Original XML structure, whitespace, and formatting are maintained
5. **Repacking**: The translated files are packed back into a new EPUB

### Supported Languages

| Language | Code |
|----------|------|
| Slovak | `sk` |
| Czech | `cs` |
| English | `en` |
| Spanish | `es` |
| French | `fr` |
| German | `de` |
| Italian | `it` |
| Portuguese | `pt` |
| Russian | `ru` |
| Japanese | `ja` |
| Chinese (Simplified) | `zh-CN` |
| Korean | `ko` |
| Arabic | `ar` |

## 🔒 Privacy & Security

- **Client-Side Processing**: EPUB extraction and repacking happen in your browser
- **No File Upload**: Your EPUB files never leave your computer (except text sent to translation API)
- **No Storage**: Files are not stored anywhere - everything is processed in memory

## ⚙️ Configuration

### Using Different Translation API

To use a different translation service, modify the `translateText` function:

```javascript
const translateText = async (text, targetLang) => {
    // Replace with your preferred translation API
    const response = await fetch('YOUR_API_ENDPOINT', {
        method: 'POST',
        headers: {
            'Authorization': 'Bearer YOUR_API_KEY',
            'Content-Type': 'application/json',
        },
        body: JSON.stringify({
            text: text,
            target_language: targetLang
        })
    });
    
    const data = await response.json();
    return data.translated_text;
};
```

## 🐛 Troubleshooting

### Translation Fails
- Check your internet connection
- Ensure the Claude API is accessible
- Try with a smaller EPUB file first

### Download Doesn't Work
- Check browser pop-up blocker settings
- Ensure JavaScript is enabled
- Try a different browser

### EPUB Not Opening After Translation
- Verify the original EPUB is valid
- Check if the EPUB reader supports the format
- Try opening with a different EPUB reader (Calibre, Adobe Digital Editions)

## 📝 Python Version

This project also includes a Python-based CLI translator:

```bash
# Install dependencies
pip install -r requirements.txt

# Translate a single file
python translate_file.py -i input.xhtml -t sk

# Use in Python code
from translator import translate_xhtml_file
result = translate_xhtml_file('input.xhtml', target='sk')
```

See `translator/README.md` for Python version documentation.

## 🤝 Contributing

Contributions are welcome! Areas for improvement:

- Add more translation providers (Google Translate, DeepL, etc.)
- Batch processing multiple EPUBs
- Progress percentage indicator
- Translation memory/caching
- Support for other ebook formats (MOBI, PDF)

## 📄 License

MIT License - feel free to use and modify for your needs.

## 🙏 Acknowledgments

- Built with [React](https://react.dev/)
- EPUB handling by [JSZip](https://stuk.github.io/jszip/)
- Translation powered by [Anthropic Claude](https://www.anthropic.com/)
- Inspired by the need to make books accessible in multiple languages

## 📧 Support

For issues, questions, or suggestions:
- Open an issue on GitHub
- Check existing issues for solutions
- Review the troubleshooting section above

---

**Made with ❤️ for book lovers worldwide**