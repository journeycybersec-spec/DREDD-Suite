# DREDD-Suite
Dredd ( Data Reconnaissance, Enumeration & Digital Discovery ) is a modular OSINT and DFIR toolkit featuring case management, hash analysis, SSL inspection, LinkedIn employee scraping, username enumeration, and WHOIS intelligence. A unified launcher provides a streamlined, professional workflow for investigators.

<h1 align="center">DreddSuite – Modular OSINT & DFIR Toolkit</h1>

<p>
DreddSuite ( Data Reconnaissance, Enumeration & Digital Discovery ) is a modular, launcher-driven toolkit for OSINT investigations, digital forensics, SSL/TLS inspection, hash analysis, LinkedIn employee enumeration, username reconnaissance, and case management.  
All modules run through a unified CrowsNest-themed launcher for a clean and consistent workflow.
</p>

<hr>

<h2>📦 Included Modules</h2>

<pre>
CaseCreation1.0
HashAndSeek1.0
LinkedInScrape1.0
SSLChecker1.0
SocialCrawl1.0
Whoislookup1.0
</pre>

<p>
Each module contains a primary Python script automatically detected and executed by <code>DreddSuiteLauncher.py</code>.
</p>

<hr>

<h2>🔷 1. CaseCreation1.0</h2>

<p><strong>Purpose:</strong> A structured case-management system for OSINT investigations.  
Creates, manages, and expands case folders in <code>CaseCreation1.0/&lt;project_name&gt;/</code>.</p>

<h3>Key Features</h3>
<ul>
<li>Create a new case:<br>
<code>python3 profile.py init --project &lt;name&gt;</code></li>

<li>Run a guided case wizard:<br>
<code>python3 profile.py wizard --project &lt;name&gt;</code></li>

<li>Open the project folder directly from the launcher.</li>

<li>Generate AI prompts for a case using <code>osint_ext.ai_cli</code>:<br>
<code>python3 -m osint_ext.ai_cli prompt --project &lt;name&gt;</code></li>
</ul>

<h3>Output Location</h3>
<pre>
CaseCreation1.0/&lt;project&gt;/exports/prompts/
</pre>

<hr>

<h2>🔷 2. HashAndSeek1.0</h2>

<p><strong>Purpose:</strong> A digital forensics tool for hashing and hash-based file searching.</p>

<h3>Key Features</h3>
<ul>
<li>Hash a file silently:<br>
<code>python3 HashAndSeek.py --auto-hash &lt;path&gt; --algo sha256</code></li>

<li>Search directories for matching hash values:<br>
<code>python3 HashAndSeek.py --auto-search &lt;hash&gt; --directory &lt;path&gt;</code></li>

<li>Outputs clean, forensic-style blocks:
<pre>
File: example.bin
Algorithm: sha256
Hash: 9f0f0a8...
</pre></li>

<li>No banners, loops, or menus in launcher mode.</li>
</ul>

<p><strong>Dependencies:</strong> None (stdlib only).</p>

<hr>

<h2>🔷 3. LinkedInScrape1.0</h2>

<p><strong>Purpose:</strong> Scrape LinkedIn employee profiles via SearXNG without APIs or browser automation.</p>

<h3>Key Features</h3>
<ul>
<li>Queries your private SearXNG instance using LinkedIn OSINT dorks</li>
<li>Parses HTML search results</li>
<li>Extracts and deduplicates <code>linkedin.com/in/</code> URLs</li>
<li>Exports results to CSV and JSON</li>
<li>No Selenium, no logins, no browser automation</li>
</ul>

<p><strong>Dependencies:</strong></p>
<ul>
<li>requests</li>
<li>beautifulsoup4</li>
</ul>

<hr>

<h2>🔷 4. SSLChecker1.0</h2>

<p><strong>Purpose:</strong> Analyze SSL/TLS certificates for potential security issues.</p>

