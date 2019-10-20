---
title: Ścieżka symboli — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6309396877a32233bfe05fff1d2173d1f8765ebb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645201"
---
# <a name="symbol-path-command"></a>Ścieżka symboli — Polecenie
Ustawia listę katalogów dla debugera do wyszukiwania symboli.

## <a name="syntax"></a>Składnia

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Argumenty
`pathname`

Opcjonalny. Rozdzielana średnikami lista ścieżek dla debugera do wyszukiwania symboli.

## <a name="remarks"></a>Uwagi
Jeśli `pathname` nie zostanie określona, polecenie wyświetli bieżące ścieżki symboli.

## <a name="example"></a>Przykład
Ten przykład dodaje dwie ścieżki do listy katalogów symboli.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example"></a>Przykład
Ten przykład wyświetla listę rozdzielonych średnikami dla bieżących ścieżek symboli.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Zobacz też

- [Okno Polecenie](../../ide/reference/command-window.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)