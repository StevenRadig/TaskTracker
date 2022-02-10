<template>
  <main class="view__about">
    <h1>About</h1>
    <h2>Version 1.0.0 (vry official 🧐)</h2>
    <p>This app was made with the Vue CLI and demonstrates an ability to create, read, update, and delete data. It is not a production level project and only built to familiarize myself with Vue. While I did build the project myself, it is based on a tutorial.</p>
    <p><strong>Features:</strong></p>
    <ul>
      <li>Create, Read, Update, Delete</li>
      <li>Double-click to toggle reminder (green border)</li>
      <li>Utilizes <a target="_blank" href="">json-server</a> to fake a REST API</li>
      <li>Routes (although just two)</li>
      <li>100 score for Chrome's lighthouse accesibility audit</li>
      <li>Custom and responsive styling</li>
    </ul>

    <p><strong>What I got from this project:</strong></p>
    <ul>
      <li>Introduction to core concepts
          <ul>
            <li>Components</li>
            <li>Data Binding</li>
            <li>Views</li>
            <li>Routes</li>
            <li>Form Submission (sort of)</li>
          </ul>
      </li>
      <li>Experience troubleshooting in Vue</li>
    </ul>

    <p><strong>Ways to improve this project:</strong></p>
    <ul>
      <li>Add ability to modify text and titles</li>
      <li>Replace text input for day/time with Vuetify time and day pickers</li>
      <li>Add functionality to sort tasks chronologically</li>
      <li>Rework the components and grid layout to be more logical</li>
      <li>Add styles for a condensed view for when many tasks are present</li>
      <li>Add a darkmode</li>
    </ul>
    
    <router-link to="/">&#8592; Go Back</router-link>
  </main>
</template>