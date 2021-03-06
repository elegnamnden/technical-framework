<p>
<img align="left" src="img/sweden-connect.png"></img>
<img align="right" src="img/digg_centered.png"></img>
</p>
<p>
<img align="center" src="img/transparent.png"></img>
</p>

# Certificate Profile for Certificates Issued by Central Signing Services

### Version 1.2 - 2020-01-17

Registration number: **2019-313** (*previously: ELN-0608*)

---

## Table of Contents

1. [**Introduction**](#introduction)

    1.1. [Requirement key words](#requirement-key-words)

    1.2. [XML namespace references](#xml-namespace-references)

    1.3. [Structure](#structure)

2. [**Certificate Profile**](#certificate-profile)

    2.1. [Standards](#standards)

    2.2. [Qualified and PKC Certificates](#qualified-and-pkc-certificates)

    2.3. [Certificate Content](#certificate-content)

    2.3.1. [Subject Attributes and Name Forms](#subject-attributes-and-name-forms)

    2.3.1.1. [Person Identifier Attributes](#person-identifier-attributes)

    2.3.1.1.1. [Data Source](#data-source)

    2.3.1.1.2. [Data Format](#data-format)

    2.3.1.2. [Other Attribute Requirements](#other-attribute-requirements)

    2.3.2. [Authentication Context and Attribute Mapping](#authentication-context-and-attribute-mapping)
    
    2.3.2.1. [Extended Authentication Information](#extended-authentication-information)

    2.3.3. [Certificate Policy](#certificate-policy)

3. [**Normative References**](#normative-references)

4. [**Changes between versions**](#changes-between-versions)

---

<a name="introduction"></a>
## 1. Introduction

This document specifies a certificate profile for certificates issued by
a signature service based on the OASIS DSS protocol \[[DSS](#dss)\], enhanced by
the DSS Extensions for Federated Central Signing Services \[[DSS-Ext](#dss-ext)\].

<a name="requirement-key-words"></a>
### 1.1. Requirement key words

The key words **MUST**, **MUST** **NOT**, **REQUIRED**, **SHALL**,
**SHALL** **NOT**, **SHOULD**, **SHOULD** **NOT**, **RECOMMENDED**,
**MAY**, and **OPTIONAL** are to be interpreted as described in
\[[RFC2119](#rfc2119)\].

These keywords are capitalized when used to unambiguously specify
requirements over protocol features and behavior that affect the
interoperability and security of implementations. When these words are
not capitalized, they are meant in their natural-language sense.

<a name="xml-namespace-references"></a>
### 1.2. XML namespace references

The prefix **saci:** stands for the SAML Authentication Context Information XML Schema 
namespace, `http://id.elegnamnden.se/auth-cont/1.0/saci`.

> Schema location URL: https://docs.swedenconnect.se/schemas/cert-schemas/1.0/CertAuthContextExtension-SAML-1.0.xsd

The prefix **sacex:** stands for the Extended Authentication Information XML Schema
namespace, `http://id.swedenconnect.se/auth-cont/1.0/ext-auth-info`.

> Schema location URL: https://docs.swedenconnect.se/schemas/cert-schemas/1.0/CertAuthContextExtension-ExtAuthInfo-1.0.xsd

<a name="structure"></a>
### 1.3. Structure

This specification uses the following typographical conventions in text:
`<Eid2Element>`, `<ns:ForeignElement>`, `Attribute`, **Datatype**,
`OtherCode`.

<a name="certificate-profile"></a>
## 2. Certificate Profile

<a name="standards"></a>
### 2.1. Standards

The following standards provides normative requirements for this
certificate profile:

Standard | Function | Reference
--- | --- | ---
RFC 5280 | Main certificate standard | \[[RFC5280](#rfc5280)\]
RFC 7773 | Authentication context extension | \[[RFC7773](#rfc7773)\]
EN 319 411-1 | Policy requirements for PKC certificates | \[[EU-POL-NCP](#eu-pol-ncp)\]
EN 319 411-2 | Policy requirements for Qualified certificates | \[[EU-POL-QC](#eu-pol-qc)\]
EN 319 412-1 | Definitions of semantic identifies and formatting rules for identity data | \[[EU-CERT-GEN](#eu-cert-gen)\]
EN 319 412-2 | Certificate profile for certificates issued to natural persons | \[[EU-CERT-NP](#eu-cert-np)\]
EN 319 412-5 | Declaration of qualified certificate properties | \[[EU-CERT-QC](#eu-cert-qc)\]


<a name="qualified-and-pkc-certificates"></a>
### 2.2. Qualified and PKC Certificates

This profile supports both Qualified Certificates as well as certificates that are not Qualified Certificates, here named PKC certificates (Public Key Certificates).

All profile requirements apply to both Qualified Certificates and to PKC certificates unless it is explicitly stated that a particular requirement applies only to PKC or Qualified Certificates.

<a name="certificate-content"></a>
### 2.3. Certificate Content

All certificates SHALL be fully compliant with  \[[RFC5280](#rfc5280)\] and \[[EU-CERT-NP](#en-cert-np)\]. All Qualified Certificates SHALL also implement mandatory QC statements as defined in \[[EU-CERT-QC](#eu-cert-qc)\].

<a name="subject-attributes-and-name-forms"></a>
#### 2.3.1. Subject Attributes and Name Forms

<a name="person-identifier-attributes"></a>
##### 2.3.1.1. Person Identifier Attributes

<a name="data-source"></a>
###### 2.3.1.1.1. Data Source

All certificates SHALL contain a unique person identifier, carried in the `serialNumber` attribute (OID 2.5.4.5) in the subject field. The person identifier SHALL be obtained from the Identity Provider in the form of a SAML attribute. For PKC certificates, the SAML attribute SHOULD be one of the attributes listed below. For Qualified Certificates, the SAML attribute SHALL be one of the attributes listed below.

Attribute | Attribute name | Specification
---|---|---
Swedish Personal Identity Number (personnummer) | urn:oid:1.2.752.29.4.13 | \[[AttrSpec](#attrspec)\]
Provisional ID | urn:oid:1.2.752.201.3.4 | \[[AttrSpec](#attrspec)\]
eIDAS Person Identifier | urn:oid:1.2.752.201.3.7 |\[[AttrSpec](#attrspec)\]


<a name="data-format"></a>
###### 2.3.1.1.1. Data Format

The identifier data obtained from the SAML assertion SHALL be stored in the `serialNumber` attribute using one of the following formats:

- using exactly the same format as it was obtained from the SAML attribute, or,
- using conventions specified in \[[EU-CERT-GEN](#eu-cert-gen)\] as defined below.

When storing a person identifier in the `serialNumber` attribute in accordance with \[[EU-CERT-GEN](#eu-cert-gen)\], the certificate SHALL include a semantics identifier as specified in section 5.1 of  \[[EU-CERT-GEN](#eu-cert-gen)\].

**Swedish Personal Identity Number (personnummer)**

When the identifier is a Swedish personal identity number (personnummer) the semantics identifier SHALL be a natural person semantics identifier using the identity type reference "PNO".

> Example: PNOSE-194911172296

**Provisional ID**

When the identifier is a provisional ID the semantics identifier SHALL be a natural person semantics identifier using a local national identity type reference "PI:SE".

> Example: PI:SE-NO:16043700158

This identifier illustrates that the identifier is a Provisional ID (PI) as defined in Sweden (SE) followed by a hyphen (-) and the actual provisional ID for a person from Norway (NO:16043700158).

When the identity type reference is "PI:SE", the `nameRegistrationAuthorities` element of SemanticsInformation shall be present and shall contain a `uniformResourceIdentifier` `generalName` with the following value:

> `http://id.elegnamnden.se/eln/name-registration-authority`

**eIDAS Person Identifier**

eIDAS person identifier attributes MAY be stored in the serial number attribute having exactly the same format as received from the SAML attribute listed above, supported by providing a semantics identifier according to \[[EU-CERT-GEN](#eu-cert-gen)\] identified by the OID `0.4.0.194121.1.3`.

**NOTE:**
> A new version of the \[[EU-CERT-GEN](#eu-cert-gen)\] is processed for approval at the time of publication of this document. The new version will specify a semantics identifier for storing eIDAS person identifier attributes using the semantics identifier OID `0.4.0.194121.1.3`. This semantics identifier (`id-etsi-qcs-semanticsId-eIDASNatural`) is not yet present in the latest published version of the standard.

<a name="other-attribute-requirements"></a>
##### 2.3.1.2. Other Attribute Requirements

An e-mail address, when present, SHALL be stored in a Subject Alternative Name extension as an rfc822Name.

<a name="authentication-context-and-attribute-mapping"></a>
#### 2.3.2. Authentication Context and Attribute Mapping

Certificates MUST include an `AuthContextExtension` according to \[[RFC7773](#rfc7773)\]. This extension SHALL include one SAML Authentication Context Information element identified by the XML schema namespace identifier:

> `http://id.elegnamnden.se/auth-cont/1.0/saci`

The `<saci:SAMLAuthContext>` element SHALL contain both an `<saci:AuthContextInfo>` element as well as an `<saci:IdAttributes>` element.

The `<saci:IdAttributes>` element SHALL contain one `<saci:AttributeMapping>` element for each 
subject attribute or other name form that was obtained from a SAML attribute in the SAML 
assertion used to authenticate the signer as part of the signature creation process. Each
`<saci:AttributeMapping>` element SHALL provide the `<saml:AttributeValue>` that were obtained from
the SAML assertion.

<a name="extended-authentication-information"></a>
##### 2.3.2.1. Extended Authentication Information

In addition to the attributes of `<saci:AuthContextInfo>` it is possible to provide additional authentication information through the extensibility of the `<saci:AuthContextInfo>` element which allows inclusion of a sequence of any element.

One such element is defined in this section, the `<sacex:ExtAuthInfo>` element.

This element MAY be included to provide a name of a parameter and its associated value. 

This element MAY be used to carry the value of any single valued attribute from the associated SAML assertion as long as the SAML attribute value is not composed of a complex type. When used to carry a SAML attribute value, the value of the `<sacex:ExtAuthInfo>` element SHALL be identical to the content of the SAML attribute value element and the `Name` attribute SHALL hold the same value as the `Name` attribute of the corresponding SAML attribute.

The `<sacex:ExtAuthInfo>` element is defined by the following XML Schema:

```
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified"
    targetNamespace="http://id.swedenconnect.se/auth-cont/1.0/ext-auth-info"
    xmlns:sacex="http://id.swedenconnect.se/auth-cont/1.0/ext-auth-info">
    
  <xs:element name="ExtAuthInfo" type="sacex:ExtAuthInfoType" />

  <xs:complexType name="ExtAuthInfoType">
    <xs:simpleContent>
      <xs:extension base="xs:string">
        <xs:attribute name="Name" type="xs:string" use="required" />
        <xs:anyAttribute namespace="##any" processContents="lax" />
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
</xs:schema>
```

**Example:**

The following example illustrates inclusion of the content of a transaction identifier SAML 
attribute as extended authentication information.

```
<saci:SAMLAuthContext
    xmlns:saci="http://id.elegnamnden.se/auth-cont/1.0/saci"
    xmlns:sacext="http://id.swedenconnect.se/auth-cont/1.0/ext-auth-info">
  <saci:AuthContextInfo IdentityProvider="http://eid.example.com/idp"
      AuthenticationInstant="2020-01-10T17:02:46.000Z"
      AuthnContextClassRef="http://id.elegnamnden.se/loa/1.0/loa3"
      AssertionRef="_936e075dc2725b016de57b9a0624c766">
    <sacext:ExtAuthInfo Name="urn:oid:1.2.752.201.3.2">dc6ac7656H89bfb51</sacext:ExtAuthInfo>
  </saci:AuthContextInfo>
  <saci:IdAttributes>...</saci:IdAttributes>
</saci:SAMLAuthContext>
```

<a name="certificate-policy"></a>
#### 2.3.3. Certificate Policy

Certificates SHALL contain at least one referenced certificate policy. PKC certificates SHALL contain at least one reference to a policy identified in \[[EU-POL-NCP](#eu-pol-ncp)\]. Qualified Certificates SHALL reference at least one certificate policy identified in \[[EU-POL-QC](#eu-pol-qc)\].


<a name="normative-references"></a>
## 3. Normative References

<a name="dss"></a>
**[DSS]**
> [OASIS Standard - Digital Signature Service Core Protocols, Elements, and Bindings Version 1.0, April 11, 2007](https://docs.oasis-open.org/dss/v1.0/oasis-dss-core-spec-v1.0-os.html).

<a name="dss-ext"></a>
**[DSS-Ext]**
> [DSS Extension for Federated Central Signing Services](https://docs.swedenconnect.se/technical-framework/latest/09_-_DSS_Extension_for_Federated_Signing_Services.html).

<a name="attrspec"></a>
**[AttrSpec]**
> [Attribute Specification for the Swedish eID Framework.](https://docs.swedenconnect.se/technical-framework/latest/04_-_Attribute_Specification_for_the_Swedish_eID_Framework.html)

<a name="rfc2119"></a>
**[RFC2119]**
> [Bradner, S., Key words for use in RFCs to Indicate Requirement Levels, March 1997](http://www.ietf.org/rfc/rfc2119.txt).

<a name="rfc3739"></a>
**[RFC3739]**
> [Santesson, S., Nystrom, M., and T. Polk, "Internet X.509 Public Key
> Infrastructure: Qualified Certificates Profile", RFC 3739, March
> 2004](https://www.ietf.org/rfc/rfc3739.txt).

<a name="rfc5280"></a>
**[RFC5280]**
> [Cooper, D., Santesson, S., Farrell, S., Boeyen, S., Housley, R., and
> W. Polk, "Internet X.509 Public Key Infrastructure Certificate and
> Certificate Revocation List (CRL) Profile", RFC 5280, May 2008](https://www.ietf.org/rfc/rfc5280.txt).

<a name="rfc7773"></a>
**[RFC7773]**
> [RFC-7773: Authentication Context Certificate Extension](https://tools.ietf.org/html/rfc7773)

<a name="eu-pol-ncp"></a>
**[EU-POL-NCP]**
> ETSI EN 319 411-1, Electronic Signatures and Infrastructures (ESI); Policy and security requirements for Trust Service Providers issuing certificates; Part 1: General requirements.

<a name="eu-pol-ncp"></a>
**[EU-POL-QC]**
> ETSI EN 319 411-2, Electronic Signatures and Infrastructures (ESI); Policy and security requirements for Trust Service Providers issuing certificates; Part 2: Requirements for trust service providers issuing EU qualified certificates

<a name="eu-cert-gen"></a>
**[EU-CERT-GEN]**
> ETSI EN 319 412-1, Electronic Signatures and Infrastructures (ESI); Certificate Profiles; Part 1: Overview and common data structures.

<a name="eu-cert-np"></a>
**[EU-CERT-NP]**
> ETSI EN 319 412-2, Electronic Signatures and Infrastructures (ESI); Certificate Profiles; Part 2: Certificate profile for certificates issued to natural persons.

<a name="eu-cert-qc"></a>
**[EU-CERT-QC]**
> ETSI EN 319 412-5, Electronic Signatures and Infrastructures (ESI); Certificate Profiles; Part 5: QCStatements.

<a name="skv704"></a>
**[SKV704]**
> [Skatteverket, SKV 704 utgåva 8, Personnummer, September
> 2007](https://docs.swedenconnect.se/technical-framework/mirror/skv/skv704-8.pdf).

<a name="skv707"></a>
**[SKV707]**
> [Skatteverket, SKV 707, Utgåva 2,
> Samordningsnummer](https://docs.swedenconnect.se/technical-framework/mirror/skv/skv707-2.pdf).


<a name="changes-between-versions"></a>
## 4. Changes between versions

**Changes between version 1.1 and version 1.2:**

- Update of logotype, fixes of typos and reference list.

- Section 2.3.2.1, "Extended Authentication Information", was added.

**Changes between version 1.0 and version 1.1:**

- Removed the requirement to store "personnummer" or "samordningsnummer".
- Updated standards references to remove old deprecated standards and replace them with the currently published documents.
- Specified optional support for using semantics identifiers in accordance with ETSI EN 319 412-1 to specify that the serialNumber attribute contains a Swedish "personnummer" or "samordningsnummer", Provisional ID or eIDAS person identifier.
- Added requirement to specify ETSI policy identifiers.
- Fix of invalid links for SKV704 and SKV707.
