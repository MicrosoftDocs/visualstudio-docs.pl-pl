---
title: Konteksty plików obszaru roboczego w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 36f986db6f2c7b483b46060e1f514acc8dd9e758
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952818"
---
# <a name="workspace-file-contexts"></a>Konteksty plików obszaru roboczego

Wszystkie szczegółowe informacje dotyczące [Otwórz Folder](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) obszary robocze są produkowane przez "kontekstu dostawcy plików", które implementują <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> interfejsu. Te rozszerzenia mogą wyszukiwać wzorce w foldery lub pliki i odczytywać pliki programu MSBuild i pliki reguł programu make, wykrywanie zależności pakietów itp. Aby można było gromadzenie szczegółowych informacji, które są im potrzebne do definiowania kontekstu pliku. Kontekst pliku przez siebie nie wykonuje żadnych działań, ale raczej zawiera dane, które następnie można wykonywać operacje na innego rozszerzenia.

Każdy <xref:Microsoft.VisualStudio.Workspace.FileContext> ma `Guid` skojarzone z nim, który identyfikuje typ danych go wykonuje. Obszar roboczy używa tej wartości w `Guid` później, aby zapewnić zgodność identyfikatorów z rozszerzeniami, które korzystają z danych za pośrednictwem <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> właściwości. Dostawcy kontekstu plików są eksportowane z metadanymi, które identyfikuje od kontekstu pliku `Guid`s go może zwrócić danych.

Po zdefiniowaniu kontekstu pliku może być skojarzona z dowolną liczbę plików lub folderów w obszarze roboczym. Podany plik lub folder może być skojarzona z dowolną liczbę kontekstów pliku. Jest to relacja wiele do wielu.

Najbardziej typowe scenariusze dotyczące konteksty plików odnoszą się do kompilacji, debugowania i usług językowych. Aby uzyskać więcej informacji zobacz inne tematy związane z tych scenariuszy.

## <a name="file-context-lifecycle"></a>Cykl życia kontekstu pliku

Cykle życia dla `FileContext` są niejednoznaczne. W dowolnym momencie składnika można asynchronicznie żądanie pewne zestawów typów kontekstu. Będzie można wyświetlić dostawców, które obsługują pewien podzbiór typów kontekstu żądania. `IWorkspace` Wystąpienia działa jako środka man między odbiorców i dostawców <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> metody. Konsumenci mogą kontekst żądania i wykonanie akcji krótkoterminowych na podstawie kontekstu, gdy inne osoby mogą kontekst żądania i obsługa długotrwałych odwołania.

Zmiany może się zdarzyć, pliki, które powodują kontekstu pliku, aby stać się nieaktualne. Dostawca może wyzwolić zdarzenie na `FileContext` do powiadamiania odbiorców aktualizacji. Na przykład jeśli podano kontekstu kompilacji dla niektórych plików, ale zmiany na dysku unieważnia tego kontekstu, następnie producentów oryginalnego wywołać zdarzenie. Żadnych użytkowników nadal odwołuje się do który `FileContext` można następnie requery nowej `FileContext`.

>[!NOTE]
>Nie zostanie wzór wypychania do klientów. Konsumenci nie będzie powiadamiany o dostawcy nowe `FileContext` po ich żądania.

## <a name="expensive-file-context-computations"></a>Plik kosztowne kontekstu obliczeń

Zawartość pliku odczytu z dysku mogą być kosztowne, szczególnie w przypadku, gdy dostawca musi rozpoznać relacji między plikami. Na przykład można wykonywać zapytania dostawcę dla kontekstu pliku niektóre pliku źródłowego, ale kontekstu pliku zależy od metadanych z pliku projektu. Podczas analizowania pliku projektu lub dokonanie oceny oprogramowania za pomocą narzędzia MSBuild jest kosztowne. Zamiast tego rozszerzenia można wyeksportować `IFileScanner` utworzyć `FileDataValue` danych podczas indeksowania w obszarze roboczym. Teraz po wyświetleniu monitu dla konteksty plików `IFileContextProvider` szybko wyszukiwać indeksowane dane. Aby uzyskać więcej informacji na temat indeksowania, zobacz [indeksowania obszaru roboczego](workspace-indexing.md) tematu.

>[!WARNING]
>Należy zachować ostrożność innych sposobów swoje `FileContext` może być kosztowne do obliczenia. Niektóre interakcje interfejsu użytkownika są synchroniczne i polegają na dużą liczbę `FileContext` żądań. Przykładami otworzyć kartę Edytor i otwierania **Eksploratora rozwiązań** menu kontekstowego. Te akcje wprowadzić wiele kontekstu kompilacji typu żądania.

## <a name="file-context-related-apis"></a>Interfejsy API skojarzone z kontekstu pliku

- <xref:Microsoft.VisualStudio.Workspace.FileContext> przechowuje dane i metadane.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> i <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> tworzenie kontekstu pliku.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> Eksportuje dostwcy kontekstu pliku.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> Służy do konsumentów można pobrać konteksty plików.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> Definiuje typy kontekstu kompilacji używające Otwórz Folder.

## <a name="file-context-actions"></a>Akcje kontekstowe plików

Gdy `FileContext` jest po prostu dane dotyczące niektórych plików <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> jest sposobem express i działają na tych danych. `IFileContextAction` jest elastyczny, jej użycie. Są dwa najbardziej typowe przypadki, w jego kompilowania i debugowania.

## <a name="reporting-progress"></a>Raport z postępów

<xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> Metody jest przekazywana `IProgress<IFileContextActionProgressUpdate>`, ale argument nie może służyć jako tego typu. `IFileContextActionProgressUpdate` jest pusty interfejs i wywoływanie `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` może zgłosić `NotImplementedException`. Zamiast tego `IFileContextAction` rzutować argumentów do innego typu, w razie potrzeby dla scenariusza.

Aby uzyskać informacje na temat typów dostarczonych przez program Visual Studio można znaleźć w temacie odpowiedni scenariusz dokumentacji.

## <a name="file-context-action-related-apis"></a>Interfejsy API skojarzone z Akcja kontekstu pliku

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> wykonuje niektóre zachowania na podstawie `FileContext`.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> tworzy wystąpienia `IFileContextAction`.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> Eksportuje typ `IWorkspaceProviderFactory<IFileContextActionProvider>`.

## <a name="file-watching"></a>Oglądanie pliku

Obszar roboczy nasłuchuje powiadomień o zmianie pliku i udostępnia <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> za pośrednictwem <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Pliki zgodne z ustawieniem "ExcludedItems" nie powoduje wygenerowanie zdarzenia powiadomień pliku. Próg między zdarzeniami jest używany dla uproszczenia powiadomień i zmniejszenie zduplikowane. Jeśli potrzebujesz reagować na zmiany plików, należy subskrybować tę usługę.

>[!TIP]
>Obszar roboczy [usługę indeksowania](workspace-indexing.md) subskrybuje do zdarzeń pliku domyślnie. Plik uzupełnienia i modyfikacje spowoduje, że odpowiednie `IFileScanner`s zdarzenia do wywołania dla nowych danych dla tego pliku. Usuwanie pliku spowoduje usunięcie indeksowane dane. Nie trzeba subskrybować usługi `IFileScanner` usługą obserwatora pliku.

## <a name="next-steps"></a>Następne kroki

* [Indeksowanie](workspace-indexing.md) -Workspace indeksowania zbiera i będzie nadal występował, informacje o obszarze roboczym.
* [Obszary robocze](workspaces.md) — Przegląd pojęć obszaru roboczego i ustawienia magazynu.
