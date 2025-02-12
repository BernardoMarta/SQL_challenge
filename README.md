# Vending Machine Database Project

## About the Project

This project implements a database schema for managing sales transactions in vending machines. It includes tables for storing information about locations, machines, products, payment methods, machine-product relationships, and sales records. The database also contains stored procedures for registering sales and calculating total sales by machine within specified date ranges. Additionally, it features views to compute the percentage of sales by payment method and the percentage of QR code payments.

This project was developed by:
* Bernardo Marta ([BernardoMarta](https://github.com/BernardoMarta))
* Raquel Vieira ([Raquel-alexandra](https://github.com/Raquel-alexandra))
* Raquel Magalhães

## How It Works

The database schema consists of the following tables:

*   **local**: Stores information about the location of each vending machine.
*   **maquina**: Stores information about each vending machine, including its location and last maintenance date.
*   **maquinaProduto**: Establishes the relationship between machines and products, specifying the unit price and stock level for each product in a given machine.
*   **metodoDePagamento**: Stores information about the available payment methods.
*   **produto**: Stores details about the products available in the vending machines.
*   **venda**: Records each sales transaction, including the machine code, product ID, sale value, date and time, and payment method.

The database also includes the following stored procedures:

*   **RegistarVenda**: Registers a new sale transaction, updating the stock level of the sold product and verifying both the product existence on the machine and if there's enough stock for selling the product.
*   **TotalVendasPorMaquina**: Calculates the total sales amount per machine within a specified date range.

Two views are defined to provide aggregated data:

*   **PercentagemMetodosPagamento**: Calculates the percentage of total sales for each payment method.
*   **PercentagemPagamentosQRCode**: Calculates the percentage of total sales made using QR code payments.

## Getting Started

### Prerequisites

*   MariaDB or MySQL database server
*   Database client (e.g., MySQL Workbench)

### Installation

1.  Clone the repository:

git clone https://github.com/BernardoMarta/Vending-Machine-Database
cd Vending-Machine-Database

2.  Create a database named `pegaevai`.

3.  Import the provided SQL schema (`PegaEvai-MySQL-Grupo-6.sql`) to create the necessary tables, procedures, and views.

4.  Optionally, import or insert the data from the SQL script into the created tables.

## Usage

1.  Connect to the MariaDB database using a database client.
2.  Execute the stored procedures to register sales or calculate total sales by machine.
3.  Query the views to retrieve aggregated data about payment methods.

**Example Usage**:

To register a sale, execute the `RegistarVenda` stored procedure:

CALL RegistarVenda(7001, 7010, 7001);

To retrieve the total sales per machine between two dates, execute the `TotalVendasPorMaquina` stored procedure:

CALL TotalVendasPorMaquina('2024-01-01 00:00:00', '2024-12-31 23:59:59');

To retrieve the sales of a specific machine between two dates, we may use the following query:

SELECT * FROM Venda WHERE codMaquina = 7001 AND dataHora BETWEEN '2024-01-01 00:00:00' AND '2024-12-31 23:59:59';

The output of these queries are the total sales per machine between those dates.

## Features

*   Comprehensive database schema for vending machine sales management.
*   Stored procedures for registering sales and calculating total sales by machine.
*   Views for analyzing payment method usage.
*   Triggers to prevent future maintenance dates.

## Contributing

Feel free to fork this repository and submit pull requests to [BernardoMarta's repository](https://github.com/BernardoMarta/Vending-Machine-Database)!

## License

This project is licensed under the MIT License.

## Acknowledgments

Thanks to the team for collaborating on the database design and implementation.
