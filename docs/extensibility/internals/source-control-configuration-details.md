---
title: Szczegóły konfiguracji kontroli źródła | Microsoft Docs
description: Dowiedz się więcej na temat implementowania kontroli źródła dla typu projektu w programie Visual Studio, która polega na konfigurowaniu systemu lub edytora projektu w celu zażądania uprawnień.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b9a3a2f33fcbb94d1e863daf69b8561f7bad4f2a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846507"
---
# <a name="source-control-configuration-details"></a>Szczegóły konfiguracji kontroli kodu źródłowego
W celu zaimplementowania kontroli źródła należy prawidłowo skonfigurować system lub Edytor projektu, aby wykonać następujące czynności:

- Zażądaj uprawnienia do przejścia do zmienionego stanu

- Zażądaj uprawnień do zapisania pliku

- Zażądaj uprawnień do dodawania, usuwania lub zmiany nazwy plików w projekcie

## <a name="request-permission-to-transition-to-changed-state"></a>Zażądaj uprawnienia do przejścia do zmienionego stanu
 Projekt lub Edytor musi zażądać uprawnień do przejścia do zmienionego stanu (zanieczyszczony) przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> . Każdy edytor implementujący <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> musi wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i odebrać zatwierdzenie zmiany dokumentu ze środowiska przed zwróceniem `True` do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> . Projekt jest zasadniczo edytorem pliku projektu, a w związku z tym jest taka sama odpowiedzialność za wdrożenie śledzenia zmian stanu dla pliku projektu jako edytora tekstu dla plików. Środowisko obsługuje zmieniony stan rozwiązania, ale musisz obsłużyć zmieniony stan dowolnego obiektu, który odwołuje się do rozwiązania, ale nie magazynu, takiego jak plik projektu lub jego elementy. Ogólnie rzecz biorąc, jeśli projekt lub Edytor jest odpowiedzialny za zarządzanie trwałością dla elementu, jest odpowiedzialny za wdrożenie śledzenia zmian stanu.

 W odpowiedzi na `IVsQueryEditQuerySave2::QueryEditFiles` wywołanie środowisko może wykonać następujące czynności:

- Odrzuć wywołanie zmiany, w takim przypadku Edytor lub projekt muszą pozostać w stanie niezmienionym (czystym).

- Wskaż, że dane dokumentu powinny zostać ponownie załadowane. W przypadku projektu środowisko spowoduje ponowne załadowanie danych dla projektu. Edytor musi ponownie załadować dane z dysku za pośrednictwem jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementacji. W obu przypadkach kontekst w projekcie lub edytorze może ulec zmianie po ponownym załadowaniu danych.

  Jest to złożone i trudne zadanie umożliwiające przeprojektowywania odpowiednich `IVsQueryEditQuerySave2::QueryEditFiles` wywołań do istniejącej bazy kodu. W związku z tym te wywołania powinny być zintegrowane podczas tworzenia projektu lub edytora.

## <a name="request-permission-to-save-a-file"></a>Zażądaj uprawnień do zapisania pliku
 Zanim projekt lub Edytor zapisze plik, musi wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> . W przypadku plików projektu te wywołania są automatycznie uzupełniane przez rozwiązanie, które wie, kiedy zapisać plik projektu. Edytory są odpowiedzialni za wykonywanie tych wywołań, chyba że implementacja edytora `IVsPersistDocData2` używa funkcji pomocnika <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> . Jeśli Edytor implementuje `IVsPersistDocData2` w ten sposób, wywołanie `IVsQueryEditQuerySave2::QuerySaveFile` lub `IVsQueryEditQuerySave2::QuerySaveFiles` zostanie wykonane dla użytkownika.

> [!NOTE]
> Zawsze zapobiegawczo te wywołania — to znaczy, na czas, kiedy Edytor może odebrać Anuluj.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Zażądaj uprawnień do dodawania, usuwania lub zmiany nazwy plików w projekcie
 Aby projekt mógł dodać, zmienić nazwę lub usunąć plik lub katalog, musi wywołać odpowiednią `IVsTrackProjectDocuments2::OnQuery*` metodę, aby zażądać uprawnienia ze środowiska. Jeśli przyznano uprawnienia, projekt musi wykonać operację, a następnie wywołać odpowiednią `IVsTrackProjectDocuments2::OnAfter*` metodę w celu powiadomienia środowiska o ukończeniu operacji. Projekt musi wywoływać metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfejsu dla wszystkich plików (na przykład plików specjalnych), a nie tylko do plików nadrzędnych. Wywołania plików są obowiązkowe, ale wywołania katalogu są opcjonalne. Jeśli projekt zawiera informacje o katalogu, należy wywołać odpowiednie <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> metody, ale jeśli nie ma tych informacji, środowisko wykryje informacje o katalogu.

 Projekt nie powinien wywoływać metod `IVsTrackProjectDocuments2` w projekcie otwartym lub zamkniętym. Detektory, które chcą uzyskać te informacje podczas uruchamiania, mogą oczekiwać na <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> zdarzenie i wykonać iterację w rozwiązaniu, aby znaleźć potrzebne informacje. W przypadku zamknięcia te informacje nie są zbędne. `IVsTrackProjectDocuments2` jest dostarczany z <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> .

 Dla każdej akcji Dodaj, Zmień nazwę i Usuń istnieje `OnQuery*` Metoda i `OnAfter*` Metoda. Wywołaj `OnQuery*` metodę, aby zażądać uprawnienia do dodawania, zmieniania nazwy lub usuwania pliku lub katalogu. Wywoływanie `OnAfter*` metody po dodaniu lub usunięciu pliku lub katalogu, a stan projektu odzwierciedla nowy stan.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Obsługa kontroli kodu źródłowego](../../extensibility/internals/supporting-source-control.md)
