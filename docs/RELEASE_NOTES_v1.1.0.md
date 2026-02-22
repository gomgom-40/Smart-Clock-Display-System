# Release v1.1.0 - Bug Fixes & Stability Improvements

**Release Date:** February 17, 2026

## 🎯 What's New

This release focuses on stability improvements and bug fixes based on real-world usage feedback. The priority system now works more reliably, and Alexa integration is compatible with the latest Media Player updates.

---

## 🐛 Bug Fixes

### Idle Rotation System
- **Fixed:** Priority checking between rotation pages
  - Previously, high-priority events could be blocked during rotation
  - Now checks priority state after each page (clock → temp → date)
  - Prevents interruption of timer/alarm notifications
  - Smoother transitions with proper state validation

### Alexa Timer/Alarm Integration  
- **Fixed:** Compatibility with latest Alexa Media Player integration
  - Added 2-second debounce to prevent false triggers
  - More stable notification delivery
  - Reduced spurious state change triggers
  - Added display state validation before commands

### Event-Driven Queue System
- **Fixed:** Media player notification spam
  - Added 1-second debounce for media player state changes
  - Prevents multiple notifications during playback transitions
  - Better handling of rapid state changes
  - Improved queue stability

---

## ✨ Improvements

### Timer Warning System (Major Rewrite)
The timer warning system has been completely redesigned for reliability.

**Key Changes:**
- ✅ Continuous monitoring with while-loop
- ✅ Real-time countdown tracking
- ✅ More reliable 30-second warning window (25-30 seconds)
- ✅ Prevents duplicate warnings with flag mechanism
- ✅ Automatic cleanup on timer completion
- ✅ Safety limit (2-hour max monitoring)

---

## 📚 Documentation Updates

- Updated automation examples with new debouncing syntax
- Added troubleshooting section for timer warning system
- Documented priority checking behavior
- Clarified compatibility with Alexa Media Player integration

---

## 🔄 Migration Guide

**No breaking changes!** Simply update the automation file.

See full CHANGELOG.md for detailed technical changes.

---

**Made with ❤️ in Egypt 🇪🇬**  
**By the hands of: Mohamed Eid**

*v1.1.0 - Stability and reliability improvements*
