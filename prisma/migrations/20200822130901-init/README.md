# Migration `20200822130901-init`

This migration has been generated by abpndr1 at 8/22/2020, 6:39:01 PM.
You can check out the [state of the schema](./schema.prisma) after the migration.

## Database Steps

```sql
CREATE UNIQUE INDEX "User.mail_unique" ON "User"("mail")
```

## Changes

```diff
diff --git schema.prisma schema.prisma
migration 20200822130816-init..20200822130901-init
--- datamodel.dml
+++ datamodel.dml
@@ -1,16 +1,16 @@
 datasource db {
   provider = "sqlite" 
-  url = "***"
+  url = "***"
 }
 generator client {
   provider = "prisma-client-js"
 }
 model User {
   id Int @id @default(autoincrement())
-  mail String
+  mail String @unique
 	name String?
   polls Poll[]
 }
```


