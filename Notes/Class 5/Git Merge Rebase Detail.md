🌿 Git Merge (Overview)

✅ Purpose

Do branches ke changes ko combine (jorna).

📌 Simple Roman Urdu

> Git Merge ka matlab hai "2 developers ka kaam aik saath jorna." Git dono branches ke changes combine karta hai aur zarurat par Merge Commit banata hai.

💼 Real-Time Office Example

* main = Production branch (company ki live application)
* feature-login = Abdul login feature bana raha hai.

Abdul ka kaam complete ho gaya, testing bhi ho gayi.

Ab company chahti hai ke login feature live application mein aa jaye.

Command:

```bash
git checkout main
git merge feature-login
```

👉 Matlab: "Abdul ka feature ab production ka hissa ban gaya."

---

😂 Funny Example

> Ammi ne daal banayi 🍲 aur Abbu naan le aaye 🫓.
>
> Merge matlab dono ko ek hi table par rakh kar dinner complete kar diya. 😄

Ya

> Shaadi mein dulha aur dulhan alag aaye the.
>
> Merge ke baad dono ek hi stage par. 💍😂

---

🌿 Git Rebase (Overview)

✅ Purpose

Apni branch ko latest branch ke upar shift karna taake history clean aur seedhi rahe.

📌 Simple Roman Urdu

> Git Rebase ka matlab hai "Latest updates le kar apni branch ko unke baad rakhna." Git tumhare commits ko uthata hai aur latest branch ke baad dobara laga deta hai.

---

💼 Real-Time Office Example

Abdul `feature-login` par kaam kar raha tha.

Isi beech Ali ne `main` branch mein Home Page add kar diya.

Ab Abdul bhi latest code lena chahta hai.

Command:

```bash
git checkout feature-login
git rebase main
```

👉 Matlab:

> "Main pehle Ali ke latest changes le leta hoon, phir apna login feature unke upar rakh deta hoon."

Is se history clean rehti hai.

---

😂 Funny Example

> School assembly mein line lagi hui hai.
>
> Principal bolte hain:
> "Pehle seniors, phir juniors."
>
> Rebase matlab tum apni purani jagah chhor kar latest line ke end mein kharay ho jao. 🚶😂

Ya

> Pizza delivery boy pehle doosri society deliver karta hai. 🍕
>
> Phir tumhara order deliver karta hai.
>
> Rebase bhi commits ko isi tarah latest ke baad arrange karta hai. 😄

---

🎯 Interview Answer (30 Seconds)

Git Merge

> "Git Merge ka use do branches ke changes combine karne ke liye hota hai. Ye original history ko preserve karta hai aur usually Merge Commit create karta hai."

Git Rebase

> "Git Rebase ka use apni branch ko latest branch ke upar move karne ke liye hota hai. Ye commits ko replay karta hai aur history ko clean aur linear bana deta hai."

---

🧠 Super Easy Trick

* 🤝 Merge = "Shaadi karwa do (2 branches ek ho gayi)."
* 🚶 Rebase = "Queue mein latest position le lo (history clean)."
