<template>
  <div class="flex h-screen w-screen items-center justify-center">
    <section class="w-[50%]">
      <h2>Code Editor</h2>
      <MonacoEditor v-model="val" :lang="lang" :options="options" class="h-[600px] w-full"> Loading... </MonacoEditor>
    </section>
  </div>
</template>

<script lang="ts" setup>
import { config, language } from '~/utils/prisma-language'

const lang = ref<'prisma'>('prisma')
const val = ref(`datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

generator client {
  provider = "prisma-client-js"
}

model User {
  id        Int      @id @default(autoincrement())
  createdAt DateTime @default(now())
  email     String   @unique
  name      String?
  role      Role     @default(USER)
  posts     Post[]
}

model Post {
  id        Int      @id @default(autoincrement())
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
  published Boolean  @default(false)
  title     String   @db.VarChar(255)
  author    User?    @relation(fields: [authorId], references: [id])
  authorId  Int?
}

enum Role {
  USER
  ADMIN
}`)

const options = {
  automaticLayout: true,
}

onMounted(async () => {
  const monaco = await import('monaco-editor')

  const PRISMA_ID = 'prisma'

  monaco.languages.register({ id: PRISMA_ID })
  monaco.languages.setLanguageConfiguration(PRISMA_ID, config)
  monaco.languages.setMonarchTokensProvider(PRISMA_ID, language)
})
</script>
