---
title: XML Schema Explorer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 575be3277dd7d876b19b9c557643cb05831255a5
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670436"
---
# <a name="xml-schema-explorer"></a>Eksplorator schematu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eksplorator schematu XML jest zintegrowany z Microsoft Visual Studio i edytorem XML, aby umożliwić Praca ze schematami języka (XSD) definicji schematu XML. Po otwarciu pliku schematu XML **schemat ustawiony** węzła pojawia się w Eksplorator schematu XML. Wszystkich schematów uwzględniony, zaimportowanych lub zmieniony dla pliku docelowego, a także wszystkie pliki, które są wywoływane za pośrednictwem `include` lub `import` instrukcji, również są wyświetlane dla Eksploratora schematu XML.  
  
 Eksplorator schematu XML można wykonać następujące czynności:  
  
- Uzyskaj krótkie omówienie zestawu schematu.  
  
- Przeglądaj i przejdź drzewa.  
  
- Wykonaj — słowo kluczowe i wyszukiwanie specyficzne dla schematu. Aby uzyskać więcej informacji, zobacz [wyszukiwania zestawu schematu](../xml-tools/searching-the-schema-set.md).  
  
- Dodaj wyniki wyszukiwania do widoku wykresu i widoku Modle zawartości  
  
- Sortuj drzewa w kolejności dokumentu, typ lub nazwa. Aby uzyskać więcej informacji, zobacz [sortowanie, filtrowanie i grupowanie](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).  
  
- Otwórz Edytor XML, a następnie przejdź do lokalizacji kodu w pliku XSD. Aby uzyskać więcej informacji, zobacz [integracja za pomocą edytora XML](../xml-tools/integration-with-xml-editor.md).  
  
- Wygeneruj przykładowy kod XML dla elementów globalnej.  
  
  Eksplorator schematu XML zawiera widok hierarchiczna schematu ustawiana za pośrednictwem widoku drzewa. Eksplorator schematu XML także wyszukiwanie, filtrowanie, nawigacji i sortowania. Aby otworzyć Eksploratora schematu XML, wykonaj jedną z następujących czynności:  
  
- Jeśli użytkownik pracuje na [widoku Start](../xml-tools/start-view.md), kliknij przycisk **Eksploratora schematu XML** łącza.  
  
- Jeśli użytkownik pracuje na [widoku wykresu](../xml-tools/graph-view.md) lub [widoku modelu zawartości](../xml-tools/content-model-view.md) i mieć węzły w obszarze roboczym, użyj menu kontekstowego, aby wybrać Eksploratora schematu XML.  
  
- Możesz również wybrać Explorerfrom schematu XML **widoku** menu.  
  
- Możesz uzyskać dostęp Explorerfrom schemat XML pliku .vb, który ma Visual Basic literał XML skojarzony z pliku XSD. Aby wyświetlić schemat w Eksplorator schematu XML, kliknij prawym przyciskiem myszy węzeł XML w literał XML lub importu przestrzeni nazw XML i wybierz **Pokaż w Eksploratorze schematu** polecenia. Aby uzyskać więcej informacji, zobacz [integracja literałów XML z Eksploratorem schematu XML](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).  
  
## <a name="tree-view"></a>Widok drzewa  
 Eksplorator schematu XML Wyświetla informacji o zestawie wstępnie skompilowanym schematu w strukturze drzewa. Struktura drzewa jest zorganizowana w następujący sposób:  
  
- Na najwyższym poziomie schematu ustawiono węzła.  
  
- Drugi poziom zawiera przestrzenie nazw.  
  
- Trzeci poziom zawiera pliki.  
  
- Czwarty poziom zawiera globalny węzłów. Może to obejmować elementy, grupy, typów złożonych typów prostych, atrybuty, grup atrybutów i `include`, `import`, i `redefine` instrukcji.  
  
  Oto przykład struktury drzewa:  
  
  ![XML Schema Explorer](../xml-tools/media/xmlschemaexplorer.gif "XMLSchemaExplorer")  
  
## <a name="selection-and-activation"></a>Wybór i aktywacja  
 Aby zaznaczyć, a następnie wybierz węzeł, kliknij jeden raz w Eksploratorze schematu.  
  
 Aby aktywować węzła, kliknij ją dwukrotnie lub naciśnij **Enter** po wybraniu węzła.  
  
-   Aktywowanie węzła spowoduje otwarcie pliku, w którym ten węzeł jest zdefiniowany (Jeśli plik nie jest już otwarty) i wybiera węzeł w pliku.  
  
-   Aktywowanie węzeł plików Otwiera wybrany plik (Jeśli nie jest już otwarty) i wyróżnienie `<schema>` węzła.  
  
-   Aktywowanie SchemaSet lub węzła obszaru nazw nic nie robi.  
  
## <a name="draging-and-dropping-nodes"></a>Draging i upuszczając węzłów  
 Możesz przeciągać i upuszczać globalnego węzłów, węzły plików i węzły przestrzeni nazw na widok Projektant XSD. Jeśli bieżący widok jest [widoku Start](../xml-tools/start-view.md), przeciągając węzeł do widoku spowoduje otwarcie [widoku wykresu](../xml-tools/graph-view.md). Jeśli bieżący widok jest [widoku modelu zawartości](../xml-tools/content-model-view.md) lub widoku wykresu widoku nie ulegnie zmianie, gdy upuścisz suszarkę węzła na niego.  
  
 Upuszczanie plików w widoku doda wszystkie węzły globalne w pliku [obszaru roboczego Projektant XSD](../xml-tools/xml-schema-designer-workspace.md). Usunięcie przestrzeni nazw w widoku doda wszystkie węzły globalne w przestrzeni nazw do obszaru roboczego. Obszar roboczy jest współużytkowana przez wszystkie widoki.  
  
 Nie można przeciągania i upuszczania węzłach lokalnym lub importów.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
-   [Wyszukiwanie zestawu schematów](../xml-tools/searching-the-schema-set.md)  
  
-   [Sortowanie, filtrowanie i grupowanie](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)  
  
-   [Menu kontekstowe](../xml-tools/context-menus-xml-schema-explorer.md)  
  
-   [Integracja literałów XML z eksploratorem schematu XML](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Dodawanie węzłów do obszaru roboczego z eksploratora schematu XML](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)
