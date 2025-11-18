# Events Aggregator

> A full-stack web application that bridges the gap between colleges and students for seamless event management and participation.

## What is this project?

Hey there! This is my Events Aggregator project - a platform I built to solve a real problem we face in college: keeping track of all the amazing events happening around campus.

The idea is simple: colleges can post their events, and students can browse and register for them all in one place. No more missing out on cool workshops, seminars, or cultural fests because you didn't see that poster in the hallway!

## Features

### For Students
- Browse events from all colleges in one centralized platform
- Register for events with just a few clicks
- View all your registered events in a personalized dashboard
- Get email notifications when new events are posted
- Search and filter events by category

### For Colleges
- Create and manage events with ease
- Upload event images and add registration links
- Track event participants
- View and manage only your college's events
- Automatic email notifications sent to all students when you post an event

## Tech Stack

I built this using the MERN stack:

**Frontend:**
- React.js - for building the user interface
- React Router - for navigation between pages
- Axios - for making API calls
- CSS - for styling (custom styles, no framework)

**Backend:**
- Node.js & Express.js - for the REST API
- MongoDB & Mongoose - for the database
- JWT - for secure authentication
- Multer - for handling image uploads
- SendGrid - for sending email notifications
- Nodemailer - for the contact form emails

## Getting Started

### Prerequisites

Before you begin, make sure you have these installed:
- Node.js (v14 or higher)
- MongoDB (local or cloud instance)
- npm or yarn package manager

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd Events-Aggregator-main
   ```

2. **Set up the Backend**
   ```bash
   cd backend
   npm install
   ```

   Create a `.env` file in the `backend` directory:
   ```env
   MONGODB_URI=your_mongodb_connection_string
   JWT_SECRET=your_secret_key_here
   SEND_GRID=your_sendgrid_api_key
   PORT=4000
   ```

3. **Set up the Frontend**
   ```bash
   cd ../frontend
   npm install
   ```

   Create a `.env` file in the `frontend` directory:
   ```env
   REACT_APP_API_URL=http://localhost:4000
   ```

### Running the Application

You need to run both the backend and frontend servers:

1. **Start the Backend** (from the `backend` directory)
   ```bash
   npm start
   ```
   The backend server will start on http://localhost:4000

2. **Start the Frontend** (from the `frontend` directory)
   ```bash
   npm start
   ```
   The frontend will start on http://localhost:3001

3. **Open your browser** and navigate to http://localhost:3001

## How It Works

### Authentication System

The app has two types of users with separate authentication flows:

1. **Students** - Can browse and register for events
2. **Colleges** - Can create and manage events

Both use JWT (JSON Web Tokens) for secure authentication. When you log in, you get a token that's stored in your browser's localStorage, which is used to verify your identity for subsequent requests.

### Key Functionalities

**Event Creation Flow (Colleges):**
1. College logs in to their dashboard
2. Fills out the event creation form with details and uploads an image
3. When submitted, the event is saved to the database
4. Automatically sends email notifications to ALL registered students
5. Event appears on the public events page

**Event Registration Flow (Students):**
1. Student browses events on the public events page
2. Clicks to view event details
3. Registers for the event
4. Student's ID is added to the event's participants list
5. Event appears in the student's dashboard

## Project Structure

```
Events-Aggregator-main/
├── backend/
│   ├── models/           # Database schemas (User, College, Event)
│   ├── routes/           # API route handlers
│   ├── middlewares/      # Authentication middleware
│   ├── emailnotif/       # SendGrid email integration
│   ├── uploads/          # Uploaded event images
│   └── server.js         # Main server file
├── frontend/
│   ├── src/
│   │   ├── components/   # React components
│   │   ├── styles/       # CSS files
│   │   └── App.js        # Main app component with routing
│   └── public/           # Static assets
└── README.md
```

## API Endpoints

### Authentication
- `POST /api/auth/student/signup` - Student registration
- `POST /api/auth/student/login` - Student login
- `POST /api/auth/college/signup` - College registration
- `POST /api/auth/college/login` - College login

### Events
- `GET /api/events/all` - Get all events (public)
- `POST /api/events` - Create new event (colleges only)
- `GET /api/college/events` - Get college's events
- `GET /api/student/events` - Get student's registered events
- `POST /api/student/register-event` - Register for an event

### Other
- `POST /send-email` - Contact form submission

## Challenges I Faced & What I Learned

1. **Authentication with two user types** - Had to figure out how to handle JWT tokens for both students and colleges with different access levels
2. **Email notifications** - Integrating SendGrid and handling base64 image encoding for email templates was tricky
3. **File uploads** - Learning multer and setting up proper file storage for event images
4. **CORS issues** - Spent time debugging cross-origin requests between frontend and backend

## Password Requirements

For security, passwords must:
- Be at least 8 characters long
- Include at least one uppercase letter
- Include at least one lowercase letter
- Include at least one number
- Include at least one special character (@$!%*?&#)
- Contain no spaces

## Future Improvements

Some ideas I'm thinking about for v2.0:
- Add event categories and filtering
- Implement event search functionality
- Add QR code generation for event tickets
- Include event reminders via email/SMS
- Add photo galleries from past events
- Implement rating and review system for events
- Add calendar integration (Google Calendar, iCal)

## Environment Variables Reference

Make sure to set up these environment variables:

**Backend (.env):**
```env
MONGODB_URI=<your-mongodb-connection-string>
JWT_SECRET=<your-jwt-secret>
SEND_GRID=<your-sendgrid-api-key>
PORT=4000
```

**Frontend (.env):**
```env
REACT_APP_API_URL=http://localhost:4000
```

For production deployment, change `REACT_APP_API_URL` to your deployed backend URL.

## Deployment

### Backend Deployment (Render/Railway/Heroku)
1. Push your code to GitHub
2. Connect your repository to your hosting platform
3. Set environment variables in the platform's dashboard
4. Deploy!

### Frontend Deployment (Vercel/Netlify)
1. Build the frontend: `npm run build`
2. Connect your repository to Vercel/Netlify
3. Set `REACT_APP_API_URL` to your deployed backend URL
4. Deploy!

## Screenshots

*Coming soon! Will add screenshots of the dashboard, event pages, and registration flow.*

## Contributing

If you have any suggestions or find any bugs, feel free to open an issue or submit a pull request. I'm always looking to improve this project!

## License

This project is licensed under the ISC License.

## Contact

If you have any questions or want to connect, feel free to reach out through the contact form in the app!

---

**Note:** This was built as a learning project to understand full-stack development with the MERN stack. If you're a student looking to learn web development, feel free to use this as a reference!

