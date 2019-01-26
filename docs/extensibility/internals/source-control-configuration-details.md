---
title: Szczegóły konfiguracji kontroli źródła | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c01c71673640814006fe6771aa841852c247fd54
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965318"
---
# <a name="source-control-configuration-details"></a>Szczegóły konfiguracji kontroli kodu źródłowego
W celu wdrożenia kontroli źródła, należy poprawnie skonfigurować system projektu lub edytora, aby wykonać następujące czynności:

-   Żądanie uprawnień do przejścia do zmiany stanu

-   Żądanie uprawnień do zapisania pliku

-   Poproś o uprawnienia do dodawania, usuwania lub zmiany nazwy plików w projekcie

## <a name="request-permission-to-transition-to-changed-state"></a>Żądanie uprawnień do przejścia do zmiany stanu
 Projekt lub Edytor musi żądać uprawnienia do przejścia do zmiany stanu (dirty) przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>. Każdy edytor, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> musi wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i uzyskać zatwierdzenie, aby zmienić dokumentu w środowisku przed zwróceniem `True` dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>. Projekt jest zasadniczo edytor dla pliku projektu, a co w efekcie ponosi odpowiedzialność tej samej dotyczące implementowania śledzenia zmianie stanu w pliku projektu, podobnie jak edytor tekstu dla jego plików. Środowisko obsługuje stan zmienionego rozwiązania, ale musi obsługiwać zmiana stanu dowolnego obiektu odwołuje się do rozwiązania, ale nie są zapisywane, takich jak plik projektu lub jego elementów. Ogólnie rzecz biorąc Jeśli projekt lub edytora jest odpowiedzialny za zarządzanie stanów trwałych dla elementu, następnie odpowiada dotyczące implementowania śledzenia zmianie stanu.

 W odpowiedzi na `IVsQueryEditQuerySave2::QueryEditFiles` wywołać, środowiska może wykonać następujące czynności:

- Odrzuć wywołanie, aby zmienić, w którym to przypadku Edytor lub projekt musi pozostać bez zmian stanu (czyszczenie).

- Wskazuje, czy należy ponownie załadować danych dokumentu. Dla projektu środowiska spowoduje ponowne załadowanie danych dla projektu. Edytor należy ponownie załadować dane z dysku za pomocą jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementacji. W obu przypadkach kontekstu w projekcie lub w edytorze można zmienić po załadowaniu danych.

  Jest to zadanie złożonej i trudnej do przeprojektować odpowiednie `IVsQueryEditQuerySave2::QueryEditFiles` wywołania do istniejącej bazy kodu. W wyniku tych wywołań powinny być włączone podczas tworzenia projektu lub edytorze.

## <a name="request-permission-to-save-a-file"></a>Żądanie uprawnień do zapisania pliku
 Zanim projekt lub Edytor zapisuje plik, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>. Pliki projektu te wywołania są automatycznie uzupełniane przez rozwiązanie, który wie, kiedy można zapisać pliku projektu. Edytory jest odpowiedzialny za wykonywanie tych wywołań, chyba że implementacja edytora `IVsPersistDocData2` korzysta z funkcji pomocnika <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>. Jeśli Edytor implementuje `IVsPersistDocData2` w ten sposób, a następnie wywołania `IVsQueryEditQuerySave2::QuerySaveFile` lub `IVsQueryEditQuerySave2::QuerySaveFiles` ma zostać dla Ciebie.

> [!NOTE]
>  Zawsze tworzyć te wywołania prewencyjnego — oznacza to, że w danym momencie, gdy edytor jest możliwość odbierania Anuluj.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Poproś o uprawnienia do dodawania, usuwania lub zmiany nazwy plików w projekcie
 Zanim projektu można dodać, zmienić lub usunięcia pliku lub katalogu, należy wywołać odpowiednie `IVsTrackProjectDocuments2::OnQuery*` metody, aby poprosić o uprawnienie ze środowiska. Jeśli uprawnienia, a następnie projekt musi ukończyć operacji, a następnie wywołaj odpowiedni `IVsTrackProjectDocuments2::OnAfter*` metodę, aby powiadomić środowiska o ukończeniu operacji. Projekt należy wywołać metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfejs wszystkie pliki (na przykład specjalnych) i nie tylko pliki nadrzędnej. Wywołania pliku są obowiązkowe, ale wywołania katalogu są opcjonalne. Jeśli projekt zawiera informacje o katalogu, a następnie wywołać odpowiednie <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> metody, ale jeśli nie ma tych informacji, a następnie środowiska wywnioskuje informacji o katalogu.

 Projekt nie powinien wywoływać metody `IVsTrackProjectDocuments2` w projekcie, Otwórz lub Zamknij. Odbiorniki, które te informacje podczas uruchamiania poczekać, aż <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> zdarzeń i iteracyjnego przeglądania rozwiązanie, aby znaleźć potrzebnych informacji. Podczas zamykania te informacje nie są potrzebne. `IVsTrackProjectDocuments2` udostępnionych w serwisie <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.

 Dla każdego Dodawanie, zmianę nazwy i akcji Usuń ma `OnQuery*` metody i `OnAfter*` metody. Wywołaj `OnQuery*` metody uprawnienia do dodawania, zmienić lub usunąć pliku lub katalogu. Wywołaj `OnAfter*` metoda po pliku lub katalogu został dodany, zmieniono jego nazwę lub został usunięty i stanie projektu odzwierciedla nowy stan.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Obsługa kontroli kodu źródłowego](../../extensibility/internals/supporting-source-control.md)