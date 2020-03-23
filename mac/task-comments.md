---
title: Komentarze do zadań
description: Dodawanie komentarzy zadań do kodu
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: d88b74ab953f97e061f4be3befc227646006f38b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "67692324"
---
# <a name="task-comments"></a>Komentarze do zadań

Podczas pisania kodu jest standardową praktyką jawnie komentować niedokończony lub wątpliwy kod lub szybkie obejścia z ostrzeżeniami. Domyślne tokeny sygnału dostarczone przez program Visual Studio dla komputerów Mac to TODO, HACK, FIXME i UNDONE. Spersonalizowane tokeny można zdefiniować w obszarze **Preferencje > programu Visual Studio > środowiska > zadania**, jak pokazano na poniższej ilustracji:

![Preferencje listy zadań](media/source-editor-image10.png)

Aby dodać nowy komentarz do zadania, dodaj komentarz zawierający słowo kluczowe zadania. Przykład:

```csharp
//TODO: Finish this for all properties.
```

Program Visual Studio dla komputerów Mac zwraca uwagę na te znaczniki, podświetlając je w konsoli **Lista zadań,** która może być wyświetlana, przechodząc do **view > Pads > Task:**

![Klawiatura listy zadań](media/source-editor-image11.png)

## <a name="see-also"></a>Zobacz też

- [Korzystanie z listy zadań (visual studio w systemie Windows)](/visualstudio/ide/using-the-task-list)