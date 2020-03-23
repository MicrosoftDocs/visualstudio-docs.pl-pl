---
title: GenerateDeploymentZarządzanie zadania | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634074"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest — zadanie

Generuje manifest wdrożenia ClickOnce. Manifest wdrożenia ClickOnce opisuje wdrożenie aplikacji, definiując unikatową tożsamość wdrożenia, identyfikując cechy wdrażania, takie jak instalacja lub tryb online, określając ustawienia aktualizacji aplikacji i lokalizacje aktualizacji oraz wskazując odpowiedni manifest aplikacji ClickOnce.

## <a name="parameters"></a>Parametry

W poniższej tabeli `GenerateDeploymentManifest` opisano parametry zadania.

| Parametr | Opis |
|--------------------------| - |
| `AssemblyName` | Parametr `String` opcjonalny.<br /><br /> Określa `Name` pole tożsamości zestawu dla wygenerowanego manifestu. Jeśli ten parametr nie jest określony, nazwa `EntryPoint` jest `InputManifest` wywnioskowana z lub parametrów. Jeśli nie można wywnioskować nazwy, zadanie zgłasza błąd. |
| `AssemblyVersion` | Parametr `String` opcjonalny.<br /><br /> Określa `Version` pole tożsamości zestawu dla wygenerowanego manifestu. Jeśli ten parametr nie jest określony, zadanie używa wartości "1.0.0.0". |
| `CreateDesktopShortcut` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli true, ikona jest tworzony na pulpicie podczas instalacji clickonce aplikacji. |
| `DeploymentUrl` | Parametr `String` opcjonalny.<br /><br /> Określa lokalizację aktualizacji dla aplikacji. Jeśli ten parametr nie jest określony, nie zdefiniowano lokalizacji aktualizacji dla aplikacji. Jeśli jednak `UpdateEnabled` parametr `true`jest , należy określić lokalizację aktualizacji. Określoną wartością powinien być w pełni kwalifikowany adres URL lub ścieżka UNC. |
| `Description` | Parametr `String` opcjonalny.<br /><br /> Określa opcjonalny opis aplikacji. |
| `DisallowUrlActivation` | Parametr `Boolean` opcjonalny.<br /><br /> Określa, czy aplikacja ma być uruchamiana automatycznie po otwarciu za pośrednictwem adresu URL. Jeśli ten `true`parametr jest , aplikacja może być uruchomiona tylko z menu **Start.** Domyślną wartością tego `false`parametru jest . To dane wejściowe `Install` mają zastosowanie `true`tylko wtedy, gdy wartość parametru jest . |
| `EntryPoint` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Wskazuje punkt wejścia dla wygenerowanego zestawu manifestu. W przypadku manifestu wdrażania ClickOnce to dane wejściowe określa manifest aplikacji ClickOnce.<br /><br />Jeśli `EntryPoint` parametr zadania nie jest `<customHostSpecified>` określony, znacznik jest wstawiany jako podrzędny `<entryPoint>` znacznik, na przykład:<br /><br /> `<entryPoint xmlns="urn:schemas-microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Zależności biblioteki DLL można dodać do manifestu aplikacji, wykonując następujące kroki:<br /><br /> 1. Rozwiąż odwołania do <xref:Microsoft.Build.Tasks.ResolveAssemblyReference>zestawu za pomocą wywołania .<br />2. Przekaż dane wyjściowe poprzedniego zadania <xref:Microsoft.Build.Tasks.ResolveManifestFiles>i samego zestawu do .<br />3. Przekaż zależności za `Dependencies` pomocą <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>parametru do . |
| `ErrorReportUrl` | Parametr <xref:System.String?displayProperty=fullName> opcjonalny.<br /><br /> Określa adres URL strony sieci Web, który jest wyświetlany w oknach dialogowych podczas instalacji ClickOnce. |
| `InputManifest` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny.<br /><br /> Wskazuje wejściowy dokument XML, który ma służyć jako podstawa generatora manifestów. Dzięki temu dane strukturalne, takie jak niestandardowe definicje manifestu, mają być odzwierciedlane w manifeście danych wyjściowych. Element główny w dokumencie XML musi być węzłem zestawu w obszarze nazw asmv1. |
| `Install` | Parametr `Boolean` opcjonalny.<br /><br /> Określa, czy aplikacja jest zainstalowaną aplikacją, czy aplikacją tylko online. Jeśli ten `true`parametr jest , aplikacja zostanie zainstalowana w menu **Start** użytkownika i może zostać usunięta za pomocą okna dialogowego **Dodawanie lub usuwanie programów.** Jeśli ten `false`parametr jest , aplikacja jest przeznaczona do użytku online ze strony internetowej. Domyślną wartością tego `true`parametru jest . |
| `MapFileExtensions` | Parametr `Boolean` opcjonalny.<br /><br /> Określa, czy jest używane mapowanie rozszerzenia nazw plików *. deploy.* Jeśli ten `true`parametr jest , każdy plik programu jest publikowany z rozszerzeniem nazwy pliku *.deploy.* Ta opcja jest przydatna w przypadku zabezpieczeń serwera sieci web, aby ograniczyć liczbę rozszerzeń nazw plików, które muszą zostać odblokowane, aby włączyć wdrażanie aplikacji ClickOnce. Domyślną wartością tego `false`parametru jest . |
| `MaxTargetPath` | Parametr `String` opcjonalny.<br /><br /> Określa maksymalną dozwoloną długość ścieżki pliku we wdrożeniu aplikacji ClickOnce. Jeśli ten parametr jest określony, długość każdej ścieżki pliku w aplikacji jest sprawdzana względem tego limitu. Wszystkie elementy, które przekraczają limit spowoduje ostrzeżenie kompilacji. Jeśli to dane wejściowe nie jest określony lub wynosi zero, nie jest wykonywane sprawdzanie. |
| `MinimumRequiredVersion` | Parametr `String` opcjonalny.<br /><br /> Określa, czy użytkownik może pominąć aktualizację. Jeśli użytkownik ma wersję, która jest mniejsza niż minimalna wymagana, nie będzie miał możliwości pominięcia aktualizacji. To dane wejściowe mają zastosowanie `Install` tylko `true`wtedy, gdy wartość parametru jest . |
| `OutputManifest` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny.<br /><br /> Określa nazwę wygenerowanego pliku manifestu wyjściowego. Jeśli ten parametr nie jest określony, nazwa pliku wyjściowego jest wywnioskowana z tożsamości wygenerowanego manifestu. |
| `Platform` | Parametr `String` opcjonalny.<br /><br /> Określa platformę docelową aplikacji. Ten parametr może mieć następujące wartości:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Wartością domyślną jest `AnyCPU`. |
| `Product` | Parametr `String` opcjonalny.<br /><br /> Określa nazwę aplikacji. Jeśli ten parametr nie jest określony, nazwa jest wywnioskowana z tożsamości wygenerowanego manifestu. Ta nazwa jest używana dla nazwy skrótu w menu **Start** i jest częścią nazwy wyświetlanej w oknie dialogowym **Dodawanie lub usuwanie programów.** |
| `Publisher` | Parametr `String` opcjonalny.<br /><br /> Określa wydawcę aplikacji. Jeśli ten parametr nie jest określony, nazwa jest wywnioskowana od zarejestrowanego użytkownika lub tożsamości wygenerowanego manifestu. Ta nazwa jest używana dla nazwy folderu w menu **Start** i jest częścią nazwy wyświetlanej w oknie dialogowym **Dodawanie lub usuwanie programów.** |
| `SuiteNamel` | Parametr `String` opcjonalny.<br /><br /> Określa nazwę folderu w menu **Start,** w którym znajduje się aplikacja po wdrożeniu ClickOnce. |
| `SupportUrl` | Parametr `String` opcjonalny.<br /><br /> Określa łącze wyświetlane w oknie dialogowym **Dodawanie lub usuwanie programów** dla aplikacji. Określoną wartością powinien być w pełni kwalifikowany adres URL lub ścieżka UNC. |
| `TargetCulture` | Parametr `String` opcjonalny.<br /><br /> Identyfikuje kulturę aplikacji i określa `Language` pole tożsamości zestawu dla wygenerowanego manifestu. Jeśli ten parametr nie jest określony, zakłada się, że aplikacja jest kultury niezmienne. |
| `TrustUrlParameters` | Parametr `Boolean` opcjonalny.<br /><br /> Określa, czy parametry zestawu url do zestawu zapytania mają być udostępniane aplikacji. Domyślną wartością tego `false`parametru jest , co oznacza, że parametry nie będą dostępne dla aplikacji. |
| `UpdateEnabled` | Parametr `Boolean` opcjonalny.<br /><br /> Wskazuje, czy aplikacja jest włączona dla aktualizacji. Domyślną wartością tego `false`parametru jest . Ten parametr ma zastosowanie tylko `Install` wtedy, `true`gdy wartość parametru jest . |
| `UpdateInterval` | Parametr `Int32` opcjonalny.<br /><br /> Określa interwał aktualizacji dla aplikacji. Domyślną wartością tego parametru jest zero. Ten parametr ma zastosowanie tylko `Install` wtedy, gdy wartości i `UpdateEnabled` parametry są zarówno `true`. |
| `UpdateMode` | Parametr `String` opcjonalny.<br /><br /> Określa, czy aktualizacje powinny być sprawdzane na pierwszym planie przed uruchomieniem aplikacji, czy w tle, gdy aplikacja jest uruchomiona. Ten parametr może mieć następujące wartości:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> Domyślną wartością tego `Background`parametru jest . Ten parametr ma zastosowanie tylko `Install` wtedy, gdy wartości i `UpdateEnabled` parametry są zarówno `true`. |
| `UpdateUnit` | Parametr `String` opcjonalny.<br /><br /> Określa jednostki dla `UpdateInterval` parametru. Ten parametr może mieć następujące wartości:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Ten parametr ma zastosowanie tylko `Install` wtedy, gdy wartości i `UpdateEnabled` parametry są zarówno `true`. |

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.GenerateManifestBase> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę parametrów klasy zadań, zobacz [Klasa podstawowa zadania](../msbuild/task-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Generowanie zadania Generowaniazarządzaj](../msbuild/generateapplicationmanifest-task.md)
- [SignFile zadanie](../msbuild/signfile-task.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
