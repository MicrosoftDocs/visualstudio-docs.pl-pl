---
title: Edytor XML i Projektant schematów
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9412d89ee7d9ad1412f0eaf9fe9341e336a65e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668708"
---
# <a name="xml-tools-in-visual-studio"></a>Narzędzia XML w Visual Studio

*XML (XML)* jest językiem znaczników, który zapewnia format do opisywania danych. KOD XML oddziela dane i swoją prezentację przy użyciu skojarzonych arkuszy stylów, takich jak Extensible Stylesheet Language (XSL) i kaskadowych arkuszy stylów (CSS). Program Visual Studio zawiera narzędzia i funkcje, które ułatwiają pracę z schematami XML, XSLT i XML.

## <a name="xml-editor"></a>Edytor XML

[Edytor XML](xml-editor.md) służy do EDYTOWANIA dokumentów XML. Zapewnia pełną kontrolę składni XML, sprawdzanie poprawności schematu podczas pisania, kodowania kolorów i IntelliSense. W przypadku podanej definicji typu schematu lub dokumentu jest on używany przez funkcję IntelliSense do wyświetlania listy dozwolonych elementów i atrybutów.

Dodatkowe funkcje obejmują:

- Obsługa fragmentów kodu XML, w tym fragmentów kodu generowanych przez schemat

- Konspekt dokumentu, aby można było rozwijać i zwijać elementy

- Możliwość wykonywania transformacji XSLT i wyświetlania wyników w postaci tekstu, XML lub HTML

- Możliwość generowania schematów języka definicji schematu XML (XSD) z dokumentu wystąpienia XML

- Obsługa edycji arkuszy stylów XSLT, w tym obsługi technologii IntelliSense

- Eksplorator schematu XML

## <a name="xml-schema-designer"></a>Projektant schematu XML

[Projektant schematu XML](xml-schema-designer.md) jest zintegrowany z programem Visual Studio i EDYTORem XML, aby umożliwić współdziałanie z schematami języka definicji schematu XML (XSD).

## <a name="xslt-debugging"></a>Debugowanie kodu XSLT

Program Visual Studio obsługuje [debugowanie arkuszy stylów XSLT](../xml-tools/debugging-xslt.md). Za pomocą debugera można ustawić punkty przerwania w arkuszu stylów XSLT, przejść do arkusza stylów XSLT z kodu i tak dalej.

> [!NOTE]
> Debuger XSLT jest dostępny tylko w wersji Enterprise programu Visual Studio.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml?displayProperty=fullName>
- [Przekształcenia XSLT](/dotnet/standard/data/xml/xslt-transformations)
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [Model DOM (XML Document Object Model)](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [Model SOM (XML Schema Object Model)](/dotnet/standard/data/xml/xml-schema-object-model-som)