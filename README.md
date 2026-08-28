<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Olaleye Ismail — SOC Analyst</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --bg: #0B0F14;
    --panel: #121821;
    --panel-2: #161D28;
    --line: #232C38;
    --text: #E6EDF3;
    --muted: #8B98A5;
    --amber: #F2A93B;
    --teal: #4FD1C5;
    --red: #E5484D;
    --radius: 3px;
  }

  * { box-sizing: border-box; }
  html { scroll-behavior: smooth; }
  @media (prefers-reduced-motion: reduce){ html { scroll-behavior: auto; } * { animation-duration: 0.01ms !important; animation-iteration-count: 1 !important; transition-duration: 0.01ms !important; } }

  body{
    margin:0;
    background: var(--bg);
    color: var(--text);
    font-family: 'Inter', sans-serif;
    line-height: 1.5;
  }

  a { color: inherit; }

  .wrap{ max-width: 1040px; margin: 0 auto; padding: 0 24px; }

  /* ---------- top bar ---------- */
  .topbar{
    border-bottom: 1px solid var(--line);
    background: rgba(11,15,20,0.9);
    position: sticky; top:0; z-index: 20;
    backdrop-filter: blur(6px);
  }
  .topbar .wrap{
    display:flex; align-items:center; justify-content:space-between;
    height: 56px;
  }
  .brand{
    font-family:'IBM Plex Mono', monospace;
    font-size: 13px; color: var(--teal); letter-spacing: 0.02em;
  }
  .brand span{ color: var(--muted); }
  .topnav{ display:flex; gap: 24px; font-size: 13px; color: var(--muted); }
  .topnav a{ text-decoration:none; }
  .topnav a:hover{ color: var(--text); }
  .topnav a:focus-visible, a:focus-visible, button:focus-visible { outline: 2px solid var(--teal); outline-offset: 2px; }

  /* ---------- hero (incident ticket) ---------- */
  .hero{ padding: 56px 0 0; }
  .ticket{
    border: 1px solid var(--line);
    background: var(--panel);
    border-radius: var(--radius);
    overflow: hidden;
  }
  .ticket-head{
    display:flex; align-items:center; justify-content:space-between;
    padding: 12px 20px;
    border-bottom: 1px solid var(--line);
    background: var(--panel-2);
    font-family:'IBM Plex Mono', monospace;
    font-size: 12px;
    color: var(--muted);
  }
  .ticket-head .id{ color: var(--amber); }
  .status-pill{
    display:inline-flex; align-items:center; gap:6px;
    border:1px solid rgba(79,209,197,0.35);
    color: var(--teal);
    background: rgba(79,209,197,0.08);
    padding: 3px 10px;
    border-radius: 999px;
    font-size: 11px;
    letter-spacing: 0.04em;
  }
  .status-pill::before{
    content:''; width:6px; height:6px; border-radius:50%;
    background: var(--teal);
    box-shadow: 0 0 0 3px rgba(79,209,197,0.15);
  }

  .ticket-body{ padding: 36px 32px 32px; }
  .eyebrow{
    font-family:'IBM Plex Mono', monospace;
    color: var(--amber);
    font-size: 12px;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    margin: 0 0 14px;
  }
  h1{
    font-family:'IBM Plex Sans', sans-serif;
    font-weight: 700;
    font-size: clamp(32px, 5vw, 48px);
    line-height: 1.1;
    margin: 0 0 16px;
    letter-spacing: -0.01em;
  }
  .role-line{
    font-size: 17px;
    color: var(--muted);
    max-width: 640px;
    margin: 0 0 28px;
  }
  .role-line strong{ color: var(--text); font-weight: 600; }

  .meta-grid{
    display:grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1px;
    background: var(--line);
    border: 1px solid var(--line);
    border-radius: var(--radius);
    overflow: hidden;
    margin-bottom: 8px;
  }
  .meta-cell{ background: var(--panel-2); padding: 14px 18px; }
  .meta-cell .k{
    font-family:'IBM Plex Mono', monospace;
    font-size: 10.5px; color: var(--muted);
    text-transform: uppercase; letter-spacing: 0.06em;
    margin-bottom: 6px;
  }
  .meta-cell .v{ font-size: 13.5px; }
  .meta-cell .v a { text-decoration:none; border-bottom: 1px solid rgba(230,237,243,0.25); }
  .meta-cell .v a:hover{ border-color: var(--teal); color: var(--teal); }

  @media (max-width: 640px){ .meta-grid{ grid-template-columns: 1fr; } }

  /* ---------- log feed strip (signature element) ---------- */
  .logfeed{
    border-top: 1px solid var(--line);
    background: #0D1218;
    overflow: hidden;
    white-space: nowrap;
    padding: 10px 0;
  }
  .logfeed-track{
    display:inline-block;
    font-family:'IBM Plex Mono', monospace;
    font-size: 12px;
    color: var(--muted);
    animation: scroll-log 42s linear infinite;
  }
  .logfeed-track span{ margin-right: 48px; }
  .logfeed-track .tag-info{ color: var(--teal); }
  .logfeed-track .tag-warn{ color: var(--amber); }
  .logfeed-track .tag-crit{ color: var(--red); }
  @keyframes scroll-log{ from{ transform: translateX(0);} to{ transform: translateX(-50%);} }
  @media (prefers-reduced-motion: reduce){ .logfeed-track{ animation: none; } }

  /* ---------- section shell ---------- */
  section{ padding: 72px 0; }
  .section-head{ margin-bottom: 32px; }
  .section-head .eyebrow{ margin-bottom: 10px; }
  h2{
    font-family:'IBM Plex Sans', sans-serif;
    font-weight: 700;
    font-size: 26px;
    margin: 0;
  }
  .section-sub{ color: var(--muted); font-size: 14.5px; margin-top: 8px; max-width: 560px; }

  /* ---------- about ---------- */
  .about-text{ color: var(--muted); font-size: 15px; max-width: 700px; }
  .about-text strong{ color: var(--text); }

  /* ---------- case files (projects) ---------- */
  .cases{ display:flex; flex-direction: column; gap: 14px; }
  .case{
    border:1px solid var(--line);
    background: var(--panel);
    border-radius: var(--radius);
    padding: 22px 24px;
    display:grid;
    grid-template-columns: 74px 1fr auto;
    gap: 20px;
    align-items:start;
    transition: border-color 0.15s ease, background 0.15s ease;
    text-decoration:none;
  }
  .case:hover{ border-color: rgba(79,209,197,0.5); background: var(--panel-2); }
  .case-sev{
    font-family:'IBM Plex Mono', monospace;
    font-size: 11px;
    text-align:center;
    padding: 5px 0;
    border-radius: 999px;
    height: fit-content;
    letter-spacing: 0.04em;
  }
  .sev-high{ color: var(--red); border:1px solid rgba(229,72,77,0.4); background: rgba(229,72,77,0.08); }
  .sev-med{ color: var(--amber); border:1px solid rgba(242,169,59,0.4); background: rgba(242,169,59,0.08); }

  .case-title{ font-size: 16.5px; font-weight: 600; margin: 0 0 6px; }
  .case-desc{ font-size: 14px; color: var(--muted); margin: 0 0 12px; max-width: 560px; }
  .case-tags{ display:flex; flex-wrap:wrap; gap: 6px; }
  .case-tags span{
    font-family:'IBM Plex Mono', monospace;
    font-size: 10.5px;
    color: var(--muted);
    border: 1px solid var(--line);
    padding: 3px 8px;
    border-radius: var(--radius);
  }
  .case-status{
    font-family:'IBM Plex Mono', monospace;
    font-size: 11px;
    color: var(--teal);
    text-align:right;
    white-space: nowrap;
  }
  @media (max-width: 640px){
    .case{ grid-template-columns: 1fr; }
    .case-status{ text-align:left; }
  }

  /* ---------- skills ---------- */
  .skills-grid{
    display:grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1px;
    background: var(--line);
    border: 1px solid var(--line);
    border-radius: var(--radius);
    overflow: hidden;
  }
  @media (max-width: 640px){ .skills-grid{ grid-template-columns: 1fr; } }
  .skill-cell{ background: var(--panel); padding: 20px 22px; }
  .skill-cell h3{
    font-family:'IBM Plex Mono', monospace;
    font-size: 11.5px;
    text-transform: uppercase;
    letter-spacing: 0.06em;
    color: var(--amber);
    margin: 0 0 10px;
  }
  .skill-cell p{ margin:0; font-size: 14px; color: var(--text); }

  /* ---------- certs ---------- */
  .certs{ display:flex; flex-wrap:wrap; gap: 10px; }
  .cert{
    display:flex; align-items:center; gap:8px;
    border:1px solid var(--line);
    background: var(--panel);
    padding: 10px 16px;
    border-radius: var(--radius);
    font-size: 13.5px;
  }
  .cert .dot{ width:7px; height:7px; border-radius:50%; }
  .dot-done{ background: var(--teal); }
  .dot-progress{ background: var(--amber); }
  .cert small{ display:block; color: var(--muted); font-family:'IBM Plex Mono', monospace; font-size: 10px; margin-top: 1px; }

  /* ---------- footer / contact ---------- */
  footer{
    border-top: 1px solid var(--line);
    padding: 48px 0 40px;
  }
  .footer-grid{ display:flex; justify-content:space-between; align-items:flex-end; flex-wrap:wrap; gap: 24px; }
  .footer-cta h2{ margin-bottom: 10px; }
  .footer-cta p{ color: var(--muted); font-size: 14px; margin: 0; max-width: 420px; }
  .btn{
    display:inline-flex; align-items:center; gap:8px;
    background: var(--teal); color: #06110F;
    font-weight: 600; font-size: 14px;
    padding: 12px 20px;
    border-radius: var(--radius);
    text-decoration:none;
    border: none;
    cursor: pointer;
  }
  .btn:hover{ background: #6fe0d5; }
  .footer-meta{ font-family:'IBM Plex Mono', monospace; font-size: 11.5px; color: var(--muted); }
</style>
</head>
<body>

  <div class="topbar">
    <div class="wrap">
      <div class="brand">OLALEYE_ISMAIL<span> // soc-analyst</span></div>
      <nav class="topnav">
        <a href="#cases">Case Files</a>
        <a href="#skills">Skills</a>
        <a href="#certs">Certifications</a>
        <a href="#contact">Contact</a>
      </nav>
    </div>
  </div>

  <div class="hero">
    <div class="wrap">
      <div class="ticket">
        <div class="ticket-head">
          <span><span class="id">CASE #SOC-2026-001</span> · PROFILE</span>
          <span class="status-pill">ANALYST ACTIVE</span>
        </div>
        <div class="ticket-body">
          <p class="eyebrow">Security Operations Center</p>
          <h1>Olaleye Ismail</h1>
          <p class="role-line"><strong>SOC Analyst</strong> — security monitoring, incident response, threat intelligence, and vulnerability management. A structured SOC training programme (Amdari) layered on top of a decade in IT support and access administration.</p>

          <div class="meta-grid">
            <div class="meta-cell">
              <div class="k">Location</div>
              <div class="v">Grimsby, UK</div>
            </div>
            <div class="meta-cell">
              <div class="k">Email</div>
              <div class="v"><a href="mailto:ismailniima@gmail.com">ismailniima@gmail.com</a></div>
            </div>
            <div class="meta-cell">
              <div class="k">LinkedIn</div>
              <div class="v"><a href="#" id="linkedin-link">Connect on LinkedIn →</a></div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="logfeed" aria-hidden="true">
      <div class="logfeed-track">
        <span class="tag-warn">[WARN]</span><span>185.220.x.x — repeated auth failures, VPN_Server_2</span>
        <span class="tag-info">[INFO]</span><span>MFA enforced across all remote access points</span>
        <span class="tag-crit">[FLAG]</span><span>IOC matched — AbuseIPDB, VirusTotal, Cisco Talos</span>
        <span class="tag-info">[INFO]</span><span>YARA rule deployed — detection coverage improved</span>
        <span class="tag-warn">[WARN]</span><span>Suspicious SSH access attempt — profiled via MISP</span>
        <span class="tag-info">[INFO]</span><span>Threat hunt complete — 0 lateral movement detected</span>
        <span class="tag-warn">[WARN]</span><span>185.220.x.x — repeated auth failures, VPN_Server_2</span>
        <span class="tag-info">[INFO]</span><span>MFA enforced across all remote access points</span>
        <span class="tag-crit">[FLAG]</span><span>IOC matched — AbuseIPDB, VirusTotal, Cisco Talos</span>
        <span class="tag-info">[INFO]</span><span>YARA rule deployed — detection coverage improved</span>
        <span class="tag-warn">[WARN]</span><span>Suspicious SSH access attempt — profiled via MISP</span>
        <span class="tag-info">[INFO]</span><span>Threat hunt complete — 0 lateral movement detected</span>
      </div>
    </div>
  </div>

  <div class="wrap">

    <section id="about">
      <div class="section-head">
        <p class="eyebrow">01 — Summary</p>
        <h2>Background</h2>
      </div>
      <p class="about-text">
        Over a decade in IT support and access administration, now applied to security operations. Comfortable across the full incident lifecycle — from triaging alerts and correlating logs in <strong>Sentinel, Splunk, and QRadar</strong>, to validating indicators against threat intel platforms, to writing detection logic and closing out remediation. Each case file below is a real investigation carried out during a structured SOC training programme, written up the way it would be reported in a live SOC.
      </p>
    </section>

    <section id="cases">
      <div class="section-head">
        <p class="eyebrow">02 — Investigations</p>
        <h2>Case Files</h2>
        <p class="section-sub">Simulated enterprise environment — Amdari SOC Programme. Click a case to read the full incident report.</p>
      </div>

      <div class="cases">
        <a class="case" href="https://github.com/ismailniima-netizen/Olaleye-ismail/blob/main/soc-vpn-bruteforce.md">
          <div class="case-sev sev-high">HIGH</div>
          <div>
            <p class="case-title">Brute-Force VPN Attack Analysis &amp; Remediation</p>
            <p class="case-desc">Detected and contained a brute-force attack against VPN infrastructure before it led to a breach — zero data loss. Correlated logs, validated attacker IPs across three threat intel platforms, and rolled out MFA org-wide within 24 hours.</p>
            <div class="case-tags"><span>SIEM</span><span>VirusTotal</span><span>AbuseIPDB</span><span>Cisco Talos</span><span>MFA</span></div>
          </div>
          <div class="case-status">RESOLVED →</div>
        </a>

        <a class="case" href="https://github.com/ismailniima-netizen/Olaleye-ismail/blob/main/soc-phishing-zenith.md">
          <div class="case-sev sev-med">MEDIUM</div>
          <div>
            <p class="case-title">Phishing Threat Analysis — Zenith Solutions</p>
            <p class="case-desc">Analysed phishing campaign artefacts to determine scope of targeting and business impact, informing containment and user awareness response.</p>
            <div class="case-tags"><span>Email Forensics</span><span>IOC Extraction</span><span>MITRE ATT&amp;CK</span></div>
          </div>
          <div class="case-status">RESOLVED →</div>
        </a>

        <a class="case" href="https://github.com/ismailniima-netizen/Olaleye-ismail/blob/main/soc-yara-aegisledger.md">
          <div class="case-sev sev-med">MEDIUM</div>
          <div>
            <p class="case-title">Threat Intel Investigation &amp; YARA Rule Development — AegisLedger</p>
            <p class="case-desc">Investigated an active threat and built custom YARA rules to close a gap in malware detection coverage.</p>
            <div class="case-tags"><span>YARA</span><span>Threat Intel</span><span>Malware Analysis</span></div>
          </div>
          <div class="case-status">RESOLVED →</div>
        </a>

        <a class="case" href="https://github.com/ismailniima-netizen/Olaleye-ismail/blob/main/soc-threat-hunting.md">
          <div class="case-sev sev-med">MEDIUM</div>
          <div>
            <p class="case-title">Autonomous Threat Hunting in a Modern Enterprise Environment</p>
            <p class="case-desc">Ran proactive, hypothesis-driven threat hunts across enterprise telemetry to surface activity standard alerting would have missed.</p>
            <div class="case-tags"><span>Threat Hunting</span><span>MITRE ATT&amp;CK</span><span>Telemetry</span></div>
          </div>
          <div class="case-status">RESOLVED →</div>
        </a>

        <a class="case" href="https://github.com/ismailniima-netizen/Olaleye-ismail/blob/main/soc-ssh-misp.md">
          <div class="case-sev sev-high">HIGH</div>
          <div>
            <p class="case-title">Unauthorised SSH Access Detection &amp; Threat Actor Profiling</p>
            <p class="case-desc">Built detection logic for unauthorised SSH access attempts and used MISP to profile the threat actor behind them.</p>
            <div class="case-tags"><span>SSH</span><span>MISP</span><span>Actor Profiling</span></div>
          </div>
          <div class="case-status">RESOLVED →</div>
        </a>

        <a class="case" href="https://github.com/ismailniima-netizen/Olaleye-ismail/blob/main/grc-patch-automation.md">
          <div class="case-sev sev-med">MEDIUM</div>
          <div>
            <p class="case-title">Automating Patch Deployment for Healthcare Web Services</p>
            <p class="case-desc">Designed an automated patch deployment process to shrink exposure windows on web-facing systems, supporting vulnerability management and compliance obligations.</p>
            <div class="case-tags"><span>GRC</span><span>Vulnerability Mgmt</span><span>Healthcare / DSPT</span></div>
          </div>
          <div class="case-status">CLOSED →</div>
        </a>
      </div>
    </section>

    <section id="skills">
      <div class="section-head">
        <p class="eyebrow">03 — Toolset</p>
        <h2>Core Skills</h2>
      </div>
      <div class="skills-grid">
        <div class="skill-cell">
          <h3>SIEM &amp; Monitoring</h3>
          <p>Microsoft Sentinel, Splunk, QRadar, log analysis, correlation rule tuning</p>
        </div>
        <div class="skill-cell">
          <h3>Endpoint &amp; Network Security</h3>
          <p>Microsoft Defender for Endpoint, EDR, Wireshark</p>
        </div>
        <div class="skill-cell">
          <h3>Vulnerability &amp; Risk</h3>
          <p>Nessus, vulnerability management, risk assessment</p>
        </div>
        <div class="skill-cell">
          <h3>Frameworks &amp; Compliance</h3>
          <p>MITRE ATT&amp;CK, NIST CSF, ISO 27001, CIS Controls, GDPR, DSPT</p>
        </div>
        <div class="skill-cell">
          <h3>Tools</h3>
          <p>Kali Linux, Metasploit, CyberChef, MISP, Active Directory</p>
        </div>
      </div>
    </section>

    <section id="certs">
      <div class="section-head">
        <p class="eyebrow">04 — Credentials</p>
        <h2>Certifications</h2>
      </div>
      <div class="certs">
        <div class="cert"><span class="dot dot-done"></span><div>CompTIA Security+<small>COMPLETE</small></div></div>
        <div class="cert"><span class="dot dot-done"></span><div>AZ-900 — Azure Fundamentals<small>COMPLETE</small></div></div>
        <div class="cert"><span class="dot dot-progress"></span><div>CompTIA CySA+<small>SCHEDULED</small></div></div>
        <div class="cert"><span class="dot dot-progress"></span><div>CISM<small>IN PROGRESS</small></div></div>
      </div>
    </section>

  </div>

  <footer id="contact">
    <div class="wrap">
      <div class="footer-grid">
        <div class="footer-cta">
          <h2>Let's talk</h2>
          <p>Open to SOC Analyst and Tier 1/2 security roles. Reach out directly or connect on LinkedIn.</p>
        </div>
        <a class="btn" href="mailto:ismailniima@gmail.com">Email me →</a>
      </div>
      <p class="footer-meta" style="margin-top:32px;">GRIMSBY, UK · CASE LOG CLOSED · © 2026</p>
    </div>
  </footer>

</body>
</html>
