https://drive.google.com/file/d/1MhQNOSxQ9Ji5OfoqroD2f7vO2nUxYj3Q/view?usp=drive_link

graph TB
    subgraph OnPrem["On-Premises"]
        AD[Active Directory]
        OnPremUsers[Users & Partners]
    end

    subgraph Azure["Azure – Primary Region (Canada Central)"]
        subgraph Hub["Hub VNet"]
            AFW[Azure Firewall Premium]
            VPN[VPN / ExpressRoute Gateway]
            Bastion[Azure Bastion]
            DNS[Private DNS Zones]
        end

        subgraph SpokeApp["Spoke – Application"]
            AGW[Application Gateway WAF_v2]
            AppService[App Service – Web Tier]
            ContainerApps[Container Apps – API Tier]
            Functions[Azure Functions]
            Redis[Azure Cache for Redis]
        end

        subgraph SpokeData["Spoke – Data"]
            SQL[Azure SQL DB Business Critical<br/>Zone-Redundant]
            Storage[Storage Account<br/>Data Lake Gen2 + Private Endpoint]
            SB[Service Bus Premium]
        end

        subgraph Shared["Shared Services"]
            KeyVault[Key Vault – Private Endpoint]
            LA[Log Analytics Workspace]
            RSV[Recovery Services Vault<br/>Immutable]
        end
    end

    subgraph Secondary["Secondary Region – Canada East"]
        SQLSecondary[SQL Failover Group Secondary]
        ASR[Azure Site Recovery]
    end

    OnPremUsers -->|Entra Connect + Conditional Access| Entra[Microsoft Entra ID]
    AD -->|Password Hash Sync| Entra
    Entra --> AGW
    AGW --> AppService
    AppService --> ContainerApps
    ContainerApps --> SQL
    ContainerApps --> SB
    Functions --> SB
    AppService --> Redis

    SpokeApp -->|Private Endpoints| SpokeData
    SpokeApp --> Hub
    SpokeData --> Hub
    Hub --> OnPrem

    SQL -->|Failover Group| SQLSecondary
    RSV --> ASR
