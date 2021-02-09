---
title: 'Instrukcje: Wyświetlanie listy elementów rozdzielanych przecinkami | Microsoft Docs'
description: Dowiedz się, jak za pomocą programu MSBuild wyświetlić listę elementów rozdzieloną przecinkami lub określić inne ciągi separatorów dla listy elementów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3ac0295b2d6f4300fa29c893d61616977ad44b87
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914411"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Instrukcje: Wyświetlanie listy elementów rozdzielanych przecinkami

Podczas pracy z listami elementów w Microsoft Build Engine (MSBuild), czasami warto wyświetlić zawartość tych list elementów w sposób łatwy do odczytania. Można też mieć zadanie, które pobiera listę elementów oddzielonych od specjalnego ciągu separatora. W obu tych przypadkach można określić ciąg separatora dla listy elementów.

## <a name="separate-items-in-a-list-with-commas"></a>Oddziel elementy na liście przecinkami

Domyślnie program MSBuild używa średników do rozdzielania elementów na liście. Rozważmy na przykład `Message` element o następującej wartości:

`<Message Text="This is my list of TXT files: @(TXTFile)"/>`

Gdy `@(TXTFile)` Lista elementów zawiera elementy *App1.txt*, *App2.txt* i *App3.txt*, komunikat jest:

`This is my list of TXT files: App1.txt;App2.txt;App3.txt`

Jeśli chcesz zmienić zachowanie domyślne, możesz określić własny separator. Składnia określająca separator listy elementów:

`@(ItemListName, '<separator>')`

Separator może być pojedynczym znakiem lub ciągiem i musi być ujęty w cudzysłów pojedynczy.

#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Aby wstawić przecinek i spację między elementami

- Użyj notacji elementu podobnego do poniższego:

    `@(TXTFile, ', ')`

## <a name="example"></a>Przykład

W tym przykładzie zadanie [exec](../msbuild/exec-task.md) uruchamia narzędzie findstr, aby znaleźć określone ciągi tekstowe w pliku, *Phrases.txt*. W poleceniu findstr ciągi wyszukiwania literału są wskazywane przez przełącznik **-c:** , więc separator elementu `-c:` jest wstawiany między elementami na `@(Phrase)` liście elementów.

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

## <a name="see-also"></a>Zobacz też

- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Elementy](../msbuild/msbuild-items.md)
