# UpTop Construction: homepage redesign, sitemap and design notes

Prepared by Nulla & Chaudhry Media, November 2026. Source material: uptopconstruction.ca (homepage, Services, About and Contact pages, reviewed 8 Nov 2026), the @uptopconstruction Instagram account and the logo file supplied by the client.

## 1. Package contents

| File | What it is |
|---|---|
| `index.html` | The homepage. Embedded CSS and vanilla JS, no build step. |
| `images/logo.png` | Logo on a transparent background, cropped from the supplied file. |
| `images/logo-light.png` | The same logo with "CONSTRUCTION LTD." in white, for dark backgrounds (footer). |
| `images/*.jpg` | Eight project photos taken from UpTop's Instagram posts, cropped to remove captions and watermarks. |

## 2. Recommended sitemap

```
/                                   Home
/services/                          Services overview (four audience doors)
  /services/contractors/            Subcontract trades
  /services/commercial-warehouse/   Warehouse and unit fit-outs
  /services/homeowners/             Home renovations
     kitchen-renovations/ · bathroom-renovations/ · basement-renovations/
     flooring/ · plumbing/ · electrical/ · exterior-painting/
  /services/builders/               Legal basements and suites
     legal-basements/ · secondary-garden-suites/ · custom-homes/
/projects/                          Projects gallery, filterable by audience
  /projects/[project-slug]/         Optional single-project pages
/about/                             About UpTop
/testimonials/                      All reviews
/contact/                           Contact details and the quote form
/privacy/                           Privacy policy (the form collects personal information)
```

| Page | Purpose | How the homepage links to it |
|---|---|---|
| Home | Lets each of the four audiences find its path in one look and reach the quote form in one click. | n/a |
| Services overview | Puts the four audience hubs side by side, the same way the homepage does, for visitors who arrive from search. | Main nav "Services". |
| Contractors | Lists the trades UpTop supplies to other contractors and how a subcontract job is quoted and scheduled. Needs a project or two that show subcontract work. | Hero path card, services card "All contractor services", footer. |
| Commercial & warehouse | Covers fit-outs, office renovations, commercial flooring and forklift barriers, with the warehouse projects from Instagram. | Hero path card, services card, footer. |
| Homeowners | The largest hub. One child page per service, reusing the current site's service pages and their URLs (see redirects below). | Hero path card, services card, footer. |
| Builders | Legal basement conversions plus secondary and garden suites, written for builders and investors who need code-compliant units. | Hero path card, services card, footer. |
| Projects | Full gallery. Each project gets an audience tag so visitors can filter to "Commercial" or "Home". Pull new entries from Instagram. | Nav "Projects", "See all projects" button, footer. |
| About | Company background, the head office, service area and team photos. Add years in business and credentials here once the client confirms them. | Nav "About", "More about UpTop" button, footer. |
| Testimonials | Every review in one place, grouped by audience once commercial and contractor reviews come in. | Nav "Reviews", footer. |
| Contact | The quote form, contact details and a map. Any page can link to `/contact/?audience=builder` (or contractor, commercial, homeowner) to preselect the client type. | Nav "Contact", every "Get a free quote" button, mobile action bar, footer. |
| Privacy | Required wherever a form collects names, emails and phone numbers. | Footer (add the link when the page exists). |

**Linking while the inner pages don't exist yet.** The main nav points to sections on the homepage (`#services`, `#projects`, and so on), so the page works on its own today. The "All ... services", "See all projects", "More about UpTop" and footer links already point to the sitemap URLs above. As each page goes live, switch its nav anchor to the page URL.

**Redirects to set up (301).** These keep the current site's search rankings:

| Current URL | New URL |
|---|---|
| `/our-services/` | `/services/` |
| `/our-services/kitchen-renovations/` | `/services/homeowners/kitchen-renovations/` |
| `/our-services/bathroom-renovations/` | `/services/homeowners/bathroom-renovations/` |
| `/our-services/flooring-solutions/` | `/services/homeowners/flooring/` |
| `/our-services/basement-renovations/` | `/services/builders/legal-basements/` |
| `/our-services/plumbing-renovations/` | `/services/homeowners/plumbing/` |
| `/our-services/electrical-renovations/` | `/services/homeowners/electrical/` |
| `/about-us/` | `/about/` |
| `/contact-us/` | `/contact/` |

## 3. Design decisions

The look follows the reference site the client liked (executivestyles.netlify.app): dark, editorial and full of motion, rebuilt around UpTop's own red, logo and job-site photos.

**An opening that lands.** The page opens on a short curtain: the logo fades in on black while a red line sweeps under it, then the curtain lifts and the headline rises word by word. The headline adapts UpTop's own Instagram tagline ("Building Dreams From The Ground Up"). On desktop, three job-site photos float beside it at different scroll speeds, each slowly zooming, with a red outlined diamond drifting behind them. The whole sequence takes about two seconds and is skipped for visitors who set their device to reduce motion.

**Four equal doors, still above the fold.** Under the headline, "Start here · I am a" offers four chips: Contractor, Commercial / warehouse, Homeowner, Builder. They match in size and style and sit in the first screen on phone, tablet and desktop. Each one jumps to that audience's row in "Who we build for", where a large numbered row (01 to 04) carries a description, a services link and a quote button. On desktop, hovering a row floats that audience's photo beside the pointer.

