# bartenderApp
Bartender App
To set up database:
Tools -> Connect to Database -> Microsoft SQL server
  Enter (localdb)\mssqllocaldb for server name
  Enter master as the Database Name
  Click OK
Right click on the database in Server Explorer and select New Query
Copy the following Script into the query editor
Right click on the query editor and select Execute.

<Query> (don't copy this part)
  
CREATE DATABASE[Bartending]
GO

USE [Bartending];
GO

CREATE TABLE [Drink](
	[DrinkId] int NOT NULL IDENTITY,
	[DrinkName] nvarchar (max) NOT NULL,
	[DrinkPrice] int NOT NULL,
	CONSTRAINT [PK_Drink] PRIMARY KEY ([DrinkID])
);
GO

CREATE TABLE [Order](
	[OrderId] int NOT NULL IDENTITY,
	[DrinkId] int NOT NULL,
	[CustomerName] nvarchar (max) NOT NULL,
	[DrinkName] nvarchar (max) NOT NULL,
	CONSTRAINT [PK_Order] PRIMARY KEY ([OrderId]),
	CONSTRAINT [FK_Order_Drink_DrinkId] FOREIGN KEY ([DrinkId]) REFERENCES [Drink] ([DrinkId]) ON DELETE CASCADE
);
GO

INSERT INTO Drink (DrinkName, DrinkPrice) VALUES
('Juice', 2),
('Water', 1),
('Milk', 3),
('Sparkling Water', 5);
GO
