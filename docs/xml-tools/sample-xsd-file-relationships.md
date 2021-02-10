---
title: 'Przykładowy plik XSD: Relacje'
description: Wyświetlanie przykładowego pliku XSD dla schematu zamówienia zakupu z adnotacjami i dokumentacją, które są używane w różnych przykładach w dokumentacji projektanta schematu XSD.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: sample
ms.assetid: 60126510-b7dd-4cb4-92d3-9883590b92f2
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9dbfd5459ae750236afde63574959fd6b7c7b37c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956571"
---
# <a name="sample-xsd-file-relationships"></a>Przykładowy plik XSD: relacje

Następujący plik XSD jest używany w różnych przykładach w dokumentacji projektanta schematu XSD. Ten plik jest schematem zamówienia zakupu z adnotacjami i dokumentacją.

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <xs:element name="pet" type="PetType"/>

  <xs:attributeGroup name="NameAgeAttributes">
    <xs:attribute name="age" type="xs:integer" use="required"/>
    <xs:attribute name="name" type="xs:string" use="required"/>
  </xs:attributeGroup>

  <xs:complexType name="PetType">
    <xs:attributeGroup ref="NameAgeAttributes"/>
  </xs:complexType>

  <xs:element name="cat" substitutionGroup="pet">
    <xs:complexType>
      <xs:complexContent>
        <xs:extension base="PetType">
          <xs:sequence>
            <xs:element name="weight" type="xs:integer"/>
            <xs:element name="color" type="xs:string"/>
            <xs:element name="breed" type="xs:integer"/>
          </xs:sequence>
        </xs:extension>
      </xs:complexContent>
    </xs:complexType>
  </xs:element>

  <xs:element name="dog" substitutionGroup="pet">
    <xs:complexType>
      <xs:complexContent>
        <xs:extension base="PetType">
          <xs:sequence>
            <xs:element name="weight" type="xs:integer"/>
            <xs:element name="color" type="xs:string"/>
            <xs:element name="breed" type="xs:integer"/>
          </xs:sequence>
        </xs:extension>
      </xs:complexContent>
    </xs:complexType>
  </xs:element>

</xs:schema>
```

> [!NOTE]
> Przykładowe firmy, organizacje, produkty, nazwy domen, adresy e-mail, logo, osoby, miejsca i zdarzenia wymienione w tym dokumencie są fikcyjne. Żadne powiązania z rzeczywistymi firmami, organizacjami, produktami, nazwami domen, adresami e-mail, logo, osobami, miejscami lub zdarzeniami nie są zamierzone ani wywnioskowane.
