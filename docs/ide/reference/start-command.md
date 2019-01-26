---
title: Uruchomienie — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0307bc8fef348aa408bf6d4fad53759df61806fb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962826"
---
# <a name="start-command"></a>Uruchomienie — Polecenie
Rozpoczyna się debugowanie projektu startowego.

## <a name="syntax"></a>Składnia

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>Argumenty
 `address`

 Opcjonalna. Adres, w którym program zawiesza wykonywanie, podobnie jak punkt przerwania w kodzie źródłowym. Ten argument jest prawidłowy tylko w trybie debugowania.

## <a name="remarks"></a>Uwagi
 **Start** polecenia po wykonaniu wykonuje operację RunToCursor do określonego adresu.

## <a name="example"></a>Przykład
 W tym przykładzie Uruchamia debuger i ignoruje wszelkie wyjątki, które występują.

```cmd
>Debug.Start
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)