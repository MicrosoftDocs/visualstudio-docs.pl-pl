---
title: Uruchomienie — Polecenie
ms.date: 11/04/2016
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
ms.openlocfilehash: 1f7488353cd4c64b0afca27060c364a1f9ddc6f8
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55912573"
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