---
title: Konteksty pliku obszaru roboczego w programie Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 36f986db6f2c7b483b46060e1f514acc8dd9e758
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952818"
---
# <a name="workspace-file-contexts"></a>Konteksty pliku obszaru roboczego

Wszystkie szczegółowe informacje w obszarach roboczych [otwartych folderów](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) są tworzone przez "dostawców kontekstu plików", które implementują <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> interfejs. Rozszerzenia te mogą szukać wzorców w folderach lub plikach, odczytywać pliki MSBuild i narzędzia reguł programu make, wykrywać zależności pakietów itp., aby gromadzić szczegółowe informacje potrzebne do zdefiniowania kontekstu pliku. Kontekst pliku nie wykonuje żadnej akcji, ale zamiast tego udostępnia dane, na które może ona działać inne rozszerzenie.

Każdy <xref:Microsoft.VisualStudio.Workspace.FileContext> z nich jest `Guid` skojarzony z tym, który identyfikuje typ danych, które wykonuje. Obszar roboczy używa tego `Guid` później, aby dopasować go do rozszerzeń, które zużywają dane za pośrednictwem <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> właściwości. Dostawca kontekstu pliku jest eksportowany z metadanymi, które identyfikują kontekst pliku, `Guid` dla którego mogą zostać wygenerowane dane.

Po zdefiniowaniu kontekstu pliku można skojarzyć z dowolną liczbą plików lub folderów w obszarze roboczym. Dany plik lub folder może być skojarzony z dowolną liczbą kontekstów plików. Jest to relacja wiele do wielu.

Najczęstsze scenariusze kontekstowe dotyczące plików są powiązane z usługami kompilowania, debugowania i języka. Aby uzyskać więcej informacji, zobacz inne tematy dotyczące tych scenariuszy.

## <a name="file-context-lifecycle"></a>Cykl życia kontekstu pliku

Cykle życia dla a `FileContext` są niejednoznaczne. W dowolnym momencie składnik może wysłać żądanie asynchronicznie dla pewnego zestawu typów kontekstowych. Zostaną zbadani dostawcy, którzy obsługują pewien podzestaw typów kontekstu żądania. `IWorkspace`Wystąpienie działa jako człowiek-Man między odbiorcą i dostawcami za pomocą <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> metody. Konsumenci mogą zażądać kontekstu i wykonywać kilka krótkoterminowych akcji opartych na kontekście, podczas gdy inne mogą zażądać kontekstu i zachować długotrwałe odwołanie.

Zmiany mogą wystąpić w przypadku plików, które powodują, że kontekst pliku staje się nieaktualny. Dostawca może wyzwalać zdarzenie w usłudze, `FileContext` aby poinformować odbiorców o aktualizacjach. Jeśli na przykład dla jakiegoś pliku jest udostępniony kontekst kompilacji, ale zmiana na dysku powoduje unieważnienie tego kontekstu, oryginalny producent może wywołać zdarzenie. Wszyscy konsumenci nadal się odwołują, ale `FileContext` mogą ponownie ponowić kwerendę dla nowego `FileContext` .

>[!NOTE]
>Nie istnieje model wypychania dla odbiorców. Klienci nie będą powiadamiani o nowym dostawcy `FileContext` po jego żądaniu.

## <a name="expensive-file-context-computations"></a>Kosztowne obliczenia kontekstu pliku

Odczytywanie zawartości pliku z dysku może być kosztowne, szczególnie gdy dostawca musi rozpoznać relację między plikami. Na przykład dostawca może być pytany dla pewnego kontekstu pliku źródłowego pliku, ale kontekst pliku zależy od metadanych z pliku projektu. Analizowanie pliku projektu lub ocenianie go za pomocą programu MSBuild jest kosztowne. Zamiast tego rozszerzenie może eksportować program `IFileScanner` w celu utworzenia `FileDataValue` danych podczas indeksowania obszaru roboczego. Teraz po wyświetleniu monitu o konteksty pliku `IFileContextProvider` można szybko wykonać zapytanie dotyczące tych indeksowanych danych. Aby uzyskać więcej informacji na temat indeksowania, zobacz temat [indeksowanie obszaru roboczego](workspace-indexing.md) .

>[!WARNING]
>Należy zachować ostrożność przy innych sposobach `FileContext` , które mogą być kosztowne do obliczenia. Niektóre interakcje interfejsu użytkownika są synchroniczne i polegają na dużej liczbie `FileContext` żądań. Przykłady obejmują otwieranie karty edytora i otwieranie menu kontekstowego **Eksplorator rozwiązań** . Te akcje tworzą wiele żądań typu kontekstu kompilacji.

## <a name="file-context-related-apis"></a>Interfejsy API związane z kontekstem pliku

- <xref:Microsoft.VisualStudio.Workspace.FileContext> przechowuje dane i metadane.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> i <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> Utwórz kontekst pliku.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> Eksportuje dostawcę kontekstu pliku.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> służy do pobierania kontekstów plików przez odbiorców.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> definiuje typy kontekstu kompilacji, które będą używane przez otwarty folder.

## <a name="file-context-actions"></a>Akcje kontekstu pliku

Gdy `FileContext` sam sam element to tylko dane dotyczące niektórych plików, <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> to sposób na to, aby przedstawić te dane i wykonywać na nich działania. `IFileContextAction` jest elastyczna w użyciu. Dwa z najpopularniejszych przypadków są kompilowane i debugowane.

## <a name="reporting-progress"></a>Raportowanie postępu

<xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A>Metoda jest przenoszona `IProgress<IFileContextActionProgressUpdate>` , ale argument nie powinien być używany jako ten typ. `IFileContextActionProgressUpdate` jest pustym interfejsem i wywoływanie `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` może zgłosić `NotImplementedException` . Zamiast tego, `IFileContextAction` należy rzutować argument na inny typ, zgodnie z potrzebami scenariusza.

Aby uzyskać informacje o typach dostarczonych przez program Visual Studio, zapoznaj się z dokumentacją odpowiedniego scenariusza.

## <a name="file-context-action-related-apis"></a>Interfejsy API powiązane z akcją kontekstu pliku

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> wykonuje pewne zachowanie na podstawie `FileContext` .
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> tworzy wystąpienia `IFileContextAction` .
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> Eksportuje typ `IWorkspaceProviderFactory<IFileContextActionProvider>` .

## <a name="file-watching"></a>Obserwowanie plików

Obszar roboczy nasłuchuje powiadomień o zmianach plików i <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> udostępnia <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . Pliki zgodne z ustawieniem "ExcludedItems" nie generują zdarzeń powiadomień o plikach. Próg między zdarzeniami jest używany na potrzeby uproszczenia powiadomień i zmniejszania. Jeśli musisz reagować na zmianę pliku, zasubskrybuj tę usługę.

>[!TIP]
>[Usługa indeksowania](workspace-indexing.md) obszaru roboczego subskrybuje zdarzenia plików domyślnie. Dodawanie i modyfikowanie plików spowoduje `IFileScanner` , że odpowiednie zdarzenia s zostaną wywołane dla nowych danych dla tego pliku. Usuwanie plików spowoduje usunięcie indeksowanych danych. Nie musisz subskrybować `IFileScanner` usługi obserwatora plików.

## <a name="next-steps"></a>Następne kroki

* [Indeksowanie](workspace-indexing.md) — indeksowanie obszaru roboczego zbiera i utrzymuje informacje o obszarze roboczym.
* [Obszary robocze](workspaces.md) — Przegląd pojęć i ustawień obszaru roboczego.
