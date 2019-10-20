---
title: 'Instrukcje: Tworzenie dokumentu XML na podstawie schematu XSD | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9e48c48d6711a1eb21157122d13790e22688855
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670949"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Instrukcje: Tworzenie dokumentu XML na podstawie schematu XSD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkcja **Generuj przykładowy kod XML** generuje przykładowy plik XML na podstawie pliku schematu XML (XSD).

 Tej opcji można użyć w następujących scenariuszach:

- Zrozumienie użycia różnych konstrukcji w schemacie.

- , Aby upewnić się, że schemat jest przeznaczony do wykonania.

  Funkcja **Generuj przykładowy kod XML** jest dostępna tylko dla elementów globalnych i wymaga prawidłowego zestawu schematu XML.

  Ta funkcja zwykle generuje prawidłowe dokumenty XML. Jeśli jednak schemat zawiera co najmniej jeden z poniższych elementów, przykład może być nieprawidłowy:

- Ograniczenia tożsamości `xs:key`, `xs:keyref` i `xs:unique`.

- `xs:pattern` aspektów.

- Wyliczenia typu `xs:QName`.

- typy `xs:ENTITY`, `xs:ENTITIES` i `xs:NOTATION`.

  Należy również pamiętać, że zawartość `xs:base64Binary` będzie generowana tylko wtedy, gdy w schemacie tego typu wystąpiły wyliczenia.

### <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Aby wygenerować dokument wystąpienia XML na podstawie pliku XSD

1. Wykonaj kroki opisane w temacie [How to: Create i Edit a XSD File Schema](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. W [Eksploratorze schematu XML](../xml-tools/xml-schema-explorer.md)kliknij prawym przyciskiem myszy element globalny `PurchaseOrder`. Wybierz pozycję **Generuj przykładowy kod XML**.

     Po wybraniu tej opcji plik PurchaseOrder. XML z następującą przykładową zawartością XML zostanie wygenerowany i otwarty w edytorze XML:

    ```
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

## <a name="see-also"></a>Zobacz też
 [Praca z danymi XML](../xml-tools/working-with-xml-data.md)
