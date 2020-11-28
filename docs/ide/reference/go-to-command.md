---
title: Przejdź do — Polecenie
description: Dowiedz się więcej o poleceniu Przejdź do i sposobie przenoszenia kursora do określonego wiersza.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b0ef161cb8108ed3244c263ee51fee4251fc05d8
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305214"
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

## <a name="see-also"></a>Zobacz także

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
