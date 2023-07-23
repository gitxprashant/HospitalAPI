# Hospital API

This is an easy-to-use API designed for hospitals to manage health records of COVID-19 patients. It allows doctors and hospital staff to register, log in, register patients, and create reports for each visit. The API also provides features to retrieve a patient's records and filter reports by status.

The API is built using Node.js and MongoDB, which are popular technologies for building web applications. It uses JSON Web Tokens (JWT) for secure authentication. The project is organized into different folders to make it easier to understand and maintain the code.

Overall, this API simplifies the process of managing COVID-19 patient records for hospital staff, ensuring security and scalability.

## Installation

To install and run the application, follow the steps below:
1. Clone the repository - `git clone https://github.com/gitxprashant/HospitalAPI.git`
2. Navigate to the project directory
3. Install the dependencies - `npm install` or `npm i`
4. Start the server: `npm start`
5. Open the app in your web browser at `http://localhost:7200`

## Dependencies

CN Hospital API requires the following dependencies:

-   `express` - Web framework for Node.js
-   `jsonwebtoken` - Generates and verifies JSON web tokens (JWTs)
-   `mongoose` - ODM (Object-Document Mapping) library for MongoDB and Node.js
-   `express-session` - for managing user sessions in Express.js applications.
-   `passport` - Authentication middleware for Node.js
-   `passport-jwt` - Passport strategy for authenticating with a JSON Web Token (JWT)
-   `nodemon` - IT automatically restarts node application when it detects any changes.

## Schemas
- Doctor Schema
```javascript
({
    username: {
        type: String,
        required: true
    },
    password: {
        type: String,
        required: true 
    },
    name: {
        type: String,
        required: true
    },
},
    {
        timestamps: true,
    }
)
```
- Patient Schema

```javascript
({
    phone: {
        type: Number,
        required: true
    },
    name: {
        type: String  
    },
    age: {
        type: Number
    },
    gender: {
        type: String
    },
},
    {
        timestamps: true
    }
)
```
- Report Schema

```javascript
({
    doctor: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'Doctor'
    },
    patient: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'Patient'
    },
    status: {
        type: String,
        enum: [
            'Negative',
            'Travelled-Quarantine',
            'Symptoms-Quarantine',
            'Positive-Admit',
        ],
        default: 'Negative'
    },
    date: {
        type: Date,
        required: true
    }
},
    {
        timestamps: true,
    }
)
```
