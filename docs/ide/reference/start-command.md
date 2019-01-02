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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f3e15e9bcea439e6e01ff3bb233622d119fa4b46
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53903933"
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