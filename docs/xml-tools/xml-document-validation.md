---
title: Sprawdzanie poprawności dokumentu XML w edytorze XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13574a13aecf7edbc9627e7b8288689206f278c2
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926702"
---
# <a name="xml-document-validation"></a>Walidacja dokumentów XML

Edytor XML sprawdza składnię XML 1,0 i sprawdza sprawdzanie poprawności danych podczas wpisywania. Edytor może sprawdzić poprawność przy użyciu definicji typu dokumentu (DTD) lub schematu. Czerwone faliste podkreślenie wyróżnia wszystkie poprawnie sformułowane błędy w formacie XML 1,0. Niebieskie faliste podkreślenia pokazują błędy semantyczne na podstawie walidacji DTD lub schematu. Każdy błąd ma skojarzony wpis na liście błędów. Możesz również wyświetlić komunikat o błędzie, zatrzymując wskaźnik myszy nad linią falistą.

Schematy używane w walidacji są dostępne przez dopasowanie `targetNamespace` skompilowanego schematu z deklaracją xmlns elementu. Skompilowane schematy są ładowane z jednej z następujących lokalizacji wymienionych w kolejności priorytetu:

- Z nazwy pliku określonej w polu **schematy** okna **Właściwości** dokumentu.

- Osadzony schemat lub DTD.

- Zewnętrzna definicja DTD lub `xsd:schemaLocation` atrybut i `xsd:noNamespaceSchemaLocation`

- Identyfikator URI przestrzeni nazw schematu XDR "x-Schema".

Schematy można również znaleźć w następujących dodatkowych lokalizacjach, gdy schemat zawiera niepustą przestrzeń nazw target:

- Inne okno edytora zawierające schemat.

- Schemat w bieżącym rozwiązaniu.

- Schemat z katalogu pamięci podręcznej schematu.

## <a name="xslt-files"></a>Pliki XSLT
Podczas edytowania pliku XSLT plik *XSLT. xsd* znajdujący się w pamięci podręcznej schematu jest używany do walidacji. Błędy walidacji są wyświetlane jako niebieskie faliste podkreślenia. Błędy kompilatora XSLT są wyświetlane jako czerwone faliste podkreślenia.

## <a name="xml-schema-xsd-files"></a>Pliki schematu XML (XSD)
Podczas edytowania pliku schematu XML plik *XSDSchema. xsd* znajdujący się w pamięci podręcznej schematu jest używany do walidacji. Błędy walidacji są wyświetlane jako niebieskie faliste podkreślenia. Wszystkie błędy kompilacji są również wyświetlane z czerwonymi falistymi podkreśleniami.

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)