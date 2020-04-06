---
title: Szczegóły konfiguracji kontroli źródła | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cf4a5c55e8093e5dcd6406cde1c60f642188495
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705292"
---
# <a name="source-control-configuration-details"></a>Szczegóły konfiguracji kontroli kodu źródłowego
Aby zaimplementować kontrolę źródła, należy poprawnie skonfigurować system lub edytor projektu, aby wykonać następujące czynności:

- Żądanie uprawnień do przejścia do zmienionego stanu

- Żądanie uprawnień do zapisywania pliku

- Żądanie uprawnień do dodawania, usuwania lub zmieniania nazwy plików w projekcie

## <a name="request-permission-to-transition-to-changed-state"></a>Żądanie uprawnienia do przejścia do zmienionego stanu
 Projekt lub edytor musi zażądać uprawnień do przejścia <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>do stanu zmienionego (brudnego) przez wywołanie . Każdy edytor, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> który <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> implementuje musi wywołać i otrzymać zatwierdzenie, aby zmienić dokument ze środowiska przed zwróceniem `True` dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>. Projekt jest zasadniczo edytor dla pliku projektu, a w rezultacie ma taką samą odpowiedzialność za implementowanie śledzenia zmienionego stanu dla pliku projektu, jak edytor tekstu nie dla swoich plików. Środowisko obsługuje zmieniony stan rozwiązania, ale należy obsługiwać zmieniony stan dowolnego obiektu odwołuje się do rozwiązania, ale nie przechowuje, takich jak plik projektu lub jego elementy. Ogólnie rzecz biorąc, jeśli projekt lub edytor jest odpowiedzialny za zarządzanie trwałości dla elementu, a następnie jest odpowiedzialny za implementowanie śledzenia zmienionego stanu.

 W odpowiedzi `IVsQueryEditQuerySave2::QueryEditFiles` na wywołanie środowisko może wykonać następujące czynności:

- Odrzuć wywołanie zmiany, w którym to przypadku edytor lub projekt musi pozostać w stanie niezmienionym (czystym).

- Należy wskazać, że dane dokumentu powinny zostać ponownie załadowane. W przypadku projektu środowisko przeładuje dane dla projektu. Edytor musi ponownie załadować dane <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> z dysku za pośrednictwem jego implementacji. W obu przypadkach kontekst w projekcie lub edytorze można zmienić, gdy dane są ponownie ładowane.

  Jest to złożone i trudne zadanie `IVsQueryEditQuerySave2::QueryEditFiles` do modernizacji odpowiednich wywołań na istniejącej bazy kodu. W rezultacie te wywołania powinny być zintegrowane podczas tworzenia projektu lub edytora.

## <a name="request-permission-to-save-a-file"></a>Żądanie uprawnień do zapisywania pliku
 Zanim projekt lub edytor zapisze plik, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>musi wywołać lub . W przypadku plików projektu te wywołania są automatycznie wykonywane przez rozwiązanie, które wie, kiedy zapisać plik projektu. Redaktorzy są odpowiedzialni za wykonywanie tych `IVsPersistDocData2` połączeń, chyba <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>że implementacja edytora używa funkcji pomocnika . Jeśli edytor implementuje `IVsPersistDocData2` w ten sposób, `IVsQueryEditQuerySave2::QuerySaveFile` `IVsQueryEditQuerySave2::QuerySaveFiles` a następnie wywołanie lub jest wykonane dla Ciebie.

> [!NOTE]
> Zawsze wykonuj te wywołania z wyprzedzeniem — to znaczy w czasie, gdy edytor może otrzymać anulowanie.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Żądanie uprawnień do dodawania, usuwania lub zmieniania nazwy plików w projekcie
 Aby projekt mógł dodawać, zmieniać nazwy lub usuwać plik lub `IVsTrackProjectDocuments2::OnQuery*` katalog, należy wywołać odpowiednią metodę żądania uprawnień ze środowiska. Jeśli uprawnienie zostanie udzielone, projekt musi zakończyć `IVsTrackProjectDocuments2::OnAfter*` operację, a następnie wywołać odpowiednią metodę, aby powiadomić środowisko, że operacja została zakończona. Projekt musi wywołać metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfejsu dla wszystkich plików (na przykład plików specjalnych), a nie tylko plików nadrzędnych. Wywołania plików są obowiązkowe, ale wywołania katalogu są opcjonalne. Jeśli projekt zawiera informacje katalogowe, należy <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> wywołać odpowiednie metody, ale jeśli nie ma tych informacji, środowisko będzie wywnioskować informacje katalogowe.

 Projekt nie powinien wywoływać `IVsTrackProjectDocuments2` metod w projekcie otwartym lub bliskim. Detektory, które chcą te informacje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> podczas uruchamiania można czekać na zdarzenie i iteracji za pośrednictwem rozwiązania, aby znaleźć informacje, których potrzebują. Po zamknięciu te informacje nie są potrzebne. `IVsTrackProjectDocuments2`jest dostarczany <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>z .

 Dla każdego dodaj, zmień nazwę i usuń `OnQuery*` akcję, `OnAfter*` istnieje metoda i metoda. Wywołanie `OnQuery*` metody, aby poprosić o uprawnienia do dodawania, zmieniania nazwy lub usuwania pliku lub katalogu. Wywołanie `OnAfter*` metody po pliku lub katalogu został dodany, zmieniono nazwę lub usunięte, a stan projektu odzwierciedla nowy stan.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Obsługa kontroli kodu źródłowego](../../extensibility/internals/supporting-source-control.md)
