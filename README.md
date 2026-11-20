System Requirements & Architecture Specification

Rwanda -FOOTBALL LEAGUE MANAGEMENT SYSTEM ANALYSIS
1. Brief Introduction
The Rwanda Football League Management System is a modern React-based web application designed to improve the management and organization of football league activities. The system provides a centralized platform where league administrators can manage football teams, schedule matches, record results, and publish football news. It also allows football fans to access league information, follow their favorite teams, and stay updated on upcoming matches and results. The system aims to improve communication between league administrators, football teams, and supporters while making football information easily accessible.

Key Components
User Authentication and Authorization: Allows users to register and log in, with role-based access control (RBAC) distinguishing administrators from normal users and fans.
Team Management: Enables administrators to add, update, delete, and manage detailed football team profiles, rosters, and standings.
Fixture Scheduling and Result Tracking: Allows administrators to schedule matches, update match statuses, and record scores with automated standings calculation.
News Publishing System: Enables administrators to publish, edit, and categorize official football news and match reports.
User Favorites System: Allows fans to select and follow their favorite football teams for personalized updates.
2. Problem Statement
Currently, football league management, particularly in regional areas, faces several challenges due to reliance on manual processes and disconnected information systems.

Major Problems
Disorganized Fixture Management: Managing match schedules using spreadsheets can lead to scheduling conflicts and difficulties in updating fixtures.
Manual Score Tracking: Recording match scores manually can result in errors and inaccurate league standings.
Lack of a Centralized News Platform: Football fans may struggle to find reliable and official league news.
Limited Digital Presence for Smaller Teams: Some football teams lack an online platform to present their profiles and achievements.
Football League Management System Analysis
Page 1 of 4
Inefficient Communication: Communication between league organizers, football teams, and fans can be difficult when information is shared through fragmented channels.
Proposed Solution
A centralized React single-page application (SPA) backed by a REST API and relational database for managing all football league activities.
Organized fixture creation and conflict-free scheduling.
Efficient match result recording and automatic league table updates.
An official platform for publishing categorized football news.
Digital team profiles showcasing rosters, stats, and achievements.
Fan engagement through a personalized favorite team dashboard.
3. Objectives
The main objective of this system is to improve football league management by providing a centralized, responsive, and efficient digital platform for administrators, teams, and fans.

3.1 For League Administrators
Efficient management of football teams and player information.
Easy creation and scheduling of football fixtures.
Accurate recording and updating of match results.
Publishing and managing football news.
Managing user accounts and role-based access permissions.
3.2 For Football Teams
Establishing a digital presence through dedicated team profiles.
Accessing official match schedules and venue details.
Monitoring team performance, points, and match results.
Increasing visibility to football supporters.
3.3 For Football Fans
Accessing football league information from one unified platform.
Following their favorite football teams.
Receiving official football news and updates.
Viewing upcoming match schedules.
Checking live and completed match results alongside league standings.
Football League Management System Analysis
Page 2 of 4
4. Data Flow Diagram (DFD)
The Data Flow Diagram illustrates how information moves between administrators, normal users, the Football League Management System, and its database. Information flows bidirectionally between external actors, the React frontend communicating via API endpoints, and the relational data storage.

4.1 DFD Level 0 (Context Diagram)
The Level 0 Context Diagram establishes the global boundary of Process 0.0 (Football League Management System) and details all primary inputs and outputs interacting with external entities and data stores.

External Entity	Inputs to the System	Outputs from the System
League Administrator	
Login credentials
Team and player details
Match fixtures
Match scores and results
News articles
Authentication status
Confirmation messages
Updated league tables
Published news feeds
Normal User / Football Fan	
Registration and login details
Favorite team selections
Search and filter queries
Team profiles
Upcoming fixtures
Match results and standings
Official news articles
Personalized favorite team feed
Centralized Data Store: League Relational Database comprising Users, Teams, Fixtures, Results, News, and Favorites tables.

4.2 DFD Level 1 (Process Decomposition)
The core system process (0.0) is decomposed into five primary sub-processes that handle specific functional domains:

1.0 User Authentication & Role Management: Processes registration and login requests, validates credentials against the Users Data Store, and issues session tokens containing Role-Based Access Control (RBAC) claims (Admin vs. Fan).
2.0 Team & Roster Management: Handles administrative CRUD operations on the Teams Data Store, managing club details, player rosters, head coach information, and stadium assignments.
3.0 Fixture Scheduling & Result Processing: Receives schedule parameters, validates venue availability to prevent conflicts, writes upcoming matches to the Fixtures Data Store, ingests final match scores, and automatically calculates points to update the Standings store.
4.0 News & Content Management: Ingests rich content articles, categorizes updates, and writes directly to the News Data Store for immediate public dissemination.
Football League Management System Analysis
Page 3 of 4s.
4.3 Frontend Data Flow Diagram (React Architecture)
The diagram below illustrates how data flows across the React frontend layers—from user interactions in public and administrative views, through routing and client state management, to the REST API service layer.

 <img width="787" height="219" alt="image" src="https://github.com/user-attachments/assets/9ae42ce5-e5ff-47ab-a06d-023df949c584" />

Figure 1: Frontend Data Flow Diagram showing unidirectional UI updates and bidirectional API synchronization across the React application.
5. Technical Architecture & React Implementation Overview
The System Architecture leverages a modern React Single-Page Application (SPA) structure mapped directly to the functional requirements identified in this analysis.

Frontend Architecture (React)
Routing Layer: Implemented via react-router-dom, maintaining strict separation between public routes (Fan Portal, Standings, News Feed) and protected routes restricted to authenticated administrative roles (Admin Dashboard, Score Entry, Team Configuration).
State & Data Synchronization: Utilizes React Context API or Redux for global application state (user session, active role, preference persistence) combined with React Query or Axios for server state management, enabling efficient API caching and automatic UI refetching upon data updates.
Component Model: Structured using a modular, reusable component hierarchy featuring isolated modules for Team Cards, Match Tables, Live Score Badges, and News Feed Containers.
Core Database Entities
Entity	Primary Attributes & Schema Structure
Users	id, name, email, password_hash, role (Admin / Fan)
Teams	id, name, logo, coach, stadium, points, stats
Matches	id, home_team_id, away_team_id, date, venue, home_score, away_score, status
News	id, title, category, content, author_id, published_at
Favorites	user_id, team_id
Football League Management System Analysis
Page 4 of 4
