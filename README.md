# school-rag
# Course Management for Document RAG System

This feature adds hierarchical course organization to the document RAG system, allowing users to structure their documents according to their academic or training needs.

## Features

### Course Structure Hierarchy

The system now supports a hierarchical organization structure:

- **Courses** - Top-level organization (e.g., "Computer Science", "Biology")
- **Years** - Subdivisions of a course (e.g., "First Year", "Second Year")
- **Semesters** - Subdivisions of a year (e.g., "Fall Semester", "Spring Semester")
- **Units** - Specific subjects within a semester (e.g., "CS101 - Introduction to Programming")

### Integrated Document Upload

- Documents (PDFs) are now uploaded to specific units
- The unit hierarchy provides context for organizing and retrieving documents
- Document metadata tracks their location in the course structure

### Contextual Question Answering

- Questions can be filtered by course, year, semester, or unit
- Answers are generated based on the selected scope of documents
- Provides more relevant answers by focusing on specific course materials

## Setup Instructions

### 1. Database Setup

The system uses SQLite for storage. The database will be automatically initialized when the application starts.

### 2. Installation

Make sure to install the required dependencies:

```bash
npm install better-sqlite3 uuid
npm install @types/better-sqlite3 @types/uuid --save-dev
```

### 3. Directory Structure

The feature adds several new files to the project:

- `/lib/db.ts` - Database configuration and connection
- `/lib/models.ts` - Data models and database operations
- `/app/course/page.tsx` - Course management page
- `/components/course-manager.tsx` - Course management component
- Updated `/components/pdf-uploader.tsx` - Modified to use course structure
- Updated `/components/question-interface.tsx` - Modified to filter by course

## Usage Guide

### Managing Course Structure

1. Navigate to the **Course Management** page
2. Create courses, years, semesters, and units in hierarchical order
3. Each level must be created before adding items to the next level

### Uploading Documents

1. From the **Document Upload** page, select a unit to upload to
   - You can also click "Upload Documents" on a unit in the Course Management page
2. Drag and drop or select PDF files to upload
3. Documents will be associated with the selected unit

### Asking Questions

1. From the **Ask Questions** page, use the filters to select which documents to search
2. You can filter by course, year, semester, or unit
3. Ask your question and receive answers based on documents within the selected scope

## Technical Notes

- SQLite database is stored in the `data` directory
- Uploaded PDFs are stored in the `uploads` directory with unit-specific subfolders
- PDF metadata is stored in the database to track its associated unit
- The system uses the metadata to filter documents during question answering
- The backend API routes handle CRUD operations for the course structure