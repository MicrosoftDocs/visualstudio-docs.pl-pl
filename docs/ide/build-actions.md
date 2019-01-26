---
title: Tworzenie akcji w przypadku plików
ms.date: 11/19/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45a0e4822bc9b6d20bd2cf63d664e6cba97c77bf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951303"
---
# <a name="build-actions"></a>Akcje kompilacji

Wszystkie pliki w projekcie programu Visual Studio mają akcji kompilacji. Akcja kompilacji Określa, co się dzieje z pliku, gdy projekt jest skompilowany.

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [tworzenia akcji w programie Visual Studio dla komputerów Mac](/visualstudio/mac/build-actions).

## <a name="set-a-build-action"></a>Ustaw akcję kompilacji

Aby ustawić akcji kompilacji dla pliku, otwórz właściwości pliku w **właściwości** okna, wybierając go w **Eksploratora rozwiązań** i naciskając klawisz **Alt** + **Wprowadź**. Lub kliknij prawym przyciskiem myszy plik w **Eksploratora rozwiązań** i wybierz polecenie **właściwości**. W **właściwości** okna, w obszarze **zaawansowane** sekcji, użyj listy rozwijanej obok **Build Action** można ustawić akcji kompilacji dla pliku.

![Tworzenie akcji w przypadku plików w programie Visual Studio](media/build-actions.png)

## <a name="build-action-values"></a>Wartości akcji kompilacji

Niektóre akcje kompilacji w przypadku C# i pliki projektu w języku Visual Basic:

* **Brak** — plik nie jest częścią kompilacji w dowolny sposób. Ta wartość umożliwia pliki dokumentacji, takie jak pliki "ReadMe", na przykład.
* **Skompilować** — plik jest przekazywany do kompilatora jako plik źródłowy.
* **Zawartość** — plik jest oznaczony jako **zawartości** jako strumień może być pobierany przez wywołanie <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType>. Dla projektów ASP.NET te pliki są zawarte w ramach lokacji, gdy aplikacja jest wdrożona.
* **Osadzony zasób** — plik jest przekazywany do kompilatora jako zasób do osadzenia w zestawie. Możesz wywołać <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> można odczytać pliku z zestawu.
* **AdditionalFiles** — plik tekstowy-source, który jest przekazywany do C# lub kompilator Visual Basic jako dane wejściowe. Ta akcja kompilacji jest głównie używane w celu zapewnienia danych wejściowych [analizatory](../code-quality/roslyn-analyzers-overview.md) która odwołuje się projekt, aby sprawdzić jakość kodu. Aby uzyskać więcej informacji, zobacz [Używanie dodatkowych plików](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md).

## <a name="see-also"></a>Zobacz także

- [C#Opcje kompilatora](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Opcje kompilatora Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [Tworzenie akcji (Visual Studio dla komputerów Mac)](/visualstudio/mac/build-actions)