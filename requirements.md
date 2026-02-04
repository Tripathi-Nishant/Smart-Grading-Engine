# Requirements Document

## Introduction

The AI-Powered Automatic Grading System is a Flask-based web application that automates the grading process for teachers by using Mistral AI OCR to extract text from handwritten student answer sheets, comparing it with reference answers, and generating grades instantly. The system provides comprehensive analytics and data management capabilities to help teachers track student performance and progress over time.

## Glossary

- **System**: The AI-Powered Automatic Grading System
- **OCR_Engine**: The Mistral AI OCR service for text extraction
- **Grading_Algorithm**: The keyword similarity matching algorithm
- **Analytics_Dashboard**: The web interface displaying performance metrics and charts
- **Database**: The SQLite database storing all grading results
- **Teacher**: The user who provides reference answers and uploads student images
- **Student_Answer**: The handwritten text extracted from uploaded images
- **Reference_Answer**: The correct answer provided by the teacher
- **Similarity_Score**: The percentage match between student and reference answers
- **Grade_Letter**: The letter grade (A, B, C, D, F) assigned based on similarity
- **Keyword_Match**: Words found in both student and reference answers
- **Missing_Keyword**: Words present in reference but absent in student answer

## Requirements

### Requirement 1: Image Upload and Processing

**User Story:** As a teacher, I want to upload images of student answer sheets, so that I can automatically extract and grade the handwritten text.

#### Acceptance Criteria

1. WHEN a teacher uploads an image file, THE System SHALL validate the file format is PNG, JPG, or JPEG
2. WHEN an invalid file format is uploaded, THE System SHALL reject the upload and display an error message
3. WHEN a valid image is uploaded, THE System SHALL store it securely in the uploads directory
4. WHEN the image file size exceeds reasonable limits, THE System SHALL reject the upload to prevent resource exhaustion
5. THE System SHALL sanitize uploaded filenames to prevent security vulnerabilities

### Requirement 2: OCR Text Extraction

**User Story:** As a teacher, I want the system to extract text from handwritten answer sheets, so that I can process student responses automatically.

#### Acceptance Criteria

1. WHEN a valid image is provided, THE OCR_Engine SHALL extract text content from the image
2. WHEN OCR processing fails, THE System SHALL return a descriptive error message
3. WHEN extracted text contains special characters, THE System SHALL clean and normalize the text
4. THE System SHALL handle empty or unreadable images gracefully
5. WHEN text extraction is successful, THE System SHALL return the cleaned text for further processing

### Requirement 3: Automatic Grading Algorithm

**User Story:** As a teacher, I want the system to automatically grade student answers by comparing them with my reference answers, so that I can save time on manual grading.

#### Acceptance Criteria

1. WHEN comparing student and reference answers, THE Grading_Algorithm SHALL calculate keyword similarity percentage
2. WHEN similarity is 90% or above, THE System SHALL assign grade A with 100 marks
3. WHEN similarity is 75-89%, THE System SHALL assign grade B with 85 marks
4. WHEN similarity is 60-74%, THE System SHALL assign grade C with 70 marks
5. WHEN similarity is 40-59%, THE System SHALL assign grade D with 55 marks
6. WHEN similarity is below 40%, THE System SHALL assign grade F with 30 marks
7. THE System SHALL identify and return matched keywords between answers
8. THE System SHALL identify and return missing keywords from student answers
9. THE System SHALL exclude common stop words from similarity calculations

### Requirement 4: Result Storage and Persistence

**User Story:** As a teacher, I want all grading results to be stored permanently, so that I can track student progress over time.

#### Acceptance Criteria

1. WHEN a grading operation completes, THE System SHALL store the result in the Database
2. THE Database SHALL persist student name, question ID, extracted text, reference text, similarity score, grade, marks, matched keywords, missing keywords, and timestamp
3. WHEN storing results, THE System SHALL handle database connection errors gracefully
4. THE System SHALL ensure data integrity during storage operations
5. WHEN the database is unavailable, THE System SHALL provide appropriate error feedback

### Requirement 5: Analytics Dashboard

**User Story:** As a teacher, I want to view comprehensive analytics of student performance, so that I can identify trends and areas needing attention.

#### Acceptance Criteria

1. WHEN accessing the dashboard, THE Analytics_Dashboard SHALL display grade distribution charts
2. WHEN viewing analytics, THE System SHALL show average performance by student
3. WHEN analyzing trends, THE System SHALL display time-series performance data
4. THE Analytics_Dashboard SHALL present data using visual charts and graphs
5. WHEN no data exists, THE System SHALL display appropriate empty state messages
6. THE System SHALL calculate and display overall class performance metrics

### Requirement 6: Data Export Functionality

**User Story:** As a teacher, I want to export grading data to CSV format, so that I can use the data in external systems or for record keeping.

#### Acceptance Criteria

1. WHEN requesting data export, THE System SHALL generate a CSV file with all grading results
2. THE CSV file SHALL include student ID, name, question ID, marks, grade, similarity score, and timestamp
3. WHEN generating exports, THE System SHALL handle large datasets efficiently
4. THE System SHALL provide the CSV file as a downloadable attachment
5. WHEN export generation fails, THE System SHALL provide appropriate error feedback

### Requirement 7: Keyword Feedback System

**User Story:** As a teacher, I want to see which keywords were matched and which were missing from student answers, so that I can provide targeted feedback.

#### Acceptance Criteria

1. WHEN displaying results, THE System SHALL highlight matched keywords from the comparison
2. WHEN showing feedback, THE System SHALL list missing keywords that students should have included
3. THE System SHALL limit displayed keywords to prevent information overload (maximum 15 each)
4. WHEN no keywords match, THE System SHALL display appropriate messaging
5. THE System SHALL present keyword feedback in a clear, readable format

### Requirement 8: Error Handling and User Experience

**User Story:** As a teacher, I want clear error messages and warnings when issues occur, so that I can understand and resolve problems quickly.

#### Acceptance Criteria

1. WHEN a student scores below 40%, THE System SHALL display a warning recommending manual review
2. WHEN required fields are missing, THE System SHALL display specific validation errors
3. WHEN system errors occur, THE System SHALL provide user-friendly error messages
4. THE System SHALL maintain application stability during error conditions
5. WHEN processing takes time, THE System SHALL provide appropriate user feedback

### Requirement 9: Web Interface and Navigation

**User Story:** As a teacher, I want an intuitive web interface to access all system features, so that I can efficiently manage the grading process.

#### Acceptance Criteria

1. THE System SHALL provide a main interface for uploading images and entering reference answers
2. THE System SHALL display grading results with all relevant information clearly formatted
3. THE System SHALL provide navigation to the analytics dashboard
4. THE System SHALL offer easy access to data export functionality
5. WHEN displaying results, THE System SHALL present information in a logical, organized manner

### Requirement 10: Data Validation and Security

**User Story:** As a teacher, I want the system to validate all inputs and maintain data security, so that I can trust the system with sensitive academic information.

#### Acceptance Criteria

1. WHEN processing user inputs, THE System SHALL validate and sanitize all data
2. THE System SHALL prevent SQL injection and other security vulnerabilities
3. WHEN handling file uploads, THE System SHALL enforce security restrictions
4. THE System SHALL validate that reference answers are provided before processing
5. THE System SHALL ensure student names and question IDs are properly formatted