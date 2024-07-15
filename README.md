# CertifiedSkillDevelopment

This project is a Java console application that simulates a customer feedback and survey system for a consumer electronics company. It allows you to manage customers, feedback, surveys, and survey responses. The project uses MySQL as the database.

### Requirements

- Java Development Kit (JDK) 11 or later
- MySQL Server
- Eclipse IDE (optional, but recommended for development)

### Setup

Clone repository and unzip compressed file

### Set up the MySQL database
CREATE DATABASE feedback_survey;

Create the necessary tables in the feedback_survey database
USE feedback_survey;

CREATE TABLE Customer (
    customer_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100)
);

CREATE TABLE Survey (
    survey_id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(255),
    description TEXT
);

CREATE TABLE Feedback (
    feedback_id INT AUTO_INCREMENT PRIMARY KEY,
    customer_id INT,
    feedback_date DATE,
    feedback_text TEXT,
    rating INT,
    FOREIGN KEY (customer_id) REFERENCES Customer(customer_id)
);

CREATE TABLE survey_response (
    response_id INT AUTO_INCREMENT PRIMARY KEY,
    survey_id INT,
    customer_id INT,
    response_date DATE DEFAULT CURRENT_DATE,
    response_text TEXT,
    FOREIGN KEY (survey_id) REFERENCES Survey(survey_id),
    FOREIGN KEY (customer_id) REFERENCES Customer(customer_id)
);

ALTER TABLE survey_response
ADD CONSTRAINT FK_survey_id FOREIGN KEY (survey_id) REFERENCES Survey(survey_id),
ADD CONSTRAINT FK_customer_id FOREIGN KEY (customer_id) REFERENCES Customer(customer_id);

ALTER TABLE survey_response
ADD INDEX idx_survey_id (survey_id);

ALTER TABLE survey_response
ADD INDEX idx_customer_id (customer_id);

### Configure database connection
package com.SurveySystem.app;
Change user name to 'root' and password as 'root@123'
compile and run 'main' class to start application

### Usage
Menu is displayed
Input given  number to perform particular operation 
