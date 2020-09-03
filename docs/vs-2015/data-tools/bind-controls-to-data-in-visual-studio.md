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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 31e2086126e9a17554c80b53858205e83fd504fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673035"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Wiązanie kontrolek z danymi w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz wyświetlić dane dla użytkowników aplikacji przez powiązanie danych z kontrolkami. Można utworzyć te kontrolki powiązane z danymi, przeciągając elementy z okna **źródła danych** na powierzchnię projektu lub kontrolki na powierzchni w programie Visual Studio.

 W tym temacie opisano źródła danych, których można użyć do tworzenia formantów powiązanych z danymi. Zawiera również opis niektórych ogólnych zadań związanych z wiązaniem danych. Aby uzyskać bardziej szczegółowe informacje na temat sposobu tworzenia formantów powiązanych z danymi, zobacz [bind Windows Forms Controls to Data in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) i [Powiązywanie formantów WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="data-sources"></a>Źródła danych
 W kontekście powiązania danych źródło danych reprezentuje dane w pamięci, które mogą być powiązane z interfejsem użytkownika. W praktyce, źródłem danych może być Klasa Entity Framework, zestaw danych, punkt końcowy usługi, który jest hermetyzowany w obiekcie serwera proxy platformy .NET, Klasa LINQ to SQL lub dowolny obiekt lub kolekcja platformy .NET. Niektóre źródła danych umożliwiają tworzenie formantów powiązanych z danymi przez przeciąganie elementów z okna **źródła danych** , a inne źródła danych. W poniższej tabeli przedstawiono, które źródła danych są obsługiwane.

|Źródło danych|Obsługa przeciągania i upuszczania w **Projektant formularzy systemu Windows**|Obsługa przeciągania i upuszczania w **PROJEKTANCIE WPF**|Obsługa przeciągania i upuszczania w **projektancie Silverlight**|
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|
|Zestaw danych|Tak|Tak|Nie|
|Entity Data Model|Tak<sup>1</sup>|Tak|Tak|
|Klasy LINQ to SQL|Nr<sup>2</sup>|Nr<sup>2</sup>|Nr<sup>2</sup>|
|Usługi ( [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] w tym usługi WCF i usługi sieci Web)|Tak|Tak|Tak|
|Obiekt|Tak|Tak|Tak|
|SharePoint|Tak|Tak|Tak|

 1. Wygeneruj model przy użyciu kreatora **Entity Data Model** , a następnie przeciągnij te obiekty do projektanta.

 2. Klasy LINQ to SQL nie są wyświetlane w oknie **źródła danych** . Można jednak dodać nowe źródło danych obiektu, które jest oparte na LINQ to SQL klasach, a następnie przeciągnąć te obiekty do projektanta, aby utworzyć formanty powiązane z danymi. Aby uzyskać więcej informacji, zobacz [Przewodnik: tworzenie klas LINQ to SQL (Projektant O-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).

## <a name="data-sources-window"></a>Data Sources — Okno
 Źródła danych są dostępne dla projektu jako elementy w oknie **źródła danych** . To okno jest widoczne lub dostępne z menu **Widok** , gdy powierzchnia projektu formularza jest aktywnym oknem w projekcie. Możesz przeciągnąć elementy z tego okna, aby utworzyć formanty, które są powiązane z danymi źródłowymi, a także skonfigurować źródła danych, klikając je prawym przyciskiem myszy.

 ![Data Sources — Okno](../data-tools/media/raddata-data-sources-window.png "okno źródeł danych raddata")

 Dla każdego typu danych, który pojawia się w oknie **źródła danych** , zostanie utworzona kontrolka domyślna po przeciągnięciu elementu do projektanta. Przed przeciągnięciem elementu z okna **źródła danych** można zmienić formant, który zostanie utworzony. Aby uzyskać więcej informacji, zobacz [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródła danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="tasks-involved-in-binding-controls-to-data"></a>Zadania związane z kontrolkami powiązań z danymi
 Poniższa tabela zawiera listę najbardziej typowych zadań, które należy wykonać, aby powiązać kontrolki z danymi.

|Zadanie|Więcej informacji|
|----------|----------------------|
|Otwórz okno **źródła danych** .|Otwórz powierzchnię projektu w edytorze i wybierz pozycję **Wyświetl**  >  **źródła danych**.|
|Dodaj źródło danych do projektu.|[Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)|
|Ustaw formant, który jest tworzony podczas przeciągania elementu z okna **źródła danych** do projektanta.|[Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|Zmodyfikuj listę kontrolek, które są skojarzone z elementami w oknie **źródła danych** .|[Dodawanie kontrolek niestandardowych do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Utwórz kontrolki powiązane z danymi.|[Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Wiązanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)|
|Powiąż z obiektem lub kolekcją.|[Wiązanie obiektów w programie Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|
|Filtrowanie danych, które pojawiają się w interfejsie użytkownika.|[Filtrowanie i sortowanie danych w aplikacji Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Dostosuj podpisy dla kontrolek.|[Dostosowywanie sposobu tworzenia podpisów dla kontrolek powiązanych z danymi przez program Visual Studio](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Zobacz też
 [Powiązanie danych](https://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa) [programu Visual Studio Data tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) Windows Forms
