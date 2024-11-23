# Lab 3. Identify design elements
## 1. Subsystem context diagrams
### Hãy vẽ biểu đồ ngữ cảnh của các hệ thống con: BankSystem, PrintService, ProjectManagementDatabase subsystems.

- **BankSystem**

  ![](https://www.planttext.com/api/plantuml/png/h5BBRi8m4BpxArPS2bA3sck442fSSa5L-GB7MHeBFo9xGnkrV5aF_QJ-Gcr2Q08ScuFZp7XcdDtz-VfUUEAEQgqOkuCLRgL148fxZnxU99NW2HrQQge0yDpkaHrfUEQDiqejhQ7uHWUpcMW_vdFuO10ULvlJiV64iGDZqWItBHS8sHCtkqqJt7KGPXr-bW8KM5alQSo3XIXHx5BeTlSGZ6nqI26kcTbQfpb9QoPH7QFQMmvIV9txTbyv-zxyIzPVL2S8GMX8Kj-VQriRIg6mTQwm2-M4AQp2UW9GLyescArIs92JvdNu7xtacnb2n91rhNDqPuUMouDypJLUmeuRKIvjSKLm5HWyN_WGf-C5rJ7SbxBoxBh_euVfz744IJ8VT3UOI8U2kY9xE9R9mrvoDXY3poJfDOprgEZPrVSIloZDmF8MpnPeYZZmlm000F__0m00)


 - **PrintService**
  
  ![](https://www.planttext.com/api/plantuml/png/h971Ri8m38RlVWgBovYq8hXMLOMqNRYXyGGXCskqa5I92rHiJyPXZxHNc5FQGxlheaYnO_jp_EVdzhsEh08tHmi03_X21-C8jLKnKiIpuGeZKo3FRIqNQkzF15qOjweDtjfdxpYT5B0ezDqfIxm2ecp4q3YixwdpH_W2C4w01wK9DziWpex2oOXN59iXqjUdLQUKkP9ckYBzaUDWFQ5tNJs577Sirdk7xnyt9iTc7riPv2WyVsd_WTzd2PiS6nPaqk-Lh6BZNQnC7U6lGhFbOh6QOPQLa-7pf557x7l2H9pFB1iD1QDm0WvFcbIEGcjoR-clVm400F__0m00)
  
  - **ProjectManagementDatabase**
    
  ![](https://www.planttext.com/api/plantuml/png/h5BBIWD14BpFLpIvc0XPz1h24aWk0HKn_a3lR6SpiZkpTFT6W_fb7lmaVy799ZuIT45mJZFLrLHrzRozl4v4aRMfIcDEO4PBvmbiYI8aSEzq1QB457HJHm2pi2RJbk7MLMIHysdmog4iYM4yjhj7ciAZWNWAKh0DCta5tJVq1r-b5N8HzK9EieUREaUbOxBW-W1xDiRvQ6o9bc1-pU6Eh5wYnuAgg3L3nGo5egFv1-tJKoizRPMlcYeZbhvb5raEHx1GThuOZFRM8k72YMxrTbDtIKcJoIR6LK7DuM7pFuBJ0pZkw8PAL1Uyh5mjveSjzCwIvBG7ms7QNizxNG5zqrs4XYsPhZIVakJt1BewaoGzckGlN3CXds-_w3i0003__mC0)
### 2. Analysis class to design element map

| **Analysis Class**             | **Design Element**               |
|--------------------------------|-----------------------------------|
| PayrollController              | PayrollController                |
| IBankSystem                    | IBankSystem                      |
| BankSystem                     | BankSystem                       |
| Paycheck                       | Paycheck                         |
| BankInformation                | BankInformation                  |
| TimecardController             | TimecardController               |
| IProjectManagementDatabase     | IProjectManagementDatabase       |
| ProjectManagementDatabase      | ProjectManagementDatabase        |
| ChargeNumList                  | ChargeNumList                    |
| IPrintService                  | IPrintService                    |
| PrintService                   | PrintService   

### 3. Design element to owning package map

| **Design Element**             | **“Owning” Package**                    |
|--------------------------------|------------------------------------------|
| PayrollController              | Applications::Payroll                   |
| IBankSystem                    | Middleware::FinancialServices           |
| BankSystem                     | Middleware::FinancialServices           |
| Paycheck                       | Business Services::Payroll Artifacts    |
| BankInformation                | Business Services::Financial Artifacts  |
| TimecardController             | Applications::Employee Activities       |
| IProjectManagementDatabase     | Middleware::ProjectManagement           |
| ProjectManagementDatabase      | Middleware::ProjectManagement           |
| ChargeNumList                  | Business Services::Project Artifacts    |
| IPrintService                  | Middleware::PrintServices               |
| PrintService                   | Middleware::PrintServices               |
### 4. Architectural layers and their dependencies
![](https://www.planttext.com/api/plantuml/png/b5HBJiCm4Dtd55OtNUK22A7-GAf4KKMvmE1Csw6s4zbEKGKz6GkEn1LmsgPrx2Q8RFAPD_EUvptbv-jxO2neMqgH97qsmIKfP198iGBu1bPeajC3wmsBGX07IxaoFVQHC7UTYtFOwLo8-djrSG76i5DXd2jRtL4VwljczxqiHBv3P4DkQKkMqCIJNaWY1vr5e_R9HUICiapWEsYC93wG0iK9n0BrbdYJWfH5lGIER3e2jLdiZ4KP20WAmHdcEdz3RcUWtAj4PLl6HxW9M7W5W-7YEd4HkMFuurm-9k8AIisbZahZSk5m8KDeFnjgIuxDNh7FGVWQ-UQQ_BCrNGEgzK_LCjVoaC4E3xgcZDUWL_XKoaSozdBMFdj6SSpscWgJHB5bQNhdPuFTiD9WAz3VQ0sD0rnZMvok6nEVz_OpJVqeThGVeEqvQeeyWRqW91vh9RHsi9OLb0D_QbI7lgghuOVhqMXBhTnU_zLrjC8_JY2ug6fkamDKMVMt-mK00F__0m00)
