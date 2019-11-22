---
title: Narzędzia XML
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ee0cf61f8ec2787894c6f67b8ac75424246c507
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297448"
---
# <a name="xml-tools-in-visual-studio"></a>Narzędzia XML w Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Język XML (Extensible Markup) * jest językiem znaczników, zapewniający format opisu danych. To ułatwia bardziej precyzyjne deklaracje elementu zawartości i bardziej znaczących wyników wyszukiwania na wielu platformach. Ponadto XML umożliwia rozdzielenie prezentacji z danych. Na przykład w formacie HTML umożliwia tagi przeglądarka do wyświetlania danych jako pogrubić lub pochylić; w pliku XML użyjesz tagi wyłącznie w celu określenia danych, takich jak nazwa miejscowości, temperaturę i ciśnienie atmosferyczne. W pliku XML używasz arkuszy stylów, takich jak arkusz stylów języka XSL (Extensible) i kaskadowych arkuszy stylów (CSS) do prezentowania danych w przeglądarce. XML oddziela dane od prezentacji i procesu. Dzięki temu można wyświetlić i przetwarzania danych, jak chcesz, stosując arkusze stylów różnych i aplikacji.

 Kod XML jest podzbiorem SGML jest zoptymalizowany pod kątem dostarczania w sieci Web. Jest on definiowany przez World Wide Web Consortium (W3C). Ta normalizacji gwarantuje, że dane ze strukturą będą jednolite i niezależny od aplikacji lub dostawców.

 Kod XML jest sercem wiele funkcji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Poniższa lista tematów zawiera nazwy narzędzia i funkcje związane z XML, które są oferowane w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

 Aby uzyskać więcej informacji, zobacz [Centrum deweloperów języka XML](https://go.microsoft.com/fwlink/?LinkID=100176), który zawiera najnowszą dokumentację, informacje techniczne, pliki do pobrania, grupy dyskusyjne i inne zasoby dla deweloperów XML.

## <a name="in-this-section"></a>W tej sekcji
 [Praca z danymi XML](../xml-tools/working-with-xml-data.md) Discusses roli XML w danych sposób odbywa się w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md) zawiera łącza do tematów dotyczących debugowanie kodu XSLT przy użyciu debugera programu Visual Studio.

## <a name="reference"></a>Tematy pomocy
 [Microsoft.VisualStudio.XmlEditor](https://go.microsoft.com/fwlink/?LinkID=165699) udostępnia [edytora XML](https://go.microsoft.com/fwlink/?LinkId=228249) drzewo za pośrednictwem analizy [System.Xml.Linq](https://go.microsoft.com/fwlink/?LinkId=228250) żadnych dokumentów XML.

 [Odwołanie do standardów XML](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) informacje na temat technologii XML, w tym XML, definicja typu dokumentu (DTD), język definicji schematu XML (XSD) i XSLT.

 <xref:System.Xml?displayProperty=fullName> W tym artykule opisano klasy i inne elementy, które tworzą <xref:System.Xml> przestrzeni nazw i zawiera łącza do bardziej szczegółowych informacji dla każdego elementu.

 <xref:System.Xml.Serialization?displayProperty=fullName> W tym artykule opisano klasy i inne elementy, które tworzą <xref:System.Xml.Serialization> przestrzeni nazw i zawiera łącza do bardziej szczegółowych informacji o każdym elemencie.

## <a name="related-sections"></a>Sekcje pokrewne
 [XML Document Object Model (DOM)](https://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) w tym artykule opisano sposób, w jaki <xref:System.Xml.XmlDocument> i jej klas skojarzonych przestrzegania W3C Document Object Model (Core), poziom 1 i specyfikacje obsługi przestrzeni nazw na poziomie 2.

 [Odczyt XML z element XmlReader](https://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) w tym artykule opisano sposób, w jaki <xref:System.Xml.XmlReader> udostępnia niebuforowany do przodu tylko, tylko do odczytu dostęp do danych XML w porównaniu z strumień XML.

 [Pisanie XML przy użyciu Element XmlWriter](https://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) w tym artykule opisano sposób, w jaki <xref:System.Xml.XmlWriter> zapewnia niebuforowany, przekazywać tylko sposób generowania strumieni XML i ułatwia tworzenie dokumentów XML, które są zgodne ze standardem W3C.

 [Przekształcenia XSLT](https://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) w tym artykule opisano sposób, w jaki <xref:System.Xml.Xsl.XslCompiledTransform> klasa implementuje specyfikacji XSLT 1.0 zalecenia.

 [Przetwarzanie danych XML przy użyciu modelu danych XPath](https://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) w tym artykule opisano sposób, w jaki <xref:System.Xml.XPath.XPathNavigator> klasy może przetwarzać dane XML przechowywane w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu. <xref:System.Xml.XPath.XPathNavigator> Klasy opiera się na języki XQuery 1.0 i XPath 2.0 Data Model i może służyć do nawigowania i edytowanie danych XML.

 [XML schematu obiektu modelu (SOM)](https://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) opisano klasy, służące do tworzenia i manipulowania schematów XML, zapewniając <xref:System.Xml.Schema.XmlSchema> klasy, aby ładować i edytować schemat.
