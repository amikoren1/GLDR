# GLDR APIS
## SITES
#### Gets list of sites added to DSCC
GET /disaster-recovery/v1beta1/virtual-sites

Response:
```
{
    "items": [
        {
            "id": "9758fdb9-1be2-4b67-b2f0-f7f071124c85",
            "serialNumber": "b5243c5a-cc95-40fc-9323-88b951884e18",
            "customerId": "95d4e310-39a1-11ed-8051-56e786f00957",
            "name": "",
            "platformType": "",
            "networkAddress": "",
            "status": "ACTIVATING",
            "connected": false,
            "updatedAt": "2023-03-13T07:47:44.366986Z",
            "type": "virtual-site",
            "resourceUri": "/api/v1/virtual-sites/9758fdb9-1be2-4b67-b2f0-f7f071124c85",
            "generation": 1,
            "refreshedAt": "2023-03-13T07:47:45.547615Z",
            "createdAt": "2023-03-13T07:47:44.233091Z",
            "version": "10.0.10"
        }
    ],
    "limit": 20000,
    "offset": 0,
    "total": 1
}
```
#### Gets specific sites information 
GET {{url}}/disaster-recovery/v1beta1/virtual-sites/{id}

Response:   
```
{
    "id": "9758fdb9-1be2-4b67-b2f0-f7f071124c85",
    "serialNumber": "b5243c5a-cc95-40fc-9323-88b951884e18",
    "customerId": "95d4e310-39a1-11ed-8051-56e786f00957",
    "name": "",
    "platformType": "",
    "networkAddress": "",
    "status": "ACTIVATING",
    "connected": false,
    "updatedAt": "2023-03-13T07:47:44.366986Z",
    "type": "virtual-site",
    "resourceUri": "/api/v1/virtual-sites/9758fdb9-1be2-4b67-b2f0-f7f071124c85",
    "generation": 1,
    "refreshedAt": "2023-03-13T07:47:45.547615Z",
    "createdAt": "2023-03-13T07:47:44.233091Z",
    "version": "10.0.10"
}
```
#### Add Site to DSCC
POST /disaster-recovery/v1beta1/virtual-sites

Body:
```
{
    "serialNumber":"{{serialNumber}}"
}
```
Response:
```
{
    "id": "96acb465-b663-4aba-90c8-0b022ccc3e06"
}
```
#### Refresh site
POST /disaster-recovery/v1beta1/virtual-sites/{id}/refresh

Response:
```
{
    "taskId": "ddd39ad3-a331-400a-9e35-0948433e58ee"
}
```
#### Delete a site from DSCC
DELETE /disaster-recovery/v1beta1/virtual-sites/{id}

Response: 
204 No Content

## VIRTUALIZATION 
#### Get list of Virtual-machines for a specific Protection site ID (remove everything after the question mark (including) - to get  for all customer sites)
GET /api/temp/zerto-virtual-machines?siteId={siteId}

Response:
```
[
    {
        "lastUpdatedAt": "2023-07-23T07:32:42Z",
        "id": "5553e594-f868-5c60-8f77-d9431df1b0fb",
        "name": "qa_s4v5_dmy_eyalgad",
        "type": "virtual-machine",
        "customerId": "fe0d3faa-ae9f-11ec-a437-ea9dc4f11500",
        "internalId": "0c363daf-b9fd-4647-b99e-50332d1a5ba6.vm-1230",
        "siteId": "0e930aa7-3b47-4da2-825b-cde9e08383f4",
        "IsAgentInstalled": false,
        "protected": false,
        "virtualDisks": [
            {
                "id": "",
                "internalId": "scsi:0:0"
            },
            {
                "id": "",
                "internalId": "scsi:0:1"
            },
            {
                "id": "",
                "internalId": "scsi:0:2"
            }
        ],
        "networkAdapters": [
            {
                "networkDetails": {
                    "id": "",
                    "internalId": "Network adapter 1"
                }
            },
            {
                "networkDetails": {
                    "id": "",
                    "internalId": "Network adapter 2"
                }
            }
        ]
    }
]
```
#### Protection site ID as param Refresh virtual machines list 
POST /api/temp/zerto-virtual-machines/refresh

