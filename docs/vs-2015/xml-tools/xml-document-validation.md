---
title: Sprawdzanie poprawności dokumentu XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ee5d3cff260346a5bcc1806b09b955642c608f14
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669490"
---
# <a name="xml-document-validation"></a>Walidacja dokumentów XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor XML sprawdza składnię XML 1,0 i sprawdza sprawdzanie poprawności danych podczas wpisywania. Edytor może sprawdzić poprawność przy użyciu definicji typu dokumentu (DTD) lub schematu. Czerwone faliste podkreślenie wyróżnia wszystkie poprawnie sformułowane błędy w formacie XML 1,0. Niebieskie faliste podkreślenia pokazują błędy semantyczne na podstawie walidacji DTD lub schematu. Każdy błąd ma skojarzony wpis na liście błędów. Możesz również wyświetlić komunikat o błędzie, zatrzymując wskaźnik myszy nad linią falistą.

 Schematy używane w walidacji są dostępne przez dopasowanie `targetNamespace` skompilowanego schematu z deklaracją xmlns elementu. Skompilowane schematy są ładowane z jednej z następujących lokalizacji wymienionych w kolejności priorytetu:

- Z nazwy pliku określonej w polu **schematy** w okno właściwości dokumentu.

- Osadzony schemat lub DTD.

- Zewnętrzna definicja DTD lub `xsd:schemaLocation` i atrybut `xsd:noNamespaceSchemaLocation`

- Identyfikator URI przestrzeni nazw schematu XDR "x-Schema".

  Schematy można również znaleźć w następujących dodatkowych lokalizacjach, gdy schemat zawiera niepustą przestrzeń nazw target:

- Inne okno edytora zawierające schemat.

- Schemat w bieżącym rozwiązaniu.

- Schemat z katalogu pamięci podręcznej schematu.

## <a name="xslt-files"></a>Pliki XSLT
 Podczas edytowania pliku XSLT plik XSLT. xsd znajdujący się w pamięci podręcznej schematu jest używany do walidacji. Błędy walidacji są wyświetlane jako niebieskie faliste podkreślenia. Błędy kompilatora XSLT są wyświetlane jako czerwone faliste podkreślenia.

## <a name="xml-schema-xsd-files"></a>Pliki schematu XML (XSD)
 Podczas edytowania pliku schematu XML plik XSDSchema. xsd znajdujący się w pamięci podręcznej schematu jest używany do walidacji. Błędy walidacji są wyświetlane jako niebieskie faliste podkreślenia. Wszystkie błędy kompilacji są również wyświetlane z czerwonymi falistymi podkreśleniami.

## <a name="see-also"></a>Zobacz też
 [Edytor XML](../xml-tools/xml-editor.md)
