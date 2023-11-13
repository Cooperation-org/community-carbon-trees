# Attestations for Community Carbon Trees

The goal of this project is to enable independent validation of tree planting efforts by [Community Carbon Trees](communitycarbontrees.org) as a pilot.

Note that the [Ceramic network may be used to store Etheruem Attestation Service compatible attestations](https://blog.ceramic.network/ceramic-ethereum-attestation-service-how-to-use-and-store-composable-attestations/)

Linked Trust [Ceramic schemas](https://github.com/Cooperation-org/LinkedTrust) and [verifiable credential vocabulary examples](https://github.com/Cooperation-org/LinkedClaims)

[ProofMode API](https://proofmode.org/verify)

[ProofMode Metadata Schema](https://gitlab.com/guardianproject/proofmode/proofmode-data-tools/-/blob/main/specs/ProofModev1.0.25.schema.json)

The generic LinkedClaim model is as follows:
```
type LinkedClaim @createModel( 
     accountRelation: LIST, 
     description: "Claim or attestation, possibly from 3rd party sources" ) 
{ 
    subjectID: String! @string(minLength: 1, maxLength: 1024)
    subjectType: SubjectType
    subjectName: String @string(minLength: 1, maxLength: 256)
    claim: String! @string(minLength: 1, maxLength: 256)     
    effectiveDate: Date 
    statement: String @string(minLength: 1, maxLength: 16384) 
    object: String @string(minLength: 1, maxLength: 1024) 
    source: ClaimSource
    rating: NormalizedRating
    amt: Measure
    confidence: Float
    sharing: Sharing
}
```

Likely we will want to add a generic relation model for lat/long, and link to a model for storing the ProofMode data 

Subset of key proofmode fields:

```
{
  "$id": "https://proofmode.org/ProofMode.v1.schema.json",
  "$schema": "http://json-schema.org/draft-04/schema#",
  "title": "ProofMode schema",
  "version": "1.0.25",
  "description": "A represenation of verifiable media proof data for use with proofmode.org tools and services",
  "type": "object",
  "properties": {
    "File Path": {
      "type": "string",
      "description": "A local path or filename of the media file at the time of proof generation"
    },
    "Hardware": {
      "type": "string",
      "descrtipion": "Information about the device type that the proof was generated on"
    },
    "DeviceID Vendor": {
      "type": "string"
    },
    "File Modified": {
      "type": "string"
    },
    "Proof Generated": {
      "type": "string"
    },
    "Location.Latitude": {
      "type": "number"
    },
    "Location.Altitude": {
      "type": "number"
    },
    "Location.Accuracy": {
      "type": "number"
    },
    "Location.Time": {
      "type": "number"
    },
    "Location.Bearing": {
      "type": "number"
    },
    "File Hash SHA256": {
      "type": "string"
    },
    "Location.Provider": {
      "type": "string"
    },
    "IPv4": {
      "type": "string"
    },
    "Location.Longitude": {
      "type": "number"
    },
    "DeviceID": {
      "type": "string"
    }
  },
  "required": [
    "File Path",
    "Hardware",
    "Proof Generated",
    "DataType",
    "File Hash SHA256"
  ]
}
```
