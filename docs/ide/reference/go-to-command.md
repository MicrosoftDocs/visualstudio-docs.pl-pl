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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 535906d8b8d7f8ba0c2984d22ceead18a0d47c2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75569208"
---
# <a name="go-to-command"></a>Przejdź do — Polecenie
Przenosi kursor do określonego wiersza.

## <a name="syntax"></a>Składnia

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Argumenty
`linenumber`\
Opcjonalny. Liczba całkowita reprezentująca liczbę wierszy, które mają zostać przechodzenie.

## <a name="remarks"></a>Uwagi
Numerowanie wierszy rozpoczyna się od jednej. Jeśli wartość `linenumber` jest mniejsza od 1, zostanie wyświetlona pierwsza linia. Jeśli wartość `linenumber` jest większa niż liczba ostatniego wiersza, zostanie wyświetlony ostatni wiersz.

Jeśli wartość `linenumber` nie jest określona, zostanie wyświetlone okno dialogowe **Przejdź do wiersza** .

Alias dla tego polecenia to GoToLn.

## <a name="example"></a>Przykład

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
