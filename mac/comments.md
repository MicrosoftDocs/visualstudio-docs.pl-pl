---
title: Skomentuj kod
description: W tym artykule opisano używanie komentarzy w edytorze źródłowym programu Visual Studio dla komputerów Mac
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 2966d8b89a2609d3fbfc2b6b4561288433641ca1
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "67693111"
---
# <a name="comments"></a>Komentarze

Podczas debugowania lub eksperymentowania z kodem, może być przydatne do komentowania bloków kodu tymczasowo lub długoterminowe.

Aby skomentować cały blok kodu:

* Wybierz kod i wybierz polecenie **Przełącz komentarze do wiersza** z menu kontekstowego

LUB

* Użyj `cmd + /` powiązania klawiszy w wybranym kodzie.

Metody te mogą służyć do komentowania i dekomentowania sekcje kodu. W plikach Języka C# można dodać dodatkowe poziomy komentarzy wierszy, co umożliwia komentowanie i brak komentarza w regionach kodów, przy jednoczesnym zachowaniu rzeczywistych komentarzy:

![komentarze wielopoziomowe](media/source-editor-image8.png)

Komentarze są również przydatne do dokumentowania kodu dla przyszłych deweloperów, którzy mogą z nim współpracować. Są one zwykle wykonywane w formie komentarzy wielowierszowych, które są dodawane w następujący sposób w każdym języku:

**C #**

```csharp
/*
 This is a multi-line
 comment in C#
*/
```

**F #**

```fsharp
(*
 This is a multi-line
  comment in F#
*)
```

## <a name="see-also"></a>Zobacz też

- [Skomentuj kod (Visual Studio w systemie Windows)](/visualstudio/ide/quickstart-editor#comment-out-code)