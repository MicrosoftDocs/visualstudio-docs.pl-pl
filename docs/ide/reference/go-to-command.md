---
title: Przejdź do — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82dd3f226931dfeca2fa0dfad38daa24684fb8da
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55947432"
---
# <a name="go-to-command"></a>Przejdź do — Polecenie
Przenosi kursor do określonego wiersza.

## <a name="syntax"></a>Składnia

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Argumenty
 `linenumber`

 Opcjonalna. Liczba całkowita reprezentująca numer wiersza, aby przejść do.

## <a name="remarks"></a>Uwagi
 Numerowanie wierszy rozpoczyna się od jednego. Jeśli wartość `linenumber` jest mniejsza niż jeden, pierwszy wyświetla wiersz. Jeśli wartość `linenumber` jest większa niż liczba ostatnim wierszu ostatniej wyświetla wiersz.

 Jeśli wartość `linenumber` nie zostanie określony, **przejdź do wiersza** Wyświetla okno dialogowe.

 Alias dla tego polecenia jest GoToLn.

## <a name="example"></a>Przykład

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)