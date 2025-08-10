# Placement Developer Test: Archery Spelling Game

## Overview
You've been given an educational archery spelling game that has several bugs and needs enhancements. Your task is to fix the existing issues and implement a new feature.

## Time Allocation
- **Total Time**: 1-2 hours
- **Bug Fixes**: 1 hours
- **Enhancements**: 1-2 hours

## Code Structure Overview

The game is built using vanilla JavaScript with a modular pattern. Here are the key components:

### Core Game Modules
- **gameData**: Stores current game state, questions, and results
- **hangmanSpellingGame**: Main game logic for checking answers and managing game flow
- **hangmanSpellingAnimation**: Handles the archery animation and visual effects
- **keyboard**: Creates and manages the on-screen letter keyboard
- **progressBar**: Shows player progress through questions
- **uiCounter**: Manages the "lives" system (3 arrows)

### UI and Navigation
- **view**: Controls section visibility and screen transitions
- **Button**: Constructor for interactive elements with animations
- **topUI/bottomUI**: Header and footer interface management
- **feedback**: Shows correct/incorrect answer animations

### Utilities
- **audio**: Sound management using Howler.js
- **animation**: GSAP-based animations for UI elements
- **random**: Random number generation and array shuffling
- **load**: Asset loading and game initialization

### Game Flow
1. **introScreen**: Welcome screen with play button
2. **gameScreen**: Main gameplay with keyboard, image, and word display
3. **endScreen**: Results summary with replay option

The game loads questions from a JSON structure, displays images and audio cues, and tracks player progress through a spelling challenge with an archery theme.

## Part 1: Bug Fixes (Critical - Must Complete)

### Bug 1: Case Sensitivity Issue
**Problem**: The game doesn't handle uppercase/lowercase letters properly in some scenarios.
**Location**: `hangmanSpellingGame.checkAnswer()` function
**Hint**: Look at how `keyLetter` is compared with `questionTextArray[i]` - should this be case sensitive?

### Bug 2: Progress Bar Off-by-One Error
**Problem**: The progress bar sometimes highlights the wrong position.
**Location**: `progressBar.highlightBarPill()` calls
**Hint**: Check the math in the function - is there an extra +1 where there shouldn't be?

### Bug 3: Audio Button Disappearing
**Problem**: Audio button sometimes doesn't show up for questions that have audio.
**Location**: `hangmanSpellingGame.addQuestionAudio()` function
**Hint**: Look carefully at the condition logic - when should the audio button appear vs disappear?

### Bug 4: Hint Button Logic Error
**Problem**: The hint system sometimes gives hints for letters that are already revealed.
**Location**: `hangmanSpellingGame.getHint()` function
**Hint**: The logic for building the `hintLetters` array doesn't filter out already revealed letters

## Part 2: Feature Enhancements (Choose 1)

### Easy Enhancement Options

**Physical Keyboard Support**
Add support for typing letters on the physical keyboard instead of just clicking.
- Listen for keydown events on the document
- Map typed letters to the game's letter checking system
- Prevent default browser behavior for game keys
- Add visual feedback when physical keys are pressed
- Handle key repeat prevention

**Sound Toggle Button**
Add ability to mute/unmute all game sounds.
- Add a mute/unmute button to the UI
- Control Howler.js global mute state
- Update button visual state to show muted/unmuted
- Remember preference using sessionStorage
- Apply to all game audio, not just specific sounds

### Medium Enhancement Options

**Difficulty Level Selection**
Implement three difficulty levels that change game behavior.
- Add difficulty selection on intro screen
- Easy: 5 lives instead of 3, hint button always available
- Medium: Current behavior (3 lives, 2 hints)
- Hard: 2 lives, no hint button available
- Modify `uiCounter` setup to accommodate different life counts
- Update UI to show selected difficulty

**Scoring System with Bonuses**
Add a comprehensive scoring system with time and accuracy bonuses.
- Base points for each correct letter (e.g., 10 points)
- Speed bonus for quick completion (bonus decreases over time)
- Accuracy bonus for fewer mistakes
- Perfect word bonus (no wrong letters)
- Display running score during gameplay
- Show detailed score breakdown on end screen
- Track high scores in sessionStorage

### Hard Enhancement Options

**Mobile-First Responsive Design**
Completely overhaul the interface for mobile devices.
- Redesign keyboard layout for touch screens
- Optimize touch target sizes (minimum 44px)
- Implement responsive scaling without breaking animations
- Add swipe gestures for navigation
- Optimize performance for mobile devices
- Test thoroughly on various screen sizes
- Maintain desktop compatibility

**Advanced Accessibility Features**
Make the game fully accessible to users with disabilities.
- Add comprehensive ARIA labels and roles
- Implement full keyboard navigation (tab order, focus management)
- Add screen reader announcements for game state changes
- Ensure minimum 4.5:1 color contrast ratios
- Add focus indicators for all interactive elements
- Support high contrast mode
- Add option for reduced motion
- Test with actual screen readers

## Deliverables

### Required Files
1. **Fixed JavaScript** 
2. **Updated HTML** (if modifications needed)
3. **Updated CSS** (if modifications needed)
4. **README.md** containing:
   - List of bugs found and how you fixed them
   - Description of enhancements implemented
   - Instructions for testing your changes
   - Any assumptions or design decisions made

### Optional Files
- **IMPROVEMENTS.md** - Additional improvements you would make given more time
- **TEST_PLAN.md** - How you would systematically test this game

## Tips

- Use browser DevTools extensively - console logs and breakpoints are essential
- Test each fix individually before moving to the next issue
- Read and understand the existing code patterns before making changes
- Keep solutions simple and maintainable
- Focus on working implementations over complex architectures
- Document any assumptions you make about unclear requirements

## Testing Your Work

- Test the game with different word lengths and character sets
- Try rapid clicking/typing to test for race conditions
- Test with audio on/off
- Verify progress tracking works correctly
- Check that all animations complete properly
- Test any new features you implement thoroughly

Remember: We value your problem-solving approach and code quality over perfect solutions. Show us how you think through problems and implement clean, working code.