---
title: Eksplorator schematu XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5e9f61c56dd7ff2a9c6c19afc20ed279a7fdf855
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669373"
---
# <a name="xml-schema-explorer"></a>Eksplorator schematu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eksplorator schematu XML jest zintegrowany z Microsoft Visual Studio i edytorem XML umożliwiającym współdziałanie z schematami języka definicji schematu XML (XSD). Po otwarciu pliku schematu XML węzeł **zestawu schematów** pojawia się w EKSPLORATORZE schematu XML. Wszystkie dołączone, zaimportowane lub ponownie zdefiniowane schematy dla pliku docelowego, a także wszystkie pliki, do których odwołuje się instrukcja `include` lub `import`, również są wyświetlane w Eksploratorze schematu XML.

 Eksplorator schematu XML umożliwia wykonywanie następujących czynności:

- Zapoznaj się z krótkim omówieniem zestawu schematów.

- Przeglądaj drzewo i przejdź do niego.

- Wykonaj słowa kluczowe i wyszukiwania specyficzne dla schematu. Aby uzyskać więcej informacji, zobacz [Wyszukiwanie zestawu schematów](../xml-tools/searching-the-schema-set.md).

- Dodaj wyniki wyszukiwania do widoku wykresu lub widoku modle zawartości

- Posortuj drzewo według kolejności dokumentu, typu lub nazwy. Aby uzyskać więcej informacji, zobacz [sortowanie, filtrowanie i grupowanie](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).

- Otwórz Edytor XML i przejdź do lokalizacji kodu w pliku XSD. Aby uzyskać więcej informacji, zobacz [integracja z edytorem XML](../xml-tools/integration-with-xml-editor.md).

- Generuj przykładowy kod XML dla elementów globalnych.

  Eksplorator schematu XML udostępnia widok hierarchiczna schematu zestawu za pomocą widoku drzewa. Eksplorator schematu XML zawiera również wyszukiwanie, filtrowanie, nawigację i sortowanie. Aby uzyskać dostęp do Eksploratora schematu XML, wykonaj jedną z następujących czynności:

- Jeśli jesteś w [widoku Start](../xml-tools/start-view.md), kliknij link **Eksplorator schematu XML** .

- Jeśli używasz [widoku wykresu](../xml-tools/graph-view.md) lub [widoku modelu zawartości](../xml-tools/content-model-view.md) i węzły w obszarze roboczym, użyj menu kontekstowego, aby wybrać Eksplorator schematu XML.

- Możesz również wybrać schemat XML Explorerfrom menu **Widok** .

- Możesz uzyskać dostęp do schematu XML Explorerfrom plik. vb, który ma Visual Basic literał XML skojarzony z plikiem XSD. Aby wyświetlić zestaw schematu w Eksploratorze schematu XML, kliknij prawym przyciskiem myszy węzeł XML w literale XML lub Importuj przestrzeń nazw XML i wybierz polecenie **Pokaż w Eksploratorze schematu** . Aby uzyskać więcej informacji, zobacz [integracja literałów XML z Eksploratorem schematu XML](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).

## <a name="tree-view"></a>Widok drzewa
 W Eksploratorze schematu XML są wyświetlane wstępnie skompilowane informacje o zestawie schematów w strukturze drzewa. Struktura drzewa jest zorganizowana w następujący sposób:

- Najwyższego poziomu jest węzłem zestawu schematów.

- Drugi poziom zawiera przestrzenie nazw.

- Trzeci poziom zawiera pliki.

- Czwarty poziom zawiera węzły globalne. Może to obejmować elementy, grupy, typy złożone, typy proste, atrybuty, grupy atrybutów i instrukcje `include`, `import` i `redefine`.

  Oto przykład struktury drzewa:

  ![Eksplorator schematu XML](../xml-tools/media/xmlschemaexplorer.gif "XMLSchemaExplorer")

## <a name="selection-and-activation"></a>Wybór i aktywacja
 Aby wyróżnić i wybrać węzeł, kliknij jeden raz w Eksploratorze schematu.

 Aby uaktywnić węzeł, kliknij go dwukrotnie lub naciśnij klawisz **Enter** po zaznaczeniu węzła.

- Aktywowanie węzła otwiera plik, w którym jest zdefiniowany ten węzeł (Jeśli plik nie jest jeszcze otwarty) i wybiera węzeł w pliku.

- Aktywowanie węzła pliku otwiera wybrany plik (jeśli nie jest jeszcze otwarty) i podświetla węzeł `<schema>`.

- Aktywowanie węzła SchemaSet lub obszaru nazw nie robi nic.

## <a name="draging-and-dropping-nodes"></a>Przeciąganie i upuszczanie węzłów
 Można przeciągać i upuszczać węzły globalne, węzły plików i węzły przestrzeni nazw do widoku projektanta XSD. Jeśli bieżący widok jest [widokiem Start](../xml-tools/start-view.md), przeciągnięcie węzła do widoku spowoduje otwarcie [widoku wykresu](../xml-tools/graph-view.md). Jeśli bieżący widok jest [widokiem modelu zawartości](../xml-tools/content-model-view.md) lub widokiem wykresu, widok nie zmieni się po porzucenia na nim węzła.

 Porzucenie plików w widoku spowoduje dodanie wszystkich węzłów globalnych w pliku do [obszaru roboczego projektanta XSD](../xml-tools/xml-schema-designer-workspace.md). Usunięcie przestrzeni nazw w widoku spowoduje dodanie wszystkich węzłów globalnych w przestrzeni nazw do obszaru roboczego. Obszar roboczy jest współużytkowany między wszystkimi widokami.

 Nie można przeciągać i upuszczać węzłów lokalnych ani importów.

## <a name="in-this-section"></a>W tej sekcji

- [Wyszukiwanie zestawu schematów](../xml-tools/searching-the-schema-set.md)

- [Sortowanie, filtrowanie i grupowanie](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)

- [Menu kontekstowe](../xml-tools/context-menus-xml-schema-explorer.md)

- [Integracja literałów XML z eksploratorem schematu XML](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Dodawanie węzłów do obszaru roboczego z eksploratora schematu XML](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)
