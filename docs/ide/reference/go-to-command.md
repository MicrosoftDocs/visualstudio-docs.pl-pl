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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 93ad14561b1fdd2aade1978831b784e014568a6c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668260"
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

Jeśli nie określono wartości dla `linenumber`, zostanie wyświetlone okno dialogowe **Przejdź do wiersza** .

Alias dla tego polecenia to GoToLn.

## <a name="example"></a>Przykład

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)