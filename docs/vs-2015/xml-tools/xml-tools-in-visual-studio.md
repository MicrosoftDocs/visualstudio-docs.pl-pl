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
ms.openlocfilehash: b9a46523c4c856367e77c345c7e44d0dbc87508f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845974"
---
# <a name="xml-tools-in-visual-studio"></a>Narzędzia XML w Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML (XML) * jest językiem znaczników, który udostępnia format do opisywania danych. Ułatwia to dokładniejsze deklaracje zawartości i bardziej zrozumiałe wyniki wyszukiwania na wielu platformach. Ponadto XML umożliwia rozdzielenie prezentacji z danych. Na przykład w kodzie HTML używasz tagów do informowania przeglądarki o wyświetlaniu danych jako pogrubienia lub kursywy; w kodzie XML używasz tagów tylko do opisywania danych, takich jak nazwa miasta, temperatura i ciśnienie atmosferyczne. W języku XML są używane arkusze stylów, takie jak Extensible Stylesheet Language (XSL) i kaskadowe arkusze stylów (CSS), aby przedstawić dane w przeglądarce. KOD XML oddziela dane od prezentacji i procesu. Dzięki temu można wyświetlać i przetwarzać dane w odpowiedni sposób, stosując różne arkusze stylów i aplikacje.

 XML jest podzbiorem języka SGML zoptymalizowanego pod kątem dostarczania w sieci Web. Jest on definiowany przez organizacja World Wide Web Consortium (W3C). Ta standaryzacja gwarantuje, że dane strukturalne będą jednorodne i niezależne od aplikacji lub dostawców.

 Język XML jest podstawowy dla wielu funkcji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . W poniższej sekcji wymieniono narzędzia i funkcje związane z językiem XML, które są oferowane w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

 Aby uzyskać więcej informacji, zobacz [Centrum deweloperów XML](https://msdn.microsoft.com/data/bb190600.aspx), w którym znajduje się Najnowsza dokumentacja, informacje techniczne, pliki do pobrania, grupy dyskusyjne i inne zasoby dla deweloperów XML.

## <a name="in-this-section"></a>W tej sekcji
 [Praca z danymi XML](../xml-tools/working-with-xml-data.md) Omawia rolę XML w sposobie obsługi danych w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md) Zawiera łącza do tematów dotyczących używania debugera programu Visual Studio do debugowania XSLT.

## <a name="reference"></a>Dokumentacja
 [ EdytorMicrosoft.VisualStudio.Xml](https://msdn.microsoft.com/library/microsoft.visualstudio.xmleditor.aspx) Uwidacznia drzewo analizy [edytora XML](https://msdn.microsoft.com/library/ms255810.aspx) za pomocą [System.Xml. LINQ](https://msdn.microsoft.com/library/system.xml.linq.aspx) dla dowolnych dokumentów XML.

 [Dokumentacja standardów XML](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) Zawiera informacje o technologiach XML, w tym XML, definicji typu dokumentu (DTD), języku definicji schematu XML (XSD) i XSLT.

 <xref:System.Xml?displayProperty=fullName> Opisuje klasy i inne elementy, które składają się na <xref:System.Xml> przestrzeń nazw i zawiera linki do bardziej szczegółowych informacji na temat każdego elementu.

 <xref:System.Xml.Serialization?displayProperty=fullName> Opisuje klasy i inne elementy, które tworzą <xref:System.Xml.Serialization> przestrzeń nazw i zawiera linki do bardziej szczegółowych informacji na temat każdego elementu.

## <a name="related-sections"></a>Sekcje pokrewne
 [Document Object Model XML (dom)](https://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) Opisuje, w jaki sposób <xref:System.Xml.XmlDocument> i skojarzone z nimi klasy są zgodne ze specyfikacjami w przestrzeni nazw W3C Document Object Model (rdzeń) Level 1 i 2.

 [Odczytywanie kodu XML za pomocą elementu XmlReader](https://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) W tym artykule opisano, jak <xref:System.Xml.XmlReader> Usługa zapewnia dostęp tylko do odczytu do danych XML za pośrednictwem strumienia XML.

 [Pisanie XML przy użyciu XmlWriter](https://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) Opisuje sposób, w jaki <xref:System.Xml.XmlWriter> zapewnia niebuforowane, tylko do przodu, sposób generowania strumieni XML i pomaga tworzyć dokumenty XML zgodne ze standardem W3C.

 [Przekształcenia XSLT](https://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) Opisuje, w jaki sposób <xref:System.Xml.Xsl.XslCompiledTransform> Klasa implementuje zalecenia XSLT 1,0.

 [Przetwarzanie danych XML przy użyciu modelu danych XPath](https://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) Opisuje, w jaki sposób <xref:System.Xml.XPath.XPathNavigator> Klasa może przetwarzać dane XML przechowywane w <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> obiekcie lub. <xref:System.Xml.XPath.XPathNavigator>Klasa jest oparta na modelu danych XQuery 1,0 i XPath 2,0 i może służyć do nawigowania i edytowania danych XML.

 [Model obiektów schematu XML (SOM)](https://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) Opisuje klasy używane do tworzenia schematów XML i manipulowania nimi przez udostępnienie <xref:System.Xml.Schema.XmlSchema> klasy w celu załadowania i edytowania schematu.
