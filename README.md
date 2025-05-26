# 🚆 SRB Voz – Selenium Test Automation Project

Automatizacija sajta [SRB Voz](https://webapi1.srbvoz.rs/ekarta/app/#!/home) korišćenjem **Selenium WebDriver**, **Java**, **TestNG**, i **Page Object Model (POM)**.  
Ovaj projekat je deo mog QA portfolija i demonstrira rad sa realnom web aplikacijom – simulirajući korisničku pretragu voza na sajtu SRB Voz.

---

## 🎯 Cilj projekta

Cilj je bio automatizovati sledeće korake kao deo korisničkog scenarija:

1. Odabrati stanicu polaska (Od)
2. Odabrati stanicu dolaska (Do)
3. Odabrati datum i vreme
4. Kliknuti na dugme „Pretraga“
5. Verifikovati da se stranica rezultata prikazuje i da su uneti podaci ispravno preneseni

---

## 📸 Screenshots (Primer forme)

> 🖼 Ovde možeš dodati screenshotove (npr. `screenshots/form.png`, `screenshots/results.png`) da bi prikazao izgled forme i rezultat stranice.

---

## 🧪 Pokrivene funkcionalnosti

- ✔ Dropdown selekcija stanica
- ✔ Izbor datuma i vremena pomoću kalendara
- ✔ Klik na dugme za pretragu
- ✔ Provera da su rezultati prikazani
- ✔ Verifikacija URL-a i preuzetih parametara
- ✔ Negativni test – ako se ne unesu svi podaci

---

## 📁 Struktura projekta

srbvozPOM/
│
├── base/ # Osnovna klasa za setup/teardown
│ └── BaseTest.java
│
├── pages/ # Page Object Model klase
│ ├── HomePage.java # Elementi i akcije na početnoj stranici
│ └── ResultsPage.java # Verifikacija na stranici rezultata
│
├── tests/ # TestNG test klasa
│ └── VozTest.java
│
├── utils/ # Utility klase (DataProvider, waitovi)
│ └── TestData.java
│
├── screenshots/ # (opciono) Slike forme i rezultata
│
├── README.md # Dokumentacija projekta


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

3. Pokreni VozTest.java kao TestNG test:

    Desni klik → Run VozTest

    Ili pokreni sve testove preko testng.xml fajla (ako postoji)


💡 Primer test podataka

@DataProvider(name = "stationData")
public Object[][] stationData() {
    return new Object[][]{
        {"Novi Sad", "Beograd Centar", "27.05.2025."},
        {"Subotica", "Niš", "28.05.2025."}
    };
}

✅ Primer test case-a (VozTest.java)

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

Ako se klikne na "Pretraga" bez unosa obaveznih polja, sistem prikazuje upozorenje,
što se može testirati kao negativan slučaj.
✍️ Autor

Nikola Medan
📍 Novi Sad, Srbija
📧 nikolamedan1991@gmail.com
📱 +381 64 562 9952
🔗 LinkedIn
🔗 GitHub
