---
title: Komentarze do zadań
description: Dodawanie zadań komentarzy w kodzie
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: d88b74ab953f97e061f4be3befc227646006f38b
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67692324"
---
# <a name="task-comments"></a>Komentarze do zadań

Podczas pisania kodu jest standardową praktyką, aby jawnie dodać komentarz niedokończone lub wątpliwe kodu lub szybkiego rozwiązania problemu z ostrzeżeniami. Tokeny sygnału domyślne, które są dostarczane przez program Visual Studio dla komputerów Mac to TODO, HACK, FIXME i UNDONE. Spersonalizowane tokenów można zdefiniować pod **programu Visual Studio > Preferencje > środowisko > zadania**, jak pokazano na poniższej ilustracji:

![Preferencje listy zadań](media/source-editor-image10.png)

Aby dodać nowy komentarz do zadania, należy dodać komentarz, który zawiera słowo kluczowe zadania. Na przykład:

```csharp
//TODO: Finish this for all properties.
```

Program Visual Studio for Mac koncentrują się na te znaczniki wyróżniając je w **listy zadań** konsoli, które można wyświetlić, przechodząc do **Widok > okienka > zadanie**:

![Konsola listy zadań](media/source-editor-image11.png)

## <a name="see-also"></a>Zobacz także

- [Korzystanie z listy zadań (Visual Studio Windows)](/visualstudio/ide/using-the-task-list)