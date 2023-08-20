---
title: "Modernizing Legacy Systems with Amplication's DB Schema Import"
datePublished: Sun Aug 20 2023 14:53:59 GMT+0000 (Coordinated Universal Time)
cuid: clljpalho00m82rnv5bsrgwp5
slug: modernizing-legacy-systems-with-amplications-db-schema-import
canonical: https://dev.to/yuvalhazaz/modernizing-legacy-systems-with-amplications-db-schema-import-221g
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692551214832/23532d07-f820-44f0-8d07-7b19773f4390.jpeg
tags: programming, backend, webdev

---

Modernizing legacy systems isn’t just about catching up with the latest and greatest tech; it’s about staying competitive. Yet, transitioning away from legacy systems can be daunting, especially with the risk of losing valuable data or facing compatibility issues. The effort involved in setting up numerous data models, crafting Data Transfer Objects (DTOs), and coding boilerplate for hundreds of existing tables, not to mention managing intricate relations, can be massive and time-consuming. This is where our latest feature - **DB Schema Import** - steps in, offering an efficient and seamless way to bring your old infrastructure into the modern era without getting lost in the complexities.

Why modernize with Amplication?
-------------------------------

### Rapid Development

Launch your projects faster. Amplication’s auto-generation tools drastically cut down the development process by handling boilerplate and infrastructure code, saving you months that you'd otherwise spend crafting code for your existing data models.

### Consistency

No more patchwork solutions. Amplication ensures your backend services are consistent, scalable, and up to industry standards.

### Stay in Control

While Amplication streamlines the development process, you retain full ownership and control of your code. It's automation with autonomy.

### Cost Savings

By reducing manual work, the risk of errors and associated costs decrease.

### Efficient Data Integration with the DB Schema Import

Transitioning away from legacy systems doesn’t mean starting from scratch. With the DB Schema Import feature, you can effortlessly bring in your existing database schema, preserving the value of your legacy data and laying the foundation for new, modern applications.

Getting started with DB Schema Import
-------------------------------------

Ready to upgrade your legacy system? Here's a quick guide:

*   **Generate your Prisma schema**: Use [Prisma's introspection](https://www.prisma.io/docs/concepts/components/introspection) to scan your legacy database and produce a **`schema.prisma`** file.
*   **Upload to Amplication**: Once your schema is ready, bring it into Amplication, which will automatically set up your entities, fields, and relations.
*   **Pick your Database**: Select either MySQL or PostgreSQL by installing the appropriate DB plugin.
*   **Build & Commit**: Generate and commit the code for your project via Amplication.

**Check out our [step-by-step guide](https://docs.amplication.com/how-to/import-prisma-schema/) for a deeper dive**

A Real-Life Example
-------------------

Let's dive into an example to demonstrate just how effortless it is to create a fully-functional service using this feature. In this walkthrough, we'll leverage a Prisma Schema file to automate the setup of entities, fields, and relations, laying the groundwork for a fully functioning application to manage events.

*   Create a new ‘Event Management’ service with Amplication
    *   Make sure to select MySQL or PostgreSQL database during the service creation wizard

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551207743/30a25243-c8fb-4bdf-8eab-36bae24bf55b.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--mBIT8gG_--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://static-assets.amplication.com/blog/modernizing-legacy-systems-with-amplications-db-schema-import/0.png)

*   After the service is created, click the “Create entities for my service” option

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551208850/0e8d068a-7646-4a01-a71c-e795c22bfa87.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--MgrXmqhT--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://static-assets.amplication.com/blog/modernizing-legacy-systems-with-amplications-db-schema-import/1.png)

*   Within the entities page, click the “Upload Prisma Schema” button

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551209748/cd32d2c6-5a96-48d2-95eb-f86cfa74b3f8.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--_E3rSz_Y--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://static-assets.amplication.com/blog/modernizing-legacy-systems-with-amplications-db-schema-import/2.png)

*   Upload this sample [Prisma schema file](https://raw.githubusercontent.com/amplication/blog-sample-projects/main/db-import-examples/event-management.prisma)

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551210688/06ff2f17-278d-4c2e-bd8a-4d5875f0eec8.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--nIu5t1KH--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://static-assets.amplication.com/blog/modernizing-legacy-systems-with-amplications-db-schema-import/3.png)

    datasource db {
      provider = "postgresql"
      url      = env("DB_URL")
    }
    
    generator client {
      provider = "prisma-client-js"
    }
    
    model Event {
        id          String      @id @default(uuid())
        name        String
        description String
        startDate   DateTime
        endDate     DateTime
        location    String
        attendees   Attendee[]
        sessions    Session[]
    }
    
    model Attendee {
        id          String      @id @default(uuid())
        name        String
        email       String     @unique
        eventId     String
        tikets      Ticket[]
        event       Event       @relation(fields: [eventId], references: [id])
    }
    
    model Ticket {
        id          String      @id @default(uuid())
        attendeeId  String
        ticketType  TicketType
        attendee    Attendee    @relation(fields: [attendeeId], references: [id])
    }
    
    model Session {
        id          String      @id @default(uuid())
        name        String
        speaker     String
        time        DateTime
        eventId     String
        event       Event       @relation(fields: [eventId], references: [id])
    }
    
    enum TicketType {
        FREE
        PAID
    }
    

Enter fullscreen mode Exit fullscreen mode

*   Watch the log as all the entities are imported.

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551211821/e468e97f-1bb5-461f-ac1a-af4652199df0.jpeg)](https://res.cloudinary.com/practicaldev/image/fetch/s--KEU-ACaH--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://static-assets.amplication.com/blog/modernizing-legacy-systems-with-amplications-db-schema-import/4.png)

*   Once the import is completed, click the entities tab to view all the newly created entities.

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551212812/9c9aae19-6d23-4da8-9149-b8c09ff80e0e.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--53fw25sc--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://static-assets.amplication.com/blog/modernizing-legacy-systems-with-amplications-db-schema-import/5.png)

*   Switch to the ERD view to see a full picture of all the created entities with their fields and relations.

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551213834/f9cf5c35-d00f-4406-ba16-4b1a7127bc59.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--AgpNt41x--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://static-assets.amplication.com/blog/modernizing-legacy-systems-with-amplications-db-schema-import/6.png)

*   Make any additional configurations or changes, and when you are ready, build and commit the code to your Git repo.
    
*   Open the newly created PR to view the generated code for your Event Management service.
    

💡 Check out this [Git repository](https://github.com/amplication/db-schema-import-example) showcasing the outcome of generating code with Amplication based on the example Prisma schema file

Gratitude to Our Beta Testers
-----------------------------

A big thank you to the beta testers of this feature. Your invaluable feedback was instrumental in refining the DB Schema Import capability, making it more robust and developer-friendly.

In Conclusion
-------------

The challenge of updating old systems is significant, especially without losing data or running into issues. However, with Amplication's Database Schema Import, the process is simplified. This tool makes it easier to move from old systems to new ones without the typical headaches. Amplication offers an easy yet sophisticated solution to complex and time-consuming challenges as you look to modernize.

About Amplication
-----------------

[Amplication](https://www.amplication.com/) helps increase velocity and consistency for backend teams. It accelerates the development of microservices and backend applications using auto-generation of all the boilerplate and infrastructure code and allows developers to focus their efforts on developing the core business processes and logic.  
Using an extensive plugin system, developers and platform teams can automate the generation of services while keeping all the best practices and know-how of the organization.

Try it now
----------

You can start using Amplication by simply visiting [https://app.amplication.com/](https://app.amplication.com/)