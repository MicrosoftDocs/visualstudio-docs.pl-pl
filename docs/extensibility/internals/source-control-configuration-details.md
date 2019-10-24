---
title: Szczegóły konfiguracji kontroli źródła | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a6c51dfe4ad9378af04da61dbd7e9011c4678f1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723795"
---
# <a name="source-control-configuration-details"></a>Szczegóły konfiguracji kontroli kodu źródłowego
W celu zaimplementowania kontroli źródła należy prawidłowo skonfigurować system lub Edytor projektu, aby wykonać następujące czynności:

- Zażądaj uprawnienia do przejścia do zmienionego stanu

- Zażądaj uprawnień do zapisania pliku

- Zażądaj uprawnień do dodawania, usuwania lub zmiany nazwy plików w projekcie

## <a name="request-permission-to-transition-to-changed-state"></a>Zażądaj uprawnienia do przejścia do zmienionego stanu
 Projekt lub Edytor musi zażądać uprawnień do przejścia do zmienionego stanu (zanieczyszczony) przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>. Każdy edytor implementujący <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> musi wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i odebrać zatwierdzenie zmiany dokumentu ze środowiska przed zwróceniem `True` dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>. Projekt jest zasadniczo edytorem pliku projektu, a w związku z tym jest taka sama odpowiedzialność za wdrożenie śledzenia zmian stanu dla pliku projektu jako edytora tekstu dla plików. Środowisko obsługuje zmieniony stan rozwiązania, ale musisz obsłużyć zmieniony stan dowolnego obiektu, który odwołuje się do rozwiązania, ale nie magazynu, takiego jak plik projektu lub jego elementy. Ogólnie rzecz biorąc, jeśli projekt lub Edytor jest odpowiedzialny za zarządzanie trwałością dla elementu, jest odpowiedzialny za wdrożenie śledzenia zmian stanu.

 W odpowiedzi na wywołanie `IVsQueryEditQuerySave2::QueryEditFiles` środowisko może wykonać następujące czynności:

- Odrzuć wywołanie zmiany, w takim przypadku Edytor lub projekt muszą pozostać w stanie niezmienionym (czystym).

- Wskaż, że dane dokumentu powinny zostać ponownie załadowane. W przypadku projektu środowisko spowoduje ponowne załadowanie danych dla projektu. Edytor musi ponownie załadować dane z dysku za pośrednictwem jego implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>. W obu przypadkach kontekst w projekcie lub edytorze może ulec zmianie po ponownym załadowaniu danych.

  Jest to złożone i trudne zadanie umożliwiające przeprojektowywania odpowiednich wywołań `IVsQueryEditQuerySave2::QueryEditFiles` na istniejącą bazę kodu. W związku z tym te wywołania powinny być zintegrowane podczas tworzenia projektu lub edytora.

## <a name="request-permission-to-save-a-file"></a>Zażądaj uprawnień do zapisania pliku
 Przed zapisaniem pliku przez projekt lub Edytor musi on wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>. W przypadku plików projektu te wywołania są automatycznie uzupełniane przez rozwiązanie, które wie, kiedy zapisać plik projektu. Edytory są odpowiedzialni za wykonywanie tych wywołań, chyba że implementacja edytora `IVsPersistDocData2` używa funkcji pomocnika <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>. Jeśli Edytor implementuje `IVsPersistDocData2` w ten sposób, zostanie wykonane wywołanie `IVsQueryEditQuerySave2::QuerySaveFile` lub `IVsQueryEditQuerySave2::QuerySaveFiles`.

> [!NOTE]
> Zawsze zapobiegawczo te wywołania — to znaczy, na czas, kiedy Edytor może odebrać Anuluj.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Zażądaj uprawnień do dodawania, usuwania lub zmiany nazwy plików w projekcie
 Aby projekt mógł dodać, zmienić nazwę lub usunąć plik lub katalog, musi wywołać odpowiednią metodę `IVsTrackProjectDocuments2::OnQuery*`, aby zażądać uprawnień ze środowiska. Jeśli przyznano uprawnienia, projekt musi wykonać operację, a następnie wywołać odpowiednią metodę `IVsTrackProjectDocuments2::OnAfter*`, aby powiadomić środowisko o ukończeniu operacji. Projekt musi wywoływać metody interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> dla wszystkich plików (na przykład plików specjalnych), a nie tylko plików nadrzędnych. Wywołania plików są obowiązkowe, ale wywołania katalogu są opcjonalne. Jeśli projekt zawiera informacje o katalogu, należy wywołać odpowiednie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>, ale jeśli nie ma tych informacji, środowisko będzie wywnioskować informacje o katalogu.

 Projekt nie powinien wywoływać metod `IVsTrackProjectDocuments2` w projekcie otwartym lub zamkniętym. Detektory, które chcą uzyskać te informacje podczas uruchamiania, mogą czekać na zdarzenie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> i wykonać iterację w rozwiązaniu, aby znaleźć potrzebne informacje. W przypadku zamknięcia te informacje nie są zbędne. `IVsTrackProjectDocuments2` podano z <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.

 Dla każdej akcji Dodaj, Zmień nazwę i Usuń istnieje metoda `OnQuery*` i Metoda `OnAfter*`. Wywołaj metodę `OnQuery*`, aby zażądać uprawnienia do dodawania, zmieniania nazwy lub usuwania pliku lub katalogu. Wywołaj metodę `OnAfter*` po dodaniu pliku lub katalogu, zmianie nazwy lub usunięciu, a stan projektu odzwierciedla nowy stan.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Obsługa kontroli kodu źródłowego](../../extensibility/internals/supporting-source-control.md)