Body:
```
{
    "siteId":"{{ProtectedSiteIdentifier}}"
}
```
Response: 
```
{
    "taskUri": "/api/v1/tasks/01955825-26e1-4130-aae3-2677d465e577"
}
```
#### Get a list of Hypervisor-host (remove everything after the question mark (including) - to get  for all customer sites)
GET /api/temp/zerto-hypervisor-hosts?siteId={siteId}

Response:
```
[
 {
        "lastUpdatedAt": "2023-07-23T07:36:46Z",
        "id": "a78daa49-00fe-3568-bed1-e88305233f8b",
        "name": "10.171.34.11",
        "type": "hypervisor-host",
        "customerId": "fe0d3faa-ae9f-11ec-a437-ea9dc4f11500",
        "siteId": "88a1703c-359e-4c0e-af66-45dd88c9fcc7",
        "internalId": "f46575fd-ad26-4b5a-b969-233dfaea0df8.host-464",
        "vraInstalled": false,
        "owningHostCluster": null,
        "associatedDatastoresClusters": null,
        "associatedDatastores": [
            {
                "id": "64b0c03a-f861-320e-a12f-21cdb7f217c4",
                "name": "inf_QANested1063_DS4",
                "owningDatastoreCluster": null
            },
            {
                "id": "d1e8bcee-9fc9-301a-987e-5f2a93e9a0cf",
                "name": "inf_QANested1063_DS5",
                "owningDatastoreCluster": null
            }
        ]
    }
]
```
#### Recovery site ID as param recovery site Refresh Hypervisor-host list 
POST /api/temp/zerto-hypervisor-hosts/refresh

Body:
```
{
    "siteId":"{{RecoverySiteIdentifier}}"
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/e977ed03-ece3-4ed0-839b-a993725d4c4c"
}
```
#### Get a list of Hypervisor-clusters (remove everything after the question mark (including) - to get  for all customer sites)
GET /api/temp/zerto-hypervisor-clusters?siteId={siteId}

Response:
```
[
     {
        "lastUpdatedAt": "2023-07-23T07:36:47Z",
        "id": "6068d627-8fca-384e-928b-8fb1ecf8e92b",
        "name": "ClusterH125H126",
        "type": "hypervisor-cluster",
        "customerId": "fe0d3faa-ae9f-11ec-a437-ea9dc4f11500",
        "siteId": "88a1703c-359e-4c0e-af66-45dd88c9fcc7",
        "internalId": "f46575fd-ad26-4b5a-b969-233dfaea0df8.domain-c8",
        "associatedDatastoresClusters": [
            {
                "id": "e8361c91-017b-30d0-81c5-0816d7081ec2",
                "name": "DatastoreClusteH125H126"
            }
        ],
        "associatedDatastores": [
            {
                "id": "64b0c03a-f861-320e-a12f-21cdb7f217c4",
                "name": "inf_QANested1063_DS4",
                "owningDatastoreCluster": null
            },
            {
                "id": "8501b19c-4908-37c1-a0ec-d985eb4c0ac4",
                "name": "inf_QANest1063_DS3",
                "owningDatastoreCluster": {
                    "id": "e8361c91-017b-30d0-81c5-0816d7081ec2",
                    "name": "DatastoreClusteH125H126"
                }
            },
            {
                "id": "d1e8bcee-9fc9-301a-987e-5f2a93e9a0cf",
                "name": "inf_QANested1063_DS5",
                "owningDatastoreCluster": null
            },
            {
                "id": "ed40b6f7-ffd9-36fa-adc9-44c0830869ff",
                "name": "inf_QANest1063_DS2",
                "owningDatastoreCluster": {
                    "id": "e8361c91-017b-30d0-81c5-0816d7081ec2",
                    "name": "DatastoreClusteH125H126"
                }
            },
            {
                "id": "4893820e-db8b-3aa5-b5f7-9b668f60ee6e",
                "name": "inf_QANested1063_DS1",
                "owningDatastoreCluster": null
            }
        ],
        "associatedNetworks": [
            {
                "id": "3c4a4234-2813-3d8a-a3d3-86196c11bd2d",
                "name": "VM Network"
            },
            {
                "id": "d6de39d3-5a73-360b-9627-7f317814a480",
                "name": "TO 1710"
            }
        ]
    }
]
```
#### Recovery site ID as param recovery site Refresh Hypervisor-cluster list
 POST /api/temp/zerto-hypervisor-clusters/refresh
 
