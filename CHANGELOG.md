# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Planned Features
- Weather forecast integration
- Calendar events display
- Custom animations library
- Voice control via Alexa routines
- Mobile dashboard UI
- Multi-language support
- Custom font builder tool
- Animation creator interface
- Web-based configuration interface

---

## [1.1.0] - 2026-02-17

### 🐛 Bug Fixes

**Idle Rotation System:**
- Fixed priority checking between rotation pages to prevent interruption
- Added condition checks after each page display (clock → temp → date)
- Prevents higher-priority events (timer/alarm) from being blocked
- Ensures smoother transitions with proper state validation

**Alexa Timer/Alarm Integration:**
- Added 2-second debounce to timer/alarm state change triggers
- Improved compatibility with latest Alexa Media Player integration updates
- More stable notification triggering, reducing false positives
- Added display state validation before executing actions

**Event-Driven Queue System:**
- Added 1-second debounce for media player state changes
- Reduces notification spam during media playback state transitions
- Better priority handling during rapid state changes
- Improved queue stability with proper condition checks

### ✨ Improvements

**Timer Warning System (Major Rewrite):**
- Complete redesign using while-loop continuous monitoring
- Real-time countdown tracking instead of polling-based checks
- More reliable 30-second warning window (25-30 seconds)
- Graceful cleanup and priority reset on timer completion
- Supports all timer/alarm types (kitchen and living room)
- Prevents duplicate warnings with `warned` flag mechanism

**Display Power Management:**
- Added display state checks before executing display commands
- Prevents commands being sent to powered-off displays
- Better handling of auto-off scenarios

### 🔧 Technical Changes

- Priority validation added between idle rotation pages
- Media player triggers now debounced (1 second)
- Alexa timer/alarm sensors debounced (2 seconds)
- Improved condition templates for state validation
- Enhanced error handling in timer warning loop
- Maximum iteration safety limit (7200) for warning system

### 📚 Documentation

- Updated automation examples with new debouncing syntax
- Added troubleshooting guide for timer warning system
- Documented priority checking behavior in idle rotation

---

## [1.0.0] - 2026-02-15

### Added - Core Features
- **Event-driven architecture** with intelligent priority queue system
- **Priority Management System** (idle → unified → timer_alarm)
- **Alexa Integration** for Timer and Alarm notifications
- **Smart Home Device Monitoring** - tracks 30+ entities
- **Auto-Brightness Control** based on sunrise/sunset times
- **Manual Brightness Override** with 30-minute auto-restore
- **Idle Display Rotation** - cycles through clock, temperature, and date
- **Unified Display Sender** - shows all device state changes
- **Timer Warning System** - alerts 30 seconds before timer expiration

### Added - Hardware Support
- **MAX7219 LED Matrix** support (1-32 modules)
- **ESP8266/ESP32** compatibility
- **Tasmota Firmware** integration (v13.1.0+)
- **Custom Font Support** (Pixelmix TTF included)
- **Pixel-level control** for advanced display manipulation

### Added - Communication
- **MQTT Protocol** integration
- **Home Assistant** full automation support
- **Real-time updates** via MQTT messaging
- **Bidirectional communication** (command & status)

### Added - Display Capabilities
- **Clock Display** (12-hour and 24-hour formats)
- **Temperature Display** with sensor integration
- **Date Display** with custom formatting
- **Scrolling Text** for long messages
- **Custom Text Positioning** (X/Y coordinates)
- **Brightness Control** (0-100%, 16 levels)
- **Scroll Speed Adjustment** (50ms-800ms per pixel)
- **Blink Rate Control** (off, slow, medium, fast)
- **Display Rotation** (normal/upside-down)

### Added - Automations
1. **Brightness Slider Control** - manual brightness adjustment
2. **Idle Page Rotation** - auto-rotates content every 10 minutes
3. **Unified Display Sender** - monitors 30+ devices:
   - 13 Switch entities
   - 6 Light entities
   - 3 Media Player entities
4. **Alexa Timer/Alarm Display** - shows notifications from:
   - Kitchen Echo Dot (timer & alarm)
   - Living Room Echo Dot (timer & alarm)
5. **Timer Warning** - 30-second advance notification

### Added - Scripts
- `clear_smart_clock_display` - Clear display and stop clock
- `display_text_on_smart_clock` - Show custom text
- `smart_clock_set_brightness` - Manual brightness with auto-restore

### Added - Documentation
- Complete README with setup instructions
- Comprehensive troubleshooting guide
- Advanced command reference
- System architecture diagrams
- Configuration examples
- Hardware wiring diagrams
- MQTT topic documentation

### Added - Repository Files
- MIT License
- .gitignore for sensitive data protection
- CHANGELOG.md for version tracking
- GitHub upload guide
- Contributing guidelines
- Issue templates

### Technical Details
- **Firmware:** Tasmota with USE_DISPLAY_MAX7219_MATRIX
- **Platform:** Home Assistant 2023.1.0+
- **Protocol:** MQTT over WiFi 2.4GHz
- **Display:** 8x8 pixel modules (MAX7219)
- **Power:** 5V DC, 500mA+ (depends on module count)
- **Update Rate:** ~10 Hz
- **NTP Sync:** Automatic time synchronization

### Configuration
- **Rules:**
  - Rule1: Auto-start clock on boot
  - Rule2: Sunrise/sunset auto-brightness
- **MQTT Topics:**
  - Command: `cmnd/tasmota_46041E/*`
  - Status: `stat/tasmota_46041E/*`
- **Input Helpers:**
  - `input_number.smart_clock_brightness`
  - `input_text.text_to_display`
  - `input_select.smart_clock_priority`

### Monitored Entities
**Switches (13):**
- Charging outlet, bedroom TV, living room switches (3)
- Bedroom light switch, main bedroom light
- Bedroom closet light switch, entrance light
- Stairs light, bathroom light
- Speaker power, raspberry pi fan

**Lights (6):**
- Bedroom LED, living room LED
- Kitchen light, dining room light
- Reception backlight, dining switch backlight

**Media Players (3):**
- Living room TV (Samsung)
- PlayStation 5
- Fire TV

### Known Issues
None reported in v1.0.0

### Security Notes
- Sensitive files excluded via .gitignore
- No WiFi passwords or MQTT credentials in repository
- Tasmota config backups excluded
- Home Assistant secrets protected

---

## Version History Summary

- **v1.0.0** (2026-02-15) - Initial public release
- Future versions will be documented here

---

## How to Update

### From Source
```bash
git pull origin main
```

### Manual Update
1. Download latest release from GitHub
2. Replace files in your project directory
3. Restart Home Assistant
4. Reflash Tasmota if firmware updates available

---

## Deprecation Notices

None in v1.0.0

---

## Breaking Changes

None in v1.0.0

---

## Contributors

- **Mohamed** - Initial development and release

Want to contribute? See [CONTRIBUTING.md](CONTRIBUTING.md)

---

## Feedback & Bug Reports

Found a bug? Have a feature request?
- Open an issue on GitHub
- Check existing issues first
- Provide detailed description and logs

---

**Last Updated:** February 15, 2026
