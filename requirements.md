# Product Requirements

## 1. Product vision

Deliver a modern, automated library platform that streamlines circulation workflows, reduces manual administration, and provides an intuitive digital catalog for an academic community.

## 2. User personas

| Persona | Primary goals | Pain points to validate | Potential product support |
|---|---|---|---|
| Student | Find resources and understand due dates | Slow searches, unclear availability, unexpected fines | Search portal, availability status, due-date reminders |
| Librarian | Issue/return books and maintain catalog accuracy | Repeated data entry, stock discrepancies | Catalog tools, circulation workflow, fine tracking |
| Library administrator | Understand utilization and produce reports | Scattered data, time-consuming reports | Usage dashboard, audit trail, report export |
| Faculty member | Locate and borrow teaching/research material | Unclear availability and renewal process | Search, availability, borrowing history |

## 3. Functional requirements

- **FR-01 Authentication and authorization:** Support role-based access for administrators, librarians, students, and faculty.
- **FR-02 Catalog management:** Create, read, update, and delete book records, authors, categories, and shelf locations.
- **FR-03 Search:** Search catalog records by relevant fields and show availability.
- **FR-04 Circulation:** Record check-out, check-in, and renewal transactions while keeping inventory consistent.
- **FR-05 Fine calculation:** Calculate overdue penalties according to approved library rules and member categories.
- **FR-06 Notifications:** Support due-date and overdue notifications.
- **FR-07 Reporting:** Provide basic inventory, circulation, overdue, and usage reports.
- **FR-08 Audit history:** Record important administrative and circulation changes.

## 4. Non-functional requirements

- **NFR-01 Security:** Hash passwords with a suitable password-hashing algorithm, enforce authorization, and protect traffic with HTTPS in production.
- **NFR-02 Performance:** Establish measurable response-time targets and test them under representative load.
- **NFR-03 Availability and scalability:** Design for reliable operation and allow the deployment architecture to scale when needed.
- **NFR-04 Maintainability:** Keep modules clearly separated, document configuration, and automate repeatable checks.
- **NFR-05 Data integrity:** Prevent invalid circulation states and maintain consistent inventory and transaction records.
- **NFR-06 Accessibility and usability:** Use clear labels, understandable errors, and accessible interaction patterns.

## 5. MVP scope

### Included in the first release

1. Login and role-based access
2. Book search and availability
3. Basic issue and return transactions
4. Fine calculation based on configured rules
5. Basic administrative reporting

### Deferred until validated

- AI-powered recommendations
- Third-party payment integration
- Mobile self-checkout and hardware integrations
- Advanced predictive analytics

## 6. Acceptance criteria examples

- A user can search for a book and see whether it is available.
- An authorized librarian can issue an available book to an eligible member.
- Returning a book updates its circulation status and availability.
- An overdue fine is calculated using the configured rule and is explainable to staff.
- A user without the required role cannot access restricted administrative operations.

## 7. Assumptions and open questions

- Which borrowing quotas and membership categories does the library use?
- What are the approved fine rates, grace periods, and renewal rules?
- Does the library already have a catalog or member database to integrate?
- Which notification channels are approved?
- What privacy, retention, and accessibility requirements apply?

These questions should be resolved with library stakeholders before implementation.
