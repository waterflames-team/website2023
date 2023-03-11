<template>
  <ContentDoc>
    <template #default="{ doc }">
      <PageBody class="text-base">
        <p class="text-center text-4xl">{{ doc.title }}</p>
        <PageSection>
          <ContentRenderer :value="doc" />
        </PageSection>
      </PageBody>
    </template>
    <template #empty>
      <h1>Post in empty</h1>
    </template>
    <template #not-found>
      <Error :code="404" wrap />
    </template>
  </ContentDoc>
</template>
