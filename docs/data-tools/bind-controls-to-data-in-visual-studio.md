---
title: Powiązywanie kontrolek z danymi
description: Powiązywanie kontrolek z danymi w programie Visual Studio. Twórz formanty powiązane z danymi, przeciągając elementy z okna źródła danych.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- displaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f92382721558d76cf9e84fa587b322d56af72247
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382172"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Wiązanie kontrolek z danymi w programie Visual Studio

Możesz wyświetlić dane dla użytkowników aplikacji przez powiązanie danych z kontrolkami. Można utworzyć te kontrolki powiązane z danymi, przeciągając elementy z okna **źródła danych** na powierzchnię projektu lub kontrolki na powierzchni w programie Visual Studio.

W tym temacie opisano źródła danych, których można użyć do tworzenia formantów powiązanych z danymi. Zawiera również opis niektórych ogólnych zadań związanych z wiązaniem danych. Aby uzyskać bardziej szczegółowe informacje na temat sposobu tworzenia formantów powiązanych z danymi, zobacz [bind Windows Forms Controls to Data in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) i [Powiązywanie formantów WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

## <a name="data-sources"></a>Źródła danych

W kontekście powiązania danych źródło danych reprezentuje dane w pamięci, które mogą być powiązane z interfejsem użytkownika. W praktyce, źródłem danych może być Klasa Entity Framework, zestaw danych, punkt końcowy usługi, który jest hermetyzowany w obiekcie serwera proxy platformy .NET, Klasa LINQ to SQL lub dowolny obiekt lub kolekcja platformy .NET. Niektóre źródła danych umożliwiają tworzenie formantów powiązanych z danymi przez przeciąganie elementów z okna **źródła danych** , a inne źródła danych. W poniższej tabeli przedstawiono, które źródła danych są obsługiwane.

| Źródło danych | Obsługa przeciągania i upuszczania w **Projektant formularzy systemu Windows** | Obsługa przeciągania i upuszczania w **PROJEKTANCIE WPF** | Obsługa przeciągania i upuszczania w **projektancie Silverlight** |
| - | - | - | - |
| Zestaw danych | Tak | Tak | Nie |
| Entity Data Model | Tak<sup>1</sup> | Tak | Tak |
| Klasy LINQ to SQL | Nr<sup>2</sup> | Nr<sup>2</sup> | Nr<sup>2</sup> |
| Usługi ( [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] w tym usługi WCF i usługi sieci Web) | Tak | Tak | Tak |
| Obiekt | Tak | Tak | Tak |
| SharePoint | Tak | Tak | Tak |

1. Wygeneruj model przy użyciu kreatora **Entity Data Model** , a następnie przeciągnij te obiekty do projektanta.

2. Klasy LINQ to SQL nie są wyświetlane w oknie **źródła danych** . Można jednak dodać nowe źródło danych obiektu, które jest oparte na LINQ to SQL klasach, a następnie przeciągnąć te obiekty do projektanta, aby utworzyć formanty powiązane z danymi. Aby uzyskać więcej informacji, zobacz [Przewodnik: tworzenie klas LINQ to SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="data-sources-window"></a>Data Sources — Okno

Źródła danych są dostępne dla projektu jako elementy w oknie **źródła danych** . To okno jest widoczne, gdy powierzchnia projektu formularza jest aktywnym oknem w projekcie lub można ją otworzyć (gdy projekt jest otwarty), wybierając opcję **Wyświetl**  >  **inne**  >  **źródła danych** systemu Windows. Możesz przeciągnąć elementy z tego okna, aby utworzyć formanty, które są powiązane z danymi źródłowymi, a także skonfigurować źródła danych, klikając je prawym przyciskiem myszy.

![Data Sources — Okno](../data-tools/media/raddata-data-sources-window.png)

Dla każdego typu danych, który pojawia się w oknie **źródła danych** , zostanie utworzona kontrolka domyślna po przeciągnięciu elementu do projektanta. Przed przeciągnięciem elementu z okna **źródła danych** można zmienić utworzony formant. Aby uzyskać więcej informacji, zobacz [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródła danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="tasks-involved-in-binding-controls-to-data"></a>Zadania związane z kontrolkami powiązań z danymi

Poniższa tabela zawiera listę najbardziej typowych zadań, które należy wykonać, aby powiązać kontrolki z danymi.

|Zadanie|Więcej informacji|
|----------| - |
|Otwórz okno **źródła danych** .|Otwórz powierzchnię projektu w edytorze i wybierz pozycję **Wyświetl**  >  **źródła danych**.|
|Dodaj źródło danych do projektu.|[Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)|
|Ustaw formant, który jest tworzony podczas przeciągania elementu z okna **źródła danych** do projektanta.|[Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|Zmodyfikuj listę kontrolek, które są skojarzone z elementami w oknie **źródła danych** .|[Dodawanie kontrolek niestandardowych do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Utwórz kontrolki powiązane z danymi.|[Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Wiązanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|
|Powiąż z obiektem lub kolekcją.|[Wiązanie obiektów w programie Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|
|Filtrowanie danych, które pojawiają się w interfejsie użytkownika.|[Filtrowanie i sortowanie danych w aplikacji Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Dostosuj podpisy dla kontrolek.|[Dostosowywanie sposobu tworzenia podpisów dla kontrolek powiązanych z danymi przez program Visual Studio](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Zobacz też

- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Windows Forms powiązania danych](/dotnet/framework/winforms/windows-forms-data-binding)
