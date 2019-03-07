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
ms.openlocfilehash: fa5206ea42385cb716c522504648e1d8fd5879ae
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525121"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Instrukcje: Tworzenie dokumentu XML na podstawie schematu XSD

**Generowanie XML przykładowe** funkcja generuje przykładowy plik XML na podstawie pliku schematu XML (XSD).

 Tej opcji można użyć w następujących scenariuszach:

-   Aby poznać użycie różnych konstrukcji w schemacie.

-   Aby upewnić się, że schemat wykonuje co ma na celu.

**Generowanie XML przykładowe** funkcja jest dostępna tylko na elementy globalne i wymaga prawidłowego zestawu schematu XML.

Ta funkcja generuje zwykle ważnych dokumentów XML. Jednakże, jeśli schemat zawiera co najmniej jeden z następujących czynności, próbki mogą być nieprawidłowe:

-   `xs:key`, `xs:keyref`, I `xs:unique` ograniczenia tożsamości.

-   `xs:pattern` zestawy reguł.

-   Wyliczenia o `xs:QName` typu.

-   `xs:ENTITY`, `xs:ENTITIES`, i `xs:NOTATION` typów.

Ponadto należy pamiętać, że `xs:base64Binary` zawartość zostanie wygenerowany tylko wtedy, gdy wyliczenia występują w schematu dla tego typu.

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Można wygenerować wystąpienia dokumentu XML na podstawie pliku XSD

1.  Postępuj zgodnie z instrukcjami w [jak: Tworzenie i edytowanie pliku schematu XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  W [Eksploratora schematu XML](../xml-tools/xml-schema-explorer.md), kliknij prawym przyciskiem myszy `PurchaseOrder` element globalny. Wybierz **wygenerować przykładowy kod XML**.

     Po wybraniu tej opcji, PurchaseOrder. *xml* pliku o następującej zawartości XML przykładowych zostanie wygenerowany i otwarty w edytorze XML:

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