for spec driven development: 



1st: first question: is the problem statement why are you developing this feature. 



2nd: what are the functional requirements: 



3rd: how the feature is will get the input and what will be the output. 



4th: constrains: 



**5th**: edge cases and errore handling.



6th: acceptance criteria. 



docs link: https://gemini.google.com/share/0efd6f566a9e



now diving deep into each step by making the example of developing the feature of chat sidebar like the chatgpt, gemini and other ai's have. 



**1. Problem Statement**



As users interact with the application, they create multiple conversations over time. However,

there is currently no easy way to revisit or continue past chats.



This makes it difficult for users to:



. Find previous discussions



. Resume earlier conversations



. Manage multiple chat threads



Solution: This feature introduces a chat history sidebar to solve this problem.



2\. Functional Requirements



The system should:



\* Display a sidebar showing a list of past chats

\* Show a short, readable title for each chat

\* Automatically generate the title from the user's first message

\* Allow users to click on any chat to open it



\* Highlight the currently active chat



\*  Add a new chat to the list after the first message is sent



\* Display chats in order from most recent to oldest



3\. inputs and outputs: Chat Opening Behavior



USER ACTION (INPUT)

When a user clicks on a chat from the sidebar



EXPECTED SYSTEM BEHAVIOR

. Open the selected chat in the main chat

area

. Display the full conversation

. Show messages in the order they were

originally sent

. Highlight the selected chat in the sidebar





4\. Constraints



The sidebar should load quickly (within 1

second for typical usage)







Titles should be short and readable

(shortened with " ... " if too long)



The sidebar should work properly on

standard laptop screens







The system should handle a reasonable

number of chats smoothly





5\. Edge Cases and Error Handling



No previous chats exist



\+ Show message: "No chat history yet"



User clicks a chat that cannot be loaded



\+ Show message: "This chat could not be opened"



Very long first message



\+ Use only the first part as the title



Multiple chats with similar titles



\+ Allowed \[each chat is still unique)



System fails to load chats



\+ Show message: "Unable to load chat history. Please try again."



Large number of chats



Sidebar should remain scrollable





6\. Acceptance Criteria



This feature is considered complete if:



Users can see a list of their past chats



The correct conversation is displayed every

time



Users can click and reopen any chat



The active chat is clearly highlighted



New chats appear automatically after first

use



Chats are ordered from most recent to

oldest



Empty and error states are handled properly



Long titles are displayed neatly without

breaking the layout





spec driven development workflow: 



Spec --> Review --> Design --> Review --> Tasks --> Build --> Validate



-->spec: in spec stage we have just created the spec discussed why and what. 



-->Review:in review stage we review the spec that we generated so we don't miss anything and there should not be mistakes in it.



-->Design:  in this we discuss about how all the technical details. how technically we are going to convert it into code. 



complete design example: by chat sidebar: https://gemini.google.com/share/3616690f1849



Design Plan: Chat History Sidebar

Technical specification for implementing a scalable, real-time chat history sidebar with

React, FastAPI, and PostgreSQL.



1\. Objective



Implement a chat history sidebar that allows users to:



. View previous chats



. Reopen any chat



. Identify the currently active chat



. Keep chats ordered by recent activity



. Continue conversations seamlessly



Frontend: React



2\. Tech Stack



Backend: FastAPI



Database: PostgreSQL / SQLite



ORM: SQLAlchemy (asyne]



Why this stack?



React is excellent for dynamic UI such as chat sidebars.



FastAPI works well for API-based high-concurrency chat systems.



Relational DBs are a natural fit because chats and messages have a clear 1-to-many

relationship.



3\. High-Level Architecture



The feature is divided into three distinct layers of responsibility:



00



A. Frontend (React)

. Render sidebar \& window

. Track active chat

. Show loading/error states



B. Backend (FastAPI)

. Return chat summaries

. Return full conversations

. Create/append messages



C. Database



. Store chats \& messages

. Maintain relationships

. Support ordered retrieval



ARCHITECTURE FLOW



Frontend \[React)



Backend \[FastAPI)



Database (PostgreSQL / SQLite)





4\. Data Model



We need two main entities: Chat (represents the conversation thread) and Message

(represents individual messages). One chat has many messages.



PYTHON (SQLALCHEMY]



from sqlalcheny import Column, String, DateTime, ForeignKey, Text

