# VideoMaMa Project Page Structure

## 📁 File Organization

The project page has been refactored for better maintainability and organization.

### Main Files
- **`main.html`** (2,311 lines) - Main page with hero section, styles, and JavaScript logic
- **`index.html`** (if exists) - Entry point that might redirect to main.html

### 📂 Sections (`sections/`)
HTML content for each major section, loaded dynamically:

1. **`sav_mav_comparison.html`** - SA-V vs MA-V comparison block
   - Video sliders with comparison overlays
   - Gallery with pagination

2. **`in_the_wild.html`** - VideoMaMa in-the-wild results
   - Bento layout with input RGB, input mask, and results
   - Alpha/Composition toggle
   - Gallery with pagination

3. **`qualitative_comparison.html`** - Multi-model qualitative comparison
   - MaGGIe, VideoMaMa, MatAnyone, SAM2-Matte
   - All-frame mask-guided vs first-frame mask-guided
   - Global alpha/composition mode switch
   - Gallery with video selection

### 📂 Data (`data/`)
JavaScript files containing video metadata arrays:

1. **`videoData.js`** - SA-V vs MA-V comparison videos (47 videos)
   - RGB videos, masks, predictions, compositions
   
2. **`bentoData.js`** - In-the-wild results (24 videos)
   - Input RGB, masks, alpha predictions, compositions

3. **`newLayoutData.js`** - Qualitative comparison videos (3 samples)
   - Input RGB/mask
   - 4 model outputs (MaGGIe, VideoMaMa, MatAnyone, SAM2-Matte)
   - Alpha and composition for each model

### 📂 Assets
- **`mav_sav/`** - SA-V vs MA-V videos
- **`videomama/`** - In-the-wild result videos
- **`comparison/`** - Qualitative comparison videos
  - `MaGGIe/` - MaGGIe results
  - `videomama/` - VideoMaMa results  
  - `MatAnyone/` - MatAnyone results
  - `mav_mask/` - SAM2-Matte results

## 🔧 How It Works

### Dynamic Loading
```javascript
// On page load, sections are loaded asynchronously
loadSection('sav-mav-section', 'sections/sav_mav_comparison.html')
loadSection('in-the-wild-section', 'sections/in_the_wild.html')
loadSection('qualitative-comparison-section', 'sections/qualitative_comparison.html')
```

### Video Data
```html
<!-- Data files are loaded before main script -->
<script src="data/videoData.js"></script>
<script src="data/bentoData.js"></script>
<script src="data/newLayoutData.js"></script>
```

## 📊 Statistics

### Before Refactoring
- **main.html**: ~3,029 lines
- All content inline
- All data arrays inline

### After Refactoring  
- **main.html**: 2,311 lines (**718 lines removed, -23.7%**)
- **3 section files**: ~240 lines total
- **3 data files**: ~725 lines total
- **Total**: More organized, easier to maintain

## ✨ Benefits

1. **Cleaner main.html** - Easier to navigate and understand
2. **Modular sections** - Edit sections independently
3. **Separated data** - Video lists don't clutter the main file
4. **Easier maintenance** - Update one section without touching others
5. **Better organization** - Clear separation of structure, data, and logic
6. **Reusable** - Sections can be reused or rearranged easily

## 🎯 Features Preserved

All original functionality works exactly the same:
- ✅ Video playback and synchronization
- ✅ Slider comparisons
- ✅ Galleries with pagination  
- ✅ Navigation buttons
- ✅ Alpha/Composition toggles
- ✅ Responsive design
- ✅ All 74 videos across all sections

## 🔄 Making Changes

### To update a section's layout:
Edit the corresponding file in `sections/`

### To add/modify videos:
Edit the corresponding file in `data/`

### To change styles or logic:
Edit `main.html` (CSS and JavaScript are still there)

### To add a new section:
1. Create HTML file in `sections/`
2. Add div container in `main.html`
3. Add `loadSection()` call in `loadAllSections()`
4. (Optional) Create data file in `data/` if needed
