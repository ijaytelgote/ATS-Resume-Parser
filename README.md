
---

# Resume Parsing API

This API retrieves and parses resumes from Google Drive links provided by users. The resume is fetched from the given URL, processed, and relevant information is extracted.

## Features

- **Extracts Resume Data:** Retrieves and parses resumes from Google Drive links.
- **Supports Various Formats:** Handles different resume formats and extracts key details.
- **Simple Integration:** Easy to integrate into your applications.

## API Endpoint

### `GET /parse`

**Description:** Parses the resume from the provided Google Drive link.

**Request:**

- **URL:** `/url`
- **Method:** `GET`
- **Content-Type:** `application/json`

**Query Parameters:**

- `url` (string): The Google Drive link to the resume file.

**Example Request:**

```http
GET /parse?url=https://drive.google.com/file/d/FILE_ID/view
Host: api.example.com
```

**Response:**

- **Status Code:** `200 OK`
- **Content-Type:** `application/json`

**Response Body:**

```json
{
  "status": "success",
  "data": {
    "name": "John Doe",
    "email": "john.doe@example.com",
    "phone": "+1234567890",
    "experience": [
      {
        "company": "ABC Corp",
        "position": "Software Engineer",
        "duration": "March 2014 - December 2016"
      }
    ],
    "education": [
      {
        "institution": "XYZ University",
        "degree": "Bachelor of Science in Computer Science",
        "duration": "August 2010 - May 2014"
      }
    ]
  }
}
```

**Error Response:**

- **Status Code:** `400 Bad Request` or `500 Internal Server Error`
- **Content-Type:** `application/json`

**Response Body:**

```json
{
  "status": "error",
  "message": "Detailed error message. If parsing was unsuccessful, the resume might not be ATS-friendly. Consider checking the resume format or content."
}
```

## Usage

1. Obtain the Google Drive link to the resume you want to parse.
2. Send a `GET` request to `/parse` with the `url` query parameter.
3. Receive the parsed resume data in the response.

## Requirements

- Ensure the resume file on Google Drive is accessible (public or shared with the appropriate permissions).

## Example

**Request:**

```http
GET https://api.example.com/parse?url=https://drive.google.com/file/d/FILE_ID/view
```

**Response:**

```json
{
  "status": "success",
  "data": {
    "name": "Jane Doe",
    "email": "jane.doe@example.com",
    "phone": "+0987654321",
    "experience": [
      {
        "company": "XYZ Inc.",
        "position": "Data Scientist",
        "duration": "June 2018 - Present"
      }
    ],
    "education": [
      {
        "institution": "ABC University",
        "degree": "Master of Science in Data Science",
        "duration": "August 2016 - May 2018"
      }
    ]
  }
}
```
## Find API
- Please find API on Rapid API's marketplace as InRecruit or redirect to https://rapidapi.com/jaymaha098/api/inrecruit

## Notes

- If parsing is unsuccessful, there is a high likelihood that the resume may not be ATS-friendly. Consider reviewing the resume’s format or content for compatibility with ATS systems.