Body:
```
{
    "siteId":"{{RecoverySiteIdentifier}}"
}
```
Response: 
```
{
    "taskUri": "/api/v1/tasks/e5d2d1f7-f3c6-44cf-92f1-a2854b40dba7"
}
```
#### Get a list of hypervisor-datastores (remove everything after the question mark (including) - to get  for all customer sites)
GET /api/temp/zerto-hypervisor-datastores?siteId={siteId}

```
[
   {
        "lastUpdatedAt": "2023-07-23T07:46:47Z",
        "id": "64b0c03a-f861-320e-a12f-21cdb7f217c4",
        "name": "inf_QANested1063_DS4",
        "type": "hypervisor-datastore",
        "customerId": "fe0d3faa-ae9f-11ec-a437-ea9dc4f11500",
        "siteId": "88a1703c-359e-4c0e-af66-45dd88c9fcc7",
        "internalId": "f46575fd-ad26-4b5a-b969-233dfaea0df8.datastore-1037",
        "owningDatastoreCluster": null
    }
]
```
#### Recovery site ID as param recovery site Refresh hypervisor-datastores list 
POST /api/temp/zerto-hypervisor-datastores/refresh

Body:
```
{
    "siteId":"{{RecoverySiteIdentifier}}"
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/3a02bf03-ebf7-42c7-81d6-656d28863730"
}
```
#### Get a list of hypervisor-networks (remove everything after the question mark (including) - to get  for all customer sites)
GET /api/temp/zerto-hypervisor-networks?siteId={siteId}

Response:
```
[
    {
        "lastUpdatedAt": "2023-07-23T07:42:45Z",
        "id": "0f1d14d7-cbf4-3af2-9589-37bdbbb61196",
        "name": "NET1_vr02_changed",
        "type": "hypervisor-network",
        "customerId": "fe0d3faa-ae9f-11ec-a437-ea9dc4f11500",
        "siteId": "0e930aa7-3b47-4da2-825b-cde9e08383f4",
        "internalId": "0c363daf-b9fd-4647-b99e-50332d1a5ba6.network-1172"
    }
]
```
#### Recovery site ID as param recovery siteRefresh hypervisor-networks list 
POST /api/temp/zerto-hypervisor-networks/refresh

Body: 
```
{
    "siteId":"{{RecoverySiteIdentifier}}"
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/a360908d-c407-45fb-9dee-6818b0d98c88"
}
```
#### Get a list of hypervisor-folders (remove everything after the question mark (including) - to get  for all customer sites)
GET /api/temp/zerto-hypervisor-folders?siteId={siteId}

Response:
```
[
    {
        "lastUpdatedAt": "2023-07-23T07:46:47Z",
        "id": "0bf8bbb6-beca-3ba0-9ec2-9b2a22f2d2c6",
        "name": "/",
        "type": "hypervisor-folder",
        "customerId": "fe0d3faa-ae9f-11ec-a437-ea9dc4f11500",
        "siteId": "88a1703c-359e-4c0e-af66-45dd88c9fcc7",
        "internalId": "f46575fd-ad26-4b5a-b969-233dfaea0df8.group-v4"
    }
]
```
#### Recovery site ID as param recovery siteRefresh hypervisor-folders list 
POST /api/temp/zerto-hypervisor-folders/refresh

Bosy:
```
{
    "siteId":"{{RecoverySiteIdentifier}}"
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/31f8dd6c-a924-4098-b4cb-a5d668bd51c1"
}
```
#### Get a list of hypervisor-datastore-clusters (remove everything after the question mark (including) - to get  for all customer sites)
GET /api/temp/zerto-hypervisor-datastore-clusters?siteId={siteId}

Response:
```
[
     {
        "lastUpdatedAt": "2023-07-23T07:42:44Z",
        "id": "a1f3b582-7d1c-3635-8935-d4f5398b3118",
        "name": "DatastoreClusterH100H122_changed",
        "type": "hypervisor-datastore-cluster",
        "customerId": "fe0d3faa-ae9f-11ec-a437-ea9dc4f11500",
        "siteId": "0e930aa7-3b47-4da2-825b-cde9e08383f4",
        "internalId": "0c363daf-b9fd-4647-b99e-50332d1a5ba6.group-p417"
    }
]
```
#### Recovery site ID as param recovery siteRefresh hypervisor-datastore-clusters list 
POST /api/temp/zerto-hypervisor-datastore-clusters/refresh

