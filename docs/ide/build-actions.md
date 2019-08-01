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
ms.openlocfilehash: 061a3cce8d1d29b57c02de4506a809994bf12910
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416498"
---
# <a name="build-actions"></a>Akcje kompilacji

Wszystkie pliki w projekcie programu Visual Studio mają akcję kompilacji. Akcja kompilacji kontroluje, co się dzieje z plikiem podczas kompilowania projektu.

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Tworzenie akcji w Visual Studio dla komputerów Mac](/visualstudio/mac/build-actions).

## <a name="set-a-build-action"></a>Ustawianie akcji kompilacji

Aby ustawić akcję kompilacji dla pliku, Otwórz właściwości pliku w oknie **Właściwości** , wybierając plik w **Eksplorator rozwiązań** i naciśnij klawisz **Alt**+**Enter**. Lub kliknij prawym przyciskiem myszy plik w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**. W oknie **Właściwości** , w sekcji **Zaawansowane** , Użyj listy rozwijanej obok pozycji **Akcja kompilacji** , aby ustawić akcję kompilacji dla tego pliku.

![Akcje kompilacji dla pliku w programie Visual Studio](media/build-actions.png)

## <a name="build-action-values"></a>Wartości akcji kompilacji

Niektóre akcje kompilacji dla C# plików projektu i Visual Basic są następujące:

* **Brak** — plik nie jest częścią kompilacji w żaden sposób. Ta wartość może być używana dla plików dokumentacji, takich jak pliki Readme, na przykład.
* **Kompiluj** — plik jest przesyłany do kompilatora jako plik źródłowy.
* **Zawartość** — plik oznaczony jako **zawartość** może zostać pobrany jako strumień przez wywołanie <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType>. W przypadku projektów ASP.NET te pliki są uwzględniane jako część lokacji podczas jej wdrażania.
* **Zasób osadzony** — plik jest przesyłany do kompilatora jako zasób, który ma zostać osadzony w zestawie. Możesz wywołać <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> , aby odczytać plik z zestawu.
* **AdditionalFiles** — plik tekstowy nieźródłowy, który jest przesyłany do kompilatora C# lub Visual Basic jako dane wejściowe. Ta akcja kompilacji służy głównie do zapewnienia danych wejściowych [analizatorów](../code-quality/roslyn-analyzers-overview.md) , do których odwołuje się projekt w celu sprawdzenia jakości kodu. Aby uzyskać więcej informacji, zobacz [Używanie dodatkowych plików](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md).

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora języka C#](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Opcje kompilatora Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [Akcje kompilacji (Visual Studio dla komputerów Mac)](/visualstudio/mac/build-actions)