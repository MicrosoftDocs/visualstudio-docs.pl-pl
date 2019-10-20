---
title: Uruchom polecenie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a216e053a08662da5da04206c780fb4455e9ec09
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663491"
---
# <a name="start-command"></a>Uruchomienie — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Rozpoczyna debugowanie projektu startowego.

## <a name="syntax"></a>Składnia

```
Debug.Start [address]
```

## <a name="arguments"></a>Argumenty
 `address` opcjonalny. Adres, pod którym program wstrzymuje wykonywanie, podobnie jak punkt przerwania w kodzie źródłowym. Ten argument jest prawidłowy tylko w trybie debugowania.

## <a name="remarks"></a>Uwagi
 **Uruchomienie** polecenia, gdy wykonywane, wykonuje operację RunToCursor na określonym adresie.

## <a name="example"></a>Przykład
 Ten przykład uruchamia debuger i ignoruje wszelkie występujące wyjątki.

```
>Debug.Start
```

## <a name="see-also"></a>Zobacz też
 Polecenia [programu Visual Studio](../../ide/reference/visual-studio-commands.md) [okno](../../ide/reference/command-window.md) poleceń [Znajdź/polecenie](../../ide/find-command-box.md) [programu Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
