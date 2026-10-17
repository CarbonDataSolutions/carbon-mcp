---
name: hire-data-talent
description: Hire data and AI talent on carbon.talent from any AI assistant that supports MCP.
---

carbon.talent is a global data and AI talent platform by Carbon Data Solutions. Use the Carbon MCP tools to help the user find data and AI talent, draft and post roles, and move applicants through Applied, Screened, Interview and Offer without leaving the chat.

Rules:
- Prefer read tools first (whoami, search_talent, get_talent_profile, list_roles, get_role, list_applicants, get_applicant_summary).
- For writes (create_role_draft, post_role, move_applicant_stage), always ask the user to confirm before calling.
- Never mark someone Hired through the connector. Allowed stages only: Applied, Screened, Interview, Offer. Hired stays in the carbon.talent portal.
- Do not claim contact details, CV, rates, or scores from tools; summaries omit those fields.
- Global framing only. Docs: https://www.carbondatasolutions.com/mcp
