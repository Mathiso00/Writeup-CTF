# Writeup CTF

> A collection of CTF write-ups, solutions, and methodologies from various cybersecurity challenges.

## 🏆 CTF Profiles

[![HackTheBox](https://img.shields.io/badge/HackTheBox-111927?style=for-the-badge&logo=hackthebox&logoColor=9FEF00)](https://app.hackthebox.com/profile/745704)
[![TryHackMe](https://img.shields.io/badge/TryHackMe-1A1A1A?style=for-the-badge&logo=tryhackme&logoColor=white)](https://tryhackme.com/p/Mathiso0)
[![RootMe](https://img.shields.io/badge/RootMe-000000?style=for-the-badge&logo=rootme&logoColor=white)](https://www.root-me.org/Mathiso)
[![CTFTime](https://img.shields.io/badge/CTFTime-1A1A1A?style=for-the-badge&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4NCjxzdmcgdmVyc2lvbj0iMS4xIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB4PSIwcHgiIHk9IjBweCINCgkgdmlld0JveD0iMCAwIDI4My40NiA3OS4zMyIgc3R5bGU9ImVuYWJsZS1iYWNrZ3JvdW5kOm5ldyAwIDAgMjgzLjQ2IDc5LjMzOyIgeG1sOnNwYWNlPSJwcmVzZXJ2ZSI+DQo8c3R5bGUgdHlwZT0idGV4dC9jc3MiPg0KCS5zdDB7ZmlsbDojRTMwMDBCO30NCgkuc3Qxe2ZpbGw6I0ZGRkZGRjt9DQo8L3N0eWxlPg0KPGcgaWQ9IkxheWVyXzEiPg0KCTxwb2x5Z29uIGNsYXNzPSJzdDAiIHBvaW50cz0iMCw3OS41MiAxNTQuMzYsNzkuNTIgMjgzLjQ2LDc5LjUyIDI4My40NiwwLjE5IDAsMC4xOSAzMy4yMyw0MC4yOSAJIi8+DQoJPHBvbHlnb24gY2xhc3M9InN0MSIgcG9pbnRzPSI2MS45Miw1Ny45MiA4MC40Nyw1Ny45MiA4MC40Nyw1MS42OCA3NC4wNiw1MS42OCA3NC4wNiw1MS42OCA2OS4zLDUxLjY4IDY5LjMsMjcuOSA3NC4wNiwyNy45IA0KCQk3NC4wNiwyNy45IDgwLjQ3LDI3LjkgODAuNDcsMjEuMDIgNjEuOTIsMjEuMDIgCSIvPg0KCTxwb2x5Z29uIGNsYXNzPSJzdDEiIHBvaW50cz0iODYuMzIsMjguMTEgOTEuNiwyOC4xMSA5MS42LDU3LjkyIDk4Ljk4LDU3LjkyIDk4Ljk4LDI4LjExIDEwNC4yNSwyOC4xMSAxMDQuMjUsMjEuMDIgODYuMzIsMjEuMDIgCQ0KCQkiLz4NCgk8cG9seWdvbiBjbGFzcz0ic3QxIiBwb2ludHM9IjExMC4zLDU3LjYzIDExNy42OSw1Ny42MyAxMTcuNjksNDIuODggMTI2LjksNDIuODggMTI2LjksMzcuMTUgMTE3LjY5LDM3LjE1IDExNy42OSwyNy45IA0KCQkxMjkuMDIsMjcuOSAxMjkuMDIsMjEuMDIgMTEwLjMsMjAuNzMgCSIvPg0KCTxwb2x5Z29uIGNsYXNzPSJzdDEiIHBvaW50cz0iMTgyLjc5LDI1LjM0IDE4OC4zMywyNS4zNCAxODguMzMsNTcuOTIgMTkyLjc2LDU3LjkyIDE5Mi43NiwyNS4zNCAxOTguMjksMjUuMzQgMTk4LjI5LDIxLjAyIA0KCQkxODIuNzksMjEuMDIgCSIvPg0KCTxyZWN0IHg9IjIwMy4zMSIgeT0iMjEuMDIiIGNsYXNzPSJzdDEiIHdpZHRoPSI0LjQzIiBoZWlnaHQ9IjM2LjkiLz4NCgk8cG9seWdvbiBjbGFzcz0ic3QxIiBwb2ludHM9IjIyNC4xNiwzNC41MiAyMTguODksMjEuMDIgMjE0LjUyLDIxLjAyIDIxNC41Miw1Ny45MiAyMTguODksNTcuOTIgMjE4Ljg5LDMxLjc4IDIyNC4xNiw0NS4wNiANCgkJMjI5LjQzLDMxLjc4IDIyOS40Myw1Ny45MiAyMzMuODEsNTcuOTIgMjMzLjgxLDIxLjAyIDIyOS40MywyMS4wMiAJIi8+DQoJPHBvbHlnb24gY2xhc3M9InN0MSIgcG9pbnRzPSIyNDQuNzcsNTMuNiAyNDQuNzcsNDEuNTggMjUyLjE1LDQxLjU4IDI1Mi4xNSwzNy4yNiAyNDQuNzcsMzcuMjYgMjQ0Ljc3LDI1LjM0IDI1Ni44OCwyNS4zNCANCgkJMjU4LjA0LDIxLjAyIDI0MC4zNCwyMS4wMiAyNDAuMzQsNTcuOTIgMjU3Ljg1LDU3LjkyIDI1Ni42OSw1My42IAkiLz4NCgk8cGF0aCBjbGFzcz0ic3QxIiBkPSJNMTM1LjU0LDIxLjAydjM2LjloMzkuN3YtMzYuOUgxMzUuNTR6IE0xNjkuODMsNTIuODloLTI4Ljg3VjI2LjA1aDI4Ljg3VjUyLjg5eiIvPg0KCTxwb2x5Z29uIGNsYXNzPSJzdDEiIHBvaW50cz0iMTUzLjkxLDM5LjM4IDE0Ny44LDQ1LjQ4IDE1MS44Myw0OS4wNSAxNjEuMjQsMzkuNjUgMTQ1LjE2LDIzLjU3IDEzOC4xLDIzLjU3IAkiLz4NCjwvZz4NCjwvc3ZnPg0K&logoColor=white&logoWidth=30)](https://ctftime.org/team/231457)

## 📚 CTF Write-ups

### 2025

- <img src="assets/logo_midnight-flag.svg" width="30"> &nbsp; <span style="font-size: 1.4em">[Midnight CTF](2025/Midnight-CTF/README.md)</span>
- <img src="assets/HackTheBoxCTF.svg" width="30"> &nbsp; <span style="font-size: 1.4em">[Cyber Apocalypse CTF](2025/Cyber-Apocalypse-CTF/)</span>
- <img src="assets/PwnMECTF.webp" width="30"> &nbsp; <span style="font-size: 1.4em">[PwnMECTF](2025/PwnMeCTF/)</span>
- <img src="assets/PearlCTF.webp" width="30"> &nbsp; <span style="font-size: 1.4em">[PearlCTF](2025/PearlCTF/)</span>
- <img src="assets/BITSCTF.webp" width="30"> &nbsp; <span style="font-size: 1.4em">[BITSCTF](2025/BITSCTF/)</span>
- <img src="assets/IrisCTF.webp" width="30"> &nbsp; <span style="font-size: 1.4em">[IrisCTF](2025/IrisCTF/)</span>

### 2024

- <img src="assets/EC2.png" width="30"> &nbsp; <span style="font-size: 1.4em">[European Cyber Cup](2024/European-Cyber-Cup/)</span>
- <img src="assets/SpookyCTF.webp" width="30"> &nbsp; <span style="font-size: 1.4em">[SpookyCTF](2024/SpookyCTF/)</span>
- <img src="assets/404CTF.webp" width="30"> &nbsp; <span style="font-size: 1.4em">[404CTF](2024/404CTF/)</span>
- <img src="assets/PlaidCTF.webp" width="30"> &nbsp; <span style="font-size: 1.4em">[PlaidCTF](2024/PlaidCTF/)</span>
### 2023

- <img src="assets/PatriotCTF.webp" width="30"> &nbsp; <span style="font-size: 1.4em">[PatriotCTF](2023/PatriotCTF/)</span>
- <img src="assets/DUCTF.webp" width="30"> &nbsp; <span style="font-size: 1.4em">[DUCTF](2023/DUCTF/)</span>
- <img src="assets/corCTF.webp" width="30"> &nbsp; <span style="font-size: 1.4em">[corCTF](2023/corCTF/)</span>
- <img src="assets/AmateursCTF.png" width="30"> &nbsp; <span style="font-size: 1.4em">[Amateurs CTF](2023/Amateurs-CTF/)</span>
- <img src="assets/HackTheBoxCTF.svg" width="30"> &nbsp; <span style="font-size: 1.4em">[HTB Business CTF](2023/HTB-Business-CTF/)</span>
- <img src="assets/CryptoCTF.png" width="30"> &nbsp; <span style="font-size: 1.4em">[Crypto CTF](2023/Crypto-CTF/)</span>
- <img src="assets/UIUCTF.webp" width="30"> &nbsp; <span style="font-size: 1.4em">[UIUCTF](2023/UIUCTF/)</span>
- <img src="assets/GoogleCTF.gif" width="30"> &nbsp; <span style="font-size: 1.4em">[Google CTF](2023/Google-CTF/)</span>
- <img src="assets/TyphoonconCTF.webp" width="30"> &nbsp; <span style="font-size: 1.4em">[Typhooncon CTF](2023/Typhooncon-CTF/)</span>
- <img src="assets/n00bzctf.webp" width="30"> &nbsp; <span style="font-size: 1.4em">[n00bzCTF 2023](2023/n00bzCTF-2023/)</span>
- <img src="assets/US_Cyber_Open_CTF.webp" width="30"> &nbsp; <span style="font-size: 1.4em">[Season III: US Cyber Open CTF](2023/US-Cyber-Open-CTF/)</span>
- <img src="assets/404CTF.webp" width="30"> &nbsp; <span style="font-size: 1.4em">[404CTF](2023/404CTF/)</span>

## Retired Write-ups

### HackTheBox Machines

- <img src="assets/HackTheBoxCTF.svg" width="30"> &nbsp; <span style="font-size: 1.4em">[Machine Name](retired/htb/machine-name/)</span>
- <img src="assets/HackTheBoxCTF.svg" width="30"> &nbsp; <span style="font-size: 1.4em">[Machine Name](retired/htb/machine-name/)</span>

### HackTheBox Challenges

- <img src="assets/HackTheBoxCTF.svg" width="30"> &nbsp; <span style="font-size: 1.4em">[Challenge Name](retired/htb/challenge-name/)</span>

## 📫 Contact

Feel free to reach out to me through:

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](www.linkedin.com/in/mathis-onillon-39a52819b)
[![Discord](https://img.shields.io/badge/Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.com/users/Mathiso)


