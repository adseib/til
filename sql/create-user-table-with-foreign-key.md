# User Tables with Foreign Key Constraint

A very quick and dirty example of setting up a user table with foreign key constraints. This prevents changes in the RoleList table without a valid User or Role ID.

```sql
CREATE TABLE dbo.Roles
(
	RoleID int PRIMARY KEY,
	RoleName char(100) ,
	RoleDesc nvarchar(4000)
)

CREATE TABLE dbo.Users
(
	UserID int PRIMARY KEY,
	UserName char(50),
	UserAge char(100),
	UserCreated date(),
)

CREATE TABLE dbo.RoleList
(
	ListNumber int PRIMARY KEY,
	RoleID int FOREIGN KEY REFERENCES dbo.Roles(RoleID),
	UserID int FOREIGN KEY REFERENCES dbo.Users(UserID),
	IsUserActive bit NOT NULL
)
```
