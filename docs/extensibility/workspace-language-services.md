---
title: Obszary robocze i usługi językowe w programie Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 2893ae2bcd70ff317ba799fea6cfd2751c685731
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952709"
---
# <a name="workspaces-and-language-services"></a>Obszary robocze i usługi językowe

Usługi językowe mogą udostępniać użytkownikom [otwartych folderów](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) te same bogate funkcje języka, które są używane do pracy z rozwiązaniami i projektami. Usługa języka może być samoczynnie aktywowana na podstawie rozszerzenia lub zawartości otwartego dokumentu, chociaż ta usługa języka "luźny plik" jest ograniczona do wyróżniania składni. Dodatkowe informacje są wymagane, aby zapewnić bogatsze środowisko podczas edytowania/przeglądania kodu źródłowego. Każda usługa języka ma własny interfejs API do inicjowania przy użyciu tych dodatkowych danych kontekstowych dla dokumentu. Jest to zazwyczaj zarządzane przez system projektu, który jest ściśle połączony zarówno z usługą językową, jak i systemem kompilacji.

## <a name="initialization"></a>Inicjalizacja

W [obszarze roboczym](workspaces.md)usługi językowe są inicjowane przez <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> punkt rozszerzenia, który jest wyspecjalizowany tylko w tej usłudze językowej i nie zna żadnej kompilacji. W ten sposób właściciel usługi językowej może zachować pojedyncze rozszerzenie otwartego folderu, niezależnie od tego, ile wzorców istnieje w folderach i plikach do uruchamiania ich kompilatora podczas kompilacji (na przykład MSBuild, pliki reguł programu make itp.). Gdy pliki, z których utworzono kontekst pliku, są zmieniane na dysku, a kontekst pliku zostanie odświeżony, Dostawca usługi językowej zostanie powiadomiony o zaktualizowanym zestawie kontekstów plików. Dostawca usług językowych może następnie zaktualizować swój model.

Gdy dokument zostanie otwarty w edytorze, program Visual Studio uważa tylko dostawców usług językowych, którzy wymagają typów kontekstu plików, dla których można znaleźć pasujący dostawca kontekstu pliku. Następnie przekazuje konteksty plików ze zgodnych dostawców do wybranego dostawcy usług językowych za pośrednictwem programu `ILanguageServiceProvider.InitializeAsync` . Informacje o tym, czym jest dostawca usług językowych z danymi kontekstu plików, to szczegóły implementacji dostawcy usług językowych, ale oczekiwane środowisko użytkownika to bogatsza usługa języka dla tego otwartego dokumentu.

## <a name="using-ilanguageserviceprovider"></a>Korzystanie z ILanguageServiceProvider

Usługa językowa zostanie powiadomiona, gdy zostanie utworzony kontekst pliku `ContextType` , który jest zgodny z jedną z `SupportedContextTypes` wartości atrybutu eksportu serwera języka.

Aby zapewnić obsługę usługi językowej, wymagane jest rozszerzenie:

- Unikatowy `Guid` . Ta wartość będzie używana dla `SupportedContextTypes` argumentów atrybutów i w `FileContext` obiekcie.
- Kontekst pliku języka
  - Fabryka dostawców
    - `ExportFileContextProviderAttribute` atrybut z powyższym unikatowym wygenerowanym `Guid` w `SupportedContextTypes`
    - Wprowadza `IWorkspaceProviderFactory<IFileContextProvider>`
  - Implementacja dostawcy `IFileContextProvider.GetContextsForFileAsync`
    - Utwórz nowy `FileContext` z `contextType` argumentem konstruktora jako unikatowym wygenerowanym `Guid`
    - Użyj `Context` właściwości, `FileContext` Aby podać dodatkowe dane do `ILanguageServiceProvider`
- Usługa języka
  - Fabryka dostawców
    - `ExportLanguageServiceProvider` atrybut z powyższym unikatowym wygenerowanym `Guid` w `SupportedContextTypes`
    - Wprowadza `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Dostawca
    - Wprowadza `ILanguageServiceProvider`
    - Służy `ILanguageServiceProvider.InitializeAsync` do włączania usług językowych dla podanych argumentów po otwarciu pliku
    - Służy `ILanguageServiceProvider.UninitializeAsync` do wyłączania usług językowych dla podanych argumentów po zamknięciu pliku

>[!WARNING]
>`ILanguageServiceProvider`Metody mogą być wywoływane przez obszar roboczy w wątku głównym. Należy rozważyć planowanie pracy w innym wątku, aby uniknąć wprowadzania opóźnień interfejsu użytkownika.

## <a name="language-server-protocol"></a>Language Server Protocol

`Microsoft.VisualStudio.Workspace.*`Interfejsy API nie są jedynym sposobem na włączenie usługi językowej w otwartym folderze. Innym rozwiązaniem jest użycie serwera języka. Aby uzyskać więcej informacji, Przeczytaj o [protokole serwera języka](language-server-protocol.md).

## <a name="related-interfaces"></a>Powiązane interfejsy

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> jest wywoływany, gdy plik pasujących typów plików jest otwarty lub zamknięty do edycji.

## <a name="next-steps"></a>Następne kroki

* [Kompilacja obszaru roboczego](workspace-build.md) — otwarty folder obsługuje systemy kompilacji, takie jak MSBuild i pliki reguł programu make.