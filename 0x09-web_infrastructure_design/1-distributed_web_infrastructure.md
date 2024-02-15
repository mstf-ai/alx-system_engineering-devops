# Infrastructure Components:

  *  Server 1 (Web Server):
        Hosts Nginx, responsible for handling HTTP requests and serving static content.
        Listens for incoming requests on port 80 (HTTP) and 443 (HTTPS).

   * Server 2 (Application Server):
        Executes dynamic code of the website.
        Collaborates with the web server to process dynamic content.

   * Server 3 (Database):
        MySQL database server, stores and retrieves data for the website.
        Part of a Primary-Replica cluster for improved scalability and reliability.

   * Load Balancer (HAProxy):
        Distributes incoming traffic among multiple servers for load balancing.
        Ensures high availability and improves performance by spreading the load.

   * Application Files (Code Base):
        Contains the website's code, including HTML, CSS, and dynamic server-side code.

#### Specifics of the Infrastructure:

   * Additional Elements:
        Server 2 (Application Server): Added to separate the web server and application server for better scalability and maintenance.
        Load Balancer (HAProxy): Introduced to distribute traffic evenly among multiple servers and enhance availability.
        Server 3 (Database): Implemented to form a Primary-Replica cluster for database scalability and redundancy.

   * Load Balancer Distribution Algorithm:
        Configured with a Round Robin distribution algorithm.
        Every server takes turns handling requests, distributing the load evenly.

   * Active-Active vs. Active-Passive Setup:
        Active-Active Setup: All servers actively handle requests simultaneously.
        Active-Passive Setup: Only one server is actively serving requests at a time; others act as backups. HAProxy in this design is configured for an Active-Active setup to maximize resource utilization.

   * Database Primary-Replica Cluster:
        Primary Node: Handles write operations and serves as the main source of truth for data.
        Replica Node: Mirrors the data from the Primary node, handles read operations, and provides redundancy.

   * Difference between Primary and Replica Nodes:
        Primary Node: Accepts write operations, ensuring data consistency across the cluster.
        Replica Node: Primarily handles read operations, reducing the load on the Primary node. Provides redundancy and improves read performance.

### Issues with the Infrastructure:

   * Single Point of Failure (SPOF):
        The web server, application server, and database each have a single instance. If any of these fail, it could lead to downtime.
        To address this, consider adding redundancy to each component (e.g., multiple web servers, application servers, and database replicas).

   * Security Issues:
        No Firewall: The infrastructure lacks a firewall, exposing servers to potential security threats.
        No HTTPS: Traffic between users and the website is not encrypted. Implementing HTTPS is crucial for secure communication.

   * No Monitoring:
        Lack of monitoring tools makes it challenging to identify performance issues, security breaches, or potential failures.
        Implement monitoring solutions to track server health, detect anomalies, and ensure timely response to incidents.