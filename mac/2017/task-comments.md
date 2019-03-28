---
title: Komentarze do zadania
description: Dodawanie zadań komentarzy w kodzie
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 3caef73ba46afd8eaf90826540248cb2d5c4efef
ms.sourcegitcommit: da73f7a0cf1795d5d400c0897ae3326191435dd0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58572902"
---
# <a name="task-comments"></a>Komentarze do zadania

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