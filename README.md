# datepicker-demo


Notes: How to switch to iOS wheel only + Android default
You only need to change 2 things:
Change 1 — Device detection (Line ~130 in the JS)
javascript// CURRENT — iOS + Android both get wheel picker
const isMobile = /iPad|iPhone|iPod|Android/i.test(navigator.userAgent) && !window.MSStream;

// CHANGE TO — iOS wheel only, Android gets native popup
const isMobile = /iPad|iPhone|iPod/i.test(navigator.userAgent) && !window.MSStream;
Just remove |Android from the regex. That's it.

Change 2 — Device badge label (3 lines below the detection)
javascript// CURRENT
document.getElementById("deviceBadge").textContent =
  /iPad|iPhone|iPod/i.test(ua) ? "iOS — Wheel picker"     :
  /Android/i.test(ua)          ? "Android — Wheel picker" :  // ← remove this line
                                 "Desktop — Browser picker";

// CHANGE TO
document.getElementById("deviceBadge").textContent =
  /iPad|iPhone|iPod/i.test(ua) ? "iOS — Wheel picker"        :
  /Android/i.test(ua)          ? "Android — Native calendar" :  // ← update label only
                                 "Desktop — Browser picker";
