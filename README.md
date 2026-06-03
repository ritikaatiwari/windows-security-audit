# Windows Security Audit

## Objective

Perform basic host enumeration and identify administrative accounts, listening services, and active network connections on a Windows workstation.

## User Enumeration

Command Used:
net localgroup administrators

Findings:

* Built-in Administrator account present.
* User account "ritik" is a member of the local Administrators group.
* No unexpected administrator accounts identified.

## Listening Ports

Command Used:
netstat -ano

Notable Listening Ports:

* TCP 135 (RPC Endpoint Mapper)
* TCP 445 (SMB File Sharing)
* TCP 7070
* TCP 6881
* TCP 5037 (Localhost only)
* TCP 11434 (Localhost only)

Observations:

* Standard Windows services were listening on ports 135 and 445.
* Several application-specific services were listening on high-numbered ports.
* Localhost-only services were not externally accessible.

## Active Connections

Observed multiple encrypted outbound HTTPS connections over port 443.

Examples:

* Microsoft services
* Google services
* GitHub-related connections
* Cloud-hosted services

Observations:

* Most outbound traffic was encrypted using HTTPS.
* No obvious connections to suspicious destinations were identified during the review.

## Security Considerations

* SMB (Port 445) should not be exposed directly to the internet.
* Administrator privileges should be limited to required accounts.
* Regular review of listening services helps reduce attack surface.
* Unknown services should be mapped to their owning processes for verification.

## Conclusion

The system appeared to be operating normally during the assessment. Administrative access was limited, standard Windows services were present, and no immediately suspicious network activity was observed.
