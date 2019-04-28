---
title: Edytor XML i Projektant schematu
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
- XML [Visual Studio], .NET Framework classes
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8854aee047fa961c4f0973397cfc2fe6ac6e6ad
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808174"
---
# <a name="xml-tools-in-visual-studio"></a>Narzędzia XML w Visual Studio

*Język XML (Extensible Markup)* jest językiem znaczników, zapewniający format opisu danych. XML oddziela dane i jego prezentacji za pomocą skojarzonego arkuszy stylów, takich jak arkusz stylów języka XSL (Extensible) i kaskadowych arkuszy stylów (CSS). Visual Studio zawiera narzędzia i funkcje, dzięki którym łatwiej jest pracować z XML, XSLT i XML, schematy.

## <a name="xml-editor"></a>Edytor XML

[Edytora XML](xml-editor.md) jest używany do edytowania dokumentów XML. Zapewnia pełną składnię XML sprawdzanie sprawdzanie poprawności schematu podczas wpisywania kolorowania i technologii IntelliSense. Jeśli definicję typu schematu lub dokumentu zostanie podany, aby wyświetlić listę dopuszczalny rozmiar elementów i atrybutów jest używany przez funkcję IntelliSense.

Dodatkowe funkcje obejmują:

- Obsługa fragmentów kodu XML, tym wygenerować schematu fragmentów kodu

- Dokumentu, tworzenie konspektu, tak aby elementy można rozszerzyć i zwinięty

- Możliwość wykonania przekształcenia XSLT i wyświetlić wyniki jako tekst, XML lub HTML

- Możliwość generowania schematy języka (XSD) definicji schematu XML z wystąpienia dokumentu XML

- Obsługa Edytowanie arkuszy stylów XSLT, łącznie z obsługą technologii IntelliSense

- Eksplorator schematu XML

## <a name="xml-schema-designer"></a>Projektant schematu XML

[Projektanta schematu XML](xml-schema-designer.md) jest zintegrowana z usługą Visual Studio i edytorem XML, które umożliwiają pracę ze schematami języka (XSD) definicji schematu XML.

## <a name="xslt-debugging"></a>Debugowanie kodu XSLT

Program Visual Studio obsługuje [debugowania arkuszy stylów XSLT](../xml-tools/debugging-xslt.md). Za pomocą debugera, możesz ustawić punkty przerwania w arkuszu stylów XSLT, krok po kroku do arkusza stylów XSLT z kodu i tak dalej.

> [!NOTE]
> Debuger XSLT jest dostępna tylko w wersji Enterprise programu Visual Studio.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml?displayProperty=fullName>
- [Przekształcenia XSLT](/dotnet/standard/data/xml/xslt-transformations)
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [Model DOM (XML Document Object Model)](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [Model SOM (XML Schema Object Model)](/dotnet/standard/data/xml/xml-schema-object-model-som)