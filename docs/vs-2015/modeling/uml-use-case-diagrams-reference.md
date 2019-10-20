---
title: 'Diagramy przypadków użycia UML: odwołanie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.usecasediagram.toolbox
- vs.teamarch.usecasediagram.diagram
- vs.teamarch.UMLModelExplorer.usecasediagram
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: aa15772b-eb67-4366-b145-b559112817df
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cbea61c2a26b1dc81487365ef8fc3f320ac95943
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657303"
---
# <a name="uml-use-case-diagrams-reference"></a>Diagramy przypadków użycia UML: Odwołanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio *Diagram przypadków użycia* podsumowuje, kto używa aplikacji lub systemu, i co można z nimi zrobić. Aby utworzyć diagram przypadków użycia UML, w menu **Architektura** kliknij **Nowy UML lub diagram warstwowy**.

 Diagram przypadków użycia działa jako fokus dla opisu wymagań użytkownika. Opisuje relacje między wymaganiami, użytkownikami i składnikami głównymi. Nie opisuje wymagania szczegółowo. można je opisać w oddzielnych diagramach lub w dokumentach, które mogą być połączone z każdym przypadkiem użycia. Aby uzyskać informacje na temat sposobu, w jaki diagramy przypadków użycia mogą pomóc zrozumieć, omówić i komunikować się z potrzebami użytkowników, zobacz [wymagania dotyczące modelu użytkownika](../modeling/model-user-requirements.md).

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> W tym temacie opisano elementy, które są dostępne na diagramach przypadków użycia. Aby uzyskać więcej informacji na temat rysowania diagramów przypadków użycia, zobacz [diagramy przypadków użycia UML: wytyczne](../modeling/uml-use-case-diagrams-guidelines.md). Aby uzyskać więcej informacji na temat tworzenia i rysowania diagramów modelowania, zobacz [Edycja modeli UML i diagramów](../modeling/edit-uml-models-and-diagrams.md).

## <a name="reading-use-case-diagrams"></a>Odczytywanie diagramów przypadków użycia
 W tabelach w poniższych sekcjach opisano elementy, które są dostępne na diagramie przypadków użycia, wraz z ich głównymi właściwościami. Aby uzyskać pełną listę właściwości, zobacz [właściwości elementów na diagramach przypadków użycia UML](../modeling/properties-of-elements-on-uml-use-case-diagrams.md).

### <a name="actors-use-cases-and-subsystems"></a>Aktory, przypadki użycia i podsystemy
 ![Elementy na diagramie przypadków użycia](../modeling/media/uml-ucovactor.png "UML_UCOvActor")

|**Przekształca**|**Element**|**Opis i główne właściwości**|
|---------------|-----------------|-----------------------------------------|
|1|**Zewnętrzny**|Reprezentuje użytkownika, organizację lub system zewnętrzny, który współdziała z aplikacją lub systemem. Aktor jest rodzajem typu.<br /><br /> **ścieżka obrazu** -   -ścieżka pliku obrazu, który powinien zostać użyty zamiast domyślnej ikony aktora. Ikona powinna być plikiem zasobów w projekcie programu Visual Studio.|
|2|**Przypadek użycia**|Reprezentuje akcje wykonywane przez co najmniej jedną aktora w celu osiągnięcia określonego celu. Przypadek użycia jest rodzajem typu.<br /><br /> **tematy** -    — podsystem, w którym występuje przypadek użycia.|
|3|**Skojarzenie**|Wskazuje, że aktor uczestniczy w przypadku użycia.|
|4|**Podsystem lub składnik**|System lub aplikacja, nad którą pracujesz, lub jej część. Mogą to być elementy z dużej sieci do pojedynczej klasy w aplikacji.<br /><br /> Przypadki użycia, które system lub składnik obsługuje w obrębie swojego prostokąta. Może być przydatne, aby pokazać niektóre przypadki użycia poza prostokątem, aby wyjaśnić zakres Twojego systemu.<br /><br /> Podsystem w diagramie przypadku użycia ma zasadniczo ten sam typ co składnik na diagramie składników.<br /><br /> -   **jest pośrednio skonkretyzowany** — w przypadku wartości false, wykonywany system ma jeden lub więcej obiektów, które bezpośrednio odpowiadają temu podsystemowi. W przypadku wartości true podsystem jest konstrukcja w projekcie, która jest wyświetlana w systemie wykonywanym tylko przez utworzenie wystąpienia jego części składowych.|

