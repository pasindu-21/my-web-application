<template>
    <q-layout>
      <q-header elevated>
        <q-toolbar>
          <q-btn flat label="Home" to="/" />
          <q-btn flat label="About" to="/about" />
        </q-toolbar>
      </q-header>
  
      <q-page-container>
        <router-view />
      </q-page-container>
    </q-layout>

    <div><h1>About us</h1></div>
  </template>
  