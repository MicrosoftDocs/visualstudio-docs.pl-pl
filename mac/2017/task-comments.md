---
title: Komentarze do zadań
description: Dodawanie komentarzy do zadań do kodu
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 4f7f3d1567972c3841af6deb37677a7e01cdb825
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74985176"
---
# <a name="task-comments"></a>Komentarze do zadań

Podczas pisania kodu, jest to standardowe rozwiązanie, aby jawnie komentować nieukończony lub wątpliwy kod lub szybkie obejścia z ostrzeżeniami. Domyślne tokeny sygnałów zapewniane przez Visual Studio dla komputerów Mac są zadaniami, HAKERami, FIXME i COFNIĘTe. Spersonalizowane tokeny można definiować w obszarze **preferencje > programu Visual Studio > zadania > środowiska**, jak pokazano na poniższej ilustracji:

![Preferencje listy zadań](media/source-editor-image10.png)

Aby dodać nowy komentarz do zadania, Dodaj komentarz zawierający słowo kluczowe Task. Na przykład:

```csharp
//TODO: Finish this for all properties.
```

Visual Studio dla komputerów Mac rysuje uwagę na te znaczniki poprzez wyróżnianie ich w konsoli **Lista zadań** , które mogą być wyświetlane, przechodząc do **widoku > konsole > zadanie**:

![Konsola listy zadań](media/source-editor-image11.png)

## <a name="see-also"></a>Zobacz też

- [Korzystanie z Lista zadań (Visual Studio w systemie Windows)](/visualstudio/ide/using-the-task-list)