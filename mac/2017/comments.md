---
title: Komentarz do kodu
description: W tym artykule opisano używanie komentarzy w edytorze źródła Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 038c2bf7205ccc642d613893635b9323afe613b9
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74982644"
---
# <a name="comments"></a>Komentarze

Podczas debugowania lub eksperymentowania z kodem może być przydatne Dodawanie komentarzy do bloków kodu jako czasowo lub długoterminowe.

Aby skomentować cały blok kodu:

* Zaznacz kod i wybierz pozycję **Przełącz Komentarze do wierszy** z menu kontekstowego.

LUB

* Użyj `cmd + /` powiązanie klawiszy na wybranym kodzie.

Te metody mogą służyć do komentowania i usuwania komentarzy do sekcji kodu. W C# plikach można dodawać dodatkowe poziomy komentarzy do wierszy, które umożliwiają stosowanie komentarzy do regionów kodów i Dodawanie komentarzy do nich, zachowując jednocześnie rzeczywiste Komentarze:

![Komentarze na poziomie kilku](media/source-editor-image8.png)

Komentarze są również przydatne do dokumentowania kodu dla przyszłych deweloperów, które mogą z nich korzystać. Są one zazwyczaj wykonywane w formie komentarzy wielowierszowych, które są dodawane w następujący sposób w każdym języku:

**C#**

```csharp
/*
 This is a multi-line
 comment in C#
*/
```

**F#**

```fsharp
(*
 This is a multi-line
  comment in F#
*)
```

## <a name="see-also"></a>Zobacz także

- [Dodawanie komentarza do kodu (Visual Studio w systemie Windows)](/visualstudio/ide/quickstart-editor#comment-out-code)