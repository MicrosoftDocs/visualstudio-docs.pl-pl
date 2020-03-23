---
title: 'Jak: Wyświetlanie listy przedmiotów oddzielonych przecinkami | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5493d3b95f7e9c0aa08ed3b06a99108e15697349
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633905"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Jak: Wyświetlanie listy elementów oddzielonych przecinkami

Podczas pracy z listami elementów w programie Microsoft Build Engine (MSBuild), czasami jest przydatne do wyświetlania zawartości tych list elementów w sposób, który jest łatwy do odczytania. Lub może mieć zadanie, które zajmuje listę elementów oddzielonych specjalnym ciągiem separatora. W obu tych przypadkach można określić ciąg separatora dla listy elementów.

## <a name="separate-items-in-a-list-with-commas"></a>Oddzielanie elementów na liście przecinkami

Domyślnie MSBuild używa średników do oddzielania elementów na liście. Rozważmy na `Message` przykład element o następującej wartości:

`<Message Text="This is my list of TXT files: @(TXTFile)"/>`

Gdy `@(TXTFile)` lista elementów zawiera elementy *App1.txt*, *App2.txt*i *App3.txt,* wiadomość jest:

`This is my list of TXT files: App1.txt;App2.txt;App3.txt`

Jeśli chcesz zmienić zachowanie domyślne, możesz określić własny separator. Składnia określania separatora listy elementów jest:

`@(ItemListName, '<separator>')`

Separator może być pojedynczy znak lub ciąg i muszą być ujęte w pojedynczych cudzysłowów.

#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Aby wstawić przecinek i odstęp między elementami

- Użyj notacji elementu podobnej do następującej:

    `@(TXTFile, ', ')`

## <a name="example"></a>Przykład

W tym przykładzie zadanie [Exec](../msbuild/exec-task.md) uruchamia narzędzie findstr, aby znaleźć określone ciągi tekstowe w pliku *Phrases.txt*. W findstr polecenia dosłowne ciągi wyszukiwania są wskazywane przez **-c:** switch, więc separator elementu jest `-c:` wstawiany między elementami na `@(Phrase)` liście elementów.

W tym przykładzie równoważne polecenie wiersza polecenia jest następujące:

`findstr /i /c:hello /c:world /c:msbuild phrases.txt`

```xml
<Project DefaultTargets = "Find"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <ItemGroup>
        <Phrase Include="hello"/>
        <Phrase Include="world"/>
        <Phrase Include="msbuild"/>
    </ItemGroup>

    <Target Name = "Find">
        <!-- Find some strings in a file -->
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
- [Items](../msbuild/msbuild-items.md)
