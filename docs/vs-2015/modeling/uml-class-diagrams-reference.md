---
title: 'Diagramy klas UML: odwołanie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.common.generalization.properties
- vs.teamarch.logicalclassdiagram.toolbox
- vs.teamarch.UMLModelExplorer.association
- vs.teamarch.common.unspecifiedtype.properties
- vs.teamarch.logicalclassdiagram.diagram
- vs.teamarch.UMLModelExplorer.logicalclassdiagram
- vs.teamarch.UMLModelExplorer.generalization
- vs.teamarch.common.unspecifiedtype
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: b7c88be0-0d86-4d65-af74-f37e8812d20f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: da4e0e3bab904b660f3d843e105b7d256a63a1b5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297228"
---
# <a name="uml-class-diagrams-reference"></a>Diagramy klas UML: Odwołanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diagram klas UML zawiera opis obiektów i struktur informacji używanych przez aplikację zarówno wewnętrznie, jak i w komunikacji z użytkownikami. Opisuje informacje bez odwołania do żadnej konkretnej implementacji. Jej klasy i relacje można zaimplementować na wiele sposobów, takich jak tabele baz danych, węzły XML i kompozycje obiektów oprogramowania.

> [!NOTE]
> Ten temat dotyczy diagramów klas UML. Istnieje inny rodzaj diagramu klas, który jest używany do wizualizacji kodu programu. Aby uzyskać więcej informacji, zobacz [projektowanie i wyświetlanie klas i typów](https://go.microsoft.com/fwlink/?LinkId=142231).

 Aby utworzyć diagram klas UML, w menu **Architektura** wybierz **Nowy UML lub diagram warstwowy**. Aby uzyskać więcej informacji na temat rysowania diagramów klas UML, zobacz [diagramy klas UML: wytyczne](../modeling/uml-class-diagrams-guidelines.md). Aby uzyskać więcej informacji na temat tworzenia i rysowania diagramów modelowania, zobacz [Edycja modeli UML i diagramów](../modeling/edit-uml-models-and-diagrams.md).

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="reading-class-diagrams"></a>Odczytywanie diagramów klas
 W tabeli w tej sekcji opisano elementy, które można wyświetlić na diagramie klas UML. Aby uzyskać informacje o właściwościach tych elementów, zobacz następujące tematy:

- [Właściwości typów w diagramach klas UML](../modeling/properties-of-types-on-uml-class-diagrams.md)

- [Właściwości atrybutów w diagramach klas UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Właściwości operacji w diagramach klas UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [Właściwości skojarzeń w diagramach klas UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)

  ![Trzy klasy pokazujące relacje i właściwości](../modeling/media/uml-classovreading.png "UML_ClassOvReading")

| **Przekształca** |       **Element**        |                                                                                                                                                             **Opis**                                                                                                                                                              |
|-----------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1     |        **Określonej**         |                                                           Definicja obiektów, które współdzielą dane strukturalne lub behawioralne. Aby uzyskać więcej informacji, zobacz [Właściwości typów w diagramach klas UML](../modeling/properties-of-types-on-uml-class-diagrams.md).                                                            |
|     1     |        Klasyfikator        |                                                                                                             Nazwa ogólna dla klasy, interfejsu lub wyliczenia. Składniki, przypadki użycia i aktory są również klasyfikatorami.                                                                                                             |
|     2     | Zwiń/rozwiń kontrolkę |                                                                                         Jeśli nie widzisz szczegółów klasyfikatora, kliknij Ekspander w lewym górnym rogu klasyfikatora. Może być również konieczne kliknięcie [+] w każdym segmencie.                                                                                         |
|     3     |      **Atrybut**       |   Wpisana wartość dołączona do każdego wystąpienia klasyfikatora.<br /><br /> Aby dodać atrybut, kliknij sekcję **atrybuty** , a następnie naciśnij klawisz **Enter**. Wpisz podpis atrybutu. Aby uzyskać więcej informacji, zobacz [właściwości atrybutów w diagramach klas UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md).   |
|     4     |      **Operacje**       | Metoda lub funkcja, która może być wykonywana przez wystąpienia klasyfikatora. Aby dodać operację, kliknij sekcję **operacje** , a następnie naciśnij klawisz **Enter**. Wpisz podpis operacji. Aby uzyskać więcej informacji, zobacz [właściwości operacji na diagramach klas UML](../modeling/properties-of-operations-on-uml-class-diagrams.md). |
|     5     |     **Skojarzenie**      |                                                                  Relacja między elementami członkowskimi dwóch klasyfikatorów. Aby uzyskać więcej informacji, zobacz [Właściwości skojarzeń na diagramach klas UML](../modeling/properties-of-associations-on-uml-class-diagrams.md).                                                                   |
|    5a     |     **Agregacja**      |                                                                                                    Skojarzenie reprezentujące relację współużytkowanej własności. Właściwość **agregacji** roli właściciela jest ustawiona na wartość **Shared**.                                                                                                     |
|    5B     |     **Budowa**      |                                                                                                      Skojarzenie reprezentujące relację częściową. Właściwość **agregacji** roli właściciela jest ustawiona na wartość **złożona**.                                                                                                      |
|     6     |   **Nazwa skojarzenia**   |                                                                                                                                         Nazwa skojarzenia. Nazwa może pozostać pusta.                                                                                                                                          |
|     7     |      **Nazwa roli**       |                       Nazwa roli, czyli jeden koniec skojarzenia. Może służyć do odwoływania się do skojarzonego obiektu. Na poprzedniej ilustracji dla każdej `O`zamówienia, `O.ChosenMenu` jest jej menu skojarzone.<br /><br /> Każda rola ma własne właściwości, które są wyświetlane w obszarze właściwości skojarzenia.                       |
|     8     |     **Liczebność**     |                                         Wskazuje, ile obiektów w tym punkcie końcowym można połączyć z każdym obiektem. W tym przykładzie każde zamówienie musi być połączone z dokładnie jednym menu.<br /><br /> **\\** \* oznacza, że nie ma górnego limitu liczby linków, które mogą zostać wykonane.                                         |
|     9     |    **Generalizacja**    |  *Określony* klasyfikator dziedziczy część swojej definicji z klasyfikatora *ogólnego* . Klasyfikator ogólny znajduje się na końcu łącznika. Atrybuty, skojarzenia i operacje są dziedziczone przez określony klasyfikator.<br /><br /> Użyj narzędzia **dziedziczenie** , aby utworzyć generalizację między dwoma klasyfikatorami.   |

 ![Pakiet zawierający interfejs i Wyliczenie](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")

|Kształt|Element|Opis|
|-----------|-------------|-----------------|
|10|**Interfejsu**|Definicja części widocznego na zewnątrz zachowania obiektu. Aby uzyskać więcej informacji, zobacz [Właściwości typów w diagramach klas UML](../modeling/properties-of-types-on-uml-class-diagrams.md).|
|11|**Licznik**|Klasyfikator, który składa się z zestawu wartości literału.|
|12|**Pakiet**|Grupa klasyfikatorów, skojarzeń, akcji, linii życia, składników i pakietów. Diagram klasy logicznej pokazuje, że klasyfikatory i pakiety elementów członkowskich są zawarte w pakiecie.<br /><br /> Nazwy są objęte zakresem pakietów, dzięki czemu **Class1** w **package1** różni się od **Class1** poza tym pakietem. Nazwa pakietu jest wyświetlana w ramach właściwości **nazwy kwalifikowanej** jej zawartości.<br /><br /> Możesz ustawić właściwość **połączony pakiet** dowolnego diagramu UML, aby odwołać się do pakietu. Wszystkie elementy, które tworzysz na tym diagramie, staną się częścią pakietu. Zostaną one wyświetlone w obszarze pakiet w **Eksploratorze modelu UML**.|
|13|**Importujuj**|Relacja między pakietami, wskazującą, że jeden pakiet zawiera wszystkie definicje innych.|
|14|**Zależności**|Definicja lub implementacja klasyfikatora zależnego może ulec zmianie, jeśli klasyfikator na końcu końca strzałki zostanie zmieniony.|

 ![Realizacja pokazana z conector i lizak](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")

|Kształt|**Element**|Opis|
|-----------|-----------------|-----------------|
|15|**Realizacja**|Klasa implementuje operacje i atrybuty zdefiniowane przez interfejs.<br /><br /> Użyj narzędzia **dziedziczenie** , aby utworzyć realizację między klasą i interfejsem.|
|16|**Realizacja**|Alternatywna Prezentacja tej samej relacji. Etykieta na symbolu lizaka identyfikuje interfejs.<br /><br /> Aby utworzyć tę prezentację, wybierz istniejącą relację realizacji. Tag akcji pojawia się blisko skojarzenia. Kliknij tag Akcja, a następnie kliknij pozycję **Pokaż jako lizak**.|

## <a name="see-also"></a>Zobacz też
 [Edytuj modele UML i diagramy](../modeling/edit-uml-models-and-diagrams.md) [UML klas diagramy: wytyczne](../modeling/uml-class-diagrams-guidelines.md) [Właściwości typów na diagramach](../modeling/properties-of-types-on-uml-class-diagrams.md) klas UML właściwości [atrybutów w](../modeling/properties-of-attributes-on-uml-class-diagrams.md) diagramach klas UML właściwości [operacji na](../modeling/properties-of-operations-on-uml-class-diagrams.md) diagramach klas UML właściwości [skojarzenia na diagramach klasy](../modeling/properties-of-associations-on-uml-class-diagrams.md) UML
