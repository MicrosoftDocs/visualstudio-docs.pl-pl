---
title: Tworzenie akcji dla plików
ms.date: 11/19/2018
ms.technology: vs-ide-compile
ms.topic: reference
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35136ac0b7b0104f1812df7a9bf8ba81f6907374
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301987"
---
# <a name="build-actions"></a>Akcje kompilacji

Wszystkie pliki w projekcie programu Visual Studio mają akcję kompilacji. Akcja kompilacji kontroluje, co dzieje się z plikiem podczas kompilowania projektu.

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. W przypadku programu Visual Studio dla komputerów Mac zobacz [Tworzenie akcji w programie Visual Studio dla komputerów Mac](/visualstudio/mac/build-actions).

## <a name="set-a-build-action"></a>Ustawianie akcji kompilacji

Aby ustawić akcję kompilacji dla pliku, otwórz właściwości pliku w oknie **Właściwości,** zaznaczając plik w **Eksploratorze rozwiązań** i naciskając klawisz **Alt**+**Enter**. Lub kliknij prawym przyciskiem myszy plik w **Eksploratorze rozwiązań** i wybierz polecenie **Właściwości**. W oknie Właściwości w sekcji **Zaawansowane** użyj listy rozwijanej obok pozycji **Akcja kompilacji,** aby ustawić akcję kompilacji dla pliku. **Properties**

![Akcje kompilacji dla pliku w programie Visual Studio](media/build-actions.png)

## <a name="build-action-values"></a>Tworzenie wartości akcji

Oto niektóre z bardziej typowych akcji kompilacji dla plików projektu Języka C# i Visual Basic:

|Akcja kompilacji | Typy projektów | Opis |
|-|-|
| **AdditionalFiles (Pliki dodatkowe)** | C#, Visual Basic | Nieskładkowy plik tekstowy, który jest przekazywany do kompilatora języka C# lub Visual Basic jako dane wejściowe. Ta akcja kompilacji jest używana głównie do dostarczania danych wejściowych do [analizatorów,](../code-quality/roslyn-analyzers-overview.md) do których odwołuje się projekt w celu zweryfikowania jakości kodu. Aby uzyskać więcej informacji, zobacz [Używanie dodatkowych plików](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md).|
| **Definicja aplikacji** | WPF | Plik definiujący aplikację. Przy pierwszym utworzeniu projektu jest to *app.xaml*. |
| **KodAnalysisDictionary** | .NET | Niestandardowy słownik wyrazów używany przez analizę kodu do sprawdzania pisowni. Zobacz [jak: Dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)|
| **Skompilować** | Wszelki | Plik jest przekazywany do kompilatora jako plik źródłowy.|
| **Zawartość** | .NET | Plik oznaczony jako **Zawartość** można pobrać jako <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType>strumień, wywołując . W przypadku projektów ASP.NET pliki te są uwzględniane jako część witryny po wdrożeniu.|
| **DesignData ( DesignData )** | WPF | Używane dla plików XAML ViewModel, aby umożliwić formanty użytkownika, które mają być wyświetlane w czasie projektowania, z fikcyjnych typów i przykładowych danych. |
| **DesignDataWithDesignTimeTworzyć** | WPF | Podobnie jak **DesignData**, ale z rzeczywistymi typami.  |
| **Zasób osadzony** | .NET | Plik jest przekazywany do kompilatora jako zasób, który ma być osadzony w zestawie. Można wywołać, <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> aby odczytać plik z zestawu.|
| **EntityDeploy (** | .NET | Dla entity framework (EF) .edmx plików, które określają wdrażanie artefaktów EF. |
| **Podróbki** | .NET | Używane dla platformy testowania microsoft fakes. Zobacz [Izolowanie kodu w trakcie testu przy użyciu microsoft fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) |
| **Brak** | Wszelki | Plik nie jest częścią kompilacji w żaden sposób. Ta wartość może służyć do plików dokumentacji, takich jak "ReadMe" plików, na przykład.|
| **Strona** | WPF | Skompiluj plik XAML do binarnego pliku .baml, aby przyspieszyć ładowanie w czasie wykonywania. |
| **Zasób** | WPF | Określa osadzanie pliku w pliku zasobu manifestu zestawu z rozszerzeniem *.g.resources*. |
| **W tle** | .NET | Używany dla pliku .akcesora, który zawiera listę wbudowanych nazwy plików zestawu, po jednym w wierszu. Dla każdego zestawu na liście wygeneruj klasy publiczne o nazwach, `ClassName_Accessor` które są podobne do oryginałów, ale za pomocą metod publicznych zamiast metod prywatnych. Służy do testowania jednostkowego. |
| **Ekran powitalny** | WPF | Określa plik obrazu, który ma być wyświetlany w czasie wykonywania podczas uruchamiania aplikacji. |
| **XamlAppDef (ekw.** | Windows Workflow Foundation | Nakazuje kompilacji tworzenie pliku XAML przepływu pracy do zestawu z osadzonym przepływem pracy. |

> [!NOTE]
> Dodatkowe akcje kompilacji mogą być definiowane przez dla określonych typów projektów, więc lista akcji kompilacji zależy od typu projektu i wartości mogą pojawić się, które nie znajdują się na tej liście.

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora C#](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Opcje kompilatora języka Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [Akcje kompilacji (Visual Studio dla komputerów Mac)](/visualstudio/mac/build-actions)