Body:
```
{
    "siteId":"{{RecoverySiteIdentifier}}"
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/0ea06a97-41d6-4b68-8eec-fc753de4eae7"
}
```
## Protection
#### Create Protection Group
POST /disaster-recovery/v1beta1/virtual-continuous-protection-groups

Body:
```
{
  "name":"PM_DEMO_LIOR10",
  "protectedSite": "{{ProtectedSiteIdentifier}}",
  "recoverySite": "{{RecoverySiteIdentifier}}",
  "hypervisor":{ 
    "host":"{{HostIdentifier}}",
    "cluster":"{{ClusterIdenitifier}}",
    "datastore":"{{DatastoreIdentifier}}",
    "datastoreCluster":"{{DatastoreClusterIdentifier}}",
    "folder":"{{FolderIdentifier}}",
    "network":"{{NetworkIdentifier}}",
    "testNetwork":"{{NetworkIdentifier}}"
    },
  "virtualMachines":[ 
      {         
         "id":"{{VmIdentifier}}"
      }
   ]
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/e977ed03-ece3-4ed0-839b-a993725d4c4c"
}
```
#### Get all protection groups data
GET /disaster-recovery/v1beta1/virtual-continuous-protection-groups

Response:
```
{
    "items": [
        {
            "id": "ea8b7d07-10f3-49cf-84a8-7d6f81f940b5",
            "status": "ready",
            "name": "vpg-4b99425",
            "protectedSite": {
                "id": "cfa2cc63-e43b-4f6e-82fb-b6737fce029b",
                "name": "accusamus"
            },
            "recoverySite": {
                "id": "cfa2cc63-e43b-4f6e-82fb-b6737fce029b",
                "name": "accusamus"
            },
            "hypervisor": {
                "host": "5ecdbc67-0bd9-321f-8cc6-03fb2c2da6b7",
                "datastore": "be556441-a07f-3ad0-998f-4288a2f09ec2",
                "cluster": "",
                "datastoreCluster": "",
                "folder": "a4a37624-f274-30a2-b1e0-16e76e758ad9",
                "network": "e3965e6a-9c8f-3c6e-81ae-543bfe8d0e8f",
                "testNetwork": "e3965e6a-9c8f-3c6e-81ae-543bfe8d0e8f"
            },
            "virtualMachines": [
                {
                    "id": "1216926d-410e-5fde-a3e6-1076aafde55e"
                     "networkAdapters": [
                        {
                            "id": "<string>",
                            "failover": {
                                "network": "",
                                "staticIP": "",
                                "replaceMacAddress": "false",
                                "isDhcp": "true",
                                "subnetMask": "",
                                "gateway": "",
                                "primaryDNS": "",
                                "secondaryDNS": "",
                                "dnsSuffix": ""
                            },
                            "test": {
                                "network": "<uuid>",
                                "staticIP": "<string>",
                                "replaceMacAddress": "false",
                                "isDhcp": "true",
                                "subnetMask": "<string>",
                                "gateway": "<string>",
                                "primaryDNS": "<string>",
                                "secondaryDNS": "<string>",
                                "dnsSuffix": "<string>"
                            }
                        }
                    ]
                }
            ],
            "type": "virtual-continuous-protection-group",
            "resourceUri": "/api/v1/virtual-continuous-protection-groups/95d4e310-39a1-11ed-8051-56e786f00957",
            "customerId": "95d4e310-39a1-11ed-8051-56e786f00957",
            "generation": 2,
            "updatedAt": "2023-03-13T08:11:21.489807Z",
            "createdAt": "2023-03-13T08:11:21.489807Z"
        }
    ],
    "limit": 20000,
    "offset": 0,
    "total": 1
}
```
#### Get data for specific protection group
GET /disaster-recovery/v1beta1/virtual-continuous-protection-groups/{id}

