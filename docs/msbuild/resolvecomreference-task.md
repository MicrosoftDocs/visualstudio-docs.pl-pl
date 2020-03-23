---
title: Zadanie ResolveComReference | Dokumenty firmy Microsoft
ms.date: 07/25/2019
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveCOMReference task
- ResolveCOMReference task [MSBuild]
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fdc6c6ccd58bcc83cc37ff3a9f7888af837ed6e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595205"
---
# <a name="resolvecomreference-task"></a>Zadanie ResolveComReference

Pobiera listę co najmniej jednej nazwy biblioteki typów lub plików *.tlb* i rozpoznaje te biblioteki typów do lokalizacji na dysku.

## <a name="parameters"></a>Parametry

 W poniższej tabeli `ResolveCOMReference` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`DelaySign`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, umieszcza klucz publiczny w zestawie. Jeśli `false`, w pełni podpisze zespół.|
|`EnvironmentVariables`|Parametr `String[]` opcjonalny.<br /><br /> Tablica par zmiennych środowiskowych, oddzielonych znakami równości. Zmienne te są przekazywane do zduplikowanych *tlbimp.exe* i *aximp.exe* oprócz lub selektywnie nadrzędne, zwykły blok środowiska..|
|`ExecuteAsTool`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`program , uruchamia *plik tlbimp.exe* i *aximp.exe* z odpowiedniej struktury docelowej poza proc, aby wygenerować niezbędne zestawy otoki. Ten parametr umożliwia wielokrotne kierowanie.|
|`IncludeVersionInInteropName`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`wersja typelib zostanie uwzględniona w nazwie otoki. Wartość domyślna to `false`.|
|`KeyContainer`|Parametr `String` opcjonalny.<br /><br /> Określa kontener, w który znajduje się para kluczy publicznych/prywatnych.|
|`KeyFile`|Parametr `String` opcjonalny.<br /><br /> Określa element zawierający parę kluczy publicznych/prywatnych.|
|`NoClassMembers`|Parametr `Boolean`opcjonalny.|
|`ResolvedAssemblyReferences`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Określa odwołania do zestawu rozwiązań.|
|`ResolvedFiles`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Określa w pełni kwalifikowane pliki na dysku, które odpowiadają fizycznym lokalizacjom bibliotek typów, które zostały dostarczone jako dane wejściowe do tego zadania.|
|`ResolvedModules`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]`opcjonalny.|
|`SdkToolsPath`|Parametr <xref:System.String?displayProperty=fullName> opcjonalny.<br /><br /> Jeśli `ExecuteAsTool` `true`tak jest , ten parametr musi być ustawiony na ścieżkę narzędzi zestawu SDK dla wersji frameworka, na którą kierowano.|
|`StateFile`|Parametr `String` opcjonalny.<br /><br /> Określa plik pamięci podręcznej dla sygnatur czasowych składnika COM. Jeśli nie jest obecny, każdy bieg będzie regenerować wszystkie otoki.|
|`TargetFrameworkVersion`|Parametr `String` opcjonalny.<br /><br /> Określa wersję struktury docelowej projektu.<br /><br /> Wartość domyślna to `String.Empty`. co oznacza, że nie ma filtrowania dla odniesienia w oparciu o ramy docelowe.|
|`TargetProcessorArchitecture`|Parametr `String` opcjonalny.<br /><br /> Określa preferowaną architekturę procesora docelowego. Przekazany do *tlbimp.exe*/machine flag po przetłumaczeniu.<br /><br /> Wartość parametru powinna być <xref:Microsoft.Build.Utilities.ProcessorArchitecture>członkiem .|
|`TypeLibFiles`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa ścieżkę pliku biblioteki typów do odwołań COM. Elementy zawarte w tym parametrze mogą zawierać metadane elementu. Aby uzyskać więcej informacji, zobacz sekcję [TypeLibFiles metadane elementu](#typelibfiles-item-metadata) poniżej.|
|`TypeLibNames`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa nazwy bibliotek typów do rozwiązania. Elementy zawarte w tym parametrze muszą zawierać niektóre metadane elementu. Aby uzyskać więcej informacji, zobacz sekcję [TypeLibNames metadanych elementu](#typelibnames-item-metadata) poniżej.|
|`WrapperOutputDirectory`|Parametr `String` opcjonalny.<br /><br /> Lokalizacja na dysku, na którym jest umieszczony wygenerowany zespół międzypionowy. Jeśli metadane tego elementu nie jest określony, zadanie używa ścieżki bezwzględnej katalogu, w którym znajduje się plik projektu.|

## <a name="typelibnames-item-metadata"></a>Metadane elementu TypeLibNames

 W poniższej tabeli opisano metadane `TypeLibNames` elementu dostępne dla elementów przekazanych do parametru.

|Metadane|Opis|
|--------------|-----------------|
|`GUID`|Wymagane metadane elementu.<br /><br /> Identyfikator GUID dla biblioteki typów. Jeśli metadane tego elementu nie jest określony, zadanie kończy się niepowodzeniem.|
|`VersionMajor`|Wymagane metadane elementu.<br /><br /> Główna wersja biblioteki typów. Jeśli metadane tego elementu nie jest określony, zadanie kończy się niepowodzeniem.|
|`VersionMinor`|Wymagane metadane elementu.<br /><br /> Wersja pomocnicza biblioteki typów. Jeśli metadane tego elementu nie jest określony, zadanie kończy się niepowodzeniem.|
|`EmbedInteropTypes`|Opcjonalne `Boolean` metadane.<br /><br />  Jeśli `true`, osadź typy międzypłciowe z tego odwołania bezpośrednio do zestawu, a nie generowania międzyop DLL.|
|`LocaleIdentifier`|Opcjonalne metadane elementu.<br /><br /> Identyfikator ustawień regionalnych (lub LCID) dla biblioteki typów. Jest to określone jako wartość 32-bitowa, która identyfikuje język ludzki preferowany przez użytkownika, regionu lub aplikacji. Jeśli metadane tego elementu nie są określone, zadanie używa domyślnego identyfikatora ustawień regionalnych "0".|
|`WrapperTool`|Opcjonalne metadane elementu.<br /><br /> Określa narzędzie otoki używane do generowania otoki złożenia dla tej biblioteki typów. Jeśli metadane tego elementu nie są określone, zadanie używa domyślnego narzędzia otoki "tlbimp". Dostępne, niewrażliwe na wielkości litery są:<br /><br /> -   `Primary`: Użyj tego narzędzia otoki, jeśli chcesz użyć już wygenerowanego podstawowego złożenia międzypłonowego dla komponentu COM. Korzystając z tego narzędzia otoki, nie należy określać katalogu wyjściowego otoki, ponieważ spowoduje to niepowodzenie zadania.<br />-   `TLBImp`: Użyj tego narzędzia otoki, jeśli chcesz wygenerować zespół międzyoperacyjny dla komponentu COM.<br />-   `AXImp`:Użyj tego narzędzia otoki, jeśli chcesz wygenerować zestaw interop dla formantu ActiveX.|

## <a name="typelibfiles-item-metadata"></a>Metadane elementu TypeLibFiles

 W poniższej tabeli opisano metadane `TypeLibFiles` elementu dostępne dla elementów przekazanych do parametru.

|Metadane|Opis|
|--------------|-----------------|
|`EmbedInteropTypes`|Parametr `Boolean`opcjonalny.<br /><br />  Jeśli `true`, osadź typy międzypłciowe z tego odwołania bezpośrednio do zestawu, a nie generowania międzyop DLL.|
|`WrapperTool`|Opcjonalne metadane elementu.<br /><br /> Określa narzędzie otoki używane do generowania otoki złożenia dla tej biblioteki typów. Jeśli metadane tego elementu nie są określone, zadanie używa domyślnego narzędzia otoki "tlbimp". Dostępne, niewrażliwe na wielkości litery są:<br /><br /> -   `Primary`: Użyj tego narzędzia otoki, jeśli chcesz użyć już wygenerowanego podstawowego złożenia międzypłonowego dla komponentu COM. Korzystając z tego narzędzia otoki, nie należy określać katalogu wyjściowego otoki, ponieważ spowoduje to niepowodzenie zadania.<br />-   `TLBImp`: Użyj tego narzędzia otoki, jeśli chcesz wygenerować zespół międzyoperacyjny dla komponentu COM.<br />-   `AXImp`: Użyj tego narzędzia otoki, jeśli chcesz wygenerować zestaw międzypłetwo dla formantu ActiveX.|

> [!NOTE]
> Im więcej informacji podasz, aby jednoznacznie zidentyfikować bibliotekę typów, tym większa możliwość, że zadanie zostanie rozpoznane do prawidłowego pliku na dysku.

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [Klasa podstawowa zadania](../msbuild/task-base-class.md).

Biblioteka DLL COM nie musi być zarejestrowana na komputerze, aby to zadanie działało.

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
