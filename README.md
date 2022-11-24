# CR-10-Mini-BigTreeTech-SKR-Mini-E3-3.0 Marlin Configuration
Marlin Config Files w/ BL Touch and TFT 35 V3 & All Metal Hotend set at 300°C

Configuration for the BigTreeTech SKR E3 Mini V2 in a Creality CR-10 Mini using the BTT TFT 35 V3 display, and a BL Touch v3.1 ABL probe mounted on a Bullseye fan duct. Additional features are enabled to take advantage of the capabilities of the BTT SKR E3 Mini V3 board, detailed below.

Compile this in the STM32G0B1RE_btt 512k environment. 

Configuration.h notes:

#define HEATER_0_MAXTEMP 315°C. If not required or other temp required use desired Max temp +15°C to allow for 15°C overshoot

Sets Hotend temp to 300

#define Z_MIN_PROBE_USES_Z_MIN_ENDSTOP_PIN

This configuration uses only the probe for Z homing. The Z-stop switch is NOT enabled and can be disconnected.

#define NOZZLE_TO_PROBE_OFFSET { -43.9, -5.6, -3.48 }

These are the offsets for a left-side mounted BL Touch on a my stock fan duct base. Change them as required for your particular BL Touch mount.

#define MULTIPLE_PROBING 2

Bed probing will test each point twice. 1st probe will be "fast" Z, 2nd will use the slower Z rate.

#define AUTO_BED_LEVELING_BILINEAR

Change this as desired. BILINEAR will work for most printers.

//#define RESTORE_LEVELING_AFTER_G28

This is disabled to work around an issue where —even with an M420 command in start G-Code— ABL would toggle to the opposite of whatever the ABL state was (Enabled/Disabled) at the time a print job started.

#define GRID_MAX_POINTS_X 5

This configuration is set to use a 5x5 (25 point) probing grid. Change as desired.

#define EXTRAPOLATE_BEYOND_GRID

By default, this is disabled. Enabling this seemed to provide better mesh data.

#define LCD_BED_LEVELING

Provides control panel probe controls.

#define LCD_BED_TRAMMING

Provides control panel bed tramming controls.

#define Z_SAFE_HOMING

Ensures the BL Touch probe is not hanging off the edge of the bed when Z homing.

#define CR10_STOCKDISPLAY

If you are using the stock display on your CR-10 Mini, this MUST be enabled.

Configuration_adv.h notes:

#define LIN_ADVANCE

This is enabled, but the K value is set to 0 which effectively disables LIN_ADVANCE. Calibrate Linear Advance and set your own K value and recompile.

#define ARC_SUPPORT

Enables G2/G3 moves to smooth curves in your prints. Required for the Arc Welder plugin for OctoPrint etc.

#define ARC_P_CIRCLES

Normally disabled by default.
