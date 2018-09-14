1. Find all time entries.

  A. SELECT *
     FROM time_entries
  B. 500 rows returned in 11ms from: SELECT *
     FROM time_entries

2. Find the developer who joined most recently.

  A. SELECT MAX (joined_on), name
     FROM developers;
  B. Dr. Danielle McLaughlin

3. Find the number of projects for each client.

  A. SELECT clients.name,
     COUNT(projects.id) AS total_projects
     FROM clients LEFT JOIN projects 
     ON clients.id = projects.client_id 
     GROUP BY clients.name;
  B.  clients.name    total_projects
     "Abbott-Stroman"	"0"
     "Carolina Code School"	"0"
     "Carter, Farrell and Goodwin"	"3"
     "Eichmann, Altenwerth and Morar"	"3"
     "Goodwin Group"	"3"
     "Jast LLC"	"3"
     "Kuhic-Bartoletti"	"3"
     "Mohr Inc"	"3"
     "Momentum Learning"	"0"
     "Ortiz, Gislason and Rutherford"	"6"
     "West Group"	"3"
     "Zieme-Ortiz"	"3"

4. Find all time entries, and show each one's client name next to it.

  A. SELECT time_entries.*, clients.name
     FROM clients 
     JOIN projects ON clients.id = projects.client_id
     JOIN time_entries ON projects.id = time_entries.project_id;
  B. 500 rows returned

5. Find all developers in the "Ohio sheep" group.

  A. SELECT developers.name, groups.name
     FROM developers
     JOIN group_assignments ON developers.id = group_assignments.developer_id
     JOIN groups ON group_assignments.group_id = groups.id
     WHERE groups.name = 'Ohio sheep';
  B.  developer.name     project.name
    "Bruce Wisoky Jr."	"Ohio sheep"
    "Eli Wunsch MD"	"Ohio sheep"
    "Reyes Vandervort IV"	"Ohio sheep"

6. Find the total number of hours worked for each client.

  A. SELECT clients.name, SUM(time_entries.duration) AS total_hours_worked
     FROM time_entries 
     JOIN projects ON time_entries.project_id = projects.id
     JOIN clients ON clients.id = projects.client_id
     GROUP BY clients.name;

  B.    client.name            total_hours_worked
     "Carter, Farrell and Goodwin"	"174"
     "Eichmann, Altenwerth and Morar"	"188"
     "Goodwin Group"	"238"
     "Jast LLC"	"166"
     "Kuhic-Bartoletti"	"223"
     "Mohr Inc"	"209"
     "Ortiz, Gislason and Rutherford"	"330"
     "West Group"	"176"
     "Zieme-Ortiz"	"166"

7. Find the client for whom Mrs. Lupe Schowalter (the developer) has worked the greatest number of hours.

  A. SELECT clients.name, developers.name, MAX(time_entries.duration) AS hours_for_client
     FROM developers 
     JOIN time_entries ON developers.id = time_entries.developer_id
     JOIN projects ON time_entries.project_id = projects.id 
     JOIN clients on projects.client_id = clients.id
     WHERE developers.name = 'Mrs. Lupe Schowalter';
  B.      clients.name       developer.name         hours_for_cleint
      "Kuhic-Bartoletti"	"Mrs. Lupe Schowalter"         "7"

8. List all client names with their project names (multiple rows for one client is fine). Make sure that        clients still show up even if they have no projects.

  A. SELECT clients.name, projects.name
     FROM clients
     LEFT JOIN projects ON clients.id = projects.client_id;
  B.    clients.name         projects.name
      "West Group"	"Ergonomic Plastic Shoes"
      "West Group"	"Gorgeous Steel Hat"
      "West Group"	"Rustic Concrete Table"
      "Mohr Inc"	"Awesome Cotton Hat"
      "Mohr Inc"	"Incredible Concrete Shirt"
      "Mohr Inc"	"Rustic Steel Chair"
      "Jast LLC"	"Awesome Rubber Shirt"
      "Jast LLC"	"Ergonomic Rubber Car"
      "Jast LLC"	"Fantastic Cotton Computer"
      "Carter, Farrell and Goodwin"	"Awesome Rubber Pants"
      "Carter, Farrell and Goodwin"	"Gorgeous Wooden Table"
      "Carter, Farrell and Goodwin"	"Rustic Granite Shirt"
      "Abbott-Stroman"	"NULL"
      "Ortiz, Gislason and Rutherford"	"Awesome Rubber Computer"
      "Ortiz, Gislason and Rutherford"	"Gorgeous Granite Car"
      "Ortiz, Gislason and Rutherford"	"Intelligent Cotton Shirt"
      "Ortiz, Gislason and Rutherford"	"Practical Wooden Shirt"
      "Ortiz, Gislason and Rutherford"	"Sleek Granite Car"
      "Ortiz, Gislason and Rutherford"	"Sleek Plastic Shoes"
      "Zieme-Ortiz"	"Fantastic Rubber Chair"
      "Zieme-Ortiz"	"Fantastic Wooden Shirt"
      "Zieme-Ortiz"	"Practical Concrete Shoes"
      "Eichmann, Altenwerth and Morar"	"Gorgeous Concrete Hat"
      "Eichmann, Altenwerth and Morar"	"Gorgeous Cotton Hat"
      "Eichmann, Altenwerth and Morar"	"Intelligent Wooden Hat"
      "Kuhic-Bartoletti"	"Awesome Plastic Computer"
      "Kuhic-Bartoletti"	"Intelligent Plastic Shirt"
      "Kuhic-Bartoletti"	"Intelligent Rubber Gloves"
      "Goodwin Group"	"Incredible Granite Table"
      "Goodwin Group"	"Intelligent Steel Shirt"
      "Goodwin Group"	"Practical Rubber Shoes"
      "Momentum Learning"	"NULL"
      "Carolina Code School"	"NULL"

9. Find all developers who have written no comments.

  A. SELECT developers.name, comments.comment
     FROM developers 
     LEFT JOIN  comments ON developers.id = comments.developer_id
     WHERE comments.developer_id IS null;
  B.      developers_name   comments.comment
      "Ms. Tremayne Kuhn"	          "null"
      "Jaylin Auer"	                "null"
      "Myles Keebler"	              "null"
      "Mr. Rogers Greenholt"	      "null"
      "Jayne Brakus DDS"	          "null"
      "Orlo Renner"	                "null"
      "Hyman Borer"	                "null"
      "Verda Zieme"	                "null"
      "Dr. Danielle McLaughlin"	    "null"
      "Joanie Krajcik PhD"	        "null"
      "Reese Dooley"	              "null"
      "Amy Dickinson"	              "null"
      "Miss Brendan Zboncak"	      "null"