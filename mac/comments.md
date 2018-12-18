---
title: Komentarz do kodu
description: W tym artykule opisano, za pomocą komentarzy w edytorze źródła programu Visual Studio dla komputerów Mac
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 1f792e5ba670854e4a3a9ce703212d18c16e5512
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295660"
---
# <a name="comments"></a>Komentarze

W przypadku debugowania lub eksperymentowania z kodem, może być przydatne dodać komentarz bloki kodu albo tymczasowo lub długoterminowych.

Aby przekształcić w komentarz cały blok kodu:

* Wybierz numer kierunkowy, a następnie wybierz pozycję **Przełącz komentarze do wierszy** z menu kontekstowego

LUB

* Użyj `cmd + /` powiązanie klawiszy w zaznaczonym kodzie.

Metody te można dodać komentarz, a następnie usuń komentarz z fragmentów kodu. Pliki C# dodatkowe poziomy wiersz komentarze może być dodana, co pozwala regionów kodów się nadal przy zachowaniu komentarze rzeczywiste komentarzem i pozbawionym znaków komentarza wierszu, podczas:

![Wielopoziomowe komentarze](media/source-editor-image8.png)

Komentarze są także przydatne do dokumentowania kodu przez przyszłych programistów, które mogą korzystać z niego. Są one zazwyczaj wykonywane w formie wielowierszowe komentarze, które są dodawane w następujący sposób w każdym języku:

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

- [Komentarz do kodu (Visual Studio Windows)](/visualstudio/ide/quickstart-editor#comment-out-code)