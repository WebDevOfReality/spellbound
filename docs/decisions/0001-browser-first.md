# ADR 0001: Browser-first, on-device inference

**Status:** accepted, 2026-09-25

**Context**
- Users are kids and families on school Chromebooks, home laptops and phones.
- Camera video of minors is sensitive.
- Servers cost money, and an open-source project can't promise to keep them running.

**Decision**
- Run the whole camera → landmarks → classifier path in the browser.
- The app ships as static files.
- Nothing leaves the device unless the user explicitly opts in. The one exception is an optional
  coach, and it only ever receives structured results.

**Consequences**
- Models must be small, so we need an efficiency discipline from day one.
- The app works offline once loaded.
- The app needs HTTPS for `getUserMedia`. Local development uses localhost.
