---
name: Database Integration and Data Persistence
about: Implement proper database storage to replace in-memory data
title: 'Implement Database Integration and Data Persistence'
labels: enhancement, database, backend, high-priority
assignees: ''
---

## Overview
Replace the current in-memory data storage with a proper database solution to ensure data persistence across application restarts.

## Current State
- Activities are stored in a Python dictionary
- Data is lost when the application restarts
- No data backup or recovery capabilities

## Proposed Implementation
- [ ] Choose database solution (PostgreSQL or SQLite for development)
- [ ] Add database dependencies to requirements.txt (SQLAlchemy, Alembic)
- [ ] Create database models for activities and participants
- [ ] Implement database connection and session management
- [ ] Add migration support for database schema changes
- [ ] Create data seed scripts for initial activities
- [ ] Add error handling for database operations
- [ ] Update API endpoints to use database operations

## Technical Details
```python
# Example model structure
class Activity(Base):
    __tablename__ = "activities"
    
    id = Column(Integer, primary_key=True)
    name = Column(String, unique=True, nullable=False)
    description = Column(Text)
    schedule = Column(String)
    max_participants = Column(Integer)
    created_at = Column(DateTime, default=datetime.utcnow)
    
class Participant(Base):
    __tablename__ = "participants"
    
    id = Column(Integer, primary_key=True)
    email = Column(String, nullable=False)
    activity_id = Column(Integer, ForeignKey("activities.id"))
    joined_at = Column(DateTime, default=datetime.utcnow)
```

## Acceptance Criteria
- [ ] Activities persist between application restarts
- [ ] Database operations are properly error-handled
- [ ] Database schema can be migrated/updated
- [ ] Initial seed data can be loaded
- [ ] All existing API functionality works with database

## Priority
**High** - Foundation for other features

## Estimated Effort
Medium (2-3 days)
