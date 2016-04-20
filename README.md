# Technical Specifications for the Swedish eID Framework #

This repository comprises the specifications of the Swedish eID Framework.

## Contents

The master branch of the repository contains the currently active specifications.

#### Tekniskt ramverk för Svensk e-legitimation

An overview document (in Swedish) that describes the different parts of the Swedish eID Framework.

> This document will be translated into English.

#### Deployment Profile for the Swedish eID Framework

This is the main specification for the Swedish eID Framework. It defines a SAML profile including metadata, request- and response processing as well as extensions for signature services. 

#### Registry for identifiers assigned by the Swedish e-identification board

This document defines the structure for identifiers assigned by the Swedish e-identification board and provides a registry for assigned identifiers.

#### Attribute Specification for the Swedish eID Framework

This document specifies an attribute profile for the Swedish eID Framework. The attribute profile defines attributes for use within the Swedish eID Framework, and a number of defined attribute sets that may be referenced by other documents as means to specify specific attribute release requirements.

#### Entity Categories for the Swedish eID Framework

This specification contains the Entity Category definitions that are defined for the Swedish eID Framework and that should be supported by Service Providers and Identity Providers that are part of the federation.

#### Implementation Profile for using OASIS DSS in Central Signing Services

This document specifies an implementation profile for exchange of sign requests and responses using the OASIS DSS protocol, enhanced by the DSS Extensions for Federated Central Signing Services.

#### Certificate profile for certificates issued by Central Signing services

This document specifies a certificate profile for certificates issued by a signature service within the Swedish eID federation.

#### DSS Extension for Federated Central Signing Services

This specifications defines elements that extends the `<dss:SignRequest>` and `<dss:SignResponse>` elements of the OASIS DSS protocol.

#### Discovery within the Swedish eID Framework

The Swedish eID Framework comprises a Discovery Service that has as its purpose to supply Service Providers with user selected Identity Providers for authentication within the federation. This specifications defines how discovery is implemented.

## Updates to the current version of the specifications

Updates to the current version of the specification should be performed in the "october-2015-updates" branch except for any changes that need to be performed in the "Updates to the Swedish eID Framework.docx" document.

## Older versions

Older version of the specification are stored in the following branches:

+ april-2014 - For the June 2014 release
+ june-2015 - For the June 2015 release
+ october-2015 - For the October 2015 release (this is also the current release/master).


