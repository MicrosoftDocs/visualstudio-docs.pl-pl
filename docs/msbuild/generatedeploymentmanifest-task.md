---
title: Generatedeploymentmanifest — zadanie | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8a2f4810c8a485d6b9013f658e221db39d8071f
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59652583"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest — zadanie

Generuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest wdrożenia. A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest wdrożenia w tym artykule opisano wdrażanie aplikacji przez określenie unikatowej tożsamości wdrożenia, identyfikujące cech wdrażania, takie jak instalowanie lub tryb online, określenie aplikacji zaktualizuj ustawienia i lokalizacje, aktualizacji i wskazanie odpowiedniego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu aplikacji.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry `GenerateDeploymentManifest` zadania.

| Parametr | Opis |
|--------------------------| - |
| `AssemblyName` | Opcjonalnie `String` parametru.<br /><br /> Określa `Name` pole tożsamości zestawu wygenerowanego manifestu. Jeśli ten parametr nie jest określony, nazwa wynika z `EntryPoint` lub `InputManifest` parametrów. Jeśli nazwa nie można wywnioskować, zadanie wyrzuca błąd. |
| `AssemblyVersion` | Opcjonalnie `String` parametru.<br /><br /> Określa `Version` pole tożsamości zestawu wygenerowanego manifestu. Jeśli nie określono tego parametru, zadanie używa wartości "1.0.0.0". |
| `CreateDesktopShortcut` | Opcjonalnie `Boolean` parametru.<br /><br /> W przypadku opcji true, tworzona jest ikona na pulpicie podczas instalacji aplikacji ClickOnce. |
| `DeploymentUrl` | Opcjonalnie `String` parametru.<br /><br /> Określa lokalizację aktualizacji dla aplikacji. Jeśli ten parametr nie jest określony, lokalizacja aktualizacji nie jest zdefiniowana dla aplikacji. Jednak jeśli `UpdateEnabled` parametr jest `true`, należy określić zaktualizowaną lokalizację. Określona wartość powinna być w pełni kwalifikowany adres URL lub ścieżką UNC. |
| `Description` | Opcjonalnie `String` parametru.<br /><br /> Określa opcjonalny opis dla aplikacji. |
| `DisallowUrlActivation` | Opcjonalnie `Boolean` parametru.<br /><br /> Określa, czy aplikacja powinna zostać uruchomiona automatycznie po otwarciu go przy użyciu adresu URL. Jeśli ten parametr jest `true`, aplikację można uruchomić tylko z **Start** menu. Wartość domyślna tego parametru to `false`. Wejście to stosuje się tylko wtedy, gdy `Install` wartość parametru jest `true`. |
| `EntryPoint` | Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Wskazuje punkt wejścia dla wygenerowanego zestawu manifestu. Aby uzyskać [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu wdrażania, dane wejściowe określają [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu aplikacji.<br /><br />Jeśli `EntryPoint` parametr zadania nie jest określony, `<customHostSpecified>` tag jest wstawiany jako element podrzędny elementu `<entryPoint>` tagu, na przykład:<br /><br /> `<entryPoint xmlns="urn:schemas-microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Za pomocą poniższej procedury, można dodać zależności DLL do manifestu aplikacji:<br /><br /> 1.  Rozpoznaj odwołania zestawu z wywołaniem <xref:Microsoft.Build.Tasks.ResolveAssemblyReference>.<br />2.  Przekazać dane wyjściowe poprzedniego zadania i samego montażu do <xref:Microsoft.Build.Tasks.ResolveManifestFiles>.<br />3.  Przekazać zależności za pomocą `Dependencies` parametr <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>. |
| `ErrorReportUrl` | Opcjonalnie <xref:System.String?displayProperty=fullName> parametru.<br /><br /> Określa adres URL strony sieci web, która jest wyświetlana w oknach dialogowych podczas instalacji ClickOnce. |
| `InputManifest` | Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Wskazuje dokument danych wejściowych XML, która będzie służyć jako podstawa do generatora manifestu. Dzięki temu dane strukturalnych, takich jak niestandardowe definicje manifestu są odzwierciedlane w manifeście danych wyjściowych. Element główny dokumentu XML musi być zbiorem węzła trustinfo w obszarze nazw asmv1. |
| `Install` | Opcjonalnie `Boolean` parametru.<br /><br /> Określa, czy aplikacja jest zainstalowaną aplikacją lub aplikacją tylko w trybie online. Jeśli ten parametr jest `true`, aplikacja zostanie zainstalowana na użytkownika **Start** menu i można go usunąć za pomocą **apletu Dodaj lub usuń programy** okno dialogowe. Jeśli ten parametr jest `false`, aplikacja jest przeznaczona do użytku online ze strony sieci web. Wartość domyślna tego parametru to `true`. |
| `MapFileExtensions` | Opcjonalnie `Boolean` parametru.<br /><br /> Określa, czy *.deploy* mapowanie rozszerzenia nazwy pliku jest używana. Jeśli ten parametr jest `true`, każdy plik programu jest publikowany razem z *.deploy* rozszerzenie nazwy pliku. Ta opcja jest przydatna dla zabezpieczeń serwera sieci web ograniczyć liczbę rozszerzeń nazw plików, które muszą być odblokowane, żeby umożliwić [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia aplikacji. Wartość domyślna tego parametru to `false`. |
| `MaxTargetPath` | Opcjonalnie `String` parametru.<br /><br /> Określa maksymalną dozwoloną długość ścieżki pliku w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia aplikacji. Jeśli ten parametr jest określony, długość każdej ścieżki pliku w aplikacji jest sprawdzana względem tego limitu. Wszystkie elementy, które przekraczają limit spowodują ostrzeżenia kompilacji. Jeśli wejście to nie jest określona lub jest równe zeru, żadne sprawdzanie nie jest przeprowadzane. |
| `MinimumRequiredVersion` | Opcjonalnie `String` parametru.<br /><br /> Określa, czy użytkownik może pominąć tę aktualizację. Jeśli użytkownik ma wersję, która jest mniejsza niż minimalna wymagana, nie będzie on możliwość pominąć tę aktualizację. Te dane wejściowe ma zastosowanie tylko jeśli wartość `Install` parametr `true`. |
| `OutputManifest` | Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa nazwę utworzonego wyjściowego pliku manifestu. Jeśli ten parametr nie jest określony, nazwa pliku wyjściowego wynika z tożsamości wygenerowanego manifestu. |
| `Platform` | Opcjonalnie `String` parametru.<br /><br /> Określa platformę docelową aplikacji. Ten parametr może mieć następujące wartości:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Wartość domyślna to `AnyCPU`. |
| `Product` | Opcjonalnie `String` parametru.<br /><br /> Określa nazwę aplikacji. Jeśli ten parametr nie jest określony, nazwa wynika z tożsamości wygenerowanego manifestu. Ta nazwa jest używaną nazwą skrótu w **Start** menu i jest częścią nazwy, która jest wyświetlana w **apletu Dodaj lub usuń programy** okno dialogowe. |
| `Publisher` | Opcjonalnie `String` parametru.<br /><br /> Określa wydawcę aplikacji. Jeśli ten parametr nie jest określony, nazwa wynika z zarejestrowanego użytkownika lub tożsamości wygenerowanego manifestu. Ta nazwa jest używana nazwa folderu na **Start** menu i jest częścią nazwy, która jest wyświetlana w **apletu Dodaj lub usuń programy** okno dialogowe. |
| `SuiteNamel` | Opcjonalnie `String` parametru.<br /><br /> Określa nazwę folderu na **Start** menu, w którym znajduje się aplikacja po wdrażania ClickOnce. |
| `SupportUrl` | Opcjonalnie `String` parametru.<br /><br /> Umożliwia określenie łącza, który pojawia się w **apletu Dodaj lub usuń programy** okno dialogowe dla aplikacji. Określona wartość powinna być w pełni kwalifikowany adres URL lub ścieżką UNC. |
| `TargetCulture` | Opcjonalnie `String` parametru.<br /><br /> Identyfikuje kulturę aplikacji i określa `Language` pole tożsamości zestawu wygenerowanego manifestu. Jeśli ten parametr nie jest określony, zakłada się, że aplikacja jest kulturowo niezmienna. |
| `TrustUrlParameters` | Opcjonalnie `Boolean` parametru.<br /><br /> Określa, czy parametry ciągu zapytania URL powinny być udostępnione do aplikacji. Wartość domyślna tego parametru to `false`, co oznacza, że parametry nie będą dostępne dla aplikacji. |
| `UpdateEnabled` | Opcjonalnie `Boolean` parametru.<br /><br /> Wskazuje, czy aplikacja jest włączona dla aktualizacji. Wartość domyślna tego parametru to `false`. Ten parametr ma zastosowanie tylko jeśli wartość `Install` parametr `true`. |
| `UpdateInterval` | Opcjonalnie `Int32` parametru.<br /><br /> Określa interwał aktualizacji dla aplikacji. Wartość domyślna tego parametru to zero. Ten parametr ma zastosowanie tylko jeśli wartości `Install` i `UpdateEnabled` parametry są zarówno `true`. |
| `UpdateMode` | Opcjonalnie `String` parametru.<br /><br /> Określa, czy aktualizacje powinny być sprawdzane na pierwszym planie, zanim aplikacja jest uruchomiona lub jest uruchomiona w tle jako aplikacja. Ten parametr może mieć następujące wartości:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> Wartość domyślna tego parametru to `Background`. Ten parametr ma zastosowanie tylko jeśli wartości `Install` i `UpdateEnabled` parametry są zarówno `true`. |
| `UpdateUnit` | Opcjonalnie `String` parametru.<br /><br /> Określa jednostki dla `UpdateInterval` parametru. Ten parametr może mieć następujące wartości:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Ten parametr ma zastosowanie tylko jeśli wartości `Install` i `UpdateEnabled` parametry są zarówno `true`. |

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.GenerateManifestBase> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę parametrów klasy zadanie, zobacz [zadań klasy bazowej](../msbuild/task-base-class.md).

## <a name="see-also"></a>Zobacz także

- [Zadania](../msbuild/msbuild-tasks.md)
- [Generateapplicationmanifest — zadanie](../msbuild/generateapplicationmanifest-task.md)
- [Signfile — zadanie](../msbuild/signfile-task.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)