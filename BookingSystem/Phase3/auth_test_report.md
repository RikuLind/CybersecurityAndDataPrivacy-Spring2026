# Auth Test Report - Riku Lind NTIS23K

---

## Testing information
- System: https://localhost:8004
- Test date and time: 1.3.2026 15.00-18.00
- Tester: Riku Lind

## List of pages and endpoints discovered manually and using ZAP, Gobuster and wfuzz

- http://localhost:8004/
- http://localhost:8004/login
- http://localhost:8004/logout
- http://localhost:8004/resources
- http://localhost:8004/reservation
- http://localhost:8004/api/reservation
- http://localhost:8004/api/resources
- http://localhost:8004/api/users
- http://localhost:8004/api/session

---

## Most critical issues

- Guest can access /api pages
- /api/users reveals information about users on the website, even to guest user
- ID-based pages reveal other users' bookings
- Reserver can modify resources made by other users

## Guest

### Allowed actions
- Login
- Register
- Can access resource creation via address bar with /resources and add a resource
- Can access reservation page via address bar with /reservation, but shows unauthorized
- Can access /api/reservation, /api/users and /api/resources

### Restricted actions
- Create a reservation, always shows unauthorized
- Access or delete existing reservation, not even via address bar

---

## Reserver

### Allowed actions
- Add a resource
- Create a reservation
- Update existing reservations owned by anyone via address bar with /resources?=id
- Delete own existing reservations
- Was able to create a reservation using the resource made by guest
- Updated a reservation made by admin user, made it owned by reserver and could delete it afterwards
- Can access all /api pages

### Restricted actions
- Delete existing reservations owned by others
- Delete existing resources owned by others
- Access existing resources via the website buttons

---

## Administrator

### Allowed actions
- Can add a resource
- Can create a reservation
- Can update existing resources
- Can delete existing reservations
- Can access all /api pages

### Restricted actions
- Can't delete a user account
- Can't delete existing resources

## Summary of role capabilities
- Guest users can access hidden pages via the address bar and therefore have too much information available
- Reservers have access to other users' bookings and resources and can modify them freely, even change them so they can be deleted
- Administrators can't delete users or existing resources