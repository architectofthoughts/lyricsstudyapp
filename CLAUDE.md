# Japanese Lyrics Study Assistant Project 📚🎵

This is a web application that helps users learn Japanese through song lyrics analysis using AI.

## Project Overview

A Japanese lyrics learning web application powered by Gemini API with Google OAuth 2.0 authentication. Users can input Japanese song lyrics and receive automatic romanization, translation, grammar explanations, key vocabulary definitions, and learning quizzes. Authorized users can login with Google account to skip API key input.

## Key Features

### 🎯 Lyrics Analysis
- **Gemini API Integration**: Uses Google's latest AI model for accurate analysis
- **Automatic Romanization**: Generates Korean pronunciation guide for Japanese lyrics
- **Contextual Translation**: Natural Korean translations considering context
- **HTML Export**: Save analysis results as standalone HTML files

### 📖 Lyrics & Interpretation
- **Line-by-line Learning**: Click each lyrics line to toggle pronunciation and interpretation
- **Clipboard Copy**: Copy lyrics, romanization, and translations at once
- **Intuitive UI**: Clean card-based interface

### 📚 Detailed Commentary
- **Japanese Teacher Perspective**: AI acts as friendly Japanese teacher for grammar explanations
- **Grammar Points**: Detailed analysis of particles, conjugations, idioms, etc.
- **Vocabulary Nuances**: Explains word choice reasoning and emotional meanings

### 🔤 Key Vocabulary
- **Core Word Extraction**: Automatically selects important Japanese words from lyrics
- **Detailed Explanations**: Etymology, usage, similar expressions
- **Learning Optimization**: Practical information helpful for Japanese learning

### 🎮 Lyrics Quiz
- **3 Quiz Types**: Romanization, fill-in-the-blank, translation quizzes
- **Random Generation**: Problems generated randomly from learned content
- **Immediate Feedback**: Answer checking and explanations

### 🔐 Google OAuth Authentication
- **Authorized Access**: jaceyoung0705@gmail.com account can login with Google
- **Auto API Key**: Authenticated users skip API key input step
- **Secure Authentication**: Google OAuth 2.0 implementation with encrypted API key storage

## Technical Stack

- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Styling**: Tailwind CSS
- **AI API**: Google Gemini 2.5 Flash Preview / Pro
- **Authentication**: Google OAuth 2.0
- **Storage**: Browser LocalStorage
- **Compatibility**: All modern browsers

## Usage Instructions

### Deployment & Access

**Production (Recommended):**
- GitHub Pages: `https://architectofthoughts.github.io/lyricsstudyapp/`
- Full Google OAuth support  
- HTTPS environment required for OAuth

**Development:**
- Local file execution: Limited to manual API key only
- Local web server: `python -m http.server 8000` for full functionality

### Setup

**Option A: Google OAuth (HTTPS only)**
1. Access via GitHub Pages URL
2. Click "Google 계정으로 로그인" button
3. Login with authorized account (jaceyoung0705@gmail.com)  
4. API key input automatically skipped

**Option B: Manual API Key**
1. Get Gemini API key from [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Enter the API key in the first input field

**Common: Lyrics Input**
- Paste Japanese lyrics in the text area

### Analysis Process
1. Click "분석하기" (Analyze) button
2. Wait for AI analysis (usually 10-30 seconds)
3. Automatically redirected to "가사 & 해석" (Lyrics & Interpretation) tab

### Learning Features
- **Lyrics & Interpretation Tab**: Click cards to view pronunciation and interpretation
- **Detailed Commentary Tab**: Read AI teacher's grammar explanations
- **Key Vocabulary Tab**: Study core vocabulary meanings and usage
- **Lyrics Quiz Tab**: Generate and solve various quiz types

### Data Management
- **HTML Export**: Save analysis results as independent HTML files
- **Clear Stored Data**: Delete analysis data from browser storage
- **Auto Save**: Analysis results automatically saved in browser for future visits

## Development Notes

### Version Management
- **Current Version**: v1.1.0 (displayed in header)
- **Version Control**: APP_VERSION constant for systematic version tracking
- **Update History**: UI fixes, encoding improvements, OAuth enhancements

### Recent Updates (v1.1.0)
- **UI Layout Fix**: Corrected textarea width responsive design (`w-fll` → `w-full`)
- **UTF-8 Encoding**: Enhanced Korean username support in Google OAuth with proper Base64 decoding
- **HTML Export**: Improved save function to exclude login state and reset authentication variables
- **Version Display**: Added version information in header for user visibility

### File Structure
- Single-page application with tabbed interface
- Uses Tailwind CSS for responsive design
- Integrates with Gemini AI API for content analysis
- LocalStorage for data persistence

### API Integration
- Gemini 2.5 Flash Preview / Pro models
- Handles Japanese text analysis, translation, and educational content generation
- API key stored locally in browser only (manual entry) or encrypted in app (OAuth users)

### OAuth Integration
- Google OAuth 2.0 for authorized user authentication
- Client ID configuration required in Google Cloud Console
- Encrypted API key storage for authorized users
- UTF-8 safe Base64 decoding for international characters
- See GOOGLE_OAUTH_SETUP.md for detailed setup instructions

## Testing Commands
- Check for linting: Look for package.json scripts
- Test functionality: Manual testing in browser
- Verify API integration: Test with valid Gemini API key
- OAuth testing: Test Google login with authorized account

## Security Considerations
- API keys stored locally only (manual entry) or encrypted in app (OAuth users)
- Google OAuth 2.0 for secure authentication
- No external data transmission except to Gemini API and Google OAuth
- Personal learning use only for copyrighted lyrics
- Check Gemini API free tier limits

## Troubleshooting

### Google OAuth Issues
- **"OAuth 2.0 policy" errors**: Follow GOOGLE_OAUTH_SETUP.md guide
- **Unauthorized email**: Check test user registration in Google Cloud Console
- **Domain mismatch**: Verify authorized JavaScript origins in OAuth settings
- **Korean encoding issues**: Fixed with UTF-8 safe Base64 decoding (v1.1.0+)

### UI Layout Issues
- **Textarea width problems**: Fixed responsive design issues (v1.1.0+)
- **Version information**: Version display now visible in header
- **Mobile compatibility**: Maintained across all screen sizes

### HTML Export Issues
- **Login state in saved files**: Fixed to exclude authentication state (v1.1.0+)
- **Clean initial state**: Saved HTML files now start fresh without login UI

### API Issues  
- **API Errors**: Check API key and internet connection
- **Analysis Failures**: Lyrics too long or special characters
- **Storage Issues**: Check browser storage capacity or cookie settings

## Setup Instructions

### For Developers
1. **GitHub Pages Deployment**: Follow DEPLOYMENT.md for hosting setup
2. **Google Cloud Setup**: Follow GOOGLE_OAUTH_SETUP.md for OAuth configuration
3. **Client ID Update**: Replace `GOOGLE_CLIENT_ID` in LyricsStudy.html
4. **API Key Encryption**: Encrypted API key already included for authorized users
5. **Testing**: Test both manual API key entry and OAuth authentication
6. **Domain Configuration**: Add GitHub Pages URL to OAuth authorized origins