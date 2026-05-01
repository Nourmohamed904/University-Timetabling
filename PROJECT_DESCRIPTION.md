# UniTime: Comprehensive University Timetabling System

UniTime is an open-source, web-based Java application (J2EE/Spring, Hibernate, MySQL) 
that helps universities solve the complex problem of creating conflict-free schedules. 
It's a distributed system where multiple department managers can work together to build 
timetables. The system covers four main areas:

1. **Course Timetabling** – Assigns classes to rooms and time slots while respecting hundreds of department-specific constraints.
2. **Examination Timetabling** – Schedules exams in periods and rooms, minimizing conflicts.
3. **Student Sectioning** – Places individual students into the right class sections based on course requests and demand.
4. **Event Management** – Manages room bookings for non-academic events.

The software is divided into four main technical layers:

| Layer                 | Location                                                  | What it does
|-----------------------|-----------------------------------------------------------|
| **Model (Hibernate)** | `JavaSource/org/unitime/timetable/model/`                 | Database entities: classes, rooms, instructors 
| **Solver**            | `JavaSource/org/unitime/timetable/solver/`                | Constraint programming engine that finds optimal schedules
| **Actions/Services**  | `JavaSource/org/unitime/timetable/action/` and `server/`  | Business logic that responds to user requests       
| **UI (GWT/FTL)**      | `JavaSource/org/unitime/timetable/gwt/` and `WebContent/` | Web interface that users see                         