---
title: Przeglądaj i wybierz okno dialogowe Typ platformy .NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 922be22619ee0bd16e2e5ac563999be7db81d45e
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851423"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Wyszukiwanie i wybieranie typu .NET, okno dialogowe
W oknie **Właściwości** , oknach dialogowych lub projektantach, takich jak projektant zmiennych, po wybraniu opcji **Przeglądaj w poszukiwaniu typów...** z listy typów danych jest okno dialogowe **Przeglądaj i wybierz typ platformy .NET** (w skrócie jako "przeglądarka typów"). W tym oknie dialogowym można wybrać typ z widoku drzewa zespołów i projektów.

 To okno dialogowe jest stosowane w wielu scenariuszach użytkowników, w tym:

- Podczas ustawiania typu zmiennej lub argumentu.

- Podczas wybierania typu dla działania rodzajowego.

- Podczas dodawania catch dla działania <xref:System.Activities.Statements.TryCatch>.

> [!NOTE]
> Przeglądarka typów może wyświetlać Visual Basic nieregularne typy tablic, ale nie wielowymiarowe typy tablicowe. Zobacz [tablice nieregularne](https://msdn.microsoft.com/library/hkhhsz9t(VS.90).aspx) i [tablice wielowymiarowe](https://msdn.microsoft.com/library/d2de1t93(VS.90).aspx) , aby uzyskać szczegółowe informacje.

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Wybieranie typu wartości lub odwołania z przeglądarki typów

#### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Aby wybrać typ wartości lub odwołania z przeglądarki typów

1. W polu **Nazwa typu** wpisz nazwę typu, który ma być używany.

2. Wykonaj jedną z następujących czynności:

    - Gdy nazwa typu, który ma być używany, pojawia się w drzewie w polu **Nazwa typu** , kliknij dwukrotnie typ, aby go zaznaczyć.

    - Wpisz wystarczającą liczbę znaków w polu **Nazwa typu** , aby jednoznacznie zidentyfikować typ, którego chcesz użyć, a następnie naciśnij klawisz ENTER, aby wybrać typ

#### <a name="to-select-a-generic-type-from-the-type-browser"></a>Aby wybrać typ ogólny z przeglądarki typów

1. W polu **Nazwa typu** wpisz nazwę typu, który ma być używany.

2. Gdy nazwa typu, który ma być używany, pojawia się w drzewie w polu **Nazwa typu** , kliknij typ, aby zaznaczyć, że pojawią się pola rozwijane.

     Wybierz typ, którego chcesz użyć, aby zamknąć ogólne z pól rozwijanych, a następnie kliknij przycisk **OK**.

## <a name="types-displayed-in-the-type-browser"></a>Typy wyświetlane w przeglądarce typów
 Typy wyświetlane w przeglądarce typów mogą się różnić w zależności od sposobu uruchomienia przeglądarki typów. Jeśli przeglądarka typów została uruchomiona z projektu przepływu pracy wewnątrz **VS2010**, domyślnie są wyświetlane wszystkie typy w przywoływanych zestawach i projektach, do których istnieją odwołania. Jeśli przeglądarka typów została uruchomiona spoza systemu projektu **VS2010** (na przykład w aplikacji do przeszukanego przepływu pracy lub w autonomicznym pliku przepływu pracy), domyślnie są wyświetlane typy ze wszystkich zestawów załadowanych w domenie aplikacji.

 Typy w przeglądarce typów mogą być filtrowane przez deweloperów projektanta działań. Dla danego działania może zostać wyświetlony tylko podzbiór typów. Na przykład w działaniu <xref:System.Activities.Statements.TryCatch> w przeglądarce typów są wyświetlane tylko typy pochodzące z <xref:System.Exception>.

## <a name="filtering-search-results-in-the-type-browser"></a>Filtrowanie wyników wyszukiwania w przeglądarce typów
 Lista typów w polu **Nazwa typu** jest krótsza podczas wpisywania więcej znaków w celu znalezienia dopasowania. Tylko typy, których w pełni kwalifikowana nazwa rozpoczyna się od ciągu, który wpisano lub typy, których krótka nazwa rozpoczyna się od ciągu, który wpisano, pojawia się na liście filtrowanej.

 Na przykład:

1. Wpisywanie **operacji** jest zgodne <xref:System.OperationCanceledException> ale nie <xref:System.InvalidOperationException>. Aby dopasować <xref:System.InvalidOperationException>, zacznij wpisywać system. I lub nieprawidłowy.

2. Wpisywanie **ogólnych** dopasowań <xref:System.GenericUriParser> ale nie typów w przestrzeni nazw <xref:System.Collections.Generic>. Aby wyszukać typy w przestrzeni nazw <xref:System.Collections.Generic>, wpisz w pełni kwalifikowaną nazwę przestrzeni nazw.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Wybieranie kontraktu usługi przy użyciu okna dialogowego przeglądarki typów
 W przypadku wybrania typu kontraktu usługi w przeglądarce typu wyświetlane są tylko typy, które mają atrybut <xref:System.ServiceModel.ServiceContractAttribute>.

## <a name="see-also"></a>Zobacz też
 [Używanie projektantów działań](../workflow-designer/using-the-activity-designers.md)
