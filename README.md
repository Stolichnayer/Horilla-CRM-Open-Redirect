# Open Redirect Vulnerability in Horilla CRM (≤ 1.0.2)
<table>
  <tr>
    <td width="150" rowspan="2">
      <a href="https://www.horilla.com/" target="_blank">
        <img src="https://avatars.githubusercontent.com/u/131998600?v=4" alt="Horilla CRM Logo" width="120"/>
      </a>
    </td>
    <td>
      <h1>Horilla CRM</h1>
      <h3> A free and open source CRM software.</h3>
    </td>
  </tr>
  <tr>
    <td>
      <table>
        <tr>
          <td>
            🔗 <a href="https://github.com/horilla-opensource/horilla-crm" target="_blank">Horilla CRM Github Repository</span></a>
          </td>
          <td style="padding-left: 15px;">
            🚀 <a href="https://github.com/horilla-opensource/horilla-crm/releases/tag/1.0.3" target="_blank"> Patched Version (v1.0.3) </span></a>
          </td>
        </tr>
      </table>
    </td>
  </tr>
</table>

## 📜 Description
Horilla CRM ≤ v1.0.2 is affected by an Open Redirect vulnerability in the `/generics/search/` endpoint within the global search functionality. The application improperly trusts the `prev_url` query parameter to determine the post-search redirect destination.

By supplying a crafted external URL in the `prev_url` parameter (e.g., `?section=home&prev_url=https://attacker.com`), an attacker can cause the application to redirect users to an arbitrary domain. This behavior enables phishing and social engineering attacks, where users may believe they are navigating within a legitimate Horilla CRM instance but are instead redirected to a malicious website controlled by the attacker.

## 🔍 Affected Versions

| Status       | Version         |
|--------------|-----------------|
| 🔴 Vulnerable |  ≤ `1.0.2`      |
| 🟢  Fixed     |  &nbsp;&nbsp;`1.0.3`      |   

## 🛠️ Steps to Reproduce

#### 1️⃣ Visit the following URL:
```
http://YOUR_HORILLA_DOMAIN/generics/search/?section=home&prev_url=https://google.com
```

<img src="/url.png" >

#### 2️⃣ The application redirects the user to https://google.com:

<img src="/redirect.png">

## ⚠️ Disclaimer
This project is intended for **educational and ethical research purposes only**. Unauthorized testing on systems without explicit permission is illegal. Use responsibly and only on systems you own or have permission to test.

## 🧑‍💻 Discovery

This vulnerability was discovered by **Alex Perrakis** (Stolichnayer).

## 🔗 References:
- [Horilla CRM Github Repository](https://github.com/horilla-opensource/horilla-crm)
- [Patched Version (v1.0.3)](https://github.com/horilla-opensource/horilla-crm/releases/tag/1.0.3)
- [Fix Commit](https://github.com/horilla-opensource/horilla-crm/commit/730b5a44ff060916780c44a4bdbc8ced70a2cd27)
