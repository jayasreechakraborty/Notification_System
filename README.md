#  Notification Service

A scalable **multi-channel notification system** built with **FastAPI**, **RabbitMQ**, and **SQLAlchemy**. The service processes notifications asynchronously and supports **Email, SMS, and In-App** notifications through a unified REST API.

---

## ✨ Features

- 📧 Send Email notifications
- 📱 Send SMS notifications using Twilio
- 🔔 Store and retrieve In-App notifications
- ⚡ Asynchronous message processing with RabbitMQ
- 🚀 RESTful API built with FastAPI
- 🗄️ Database support with SQLite/PostgreSQL
- 📖 Interactive Swagger API documentation
- ☁️ Deployable on Render with Docker support

---

## 🔄 System Flow

1. **Client** sends a notification request to the FastAPI API.
2. **FastAPI** validates the request and publishes it to a RabbitMQ queue.
3. **RabbitMQ** stores the message and delivers it to the worker service.
4. **Worker Service** processes the notification based on its type:
   - 📧 Email → Sent using SMTP
   - 📱 SMS → Sent using Twilio
   - 🔔 In-App → Stored in the database
5. For **In-App** notifications, users can retrieve their notifications using the API endpoint.

```text
Client
   │
   ▼
FastAPI API
   │
   ▼
RabbitMQ Queue
   │
   ▼
Worker Service
   ├── 📧 Email (SMTP)
   ├── 📱 SMS (Twilio)
   └── 🔔 In-App (SQLite/PostgreSQL)
```

---

## 🛠️ Tech Stack

- Python
- FastAPI
- RabbitMQ
- SQLAlchemy
- SQLite / PostgreSQL
- Twilio
- Pika
- Docker
- Render

---

## 📂 Project Structure

```text
notification_services/
│
├── db/
│   ├── database.py
│   └── models.py
│
├── services/
│   ├── email.py
│   ├── sms.py
│   ├── in_app.py
│   ├── queue_publisher.py
│   └── credentials.py
│
├── main.py
├── worker.py
├── requirements.txt
├── render.yaml
└── README.md
```

---

## 🚀 Getting Started

### Clone the Repository

```bash
git clone https://github.com/yourusername/notification_services.git

cd notification_services
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Configure Environment Variables

Create a `.env` file using the provided `.env.example` and configure:

- RabbitMQ URL
- Database URL
- SMTP Credentials
- Twilio Credentials

### Start RabbitMQ

Run RabbitMQ locally or using Docker.

```bash
docker run -d --name rabbitmq \
-p 5672:5672 \
-p 15672:15672 \
rabbitmq:management
```

### Run the API

```bash
uvicorn main:app --reload
```

### Start the Worker

```bash
python worker.py
```

---

## 📌 API Endpoints

| Method | Endpoint | Description |
|---------|----------|-------------|
| POST | `/notify` | Queue a notification |
| GET | `/notifications/{user_id}` | Retrieve user notifications |
| GET | `/health` | Service health check |

Once the server is running, access the interactive API documentation at:

```
http://localhost:8000/docs
```

---

## 🌐 Live Demo

**Deployed on Render**

https://notification-system-4m5j.onrender.com

---

## 🔮 Future Enhancements

- User Authentication & Authorization
- Push Notification Support
- Notification Templates
- Rate Limiting
- Scheduled Notifications
- Notification Analytics
- User Preference Management
- Automated Testing

---

## 👨‍💻 Author

**Made with ❤️ using Python, FastAPI, and RabbitMQ**

If you found this project helpful, consider giving it a ⭐ on GitHub.

---

## 📜 License

This project is licensed under the **MIT License**.
