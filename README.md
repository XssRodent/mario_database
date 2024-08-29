# Mario Database Project

This repository contains the Mario Database project, which is a part of the FreeCodeCamp Relational Database course. The project involves designing and implementing a relational database to manage characters, actions, and various interactions within the Mario universe. The aim of this project is to practice and demonstrate the understanding of relational database concepts, SQL, and database design.

## Project Overview

The Mario Database project simulates a database system that stores information about characters from the Mario video game series, along with their actions and interactions. This project involves creating tables, defining relationships, and writing queries to retrieve and manipulate data.

## Project Structure

The project includes the following key components:

- **Database Schema**: Definition of tables, columns, and relationships.
- **SQL Scripts**: Scripts to create and populate the database.
- **Queries**: Examples of SQL queries to interact with the database.
- **README.md**: Project documentation.

## Database Schema

The database consists of the following tables:

1. **`characters`**: Stores information about Mario characters.
   - `character_id` (Primary Key): Unique identifier for each character.
   - `name`: Name of the character.
   - `type`: Type of character (e.g., Hero, Villain).
   - `description`: A brief description of the character.

2. **`actions`**: Stores different actions that characters can perform.
   - `action_id` (Primary Key): Unique identifier for each action.
   - `name`: Name of the action (e.g., Jump, Run, Attack).
   - `description`: Description of the action.

3. **`character_actions`**: Stores the relationship between characters and their actions.
   - `character_id` (Foreign Key): References `characters.character_id`.
   - `action_id` (Foreign Key): References `actions.action_id`.
   - Composite Primary Key: (`character_id`, `action_id`).

## Getting Started

To run this project locally, you'll need to have PostgreSQL installed on your machine. Follow these steps:

1. **Clone the Repository**:

    ```bash
    git clone https://github.com/yourusername/mario-database-project.git
    cd mario-database-project
    ```

2. **Set Up the Database**:

   - Start your PostgreSQL server.
   - Create a new database:

    ```sql
    CREATE DATABASE mario_db;
    ```

   - Connect to the `mario_db` database:

    ```bash
    psql -d mario_db
    ```

   - Run the SQL script to create tables and populate data:

    ```sql
    \i create_tables.sql
    \i populate_data.sql
    ```

3. **Run Queries**:

   - Use the `queries.sql` file to run various SQL queries and interact with the database.

## Example Queries

Here are a few example queries you can run to interact with the Mario Database:

- List all characters and their actions:

    ```sql
    SELECT c.name AS character_name, a.name AS action_name
    FROM character_actions ca
    JOIN characters c ON ca.character_id = c.character_id
    JOIN actions a ON ca.action_id = a.action_id;
    ```

- Find all actions performed by a specific character (e.g., Mario):

    ```sql
    SELECT a.name AS action_name
    FROM character_actions ca
    JOIN actions a ON ca.action_id = a.action_id
    WHERE ca.character_id = (SELECT character_id FROM characters WHERE name = 'Mario');
    ```

## Learning Objectives

This project is designed to help you achieve the following learning objectives:

- Understand the fundamentals of relational databases.
- Learn how to design a database schema based on real-world scenarios.
- Practice writing SQL queries to retrieve and manipulate data.
- Develop skills in database normalization and optimization.



## License

This project is part of the FreeCodeCamp curriculum and is open for educational purposes.

## Acknowledgments

- Thanks to FreeCodeCamp for providing the opportunity to learn and practice relational database concepts.
- Thanks to the PostgreSQL community for their robust and powerful database management system.