Response:
```
{
    "id": "ea8b7d07-10f3-49cf-84a8-7d6f81f940b5",
    "status": "ready",
    "name": "vpg-4b99425",
    "protectedSite": {
        "id": "cfa2cc63-e43b-4f6e-82fb-b6737fce029b",
        "name": "accusamus"
    },
    "recoverySite": {
        "id": "cfa2cc63-e43b-4f6e-82fb-b6737fce029b",
        "name": "accusamus"
    },
    "hypervisor": {
        "host": "5ecdbc67-0bd9-321f-8cc6-03fb2c2da6b7",
        "datastore": "be556441-a07f-3ad0-998f-4288a2f09ec2",
        "cluster": "",
        "datastoreCluster": "",
        "folder": "a4a37624-f274-30a2-b1e0-16e76e758ad9",
        "network": "e3965e6a-9c8f-3c6e-81ae-543bfe8d0e8f",
        "testNetwork": "e3965e6a-9c8f-3c6e-81ae-543bfe8d0e8f"
    },
    "virtualMachines": [
        {
            "id": "1216926d-410e-5fde-a3e6-1076aafde55e"
            "networkAdapters": [
                        {
                            "id": "<string>",
                            "failover": {
                                "networkID": "",
                                "staticIP": "",
                                "replaceMacAddress": "false",
                                "isDhcp": "true",
                                "subnetMask": "",
                                "getway": "",
                                "primaryDNS": "",
                                "secondaryDNS": "",
                                "dnsSuffix": ""
                            },
                            "test": {
                                "networkID": "<uuid>",
                                "staticIP": "<string>",
                                "replaceMacAddress": "false",
                                "isDhcp": "true",
                                "subnetMask": "<string>",
                                "getway": "<string>",
                                "primaryDNS": "<string>",
                                "secondaryDNS": "<string>",
                                "dnsSuffix": "<string>"
                            }
                        }
                    ]
                }
            ],
        }
    ],
    "type": "virtual-continuous-protection-group",
    "resourceUri": "/api/v1/virtual-continuous-protection-groups/95d4e310-39a1-11ed-8051-56e786f00957",
    "customerId": "95d4e310-39a1-11ed-8051-56e786f00957",
    "generation": 2,
    "updatedAt": "2023-03-13T08:11:21.489807Z",
    "createdAt": "2023-03-13T08:11:21.489807Z"
}
```
#### Refresh protection group data from ZVM
POST /disaster-recovery/v1beta1/virtual-continuous-protection-groups/refresh/

Response:
202 Accepted
#### Update VPG
PUT /disaster-recovery/v1beta1/virtual-continuous-protection-groups/{vpgId}

Body:
```
{
    "name": "S4EGS3_v1" ,
    "hypervisor":{ 
        "host":"{{tmp_vpg_host}}",
        "cluster":"{{tmp_vpg_cluster}}",
        "datastore":"{{tmp_vpg_datastore}}",
        "datastoreCluster":"{{tmp_vpg_datastoreCluster}}",
        "folder":"{{tmp_vpg_folder}}",
        "network":"{{tmp_vpg_network}}",
        "testNetwork":"{{tmp_vpg_testNetwork}}"
    },
    "virtualMachines":[
        {"id":"fe68326c-b08f-5516-a82c-e6c56ddd8d60"}
        ]
}


```
Response:
```
{
    "taskUri": "/api/v1/tasks/87831e92-b402-4e92-b60f-4be8e995ceac"
}
```

#### Delete a protection group 
DELETE /disaster-recovery/v1beta1/virtual-continuous-protection-groups/{{DSCC_VPG_UDID}}

Response:
```
{
    "taskUri": "/api/v1/tasks/e977ed03-ece3-4ed0-839b-a993725d4c4c"
}
```

## REPLICATION
#### Get all replication groups data
GET /disaster-recovery/v1beta1/virtual-continuous-protection-replicas/

