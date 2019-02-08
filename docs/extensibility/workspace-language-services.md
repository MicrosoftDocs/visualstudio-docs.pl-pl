---
title: Obszary robocze i usług językowych w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 2893ae2bcd70ff317ba799fea6cfd2751c685731
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55929781"
---
# <a name="workspaces-and-language-services"></a>Obszary robocze i usług językowych

Usługi języka może zapewnić [Otwórz Folder](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) użytkowników te same funkcje zaawansowane języka są używane do podczas pracy z rozwiązaniami i projektami. Usługa języka własnym może aktywować na podstawie rozszerzenia pliku lub zawartości otwartym dokumencie chociaż "luźne plik" Usługa języka jest ograniczona do wyróżniania składni. Wymagane są dodatkowe informacje, aby zapewnić rozbudowane środowisko podczas edycji/przeglądania kodu źródłowego. Każda usługa język ma własną interfejsu API do inicjowania, za pomocą tych dodatkowych kontekstowych danych dokumentu. Zazwyczaj jest to zarządzane przez system projektu, który jest ściśle powiązany z usługą języka i systemu kompilacji.

## <a name="initialization"></a>Inicjalizacja

W [obszaru roboczego](workspaces.md), usługi w języka są inicjowane przez <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> punktu rozszerzenia, który specjalizuje się tylko w tym usługi językowej i nie zna tworzenia kompilacji. W ten sposób Właściciel usługi języka może zachować pojedynczego Otwórz Folder rozszerzenia niezależnie od tego, ile wzorce występują w foldery i pliki do uruchamiania ich kompilatora podczas kompilacji (na przykład program MSBuild, pliki reguł programu make itp.). Jeśli pliki, z których utworzono kontekstu pliku zostaną zmienione na dysku i kontekstu pliku są odświeżane, dostawca usługi języka jest powiadamiany o zaktualizowany zestaw konteksty plików. Dostawcy usług językowych można zaktualizować swój model.

Po otwarciu dokumentu w edytorze programu Visual Studio analizuje tylko język dostawców usług, które wymagają typów kontekstu plików, dla których można znaleźć pasującego dostwcy kontekstu pliku. Następnie przekazuje kontekstów pliku z dostawców pasujących do dostawcy usług w wybranym języku za pośrednictwem `ILanguageServiceProvider.InitializeAsync`. Dostawcy usług języka działanie z pliku danych kontekstu jest szczegółowo opisuje implementacja dostawcy usługi w języka, że oczekiwanego komfortu to bardziej rozbudowane usługa języka w tym otworzyć dokument.

## <a name="using-ilanguageserviceprovider"></a>Using ILanguageServiceProvider

Usługa językowa zostanie powiadomiony, gdy kontekstu pliku jest tworzona przy użyciu `ContextType` odpowiada jednej z `SupportedContextTypes` wartości serwera języka export — atrybut.

Aby zapewnić obsługę usługi językowej, rozszerzenia będą potrzebne:

- Unikatowy `Guid`. To posłuży do `SupportedContextTypes` atrybutu argumentów i `FileContext` obiektu.
- Język kontekstu pliku
  - Fabryki dostawców
    - `ExportFileContextProviderAttribute` atrybut z powyższych jednoznacznie generowane `Guid` w `SupportedContextTypes`
    - Implementuje `IWorkspaceProviderFactory<IFileContextProvider>`
  - Implementacja dostawcy `IFileContextProvider.GetContextsForFileAsync`
    - Utworzyć nową `FileContext` z `contextType` argumentu konstruktora jako unikatowego wygenerowany `Guid`
    - Użyj `Context` właściwość `FileContext` zapewniające dodatkowe dane do `ILanguageServiceProvider`
- Usługa językowa
  - Fabryki dostawców
    - `ExportLanguageServiceProvider` atrybut z powyższych jednoznacznie generowane `Guid` w `SupportedContextTypes`
    - Implementuje `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Dostawca
    - Implementuje `ILanguageServiceProvider`
    - Użyj `ILanguageServiceProvider.InitializeAsync` umożliwiające usług językowych dla podanych argumentów, gdy plik jest otwarty
    - Użyj `ILanguageServiceProvider.UninitializeAsync` wyłączenie usługi w języka dla podanych argumentów, gdy plik jest zamknięty.

>[!WARNING]
>`ILanguageServiceProvider` Metody może być wywoływany przez obszar roboczy w wątku głównym. Należy wziąć pod uwagę planowania pracy w innym wątku, aby uniknąć wprowadzenie opóźnienia interfejsu użytkownika.

## <a name="language-server-protocol"></a>Language Server Protocol

`Microsoft.VisualStudio.Workspace.*` Interfejsy API są jedynym sposobem, aby włączyć usługi języka w otwartym folderze. Innym rozwiązaniem jest użycie serwera języka. Aby uzyskać więcej informacji, przeczytaj o [Language Server Protocol](language-server-protocol.md).

## <a name="related-interfaces"></a>Powiązane interfejsy

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> jest wywoływane, gdy otwarcie lub zamknięcie do edycji plików zgodnych typów plików.

## <a name="next-steps"></a>Następne kroki

* [Obszar roboczy kompilacji](workspace-build.md) — funkcja otwierania folderu obsługuje tworzenie systemów, takich jak MSBuild i pliki reguł programu make.