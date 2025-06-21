+++
title = 'Spring Security in Action 2 Notes'
date = 2025-03-24T21:49:33-06:00
draft = false
+++

# Chapter 2
For the apps that you develop with the Spring Framework, Spring Security is an excellent choice for application-level
security.

To customize the handling of authentication and authorization, we’ll need to define a bean of type SecurityFilterChain.

An object that implements a `UserDetailsService` interface with Spring Security manages the details about users.

It is good practice to separate the responsibilities even for the configuration classes.