Response:
```
{
    "items": [
        {
            "id": "a1d7ed4d-8c0d-4876-80cd-dc17ed2569a8",
            "name": "vpg-71bf908",
            "slaStatus": "MEETING_SLA",
            "customerId": "95d4e310-39a1-11ed-8051-56e786f00957",
            "healthStatus": "OK",
            "rpo": {
                "configuredSeconds": 300,
                "actualSeconds": 5,
                "status": "OK"
            },
            "history": {
                "configuredMinutes": 1440,
                "actualMinutes": 10
            },
            "type": "virtual-continuous-protection-replica",
            "resourceUri": "/api/v1/virtual-continuous-protection-replicas/a1d7ed4d-8c0d-4876-80cd-dc17ed2569a8",
            "generation": 2,
            "updatedAt": "2023-03-13T07:55:00.69804Z",
            "createdAt": "2023-03-13T07:55:00.413094Z"
        }
    ],
    "limit": 20000,
    "offset": 0,
    "total": 1
}
```
#### Get data for specific replication group
GET /disaster-recovery/v1beta1/virtual-continuous-protection-replicas/{{DSCC_VPG_UDID}}

Response:
```
{
    "id": "a1d7ed4d-8c0d-4876-80cd-dc17ed2569a8",
    "name": "vpg-71bf908",
    "slaStatus": "MEETING_SLA",
    "customerId": "95d4e310-39a1-11ed-8051-56e786f00957",
    "healthStatus": "OK",
    "rpo": {
        "configuredSeconds": 300,
        "actualSeconds": 5,
        "status": "OK"
    },
    "history": {
        "configuredMinutes": 1440,
        "actualMinutes": 10
    },
    "type": "virtual-continuous-protection-replica",
    "resourceUri": "/api/v1/virtual-continuous-protection-replicas/a1d7ed4d-8c0d-4876-80cd-dc17ed2569a8",
    "generation": 2,
    "updatedAt": "2023-03-13T07:55:00.69804Z",
    "createdAt": "2023-03-13T07:55:00.413094Z"
}
```
#### Get checkpoints for specific replica VPG
GET /disaster-recovery/v1beta1/virtual-continuous-protection-replicas/:vpgid/checkpoints

Response:
```
Replications : Get checkpoints for specific replica VPG - response should be : 

{

    "items": [
        {

            "id": "31",

            "tag": "",

            "timestamp": "2023-07-24T10:41:43Z",

            "customerId": "26ddc1fa-2016-11ee-974b-eaee3c8a2752"

        }
    ],

    "limit": 20000,

    "offset": 0,

    "total": 30,

    "createdAt": "2023-07-24T10:41:47.126752Z",

    "updatedAt": "2023-07-24T10:41:47.126752Z",

    "refreshedAt": "2023-07-24T10:41:47.126752Z"

}
```
#### Refresh checkpoint data for specific vpg
POST /disaster-recovery/v1beta1/virtual-continuous-protection-replicas/:vpgid/checkpoints/refresh

Response:
202 Accepted

#### Refresh replication data from ZVM
POST /disaster-recovery/v1beta1/virtual-continuous-protection-replicas/refresh

Body:
```
{    "recoverySiteId": "8c15b12c-818f-498a-bcb3-573088bc285b"}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/0ea06a97-41d6-4b68-8eec-fc753de4eae7"
}
```

## RECOVERY

#### Get all recovery groups data
GET /disaster-recovery/v1beta1/virtual-continuous-protection-recovery/

Response:
```
 {

    "items": [

        {

            "id": "505e224a-18ff-46ba-9ab3-562b5f8f2232",

            "name": "hjr6uy5u6",

            "type": "virtual-continuous-protection-recovery",

            "status": "READY",

            "customerId": "26ddc1fa-2016-11ee-974b-eaee3c8a2752",

            "actions": [

                {

                    "name": "test",

                    "enabled": true,

                    "reason": ""

                },

                {

                    "name": "stop",

                    "enabled": false,

                    "reason": ""

                },

                {

                    "name": "failover",

                    "enabled": true,

                    "reason": ""

                },

                {

                    "name": "move",

                    "enabled": false,

                    "reason": ""

                },

                {

                    "name": "rollback",

                    "enabled": false,

                    "reason": ""

                },

                {

                    "name": "commit",

                    "enabled": false,

                    "reason": ""

                }

            ],

            "resourceUri": "/disaster-recovery/v1beta1/virtual-continuous-protection-recoveries/505e224a-18ff-46ba-9ab3-562b5f8f2232",

            "createdAt": "2023-07-24T10:39:09.141799Z",

            "updatedAt": "2023-07-24T10:39:09.141799Z",

            "generation": 1,

            "lastTestedAt": ""

        }

    ],

    "limit": 20000,

    "offset": 0,

    "total": 1

}
```
#### Get data for specific recovery group
GET /disaster-recovery/v1beta1/virtual-continuous-protection-recovery/{{DSCC_VPG_UDID}}

