---
title: 'Instrukcje: Tworzenie dokumentu XML na podstawie schematu XSD'
description: Dowiedz się, jak używać funkcji Generuj przykładową XML do tworzenia dokumentu XML na podstawie schematu XSD.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6bc802d48bc76bc5f0c6a4c272bf994e87bb8443
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970312"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Instrukcje: Tworzenie dokumentu XML na podstawie schematu XSD

Funkcja **Generuj przykładowy kod XML** generuje przykładowy plik XML na podstawie pliku schematu XML (XSD).

Tej opcji można użyć w następujących scenariuszach:

- Zrozumienie użycia różnych konstrukcji w schemacie.

- , Aby upewnić się, że schemat jest przeznaczony do wykonania.

Funkcja **Generuj przykładowy kod XML** jest dostępna tylko dla elementów globalnych i wymaga prawidłowego zestawu schematu XML.

Ta funkcja zwykle generuje prawidłowe dokumenty XML. Jeśli jednak schemat zawiera co najmniej jeden z poniższych elementów, przykład może być nieprawidłowy:

- `xs:key` `xs:keyref` Ograniczenia tożsamości, i `xs:unique` .

- `xs:pattern` Facets.

- Wyliczenia `xs:QName` typu.

- `xs:ENTITY`, `xs:ENTITIES` i `xs:NOTATION` .

Należy również pamiętać, że `xs:base64Binary` zawartość zostanie wygenerowana tylko wtedy, gdy w schemacie tego typu wystąpiły wyliczenia.

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Aby wygenerować dokument wystąpienia XML na podstawie pliku XSD

1. Wykonaj kroki opisane w temacie [How to: Create i Edit a XSD File Schema](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. W [Eksploratorze schematu XML](../xml-tools/xml-schema-explorer.md), kliknij prawym przyciskiem myszy `PurchaseOrder` element globalny, a następnie wybierz polecenie **Generuj przykładowy kod XML**.

     Po wybraniu tej opcji PurchaseOrder. plik *XML* z następującą przykładową zawartością XML zostanie wygenerowany i otwarty w edytorze XML:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PurchaseOrder OrderDate="1900-01-01" xmlns="http://tempuri.org/PurchaseOrderSchema.xsd">
      <ShipTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </ShipTo>
      <ShipTo country="US">
        <name>name2</name>
        <street>street2</street>
        <city>city2</city>
        <state>state2</state>
        <zip>-79228162514264337593543950335</zip>
      </ShipTo>
      <BillTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </BillTo>
    </PurchaseOrder>
    ```
