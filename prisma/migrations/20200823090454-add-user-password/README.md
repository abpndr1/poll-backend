# Migration `20200823090454-add-user-password`

This migration has been generated by abpndr1 at 8/23/2020, 2:34:54 PM.
You can check out the [state of the schema](./schema.prisma) after the migration.

## Database Steps

```sql
PRAGMA foreign_keys=OFF;
CREATE TABLE "new_User" (
    "id" INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,
    "mail" TEXT NOT NULL,
    "name" TEXT,
    "password" TEXT NOT NULL DEFAULT 'test'
);
INSERT INTO "new_User" ("id", "mail", "name") SELECT "id", "mail", "name" FROM "User";
DROP TABLE "User";
ALTER TABLE "new_User" RENAME TO "User";
CREATE UNIQUE INDEX "User.mail_unique" ON "User"("mail");
PRAGMA foreign_key_check;
PRAGMA foreign_keys=ON
```

## Changes

```diff
diff --git schema.prisma schema.prisma
migration 20200822130901-init..20200823090454-add-user-password
--- datamodel.dml
+++ datamodel.dml
@@ -1,7 +1,7 @@
 datasource db {
   provider = "sqlite" 
-  url = "***"
+  url = "***"
 }
 generator client {
   provider = "prisma-client-js"
@@ -10,8 +10,9 @@
 model User {
   id Int @id @default(autoincrement())
   mail String @unique
 	name String?
+  password String @default("test")
   polls Poll[]
 }
 model Poll {
```


