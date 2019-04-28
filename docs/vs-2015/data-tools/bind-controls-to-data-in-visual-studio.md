---
title: Powiązywanie kontrolek z danymi
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- displaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1d0e34075fbadcc998dba09d1b7c13a5ffacc606
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62556925"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Powiązywanie kontrolek z danymi w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można wyświetlić dane użytkownikom aplikacji przez powiązanie danych kontrolki. Można utworzyć te formanty powiązane z danymi przez przeciąganie elementów z **źródeł danych** okna na powierzchnię projektową lub formantów na powierzchni w programie Visual Studio.

 W tym temacie opisano źródła danych, których można użyć w celu tworzenia formantów powiązanych z danymi. Opisuje także niektóre ogólne zadania podczas wiązania z danymi. Aby uzyskać bardziej szczegółowe informacje o sposobie tworzenia formantów powiązanych z danymi, zobacz [formanty powiązania formularzy Windows do danych w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) i [WPF powiązać kontrolki z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="data-sources"></a>Źródła danych
 W kontekście powiązania danych źródło danych reprezentuje dane w pamięci, która może być powiązana z poziomu interfejsu użytkownika. W praktyce źródła danych może być klasą Entity Framework, zestaw danych, punktu końcowego usługi, które są hermetyzowane w obiekcie proxy .NET, LINQ to SQL klas, lub dowolnego obiektu .NET lub kolekcji. Niektóre źródła danych umożliwiają tworzenie formantów powiązanych z danymi przez przeciąganie elementów z **źródeł danych** okna, podczas gdy inne źródła danych nie obsługują. W poniższej tabeli przedstawiono, jakie źródła danych są obsługiwane.

|Źródło danych|Obsługa przeciągania i upuszczania w **Windows Forms Designer**|Obsługa przeciągania i upuszczania w **projektanta WPF**|Obsługa przeciągania i upuszczania w **projektanta Silverlight**|
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|
|Zestaw danych|Tak|Yes|Nie|
|Entity Data Model|Tak<sup>1</sup>|Tak|Tak|
|Klasy LINQ do SQL|Nie<sup>2</sup>|Nie<sup>2</sup>|Nie<sup>2</sup>|
|Usługi (łącznie z [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], WCF services oraz usług sieci web)|Tak|Yes|Tak|
|Obiekt|Tak|Yes|Tak|
|Program SharePoint|Tak|Yes|Tak|

 1. Generowanie modelu przy użyciu **modelu Entity Data Model** kreatora, a następnie przeciągnij te obiekty do projektanta.

 2. Klasy LINQ do SQL nie są wyświetlane w **źródeł danych** okna. Można jednak dodać nowe źródło danych obiektu opartego na LINQ do klas SQL, a następnie przeciągnąć te obiekty do projektanta w celu tworzenia formantów powiązanych z danymi. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie składnika LINQ to SQL klas (Projektant O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).

## <a name="data-sources-window"></a>Data Sources — Okno
 Źródła danych są dostępne dla projektu jako elementy **źródeł danych** okna. To okno jest widoczne, lub jest dostępny z **widoku** menu, gdy powierzchnię projektową formularza jest aktywnym oknem w projekcie. Można przeciągnąć elementy z tego okna, aby utworzyć formanty powiązane z danymi źródłowymi, a źródłami danych można również skonfigurować, klikając prawym przyciskiem myszy.

 ![Okno źródeł danych](../data-tools/media/raddata-data-sources-window.png "raddata okna źródeł danych")

 Dla każdego typu danych, która pojawia się w **źródeł danych** okna, tworzony jest domyślny formant podczas przeciągania elementu do projektanta. Przed przeciągnięciem elementu z **źródeł danych** oknie można zmienić formant, który zostanie utworzony. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="tasks-involved-in-binding-controls-to-data"></a>Zadania związane z powiązaniem formantów z danymi
 W poniższej tabeli wymieniono niektóre z najczęściej wykonywane czynności należy wykonać, aby powiązać formanty z danymi.

|Zadanie|Więcej informacji|
|----------|----------------------|
|Otwórz **źródeł danych** okna.|Otwórz powierzchni projektowej w edytorze i wybierz polecenie **widoku** > **źródeł danych**.|
|Dodaj źródło danych do projektu.|[Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)|
|Ustaw formant, który jest tworzony podczas przeciągania elementu z **źródeł danych** okna projektanta.|[Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|Zmodyfikuj listę formantów, które są skojarzone z elementami w **źródeł danych** okna.|[Dodawanie kontrolek niestandardowych do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Tworzenie formantów powiązanych z danymi.|[Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Wiązanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)|
|Powiąż z obiektem lub kolekcji.|[Wiązanie obiektów w programie Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|
|Filtrować dane wyświetlane w interfejsie użytkownika.|[Filtrowanie i sortowanie danych w aplikacji Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Dostosuj podpisy dla formantów.|[Dostosowywanie sposobu tworzenia podpisów dla kontrolek powiązanych z danymi przez program Visual Studio](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Zobacz też
 [Narzędzia Visual Studio data tools dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) [powiązanie danych formularzy Windows](http://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa)
