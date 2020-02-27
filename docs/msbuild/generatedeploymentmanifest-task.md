---
title: GenerateDeploymentManifest — — zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateDeploymentManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateDeploymentManifest task
- GenerateDeploymentManifest task [MSBuild]
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ca55f3eeb9b3119b27e67dcb0255f8386c521af6
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634074"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest — zadanie

Generuje manifest wdrażania ClickOnce. Manifest wdrożenia ClickOnce opisuje wdrożenie aplikacji przez zdefiniowanie unikatowej tożsamości dla wdrożenia, zidentyfikowanie cech wdrożenia, takich jak instalacja lub tryb online, określanie ustawień aktualizacji aplikacji i lokalizacji aktualizacji oraz Wskazywanie odpowiedniego manifestu aplikacji ClickOnce.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry zadania `GenerateDeploymentManifest`.

| Parametr | Opis |
|--------------------------| - |
| `AssemblyName` | Opcjonalny parametr `String`.<br /><br /> Określa pole `Name` tożsamości zestawu dla wygenerowanego manifestu. Jeśli ten parametr nie jest określony, nazwa jest wywnioskowana na podstawie parametrów `EntryPoint` lub `InputManifest`. Jeśli nie można wywnioskować nazwy, zadanie zgłosi błąd. |
| `AssemblyVersion` | Opcjonalny parametr `String`.<br /><br /> Określa pole `Version` tożsamości zestawu dla wygenerowanego manifestu. Jeśli ten parametr nie jest określony, zadanie używa wartości "1.0.0.0". |
| `CreateDesktopShortcut` | Opcjonalny parametr `Boolean`.<br /><br /> W przypadku wartości true na pulpicie zostanie utworzona ikona podczas instalacji aplikacji ClickOnce. |
| `DeploymentUrl` | Opcjonalny parametr `String`.<br /><br /> Określa lokalizację aktualizacji aplikacji. Jeśli ten parametr nie jest określony, nie zdefiniowano lokalizacji aktualizacji dla aplikacji. Jeśli jednak parametr `UpdateEnabled` jest `true`, należy określić lokalizację aktualizacji. Określona wartość powinna być w pełni kwalifikowanym adresem URL lub ścieżką UNC. |
| `Description` | Opcjonalny parametr `String`.<br /><br /> Określa opcjonalny opis aplikacji. |
| `DisallowUrlActivation` | Opcjonalny parametr `Boolean`.<br /><br /> Określa, czy aplikacja powinna być uruchamiana automatycznie podczas otwierania przy użyciu adresu URL. Jeśli ten parametr jest `true`, aplikacja może zostać uruchomiona tylko z menu **Start** . Wartość domyślna tego parametru to `false`. Dane wejściowe są stosowane tylko wtedy, gdy wartość parametru `Install` jest `true`. |
| `EntryPoint` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Wskazuje punkt wejścia dla wygenerowanego zestawu manifestu. W przypadku manifestu wdrażania ClickOnce dane wejściowe określają manifest aplikacji ClickOnce.<br /><br />Jeśli `EntryPoint` parametr zadania nie zostanie określony, tag `<customHostSpecified>` zostanie wstawiony jako element podrzędny tagu `<entryPoint>`, na przykład:<br /><br /> `<entryPoint xmlns="urn:schemas-microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Zależności bibliotek DLL można dodać do manifestu aplikacji, wykonując następujące czynności:<br /><br /> 1. Rozwiąż odwołania do zestawów za pomocą wywołania do <xref:Microsoft.Build.Tasks.ResolveAssemblyReference>.<br />2. Przekaż dane wyjściowe poprzedniego zadania i samego zestawu do <xref:Microsoft.Build.Tasks.ResolveManifestFiles>.<br />3. Przekaż zależności przy użyciu parametru `Dependencies`, aby <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>. |
| `ErrorReportUrl` | Opcjonalny parametr <xref:System.String?displayProperty=fullName>.<br /><br /> Określa adres URL strony sieci Web, która jest wyświetlana w oknach dialogowych podczas instalacji ClickOnce. |
| `InputManifest` | Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Wskazuje wejściowy dokument XML, który ma stanowić podstawę dla generatora manifestów. Dzięki temu dane strukturalne, takie jak niestandardowe definicje manifestu, zostaną odzwierciedlone w manifeście danych wyjściowych. Element główny w dokumencie XML musi być węzłem zestawu w przestrzeni nazw asmv1. |
| `Install` | Opcjonalny parametr `Boolean`.<br /><br /> Określa, czy aplikacja jest zainstalowaną aplikacją, czy tylko w trybie online. Jeśli ten parametr jest `true`, aplikacja zostanie zainstalowana w menu **Start** użytkownika i będzie można ją usunąć za pomocą okna dialogowego **Dodawanie lub usuwanie programów** . Jeśli ten parametr jest `false`, aplikacja jest przeznaczona do użycia w trybie online ze strony sieci Web. Wartość domyślna tego parametru to `true`. |
| `MapFileExtensions` | Opcjonalny parametr `Boolean`.<br /><br /> Określa, czy jest używane Mapowanie rozszerzenia nazwy pliku *. deploy* . Jeśli ten parametr jest `true`, każdy plik programu jest publikowany z rozszerzeniem nazwy pliku *. deploy* . Ta opcja przydaje się do zabezpieczenia serwera sieci Web, aby ograniczyć liczbę rozszerzeń nazw plików, które muszą być odblokowane w celu włączenia wdrożenia aplikacji ClickOnce. Wartość domyślna tego parametru to `false`. |
| `MaxTargetPath` | Opcjonalny parametr `String`.<br /><br /> Określa maksymalną dozwoloną długość ścieżki pliku we wdrożeniu aplikacji ClickOnce. Jeśli ten parametr jest określony, długość każdej ścieżki pliku w aplikacji jest sprawdzana względem tego limitu. Wszystkie elementy, które przekraczają limit, spowodują ostrzeżenie dotyczące kompilacji. Jeśli nie określono tego parametru wejściowego lub wartość jest równa zero, sprawdzanie nie jest wykonywane. |
| `MinimumRequiredVersion` | Opcjonalny parametr `String`.<br /><br /> Określa, czy użytkownik może pominąć aktualizację. Jeśli użytkownik ma wersję, która jest mniejsza niż wymagana minimum, nie będzie mieć opcji pomijania aktualizacji. Te dane wejściowe są stosowane tylko wtedy, gdy wartość parametru `Install` jest `true`. |
| `OutputManifest` | Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa nazwę wygenerowanego pliku manifestu wyjściowego. Jeśli ten parametr nie jest określony, nazwa pliku wyjściowego jest wywnioskowana z tożsamości wygenerowanego manifestu. |
| `Platform` | Opcjonalny parametr `String`.<br /><br /> Określa platformę docelową aplikacji. Ten parametr może mieć następujące wartości:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Wartością domyślną jest `AnyCPU`. |
| `Product` | Opcjonalny parametr `String`.<br /><br /> Określa nazwę aplikacji. Jeśli ten parametr nie jest określony, nazwa jest wywnioskowana z tożsamości wygenerowanego manifestu. Ta nazwa jest używana jako nazwa skrótu w menu **Start** i jest częścią nazwy, która pojawia się w oknie dialogowym **Dodaj lub usuń programy** . |
| `Publisher` | Opcjonalny parametr `String`.<br /><br /> Określa wydawcę aplikacji. Jeśli ten parametr nie jest określony, nazwa zostanie wywnioskowana z zarejestrowanego użytkownika lub tożsamość wygenerowanego manifestu. Ta nazwa jest używana jako nazwa folderu w menu **Start** i jest częścią nazwy, która pojawia się w oknie dialogowym **Dodaj lub usuń programy** . |
| `SuiteNamel` | Opcjonalny parametr `String`.<br /><br /> Określa nazwę folderu w menu **Start** , w którym znajduje się aplikacja po wdrożeniu ClickOnce. |
| `SupportUrl` | Opcjonalny parametr `String`.<br /><br /> Określa łącze, które pojawia się w oknie dialogowym **Dodaj lub usuń programy** dla aplikacji. Określona wartość powinna być w pełni kwalifikowanym adresem URL lub ścieżką UNC. |
| `TargetCulture` | Opcjonalny parametr `String`.<br /><br /> Identyfikuje kulturę aplikacji i określa pole `Language` tożsamości zestawu dla wygenerowanego manifestu. Jeśli ten parametr nie jest określony, zakłada się, że aplikacja ma niezmienną kulturę. |
| `TrustUrlParameters` | Opcjonalny parametr `Boolean`.<br /><br /> Określa, czy parametry ciągu zapytania URL mają być dostępne dla aplikacji. Wartość domyślna tego parametru to `false`, co oznacza, że parametry nie będą dostępne dla aplikacji. |
| `UpdateEnabled` | Opcjonalny parametr `Boolean`.<br /><br /> Wskazuje, czy aplikacja jest włączona dla aktualizacji. Wartość domyślna tego parametru to `false`. Ten parametr ma zastosowanie tylko wtedy, gdy wartość parametru `Install` jest `true`. |
| `UpdateInterval` | Opcjonalny parametr `Int32`.<br /><br /> Określa interwał aktualizacji aplikacji. Wartość domyślna tego parametru to zero. Ten parametr ma zastosowanie tylko wtedy, gdy wartości `Install` i `UpdateEnabled` parametrów są `true`. |
| `UpdateMode` | Opcjonalny parametr `String`.<br /><br /> Określa, czy aktualizacje mają być sprawdzane na pierwszym planie przed uruchomieniem aplikacji, czy w tle, gdy aplikacja jest uruchomiona. Ten parametr może mieć następujące wartości:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> Wartość domyślna tego parametru to `Background`. Ten parametr ma zastosowanie tylko wtedy, gdy wartości `Install` i `UpdateEnabled` parametrów są `true`. |
| `UpdateUnit` | Opcjonalny parametr `String`.<br /><br /> Określa jednostki dla parametru `UpdateInterval`. Ten parametr może mieć następujące wartości:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Ten parametr ma zastosowanie tylko wtedy, gdy wartości `Install` i `UpdateEnabled` parametrów są `true`. |

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.GenerateManifestBase>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą parametrów klasy Task, zobacz [Klasa bazowa zadania](../msbuild/task-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [GenerateApplicationManifest —, zadanie](../msbuild/generateapplicationmanifest-task.md)
- [SignFile —, zadanie](../msbuild/signfile-task.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