**One form, four entry points.** Every quote button carries its audience. "Free quote" on the Builders row scrolls to the form, ticks "Builder" and loads the builder project types, so the client can see which audience each lead came from.

**The quote form is always one click away.** The header keeps a red "Free quote" button on desktop. On phones and tablets a bar with "Call" and "Free quote" slides up once the visitor scrolls past the hero. Every section ends with its own quote button.

**Motion with a job to do.** Section titles and copy fade up as they enter, photos wipe open from the top, a thin red bar across the top of the screen tracks scroll progress, and a scrolling band lists the services between the hero and the audience rows. On desktop a red ring cursor follows the pointer and the main buttons lean toward it. All of it runs on plain CSS and about 260 lines of vanilla JavaScript, with no libraries.

**Brand carried over.** The logo red (#B32E27, sampled from the logo file) fills the buttons. The brighter red from the current site (#EC1C24) draws the thin lines, labels and cursor. Outfit and Roboto, the current site's fonts, carry the type: Outfit at 700 and 200 weights gives the headlines their heavy-and-light contrast. The services section switches to a warm paper background so the full list reads like a printed price sheet.

**Real proof only.** Every photo comes from UpTop's Instagram and every project caption restates the matching post. The ten reviews rotate one at a time in large type, word for word from the current site.

**Built to extend.** CSS is grouped into numbered sections with brand tokens at the top, breakpoints at 640px and 1024px, and the reveal effects are opt-in classes (`reveal`, `img-reveal`, `data-stagger`, `split-word`) that inner pages can reuse. Without JavaScript all content still shows.

## 4. Platform recommendation

Stay on WordPress. The client already hosts there, runs Contact Form 7 and can add projects and reviews without a developer. Rebuild this design as a lightweight custom theme, or a block theme with these styles, and keep Elementor out of it. Elementor templates are why the current site's header and footer have stopped rendering.

To connect the form, create a Contact Form 7 form whose field names match this page (`audience`, `project`, `name`, `email`, `phone`, `message`). Set its mail recipient to info@uptopconstruction.ca, then set `FORM_ENDPOINT` in `index.html` to that form's REST URL and replace `[CF7 FORM ID]`. If the site leaves WordPress later, Formspree or any service that accepts multipart form posts works with the same code.

## 5. What was verified, what is assumed, what is still open

**Checked against the current site or Instagram**
- Phone 647-641-0909 (first number on the Contact page; also the number in UpTop's Instagram captions). The WhatsApp link uses 647-641-0900, the number in the current site's WhatsApp widget.
- Email info@uptopconstruction.ca. The Gmail address is left off, as agreed.
- Address: 3300 Highway 7 W, Suite 600, Vaughan ON L4K 4M3.
- Service area: "Vaughan, Toronto, and Ontario" (Services page). The About page also says "in the heart of Toronto". The homepage uses Vaughan to match the address.
- Homeowner services: the six core services on the current homepage plus complete home remodelling and exterior painting (Services page, Instagram).
- "Licensed & Insured", clear pricing, clean crews and the 10% first-booking offer: from the current site, kept at the client's request.
- All ten testimonials: reproduced word for word from the current homepage, with names as shown there. One uses the word "seamless". It is the reviewer's own wording, so it stays.
- Project captions: restated from the matching Instagram posts (July to August 2026, plus a November 2025 basement post).

**Assumed, needs the client's confirmation**
- Contractor services: you confirmed subcontract trades. The specific list (flooring, painting, plumbing, electrical, stairs, demolition) comes from services that appear on the site and in Instagram posts.
- Builder services: you confirmed legal basements. Secondary and garden suites and custom home builds come from the current Services page. Confirm that UpTop offers them to builders.
- Commercial services: fit-outs (confirmed by you), plus office renovations, commercial flooring, forklift barriers and commercial painting, all shown in Instagram posts.

**Still open (placeholders in the page)**
- `[BUSINESS HOURS]`: not listed anywhere on the current site.
- `[FORM ENDPOINT URL]` and `[CF7 FORM ID]`: the form runs in demo mode until connected and says so on submit.
- Licence and insurance details: shown as "Licensed and insured" only, per your instruction. Nothing more specific was verified.

**Gaps to fill**
- Photo resolution. Instagram serves these images at 360px wide, which is fine on most screens but soft on high-density displays. Ask the client for the original photos and videos, and drop them into `images/` under the same file names.
- No project in the gallery documents subcontract work for another contractor. The Contractors card uses a commercial repaint photo. Ask for one or two subcontract jobs.
- Every testimonial comes from a homeowner or a property owner. Ask the client for one commercial review and one from a contractor, so those audiences see themselves on the page.
- Years in business, project counts and team details: the current About page shows empty counters ("+Years Business"), so the new homepage leaves out numbers entirely.

**Problems on the live site to raise with the client now**
- Hidden spam links (plaenecut, duftnu, hurtiggraas and others) appear at the top of every page, and Russian-language casino links sit at the bottom of the homepage. That pattern usually means the WordPress install has been compromised. Clean it, update core and plugins, and rotate the admin passwords before the redesign goes live.
- The header and footer templates no longer render, so the live site shows no logo or navigation.
- `/our-team/` returns a 404.
