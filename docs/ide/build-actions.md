---
title: Akcje kompilacji dla plików
ms.date: 11/19/2018
ms.technology: vs-ide-compile
ms.topic: reference
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35136ac0b7b0104f1812df7a9bf8ba81f6907374
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315112"
---
# <a name="build-actions"></a>Akcje kompilacji

Wszystkie pliki w projekcie programu Visual Studio mają akcję kompilacji. Akcja kompilacji kontroluje, co się dzieje z plikiem podczas kompilowania projektu.

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Tworzenie akcji w Visual Studio dla komputerów Mac](/visualstudio/mac/build-actions).

## <a name="set-a-build-action"></a>Ustawianie akcji kompilacji

Aby ustawić akcję kompilacji dla pliku, Otwórz właściwości pliku w oknie **Właściwości** , wybierając plik w **Eksplorator rozwiązań** i naciśnij klawisz **Alt** + **Enter**. Lub kliknij prawym przyciskiem myszy plik w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**. W oknie **Właściwości** , w sekcji **Zaawansowane** , Użyj listy rozwijanej obok pozycji **Akcja kompilacji** , aby ustawić akcję kompilacji dla tego pliku.

![Akcje kompilacji dla pliku w programie Visual Studio](media/build-actions.png)

## <a name="build-action-values"></a>Wartości akcji kompilacji

Niektóre z bardziej typowych akcji kompilacji dla plików projektu C# i Visual Basic są następujące:

|Akcja kompilacji | Typy projektów | Opis |
|-|-|
| **AdditionalFiles** | C#, Visual Basic | Plik tekstowy nieźródłowy, który jest przesyłany do kompilatora C# lub Visual Basic jako dane wejściowe. Ta akcja kompilacji służy głównie do zapewnienia danych wejściowych [analizatorów](../code-quality/roslyn-analyzers-overview.md) , do których odwołuje się projekt w celu sprawdzenia jakości kodu. Aby uzyskać więcej informacji, zobacz [Używanie dodatkowych plików](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md).|
| **ApplicationDefinition** | WPF | Plik, który definiuje aplikację. Podczas pierwszego tworzenia projektu jest to *App. XAML*. |
| **CodeAnalysisDictionary** | .NET | Niestandardowy słownik słów używany przez analizę kodu do sprawdzania pisowni. Zobacz [jak: Dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)|
| **Opracowania** | dowolny | Plik jest przesyłany do kompilatora jako plik źródłowy.|
| **Zawartość** | .NET | Plik oznaczony jako **zawartość** może zostać pobrany jako strumień przez wywołanie <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType> . W przypadku projektów ASP.NET te pliki są uwzględniane jako część lokacji podczas jej wdrażania.|
| **DesignData** | WPF | Używane dla plików ViewModel języka XAML, aby umożliwić wyświetlanie kontrolek użytkownika w czasie projektowania przy użyciu fikcyjnych typów i przykładowych danych. |
| **DesignDataWithDesignTimeCreateable** | WPF | Podobnie jak **DesignData**, ale z rzeczywistymi typami.  |
| **Zasób osadzony** | .NET | Plik jest przesyłany do kompilatora jako zasób, który ma zostać osadzony w zestawie. Możesz wywołać, <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> Aby odczytać plik z zestawu.|
| **EntityDeploy** | .NET | W przypadku plików Entity Framework (EF). edmx, które określają wdrożenie artefaktów EF. |
| **Fakes** | .NET | Używane dla środowiska testowania sztucznej firmy Microsoft. Zobacz [Izolowanie testowanego kodu za pomocą](../test/isolating-code-under-test-with-microsoft-fakes.md) elementów sztucznych firmy Microsoft |
| **Brak** | dowolny | Plik nie jest częścią kompilacji w żaden sposób. Ta wartość może być używana dla plików dokumentacji, takich jak pliki Readme, na przykład.|
| **Strona** | WPF | Kompiluj plik XAML do pliku typu binary. BAML w celu przyspieszenia ładowania w czasie wykonywania. |
| **Zasób** | WPF | Określa, aby osadzić plik w pliku zasobów manifestu zestawu z rozszerzeniem *. g. resources*. |
| **W tle** | .NET | Używane dla pliku. akcesora, który zawiera listę skompilowanych nazw plików zestawu, po jednym w każdym wierszu. Dla każdego zestawu na liście Generuj klasy publiczne z nazwami, `ClassName_Accessor` które są podobnie jak oryginały, ale z metodami publicznymi, a nie metodami prywatnymi. Używany do testowania jednostkowego. |
| **Ekran powitalny** | WPF | Określa plik obrazu, który będzie wyświetlany w czasie wykonywania podczas uruchamiania aplikacji. |
| **XamlAppDef** | Windows Workflow Foundation | Instruuje kompilację, aby kompilować plik XAML przepływu pracy w zestawie z osadzonym przepływem pracy. |

> [!NOTE]
> Dodatkowe akcje kompilacji mogą być definiowane przez dla określonych typów projektów, więc lista akcji kompilacji zależy od typu projektu i wartości, które nie znajdują się na liście.

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora C#](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Opcje kompilatora Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [Akcje kompilacji (Visual Studio dla komputerów Mac)](/visualstudio/mac/build-actions)