<h3>Checks Performed</h3>
<ul>
<li>Certificate validity</li>
<li>Self-signed status</li>
<li>Domain mismatch</li>
<li>Forward secrecy</li>
<li>Protocol strength</li>
<li>HSTS status</li>
<li>Certificate chain validation</li>
</ul>

<h3>Example Output</h3>
<pre>
Certificate: ✅ Valid
Self-Signed: ❌ Self-signed
Forward Secrecy: ❌ Not supported
HSTS: ❌ Not enabled
</pre>

<p><strong>Dependency:</strong> cryptography</p>

<hr>

<h2>🔷 5. SocialCrawl1.0</h2>

<p><strong>Purpose:</strong> Enumerate usernames across many sites using async HTTP enumeration.</p>

<h3>Key Features</h3>
<ul>
<li>Search for username availability across multiple platforms</li>
<li>Uses <code>sites.json</code> for site definitions</li>
<li>Optional alias detection</li>
<li>Optional HTML report generation</li>
<li>Optional stealth mode (rotating user agents)</li>
<li>Fast async enumeration with <code>httpx</code></li>
</ul>

<p><strong>Dependencies:</strong></p>
<ul>
<li>httpx</li>
<li>beautifulsoup4</li>
</ul>

<hr>

<h2>🔷 6. Whoislookup1.0</h2>

<p><strong>Purpose:</strong> Perform WHOIS lookups for domains and IPs with clean formatting.</p>

<h3>Key Features</h3>
<ul>
<li>Domain WHOIS lookup</li>
<li>IP WHOIS lookup</li>
<li>Structured output (registrant, admin, creation date, expiration date, etc.)</li>
</ul>

<p><strong>Dependency:</strong> python-whois</p>

<hr>

<h2>🔷 7. DreddSuiteLauncher.py</h2>

<p><strong>Purpose:</strong> The unified command launcher for all modules.</p>

<h3>Key Features</h3>
<ul>
<li>Auto-detects module folders and entry scripts</li>
<li>CrowsNest blue-themed UI</li>
<li>Per-module submenus:
  <ul>
    <li>Case Creation</li>
    <li>HashAndSeek</li>
    <li>LinkedInScrape</li>
    <li>SSLChecker</li>
    <li>SocialCrawl</li>
    <li>WhoisLookup</li>
  </ul>
</li>
<li>Graceful fallback when imports fail</li>
<li>Automatic module routing</li>
</ul>

<hr>

<h2>📦 Installation</h2>

<p>Install all dependencies with:</p>

<pre><code>pip install -r requirements.txt
</code></pre>

<p>Run the suite:</p>

<pre><code>python3 DreddSuiteLauncher.py
</code></pre>

<hr>

<h2>📁 requirements.txt</h2>

<pre>
beautifulsoup4
cryptography
fastapi
httpx
PyYAML
requests
python-whois
</pre>

<hr>

<h2>📁 Project Structure</h2>

<pre>
DreddSuite/
│
├── DreddSuiteLauncher.py
├── requirements.txt
│
├── CaseCreation1.0/
│   ├── profile.py
│   ├── osint_ext/
│   └── <project folders>
│
├── HashAndSeek1.0/
│   └── HashAndSeek.py
│
├── LinkedInScrape1.0/
│   └── linkedin_enum.py
│
├── SSLChecker1.0/
│   └── sslcheck.py
│
├── SocialCrawl1.0/
│   ├── socialcrawl.py
│   ├── alias_engine.py
│   └── sites.json
│
└── Whoislookup1.0/
    └── whois_lookup.py
</pre>

<hr>

<h2>🛡 License</h2>
<p>DreddSuite Non-Commercial License (DNCL-1.0)</p>

<hr>

<h2>🎯 Summary</h2>

<p>
DreddSuite is a complete OSINT and DFIR toolkit with modular architecture, automatic launcher integration, clean output, and only minimal Python dependencies.  
It is ready for production use, GitHub release, and further expansion.
</p>
