---
title: Walidacja dokumentów XML | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bde8d47c7437700d43339bf614f48a571997dfd7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158579"
---
# <a name="xml-document-validation"></a>Walidacja dokumentów XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor XML sprawdza składni XML 1.0 i wykonuje sprawdzanie poprawności danych podczas wpisywania. Edytor może sprawdzić przy użyciu definicji typu dokumentu (DTD) lub schematu. Czerwone faliste podkreślenia Podświetl błędy sformułowany XML 1.0. Niebieskie faliste podkreślenia Pokaż błędy semantyczne w oparciu o DTD lub schematu sprawdzania poprawności. Każdy z błędów ma skojarzony wpis na liście błędów. Można również wyświetlić komunikat o błędzie, przez umieszczenie wskaźnika myszy nad falistą linią.  
  
 Schematy używane podczas sprawdzania poprawności znajdują się przez dopasowanie `targetNamespace` skompilowanych schematu z deklaracją xmlns elementu. Skompilowany schematy są załadowane z jednej z następujących lokalizacji, w kolejności priorytetu:  
  
- Z pliku o nazwie określonej w **schematów** pola w oknie właściwości dokumentu.  
  
- Wbudowany schemat lub DTD.  
  
- Zewnętrznej definicji DTD lub `xsd:schemaLocation` i `xsd:noNamespaceSchemaLocation` atrybutu  
  
- "X-schema" XDR schematu identyfikatora URI obszaru nazw.  
  
  Schematy można także znaleźć w następujących lokalizacjach dodatkowych, jeśli schemat zawiera pusty docelowego obszaru nazw:  
  
- Inne okno edytora, która zawiera schemat.  
  
- Schemat w bieżącym rozwiązaniu.  
  
- Schemat z katalogu pamięci podręcznej schematu.  
  
## <a name="xslt-files"></a>Pliki XSLT  
 Podczas edytowania pliku XSLT, plik xslt.xsd, znajdujący się w pamięci podręcznej schematów służy do sprawdzania poprawności. Błędy sprawdzania poprawności są wyświetlane jako niebieskie faliste podkreślenia. Błędy kompilatora XSLT są wyświetlane jako czerwone faliste podkreślenia.  
  
## <a name="xml-schema-xsd-files"></a>Pliki schematów (XSD) XML  
 Edytując plik schematu XML, plik xsdschema.xsd, znajdujący się w pamięci podręcznej schematów służy do sprawdzania poprawności. Błędy sprawdzania poprawności są wyświetlane jako niebieskie faliste podkreślenia. Błędy kompilacji są także wyświetlane czerwoną, falistą.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor XML](../xml-tools/xml-editor.md)
