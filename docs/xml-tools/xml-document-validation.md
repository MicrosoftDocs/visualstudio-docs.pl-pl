---
title: Walidacja dokumentów XML w edytorze XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01f66f80c2a396a9aad57bdf131f08afd2b73594
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020585"
---
# <a name="xml-document-validation"></a>Walidacja dokumentów XML

Edytor XML sprawdza składni XML 1.0 i wykonuje sprawdzanie poprawności danych podczas wpisywania. Edytor może sprawdzić przy użyciu definicji typu dokumentu (DTD) lub schematu. Czerwone faliste podkreślenia Podświetl błędy sformułowany XML 1.0. Niebieskie faliste podkreślenia Pokaż błędy semantyczne w oparciu o DTD lub schematu sprawdzania poprawności. Każdy z błędów ma skojarzony wpis na liście błędów. Można również wyświetlić komunikat o błędzie, przez umieszczenie wskaźnika myszy nad falistą linią.

 Schematy używane podczas sprawdzania poprawności znajdują się przez dopasowanie `targetNamespace` skompilowanych schematu z deklaracją xmlns elementu. Skompilowany schematy są załadowane z jednej z następujących lokalizacji, w kolejności priorytetu:

-   Z pliku o nazwie określonej w **schematów** pola dokumentu **właściwości** okna.

-   Wbudowany schemat lub DTD.

-   Zewnętrznej definicji DTD lub `xsd:schemaLocation` i `xsd:noNamespaceSchemaLocation` atrybutu

-   "X-schema" XDR schematu identyfikatora URI obszaru nazw.

Schematy można także znaleźć w następujących lokalizacjach dodatkowych, jeśli schemat zawiera pusty docelowego obszaru nazw:

-   Inne okno edytora, która zawiera schemat.

-   Schemat w bieżącym rozwiązaniu.

-   Schemat z katalogu pamięci podręcznej schematu.

## <a name="xslt-files"></a>Pliki XSLT
 Podczas edytowania pliku XSLT *xslt.xsd* plik znajdujący się w pamięci podręcznej schematu jest używany do sprawdzania poprawności. Błędy sprawdzania poprawności są wyświetlane jako niebieskie faliste podkreślenia. Błędy kompilatora XSLT są wyświetlane jako czerwone faliste podkreślenia.

## <a name="xml-schema-xsd-files"></a>Pliki schematów (XSD) XML
 Podczas edytowania pliku schematu XML *xsdschema.xsd* plik znajdujący się w pamięci podręcznej schematu jest używany do sprawdzania poprawności. Błędy sprawdzania poprawności są wyświetlane jako niebieskie faliste podkreślenia. Błędy kompilacji są także wyświetlane czerwoną, falistą.

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)