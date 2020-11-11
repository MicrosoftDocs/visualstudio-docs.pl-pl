---
title: Komentarze do zadań
description: Dodawanie komentarzy do zadań do kodu
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 02eacb312931d941b716ee65f91cd478eac8bb8a
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493533"
---
# <a name="task-comments"></a>Komentarze do zadań

Podczas pisania kodu, jest to standardowe rozwiązanie, aby jawnie komentować nieukończony lub wątpliwy kod lub szybkie obejścia z ostrzeżeniami. Domyślne tokeny sygnałów zapewniane przez Visual Studio dla komputerów Mac są zadaniami, HAKERami, FIXME i COFNIĘTe. Spersonalizowane tokeny można definiować w obszarze **preferencje > programu Visual Studio > zadania > środowiska** , jak pokazano na poniższej ilustracji:

![Preferencje listy zadań](media/source-editor-image10.png)

Aby dodać nowy komentarz do zadania, Dodaj komentarz zawierający słowo kluczowe Task. Na przykład:

```csharp
//TODO: Finish this for all properties.
```

Visual Studio dla komputerów Mac rysuje uwagę na te znaczniki, zaznaczając je w oknie **Lista zadań** , które można wyświetlić za pomocą menu **Wyświetl zadania >** :

![Okno listy zadań zawierające pojedynczy element do wykonania](media/source-editor-image11.png)

## <a name="see-also"></a>Zobacz też

- [Korzystanie z Lista zadań (Visual Studio w systemie Windows)](/visualstudio/ide/using-the-task-list)