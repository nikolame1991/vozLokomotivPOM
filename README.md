# 🚆 SRB Voz – Selenium Test Automation Project

Automatizacija sajta SRB Voz korišćenjem Selenium WebDriver, Java, TestNG i Page Object Model (POM).  
Ovaj projekat je deo mog QA portfolija i demonstrira rad sa realnom web aplikacijom – simulirajući korisničku pretragu voza na sajtu SRB Voz.

---

## 🎯 Cilj projekta

Automatizovati korisnički scenario koji uključuje:

- Odabir stanice polaska (Od)  
- Odabir stanice dolaska (Do)  
- Odabir datuma i vremena putovanja  
- Klik na dugme „Pretraga“  
- Verifikaciju da se stranica rezultata prikazuje i da su podaci ispravno preneseni  

---

## 📸 Screenshots (primer forme)

Ovde možeš dodati screenshotove za bolju vizualizaciju:

![Forma za pretragu](screenshots/form.png)  
![Stranica rezultata](screenshots/results.png)

---

## 🧪 Pokrivene funkcionalnosti

✔ Dropdown selekcija stanica  
✔ Izbor datuma i vremena pomoću kalendara  
✔ Klik na dugme za pretragu  
✔ Provera da su rezultati prikazani  
✔ Verifikacija URL-a i preuzetih parametara  
✔ Negativni test – validacija obaveznih polja  

---

## 📁 Struktura projekta

srbvozPOM/
├── base/ # Osnovna klasa za setup/teardown
│ └── BaseTest.java
├── pages/ # Page Object Model klase
│ ├── HomePage.java # Elementi i akcije na početnoj stranici
│ └── ResultsPage.java # Verifikacija na stranici rezultata
├── tests/ # TestNG test klase
│ └── VozTest.java
├── utils/ # Utility klase (DataProvider, waitovi)
│ └── TestData.java
├── screenshots/ # (opciono) Slike forme i rezultata
└── README.md # Dokumentacija projekta

---

## 🛠️ Tehnologije i alati

- ✅ Java 11+  
- ✅ Selenium WebDriver  
- ✅ TestNG  
- ✅ Page Object Model (POM)  
- ✅ WebDriverWait (Explicit Waits)  
- ✅ Git & GitHub  
- ✅ IntelliJ IDEA  

---

## ▶️ Kako pokrenuti testove

1. Kloniraj repozitorijum:

```bash
git clone https://github.com/nikolame1991/srbvozPOM.git
2. Otvori projekat u svom IDE-u (npr. IntelliJ IDEA)

3. Proveri da li je ChromeDriver pravilno podešen i verzija kompatibilna sa tvojim Chrome browserom

4. Pokreni test klasu VozTest.java kao TestNG test:

5. Desni klik na fajl → Run VozTest

6. Opcionalno, pokreni sve testove preko testng.xml fajla (ako postoji)

💡 Primer test podataka

@DataProvider(name = "stationData") 
public Object[][] stationData() { 
  return new Object[][] { 
    {"Novi Sad", "Beograd Centar", "27.05.2025."}, 
    {"Subotica", "Niš", "28.05.2025."} 
  }; 
}

✅ Primer test case (VozTest.java)

@Test(dataProvider = "stationData", dataProviderClass = TestData.class)
public void testSearchTrains(String from, String to, String date) {
    HomePage home = new HomePage(driver);
    home.selectDepartureStation(from);
    home.selectArrivalStation(to);
    home.selectDate(date);
    home.clickSearchButton();

    ResultsPage results = new ResultsPage(driver);
    Assert.assertTrue(results.isResultDisplayed());
}

❗ Negativni test

Testira se ponašanje sistema ako korisnik pokuša da pretraži bez unosa obaveznih polja.
Sistem bi trebalo da prikaže upozorenje ili poruku o grešci, što je deo negativnih test slučajeva.

✍️ Autor
Nikola Medan
📍 Novi Sad, Srbija
📧 nikolamedan1991@gmail.com
📱 +381 64 562 9952
🔗 LinkedIn
🐙 GitHub
