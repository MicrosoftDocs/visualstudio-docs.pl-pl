---
title: Projektant przepływu pracy — przeglądanie i wybieranie typu .NET okno dialogowe
description: Dowiedz się, jak można użyć okna dialogowego Przeglądaj i wybierz typ platformy .NET, aby wybrać typ z widoku drzewa zespołów i projektów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7e887cf339647df9bca7fdc3d07a45dd44901c42
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438181"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Wyszukiwanie i wybieranie typu .NET, okno dialogowe

W oknie **Właściwości** , oknach dialogowych lub projektantach, takich jak projektant zmiennych, w przypadku wybrania opcji **Przeglądaj w poszukiwaniu typów** z listy typów danych jest okno dialogowe **Przeglądaj i wybierz typ platformy .NET** (nazywane "przeglądarką typu"). W tym oknie dialogowym można wybrać typ z widoku drzewa zespołów i projektów.

To okno dialogowe jest stosowane w wielu scenariuszach użytkowników, w tym:

- Podczas ustawiania typu zmiennej lub argumentu.

- Podczas wybierania typu dla działania rodzajowego.

- Podczas dodawania catch do <xref:System.Activities.Statements.TryCatch> działania.

> [!NOTE]
> Przeglądarka typów może wyświetlać Visual Basic nieregularne typy tablic, ale nie wielowymiarowe typy tablicowe. Zobacz [tablice nieregularne](/previous-versions/visualstudio/visual-studio-2008/hkhhsz9t(v=vs.90)) i [tablice wielowymiarowe](/previous-versions/visualstudio/visual-studio-2008/d2de1t93(v=vs.90)) , aby uzyskać szczegółowe informacje.

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Wybieranie typu wartości lub odwołania z przeglądarki typów

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Aby wybrać typ wartości lub odwołania z przeglądarki typów

1. W polu **Nazwa typu** wpisz nazwę typu, który ma być używany.

2. Wykonaj jedną z następujących czynności:

    - Gdy nazwa typu, który ma być używany, pojawia się w drzewie w polu **Nazwa typu** , kliknij dwukrotnie typ, aby go zaznaczyć.

    - Wpisz wystarczającą liczbę znaków w polu **Nazwa typu** , aby jednoznacznie zidentyfikować typ, którego chcesz użyć, a następnie naciśnij klawisz ENTER, aby wybrać typ

### <a name="to-select-a-generic-type-from-the-type-browser"></a>Aby wybrać typ ogólny z przeglądarki typów

1. W polu **Nazwa typu** wpisz nazwę typu, który ma być używany.

2. Gdy nazwa typu, który ma być używany, pojawia się w drzewie w polu **Nazwa typu** , kliknij typ, aby zaznaczyć, że pojawią się pola rozwijane.

     Wybierz typ, którego chcesz użyć, aby zamknąć ogólne z pól rozwijanych, a następnie kliknij przycisk **OK**.

## <a name="types-displayed-in-the-type-browser"></a>Typy wyświetlane w przeglądarce typów

Typy wyświetlane w przeglądarce typów mogą się różnić w zależności od sposobu uruchomienia przeglądarki typów. Jeśli przeglądarka typów została uruchomiona z projektu przepływu pracy wewnątrz **VS2010** , domyślnie są wyświetlane wszystkie typy w przywoływanych zestawach i projektach, do których istnieją odwołania. Jeśli przeglądarka typów została uruchomiona spoza systemu projektu **VS2010** (na przykład w aplikacji do przeszukanego przepływu pracy lub w autonomicznym pliku przepływu pracy), domyślnie są wyświetlane typy ze wszystkich zestawów załadowanych w domenie aplikacji.

Typy w przeglądarce typów mogą być filtrowane przez deweloperów projektanta działań. Dla danego działania może zostać wyświetlony tylko podzbiór typów. Na przykład w <xref:System.Activities.Statements.TryCatch> działaniu w <xref:System.Exception> przeglądarce typów są wyświetlane tylko typy pochodne od.

## <a name="filtering-search-results-in-the-type-browser"></a>Filtrowanie wyników wyszukiwania w przeglądarce typów

Lista typów w polu **Nazwa typu** jest krótsza podczas wpisywania więcej znaków w celu znalezienia dopasowania. Tylko typy, których nazwa fullyqualified rozpoczyna się od ciągu, który wpisano lub typy, których krótka nazwa rozpoczyna się od ciągu, który wpisano, pojawia się na liście filtrowanej.

Na przykład:

1. Wpisywanie **operacji** jest zgodne, <xref:System.OperationCanceledException> ale nie <xref:System.InvalidOperationException> . Aby dopasować <xref:System.InvalidOperationException> , zacznij wpisywać system. I lub nieprawidłowy.

2. Wpisywanie dopasowań **ogólnych** <xref:System.GenericUriParser> , ale nie typów w <xref:System.Collections.Generic> przestrzeni nazw. Aby wyszukać typy w <xref:System.Collections.Generic> przestrzeni nazw, wpisz w pełni kwalifikowaną nazwę przestrzeni nazw.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Wybieranie kontraktu usługi przy użyciu okna dialogowego przeglądarki typów

W przypadku wybrania typu kontraktu usługi w przeglądarce typu wyświetlane są tylko typy, które mają <xref:System.ServiceModel.ServiceContractAttribute> atrybut.

## <a name="see-also"></a>Zobacz też

- [Używanie projektantów działań](control-flow-activity-designers.md)
