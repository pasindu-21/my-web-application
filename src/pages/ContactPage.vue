<template>
    
    <q-layout>
      <q-header elevated>
        <q-toolbar>
          <q-btn flat label="Home" to="/" />
          <q-btn flat label="Contact" to="/contact" />
        </q-toolbar>
      </q-header>
  
      <q-page-container>

        <router-view />
      </q-page-container>
      <div><h1>Contact Me</h1></div>
    </q-layout>

    
  </template>
  