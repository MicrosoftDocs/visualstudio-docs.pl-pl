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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 946c4e39b48d15352ef5fa8ae240fb3fe9da5b9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645235"
---
# <a name="start-command"></a>Uruchomienie — Polecenie
Rozpoczyna debugowanie projektu startowego.

## <a name="syntax"></a>Składnia

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>Argumenty
`address`

Opcjonalny. Adres, pod którym program wstrzymuje wykonywanie, podobnie jak punkt przerwania w kodzie źródłowym. Ten argument jest prawidłowy tylko w trybie debugowania.

## <a name="remarks"></a>Uwagi
**Uruchomienie** polecenia, gdy wykonywane, wykonuje operację RunToCursor na określonym adresie.

## <a name="example"></a>Przykład
Ten przykład uruchamia debuger i ignoruje wszelkie występujące wyjątki.

```cmd
>Debug.Start
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)