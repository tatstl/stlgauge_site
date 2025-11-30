# Disclaimer Files - Usage Guide

This directory contains disclaimer content in multiple formats for use in both the website and the STLGauge application.

## Files

### 1. `disclaimer-translations.json`
**Format:** JSON
**Purpose:** Multilingual disclaimer translations
**Languages:** English, Spanish, German, French, Japanese, Korean, Chinese, Arabic, Russian

**Usage in Application:**
```javascript
// Import the translations
const disclaimerTranslations = require('./disclaimer-translations.json');

// Get disclaimer for current language
const currentLanguage = 'en'; // or 'es', 'de', 'fr', 'ja', 'ko', 'zh', 'ar', 'ru'
const disclaimer = disclaimerTranslations[currentLanguage];

// Access specific sections
console.log(disclaimer.title);              // "Disclaimer"
console.log(disclaimer.alphaWarning);       // "ALPHA SOFTWARE NOTICE:"
console.log(disclaimer.alphaText);          // Full alpha warning text
console.log(disclaimer.noWarrantyTitle);    // "No Warranty"
console.log(disclaimer.noWarrantyText);     // Full warranty disclaimer
// ... and so on
```

**Structure:**
```json
{
  "en": {
    "title": "Disclaimer",
    "alphaWarning": "ALPHA SOFTWARE NOTICE:",
    "alphaText": "...",
    "noWarrantyTitle": "No Warranty",
    "noWarrantyText": "...",
    "liabilityTitle": "Limitation of Liability",
    "liabilityText": "...",
    "verificationTitle": "Verification Required",
    "verificationText": "...",
    "verification1": "...",
    "verification2": "...",
    "verification3": "...",
    "verification4": "...",
    "verification5": "...",
    "userResponsibilityTitle": "User Responsibility",
    "userResponsibilityText": "...",
    "responsibility1": "...",
    "responsibility2": "...",
    "responsibility3": "...",
    "responsibility4": "...",
    "responsibility5": "...",
    "technicalLimitationsTitle": "Technical Limitations",
    "technicalLimitationsText": "...",
    "limitation1": "...",
    "limitation2": "...",
    "limitation3": "...",
    "limitation4": "...",
    "limitation5": "...",
    "limitation6": "...",
    "governingLawTitle": "Governing Law",
    "governingLawText": "...",
    "acknowledgment": "..."
  },
  "es": { ... },
  "de": { ... },
  // ... other languages
}
```

### 2. `DISCLAIMER.txt`
**Format:** Plain Text
**Purpose:** Human-readable disclaimer in English
**Use Cases:**
- Display in console/terminal
- Include in installation packages
- Text-based license viewers
- Command-line tools

### 3. `DISCLAIMER.md`
**Format:** Markdown
**Purpose:** Formatted disclaimer with visual emphasis
**Use Cases:**
- GitHub repository
- Documentation sites
- In-app help/about dialogs (if markdown rendering is supported)
- README files

## Integration Examples

### Electron Application (Main Process)

```javascript
const { app, BrowserWindow, ipcMain } = require('electron');
const fs = require('fs');
const path = require('path');

// Load disclaimer translations
const disclaimerPath = path.join(__dirname, 'disclaimer-translations.json');
const disclaimers = JSON.parse(fs.readFileSync(disclaimerPath, 'utf8'));

// Handle disclaimer request from renderer
ipcMain.handle('get-disclaimer', (event, language) => {
  return disclaimers[language] || disclaimers['en'];
});
```

### Electron Application (Renderer Process)

```javascript
// Request disclaimer in current language
const disclaimer = await window.api.getDisclaimer('en');

// Display in a dialog or modal
showDisclaimerModal({
  title: disclaimer.title,
  content: disclaimer
});
```

### React Component Example

```jsx
import React, { useState, useEffect } from 'react';
import disclaimerTranslations from './disclaimer-translations.json';

function DisclaimerModal({ language = 'en', onClose }) {
  const [disclaimer, setDisclaimer] = useState(null);

  useEffect(() => {
    setDisclaimer(disclaimerTranslations[language]);
  }, [language]);

  if (!disclaimer) return null;

  return (
    <div className="disclaimer-modal">
      <h2>{disclaimer.title}</h2>

      <section>
        <strong>{disclaimer.alphaWarning}</strong>
        <p>{disclaimer.alphaText}</p>
      </section>

      <section>
        <h3>{disclaimer.noWarrantyTitle}</h3>
        <p>{disclaimer.noWarrantyText}</p>
      </section>

      <section>
        <h3>{disclaimer.liabilityTitle}</h3>
        <p>{disclaimer.liabilityText}</p>
      </section>

      <section>
        <h3>{disclaimer.verificationTitle}</h3>
        <p>{disclaimer.verificationText}</p>
        <ul>
          <li>{disclaimer.verification1}</li>
          <li>{disclaimer.verification2}</li>
          <li>{disclaimer.verification3}</li>
          <li>{disclaimer.verification4}</li>
          <li>{disclaimer.verification5}</li>
        </ul>
      </section>

      <section>
        <h3>{disclaimer.userResponsibilityTitle}</h3>
        <p>{disclaimer.userResponsibilityText}</p>
        <ul>
          <li>{disclaimer.responsibility1}</li>
          <li>{disclaimer.responsibility2}</li>
          <li>{disclaimer.responsibility3}</li>
          <li>{disclaimer.responsibility4}</li>
          <li>{disclaimer.responsibility5}</li>
        </ul>
      </section>

      <section>
        <h3>{disclaimer.technicalLimitationsTitle}</h3>
        <p>{disclaimer.technicalLimitationsText}</p>
        <ul>
          <li>{disclaimer.limitation1}</li>
          <li>{disclaimer.limitation2}</li>
          <li>{disclaimer.limitation3}</li>
          <li>{disclaimer.limitation4}</li>
          <li>{disclaimer.limitation5}</li>
          <li>{disclaimer.limitation6}</li>
        </ul>
      </section>

      <section>
        <h3>{disclaimer.governingLawTitle}</h3>
        <p>{disclaimer.governingLawText}</p>
      </section>

      <section>
        <strong>{disclaimer.acknowledgment}</strong>
      </section>

      <button onClick={onClose}>Close</button>
    </div>
  );
}

export default DisclaimerModal;
```

## Recommendations for Application Integration

1. **First Launch**: Display disclaimer on first application launch and require user acceptance
2. **Help Menu**: Add "Disclaimer" option in Help menu
3. **About Dialog**: Include link to disclaimer in About dialog
4. **Settings**: Add disclaimer accessibility in application settings
5. **Console Output**: Show disclaimer text when running in CLI mode
6. **License File**: Include DISCLAIMER.txt in distribution packages

## File Locations for Electron App

Suggested structure:
```
your-electron-app/
├── resources/
│   ├── disclaimer-translations.json
│   ├── DISCLAIMER.txt
│   └── DISCLAIMER.md
├── main.js
└── renderer/
    └── components/
        └── DisclaimerModal.jsx
```

## Notes

- All translations are consistent across all 9 supported languages
- The JSON structure makes it easy to add new languages
- Text and Markdown versions are provided for non-web contexts
- All files contain the same legal content, just in different formats