from sqlalcheny.orm import relationship

from sqlalcheny.sql import func

from database import Base



ctass Chat(Base):

tabtenane\_ = "chats"



id = Column(String, primary\_key=True)

title = Column(String, nullable=False]

created\_at = Column(DateTime(timezone=True), server\_default=func.now\[))

updated\_at = Column(DateTime(timezone=True), server\_default=func.now(), onupdate=func.now())



messages = relationship("Message", back\_populates="chat", cascade="all, delete-orphan")



class Message(Base):

\_tablenane\_ = "nessages"



id = Column(String, primary\_key=True)

chat\_id = Column(String, ForeignKey("chats.id"), nullable=False)

role = Column\[String, nullable=False)

\# "user" or "assistant"

content = Column(Text, nullable=False)

created\_at = Column(DateTime(timezone=True), server\_default=func.now())



chat - relationship("Chat", back\_populates="messages")



5\. Core Design Decisions



Decision 1: Store chats and messages separately

Why: A chat contains metadata, while messages vary in number. Separation makes retrieval and

ordering efficient.



Decision 2: Use updated\_at to sort chats

Why: The sidebar should surface most recently active chats first. Updating this timestamp on new

messages naturally handles sorting.



Decision 3: Fetch summaries for sidebar

Why: Sidebar load times must be fast. Fetching thousands of message contents upfront.





6\. Core Functional Flows



A. Load Sidebar



Triggered on app open. Requests summaries sorted by updated\_at DESC.



JSON (RESPONSE)



"id": "chat\_101",

"title": "Explaim overfitting",

"updated\_at": "2026-84-06T10:15:00"



B. Open Chat



Triggered by click. Requests full chat + messages ordered by created\_at ASC.



PYTHON (QUERY)



stmt = (

select (Message)

.where(Message,chat\_id == chat\_id)

.order\_by(Message.created\_at.asc\[)>





C. Title Generation



Titles are generated from the first user message, truncated if necessary.



PYTHON



def generate\_chat\_title(first\_message: str, rax\_len: int = 58) -> str:

title = first\_message.strip()

if len(title) <= max\_len:

return title

return title\[:max\_len]. rstrip() + " ... "







7\. Development Plan



1

Database \& Models

Create models, establish relationships, and apply indexes to `updated\_at` and `chat\_id`.



2

Backend APIs

Implement FastAPI routes for fetching summaries, single chats, and appending messages.



3

Frontend UI

Build React Sidebar, ChatWindow, wiring clicks, and handling empty/loading states. 





Q: why two documents?



because in future if you want to move from one stack to another stack then its easy. I don't have to rewrite the spec document. 



the process is again review this design phase. 



and after that



Tasks: define what tasks to achieve. 



tasks docs link: gemini.google.com/share/81ffef0ead42



example of tasks phase: 



Chat App Implementation Plan

🔹 1. Database \& Models

Create Chat and Message tables

Define one-to-many relationship

Add indexes (updated\_at, chat\_id)

🔹 2. Backend (FastAPI)

Implement core APIs:

GET /chats → fetch chat summaries (sorted by recency)

GET /chats/{id} → fetch full chat (ordered messages)

POST /chats → create new chat (generate title + store first message)

POST /chats/{id}/messages → append message + update updated\_at

Add:

title generation logic

error handling

🔹 3. Frontend (React)

Build UI components:

ChatSidebar → list chats, highlight active, handle empty/error

ChatWindow → display messages

Manage state:

chat list

selected chat

loading + error states

Implement flows:

load sidebar

open chat

create chat

append message

🔹 4. Integration

Connect frontend with backend APIs

Ensure correct ordering:

chats → recent first

messages → chronological

Update sidebar dynamically





in building phase we build the feature. 



then after that validation part comes. fulfilled the acceptance criteria. 







how i am going to use this. 



I will instruct the ai to create the spec for me. 



( tip: create the custom slash command to create the spec document ) 



for design phase: use ai to create the technical design ( plan mode can be used). 



after the technical design we have to verify each 



then ai will create tasks for us like creating to-dos. 



then it will build it .



then we have to validate it. 



now how we gona integrate GitHub: 



first we pull all the latest changes from GitHub then create the new branch and then switch to that branch. 





after completing the phase git commit it 



--> git push --> create and merge PR --> delete the branch --> switch to main branch. 

