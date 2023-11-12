ALX 0X19- Postmortem
****

**Postmortem: Infrastructure Outage**

**Duration of Outage:**
- Start Time: November 10, 2023, 15:45 UTC
- End Time: November 10, 2023, 17:30 UTC

**Impact:**
- Service Affected: File Storage API
- User Experience: Users experienced intermittent timeouts and delays accessing files, with a 20% degradation in API response times.

**Root Cause:**
The outage was caused by a sudden surge in traffic due to a marketing campaign, causing the file storage servers to exhaust available connections, leading to a cascading failure.

**Timeline:**
- **15:45 UTC:** Issue detected via monitoring alerts on elevated error rates and latency.
- **15:50 UTC:** Initial investigation focused on potential software bugs, but no anomalies found.
- **16:00 UTC:** Assumed the issue was related to recent code deployment; rolled back changes with no improvement.
- **16:15 UTC:** Incorrectly suspected a network issue; network logs and configurations were reviewed.
- **16:30 UTC:** Escalated incident to the Infrastructure Team for further investigation.
- **17:00 UTC:** Root cause identified as connection exhaustion due to increased API traffic.
- **17:15 UTC:** Implemented a temporary fix by increasing connection limits on file storage servers.
- **17:30 UTC:** Normalized traffic and restored the API to full functionality.

**Root Cause and Resolution:**
- **Cause:** The surge in traffic overwhelmed the file storage servers, exhausting available connections in the connection pool.
- **Resolution:** Increased connection limits on the file storage servers to accommodate the increased load. A long-term solution will involve optimizing the connection handling mechanism and implementing dynamic scaling based on traffic patterns.

**Corrective and Preventative Measures:**
- **Improvements/Fixes:**
- Enhance monitoring: Implement additional monitoring to proactively identify unusual traffic patterns and potential capacity issues.
- Auto-scaling: Investigate and implement auto-scaling mechanisms for critical infrastructure components to handle sudden increases in demand.
- **Tasks:**
1. **Monitoring Enhancement:** Implement anomaly detection in monitoring systems to identify traffic spikes and resource utilization abnormalities.
2. **Auto-scaling Implementation:** Research and implement auto-scaling solutions for critical infrastructure components, starting with the file storage servers.
3. **Capacity Planning:** Conduct a thorough capacity planning exercise to ensure that infrastructure can handle projected increases in user traffic.