Response:
```
   {
    "id": "ea8b7d07-10f3-49cf-84a8-7d6f81f940b5",
    "name": "vpg-4b99425",
    "type": "virtual-continuous-protection-recovery",
    "status": "READY",
    "customerId": "95d4e310-39a1-11ed-8051-56e786f00957",
    "actions": [
        {
            "name": "test",
            "enabled": true,
            "reason": ""
        },
        {
            "name": "stop",
            "enabled": false,
            "reason": ""
        },
        {
            "name": "failover",
            "enabled": true,
            "reason": ""
        },
        {
            "name": "move",
            "enabled": false,
            "reason": ""
        },
        {
            "name": "rollback",
            "enabled": false,
            "reason": ""
        },
        {
            "name": "commit",
            "enabled": false,
            "reason": ""
        }
    ],
    "resourceUri": "/api/v1/virtual-continuous-protection-recoveries/ea8b7d07-10f3-49cf-84a8-7d6f81f940b5",
    "createdAt": "2023-03-13T08:11:40.975818Z",
    "updatedAt": "2023-03-13T08:11:40.975818Z",
    "generation": 1
}  
```
#### Initiate Failover Live Operation 
POST /disaster-recovery/v1beta1/virtual-continuous-protection-recovery/{{DSCC_VPG_UDID}}/Failover

Response:
```
{
    "taskUri": "/api/v1/tasks/0ea06a97-41d6-4b68-8eec-fc753de4eae7"
}
```
#### Initiate Failover Live-Commit  Operation 
POST /disaster-recovery/v1beta1/virtual-continuous-protection-recoveries/:DsccVpgId/FailoverCommit

Response:
```
{
    "taskUri": "/api/v1/tasks/0ea06a97-41d6-4b68-8eec-fc753de4eae7"
}
```
#### Initiate Failover Live-Rollback Operation 
POST /disaster-recovery/v1beta1/virtual-continuous-protection-recoveries/:DsccVpgId/FailoverRollback

Response:
```
{
    "taskUri": "/api/v1/tasks/0ea06a97-41d6-4b68-8eec-fc753de4eae7"
}
```
#### Initiate Failover Test Operation
 POST /disaster-recovery/v1beta1/virtual-continuous-protection-recoveries/{{VpgId}}/FailoverTest

Response:
```
{
    "taskUri": "/api/v1/tasks/0ea06a97-41d6-4b68-8eec-fc753de4eae7"
}
```
#### Initiate Failover Test-Stop Operation 
POST /disaster-recovery/v1beta1/virtual-continuous-protection-recoveries/{{VpgId}}/FailoverTestStop

Response:
```
{
    "taskUri": "/api/v1/tasks/0ea06a97-41d6-4b68-8eec-fc753de4eae7"
}
```
## REPORTS
#### post 
POST /disaster-recovery/api/v1/virtual-continuous-protection-reports - with 
Body : 
```
{

"siteId":"{{dsccSiteId}}",

"reportType":"recovery",

"startDate":"2022-11-05T11:04:05Z",

"endDate":"2023-09-20T15:04:05Z",

"recoveryOperation":["FailoverTest","Failover"],

"protectionGroup":["{{wrkVPGID}}"],

"state":""

}
```
 

Response : Status 202 Accepted - body :
```
{

    "taskUri": "/api/v1/tasks/76730514-af9e-4913-b3f2-75db02e1988f"

}
```
 
#### Get
GET /disaster-recovery/api/v1/virtual-continuous-protection-reports


Response : status 200 OK - body :
```
[

    {

        "id": "02243f39-2b1c-4f8d-b040-556789bbb198",

        "timeCreated": "2023-06-01T05:52:50.739817Z",

        "downloaded": false

    }
]

```
#### Get 
GET /disaster-recovery/api/v1/virtual-continuous-protection-reports/:repID

Response:
```
<FILE>
```