### <a name="structuring-use-cases"></a>Tworzenie struktury przypadków użycia
 ![Przypadki użycia z opcją include, rozszerzając i generalize](../modeling/media/uml-ucovstructure.png "UML_UCOvStructure")

|Kształt|**Element**|Opis|
|-----------|-----------------|-----------------|
|5|**Być**|W tym wywołania przypadku użycia lub wywołuje dołączone. Dołączenie służy do pokazania, jak przypadek użycia jest podzielony na mniejsze kroki. Uwzględniony przypadek użycia znajduje się na końcu grotu strzałki.<br /><br /> Należy zauważyć, że diagram nie pokazuje kolejności kroków. Aby opisać te szczegóły, można użyć diagramu aktywności, diagramu sekwencji lub innego dokumentu.|
|6|**Sunąć**|Rozszerzenie przypadku użycia dodaje cele i kroki do rozszerzonego przypadku użycia. Rozszerzenia działają tylko w określonych warunkach. Rozszerzony przypadek użycia znajduje się na końcu strzałki.<br /><br /> Należy zauważyć, że na diagramie nie są widoczne dokładne sytuacje, w których ma zastosowanie rozszerzenie: można je zarejestrować w komentarzu lub w innym dokumencie.|
|7|**Dziedziczenie**|Odnosi się do wyspecjalizowanego i uogólnionego elementu. Uogólniony element znajduje się na końcu strzałki.<br /><br /> Wyspecjalizowany przypadek użycia dziedziczy cele i uczestników jego generalizacji oraz może dodać bardziej szczegółowe cele i kroki w celu ich osiągnięcia.<br /><br /> Wyspecjalizowany aktor dziedziczy przypadki użycia, atrybuty i skojarzenia jego generalizacji i może dodać więcej.|
|8|**Zależności**|Wskazuje, że projekt źródła zależy od projektu obiektu docelowego.|
|9|**Komentarz**|Służy do dodawania notatek ogólnych do diagramu.|
|10|**Artefaktu**|Artefakt zawiera link do innego diagramu lub dokumentu. Można go utworzyć, przeciągając plik z Eksplorator rozwiązań. Może być połączony z zależnością do dowolnego innego elementu na diagramie. Artefakt jest zazwyczaj używany do łączenia przypadku użycia z diagramem sekwencji, stroną programu OneNote, dokumentem programu Word lub prezentacją programu PowerPoint, która szczegółowo opisuje. Dokument może być elementem w rozwiązaniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub dokumentem w lokalizacji udostępnionej, takiej jak witryna programu SharePoint.<br /><br /> -   **Hyperlink**. Adres URL lub ścieżka pliku diagramu lub dokumentu.<br /><br /> Kliknij dwukrotnie artefakt, aby otworzyć plik lub stronę sieci Web, do której się łączą.|
|11 (niepokazywany)|**Pakiety**|Przypadki użycia, aktory i podsystemy mogą być zawarte w pakietach. Kształty pakietów nie są wyświetlane na diagramie, ale można ustawić właściwość **LinkedPackage** diagramu. Elementy, które następnie tworzysz na diagramie, są umieszczane w pakiecie. Aby uzyskać więcej informacji, zobacz [Definiowanie pakietów i przestrzeni nazw](../modeling/define-packages-and-namespaces.md).|

## <a name="see-also"></a>Zobacz też
 [Diagramy przypadków użycia UML: wytyczne](../modeling/uml-use-case-diagrams-guidelines.md) [Edycja modeli UML i diagramów](../modeling/edit-uml-models-and-diagrams.md) [diagramy sekwencji UML: referencyjne](../modeling/uml-sequence-diagrams-reference.md) [diagramy klas UML:](../modeling/uml-class-diagrams-reference.md) referencyjne diagramy [składników UML](../modeling/uml-component-diagrams-reference.md) : referencyjne [diagramy składników UML: odwołanie](../modeling/uml-component-diagrams-reference.md)
