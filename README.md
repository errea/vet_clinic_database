![](https://img.shields.io/badge/Microverse-blueviolet)

# Vet clinic database: database performance audit

> For this project you need special preparation. As the goal of this project is to solve some performance issue, first we need to introduce those issues. In order to do that, you will populate your database with a significant number of data. [Find project specifications here](https://github.com/microverseinc/curriculum-databases/blob/main/db-structure/vet_clinic_performance_audit.md)

      

<div align="center">

[![View Code](https://img.shields.io/badge/View%20-Code-green)](https://github.com/errea/vet_clinic_database)
[![Github Issues](https://img.shields.io/badge/GitHub-Issues-orange)](https://github.com/errea/vet_clinic_database/issues)
[![GitHub Pull Requests](https://img.shields.io/badge/GitHub-Pull%20Requests-blue)](https://github.com/errea/vet_clinic_database/pull/1)

</div>

## Project description

This project is about building a mobile web application to check a list of metrics (numeric values) that you will create making use of React and Redux and also making a call from an API.

## Database Preparation

Please complete the following steps:

1. Make sure that you have your database set up with the schema and data from your previous projects.
2. Run the following query to add an extra column to the owners table:

``` sql
-- Add an email column to your owners table
ALTER TABLE owners ADD COLUMN email VARCHAR(120);

```
3. Run the following statements to add data to your database (executing them might take a few minutes):
``` sql

-- This will add 3.594.280 visits considering you have 10 animals, 4 vets, and it will use around ~87.000 timestamps (~4min approx.)
INSERT INTO visits (animal_id, vet_id, date_of_visit) SELECT * FROM (SELECT id FROM animals) animal_ids, (SELECT id FROM vets) vets_ids, generate_series('1980-01-01'::timestamp, '2021-01-01', '4 hours') visit_timestamp;

-- This will add 2.500.000 owners with full_name = 'Owner <X>' and email = 'owner_<X>@email.com' (~2min approx.)
insert into owners (full_name, email) select 'Owner ' || generate_series(1,2500000), 'owner_' || generate_series(1,2500000) || '@mail.com';

```
4. Depening on your machine speed, it might be enough or not. Check that by running `explain analyze SELECT COUNT(*) FROM visits where animal_id = 4`: - If you get Execution time: X ms and X >= 1000: that should be enough, you can continue to the project requirements. - If you get Execution time: X ms and X < 1000: please go back to point 3. and repeat until you get a value bigger than 1000ms.
## Built with

- PostgresSQL.

- SQL queries.

- Gitflow


## Getting Started

To get a local copy up and running follow these simple example steps:

- On the project, GitHub page, navigate to the [main page of the repository](https://github.com/errea/vet_clinic_database)

- Copy the project URL as displayed on HTTPS tab

- If you're running Windows Operating System, open your command prompt. On Linux, Open your terminal

- Change the current working directory to the location where you want the cloned directory to be made. Leave as it is if the current location is where you want the project to be.

- Type `git clone`, and then paste the URL you copied in Step 3.<br>

  `$ git clone https://github.com/errea/vet_clinic_database.git` <em>Press Enter key</em><br>

- Your local copy will be created.

- Please note that you must have Git installed on your PC, this can be done [here](https://gist.github.com/derhuerst/1b15ff4652a867391f03)

- After you get the project aiming to the desired directory, you need now to install dependencies by running npm install.

## ✒️  Authors <a name = "author"></a>

👤 **Eri**

- Github: [@errea](https://github.com/errea)
- Twitter: [@Erreakay](https://github.com/errea)
- Linkedin: [Eri Okereafor](https://www.linkedin.com/in/eri-ngozi-okereafor/)

## 🤝 Contributing

Contributions, issues and feature requests are welcome!

Feel free to check the [issues page](https://github.com/errea/vet_clinic_database/issues)
## 👍 Show your support

- Microverse: [@microverse](https://www.microverse.org/)

## Acknowledgments

- Microverse


## 📝 License