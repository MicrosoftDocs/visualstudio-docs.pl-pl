---
title: 'Instrukcje: Wyświetlanie listy elementów rozdzielanych przecinkami | Microsoft Docs'
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
ms.openlocfilehash: 677278d08e3223f759afc64692481311bfba3356
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596336"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Instrukcje: Wyświetlanie listy elementów rozdzielanych przecinkami
Podczas pracy z listami elementów w [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]), czasami warto wyświetlić zawartość tych list elementów w sposób łatwy do odczytania. Można też mieć zadanie, które pobiera listę elementów oddzielonych od specjalnego ciągu separatora. W obu tych przypadkach można określić ciąg separatora dla listy elementów.

## <a name="separate-items-in-a-list-with-commas"></a>Oddziel elementy na liście przecinkami
Domyślnie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] używa średników do rozdzielania elementów na liście. Rozważmy na przykład element `Message` z następującą wartością:

`<Message Text="This is my list of TXT files: @(TXTFile)"/>`

Gdy lista elementów `@(TXTFile)` zawiera elementy *APP1. txt*, *APP2. txt*i *APP3. txt*, komunikat jest:

`This is my list of TXT files: App1.txt;App2.txt;App3.txt`

Jeśli chcesz zmienić zachowanie domyślne, możesz określić własny separator. Składnia określająca separator listy elementów:

`@(ItemListName, '<separator>')`

Separator może być pojedynczym znakiem lub ciągiem i musi być ujęty w cudzysłów pojedynczy.

#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Aby wstawić przecinek i spację między elementami

- Użyj notacji elementu podobnego do poniższego:

    `@(TXTFile, ', ')`

## <a name="example"></a>Przykład
W tym przykładzie zadanie [exec](../msbuild/exec-task.md) uruchamia narzędzie findstr, aby znaleźć określone ciągi tekstowe w pliku, retexts *. txt*. W poleceniu findstr ciągi wyszukiwania literału są wskazywane przez przełącznik **-c:** , więc separator elementu `-c:` jest wstawiany między elementami na liście `@(Phrase)` elementów.

W tym przykładzie równoważne polecenie wiersza polecenia to:

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

## <a name="see-also"></a>Zobacz także
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Elementy](../msbuild/msbuild-items.md)
