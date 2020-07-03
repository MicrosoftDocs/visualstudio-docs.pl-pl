---
title: Dodawanie komentarza do kodu
description: W tym artykule opisano używanie komentarzy w edytorze źródła Visual Studio dla komputerów Mac
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.topic: how-to
ms.openlocfilehash: a0aa3de91f1a2c75d73409d89f3cbc8894faacab
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939119"
---
# <a name="comments"></a>Komentarze

Podczas debugowania lub eksperymentowania z kodem może być przydatne Dodawanie komentarzy do bloków kodu jako czasowo lub długoterminowe.

Aby skomentować cały blok kodu:

* Zaznacz kod i wybierz pozycję **Przełącz Komentarze do wierszy** z menu kontekstowego.

LUB

* Użyj `cmd + /` powiązanie klawiszy na wybranym kodzie.

Te metody mogą służyć do komentowania i usuwania komentarzy do sekcji kodu. W plikach języka C# można dodawać dodatkowe poziomy komentarzy do wierszy, które umożliwiają regiony kodów do komentowania i usuwania komentarzy, zachowując jednocześnie rzeczywiste Komentarze:

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

## <a name="see-also"></a>Zobacz też

- [Dodawanie komentarza do kodu (Visual Studio w systemie Windows)](/visualstudio/ide/quickstart-editor#comment-out-code)