# Migration `20200722145142-user-authentication`

This migration has been generated by rntjr at 7/22/2020, 2:51:42 PM.
You can check out the [state of the schema](./schema.prisma) after the migration.

## Database Steps

```sql
ALTER TABLE "public"."Post" DROP CONSTRAINT "Post_authorId_fkey"

ALTER TABLE "public"."Profile" DROP CONSTRAINT "Profile_userId_fkey"

DROP TABLE "public"."Post";

DROP TABLE "public"."Profile";
```

## Changes

```diff
diff --git schema.prisma schema.prisma
migration ..20200722145142-user-authentication
--- datamodel.dml
+++ datamodel.dml
@@ -1,0 +1,19 @@
+// This is your Prisma schema file,
+// learn more about it in the docs: https://pris.ly/d/prisma-schema
+
+datasource db {
+  provider = "postgresql"
+  url = "***"
+}
+
+generator client {
+  provider = "prisma-client-js"
+}
+
+model User {
+  id       Int     @default(autoincrement()) @id
+  email    String  @unique
+  name     String?
+  username String  @unique
+  password String
+}
```

