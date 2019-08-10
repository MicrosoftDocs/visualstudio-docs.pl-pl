---
title: 'Instrukcje: Tworzenie dokumentu XML na podstawie schematu XSD'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7739f33bad62667fdc7be8704237ebdd3932739c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918564"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Instrukcje: Tworzenie dokumentu XML na podstawie schematu XSD

Funkcja **Generuj przykładowy kod XML** generuje przykładowy plik XML na podstawie pliku schematu XML (XSD).

Tej opcji można użyć w następujących scenariuszach:

- Zrozumienie użycia różnych konstrukcji w schemacie.

- , Aby upewnić się, że schemat jest przeznaczony do wykonania.

Funkcja **Generuj przykładowy kod XML** jest dostępna tylko dla elementów globalnych i wymaga prawidłowego zestawu schematu XML.

Ta funkcja zwykle generuje prawidłowe dokumenty XML. Jeśli jednak schemat zawiera co najmniej jeden z poniższych elementów, przykład może być nieprawidłowy:

- Ograniczenia tożsamości `xs:keyref`,i `xs:unique` . `xs:key`

- `xs:pattern`Facets.

- `xs:QName` Wyliczenia typu.

- `xs:ENTITY`, `xs:ENTITIES`i .`xs:NOTATION`

Należy również pamiętać, `xs:base64Binary` że zawartość zostanie wygenerowana tylko wtedy, gdy w schemacie tego typu wystąpiły wyliczenia.

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Aby wygenerować dokument wystąpienia XML na podstawie pliku XSD

1. Wykonaj kroki opisane w [temacie How to: Tworzenie i edytowanie pliku](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)schematu XSD.

2. W [Eksploratorze schematu XML](../xml-tools/xml-schema-explorer.md), kliknij `PurchaseOrder` prawym przyciskiem myszy element globalny. Wybierz pozycję **Generuj przykładowy kod XML**.

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