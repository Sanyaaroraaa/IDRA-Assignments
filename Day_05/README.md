<div align="center">

# 🏨 Hotel Room Booking System
### *Day 05 Core Mini Project | Python OOP & State Management*

![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-2ea44f?style=for-the-badge)
![Architecture](https://img.shields.io/badge/Architecture-Modular_OOP-8A2BE2?style=for-the-badge)

<p align="center">
  An end-to-end, menu-driven hotel reservation and inventory management application designed to handle real-time room availability, booking records, bill calculations, and cancellations.
</p>

</div>

---

## 📑 Table of Contents
- [Executive Overview](#-executive-overview)
- [System Architecture](#-system-architecture)
  - [High-Level Component Flow](#1-high-level-component-flow)
  - [Class & Domain Model](#2-class--domain-model)
  - [Transactional State Lifecycle](#3-transactional-state-lifecycle)
- [Core Feature Matrix](#-core-feature-matrix)
- [In-Memory Data Schemas](#-in-memory-data-schemas)
- [Setup & Execution Guide](#-setup--execution-guide)

---

## 📌 Executive Overview

The **Hotel Room Booking System** simulates real-world hotel front-desk operations. It manages room availability pools across multiple tiers (Standard, Deluxe, Suite), computes stay-duration pricing dynamically, records guest transactions, and guarantees state consistency with automatic inventory rollback during cancellations.

---

## 🏗️ System Architecture

### 1. High-Level Component Flow

```mermaid
flowchart TD
    CLI([👤 User / Front Desk CLI]) --> Router{Select Action}

    Router -->|1. View Rooms| CheckModule[Availability & Catalog Engine]
    Router -->|2. Book Room| BookingModule[Reservation & Allocation Engine]
    Router -->|3. View Bookings| LedgerModule[Guest Ledger & Directory Engine]
    Router -->|4. Cancel Booking| CancellationModule[Cancellation & Release Engine]
    Router -->|5. Exit| Terminate([Graceful Shutdown])

    CheckModule <--> RoomDB[(Room Inventory)]
    BookingModule <--> RoomDB
    BookingModule ---> BookingDB[(Bookings Ledger)]
    LedgerModule <---> BookingDB
    CancellationModule <---> BookingDB
    CancellationModule <---> RoomDB
```

---

### 2. Class & Domain Model

```mermaid
classDiagram
    class HotelSystem {
        -dict rooms_inventory
        -dict active_bookings
        +display_available_rooms()
        +book_room(guest_name, room_type, nights)
        +cancel_reservation(booking_id)
        +view_active_bookings()
    }

    class Room {
        -int room_no
        -str room_type
        -float price_per_night
        -bool is_available
        +set_status(status)
    }

    class BookingRecord {
        -str booking_id
        -str guest_name
        -int room_no
        -int duration_nights
        -float total_amount
    }

    HotelSystem "1" *-- "many" Room : manages
    HotelSystem "1" *-- "many" BookingRecord : tracks
```

---

### 3. Transactional State Lifecycle

```mermaid
stateDiagram-v2
    [*] --> Available : Room Initialized
    Available --> Blocked : Booking Requested
    Blocked --> Confirmed : Details Validated & Bill Computed
    Blocked --> Available : Validation Failed / Cancelled
    Confirmed --> Occupied : Active Reservation
    Occupied --> Available : Booking Cancelled / Released
    Available --> [*] : Exit System
```

---

## ✨ Core Feature Matrix

| Feature | Implementation Logic | Operational Outcome |
| :--- | :--- | :--- |
| **Inventory Querying** | Categorical filtering on room map | Real-time status lookup by room category & rate |
| **Smart Allocation** | First-available room ID resolution | Eliminates room collisions and double-booking |
| **Dynamic Billing** | Nightly rate $\times$ duration calculator | Computes total costs instantly |
| **Atomic Cancellation** | Reversible transaction state | Frees room flag and purges booking ledger entry |
| **Input Validation** | Defensive loops & input guards | Prevents unexpected crashes on invalid inputs |

---

## 🗄️ In-Memory Data Schemas

### `Room` Schema
```json
{
  "room_number": 101,
  "room_type": "Deluxe",
  "price_per_night": 2500.0,
  "is_available": true
}
```

### `BookingRecord` Schema
```json
{
  "booking_id": "RES-101",
  "guest_name": "John Doe",
  "room_number": 101,
  "room_type": "Deluxe",
  "nights": 3,
  "total_bill": 7500.0,
  "status": "CONFIRMED"
}
```

---

## 🚀 Setup & Execution Guide

1. Open `Hotel_Room_Booking_System.ipynb` in **Jupyter Notebook**, **VS Code**, or **Google Colab**.
2. Run all cells in order (`Restart & Run All`) to start the interactive console interface.
