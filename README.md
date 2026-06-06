# FRED Proxy — minimal Vercel deployment

One serverless function. Proxies BLS employment data from the FRED/ALFRED API.

## Deploy (2 minutes)

1. Push this folder to a GitHub repo (e.g. `fred-proxy`)
2. Go to vercel.com → Add New Project → select the repo → Deploy
3. Settings → Environment Variables → add:
   - Name:  `FRED_API_KEY`
   - Value: your key from fred.stlouisfed.org/docs/api/api_key.html
4. Deployments → Redeploy

Your proxy is live at: `https://fred-proxy-xxx.vercel.app`

## Usage

### Latest revised data (default FRED)
GET /api/fred?series_id=PAYEMS

### First-release only (announcement data — no revisions)
GET /api/fred?series_id=PAYEMS&output_type=4&realtime_start=1776-07-04&realtime_end=9999-12-31

### What was known on a specific date (real-time model input)
GET /api/fred?series_id=PAYEMS&realtime_start=2026-06-03&realtime_end=2026-06-03

### Full vintage history (all revisions ever)
GET /api/fred?series_id=PAYEMS&output_type=2&realtime_start=1776-07-04&realtime_end=9999-12-31

### Monthly change (units=chng)
GET /api/fred?series_id=PAYEMS&units=chng

## Allowed series (BLS employment only)
PAYEMS  — Total nonfarm payrolls
USPRIV  — Private payrolls
USLAH   — Leisure & hospitality
MANEMP  — Manufacturing
USCONS  — Construction
HLTHSL  — Healthcare & social assistance
USFIRE  — Financial activities
USINFO  — Information / tech
USTRADE — Retail trade
USPBS   — Professional & business services
USLOCAL — Local government
USGOVT  — Federal government
CES4300000001 — Transportation & warehousing
UNRATE  — Unemployment rate
U6RATE  — Broad unemployment (U-6)
CIVPART — Labour force participation rate
CES0500000003 — Average hourly earnings
ICSA    — Initial jobless claims
JTSJOL  — JOLTS job openings (level)
JTSJOR  — JOLTS job openings (rate)
JTSQUR  — JOLTS quits rate
