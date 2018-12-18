---
title: Narzędzia XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f87c06e2bfc3885c0f52230e927933ff3cb0d87c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055001"
---
# <a name="xml-tools-in-visual-studio"></a>Narzędzia XML w programie Visual Studio

*Język XML (Extensible Markup)* jest językiem znaczników, zapewniający format opisu danych. To ułatwia bardziej precyzyjne deklaracje elementu zawartości i bardziej znaczących wyników wyszukiwania na wielu platformach. Ponadto XML umożliwia rozdzielenie prezentacji z danych. Na przykład w formacie HTML umożliwia tagi przeglądarka do wyświetlania danych jako pogrubić lub pochylić; w pliku XML użyjesz tagi wyłącznie w celu określenia danych, takich jak nazwa miejscowości, temperaturę i ciśnienie atmosferyczne. W pliku XML używasz arkuszy stylów, takich jak arkusz stylów języka XSL (Extensible) i kaskadowych arkuszy stylów (CSS) do prezentowania danych w przeglądarce. XML oddziela dane od prezentacji i procesu. Dzięki temu można wyświetlić i przetwarzania danych, jak chcesz, stosując arkusze stylów różnych i aplikacji.

Kod XML jest podzbiorem SGML jest zoptymalizowany pod kątem dostarczania w sieci Web. Jest on definiowany przez World Wide Web Consortium (W3C). Ten normalizacji gwarantuje, że dane ze strukturą są jednolite i niezależny od aplikacji lub dostawców.

Kod XML jest sercem wielu funkcji programu Visual Studio i .NET Framework. Na poniższej liście artykułu nazwy, narzędzia i funkcje związane z XML, które są oferowane w programie Visual Studio i .NET Framework.

Aby uzyskać więcej informacji, zobacz <xref:System.Xml?displayProperty=fullName> dokumentacji.

## <a name="reference"></a>Tematy pomocy

[Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699) udostępnia [edytora XML](http://go.microsoft.com/fwlink/?LinkId=228249) drzewo za pośrednictwem analizy [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) żadnych dokumentów XML.

[Odwołanie do standardów XML](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) informacje na temat technologii XML, w tym XML, definicja typu dokumentu (DTD), język definicji schematu XML (XSD) i XSLT.

<xref:System.Xml?displayProperty=fullName> W tym artykule opisano klasy i inne elementy, które tworzą <xref:System.Xml> przestrzeni nazw i zawiera łącza do bardziej szczegółowych informacji dla każdego elementu.

<xref:System.Xml.Serialization?displayProperty=fullName> W tym artykule opisano klasy i inne elementy, które tworzą <xref:System.Xml.Serialization> przestrzeni nazw i zawiera łącza do bardziej szczegółowych informacji o każdym elemencie.

## <a name="related-sections"></a>Sekcje pokrewne

[XML Document Object Model (DOM)](/dotnet/standard/data/xml/xml-document-object-model-dom) w tym artykule opisano sposób, w jaki <xref:System.Xml.XmlDocument> i jej klas skojarzonych przestrzegania W3C Document Object Model (Core), poziom 1 i specyfikacje obsługi przestrzeni nazw na poziomie 2.

[Przetwarzanie danych XML przy użyciu elementu XmlReader i XmlWriter](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc189001\(v\=vs.95\))

[Przekształcenia XSLT](/dotnet/standard/data/xml/xslt-transformations) w tym artykule opisano sposób, w jaki <xref:System.Xml.Xsl.XslCompiledTransform> klasa implementuje specyfikacji XSLT 1.0 zalecenia.

[Przetwarzanie danych XML przy użyciu modelu danych XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model) w tym artykule opisano sposób, w jaki <xref:System.Xml.XPath.XPathNavigator> klasy może przetwarzać dane XML przechowywane w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu. <xref:System.Xml.XPath.XPathNavigator> Klasy opiera się na języki XQuery 1.0 i XPath 2.0 Data Model i może służyć do nawigowania i edytowanie danych XML.

[XML schematu obiektu modelu (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som) opisano klasy, służące do tworzenia i manipulowania schematów XML, zapewniając <xref:System.Xml.Schema.XmlSchema> klasy, aby ładować i edytować schemat.