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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23a7a59ca23dc444bcdc714ade2fce5bedb87e8c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55934228"
---
# <a name="symbol-path-command"></a>Ścieżka symboli — Polecenie
Określa listę katalogów do wyszukiwania symboli w debugerze.

## <a name="syntax"></a>Składnia

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Argumenty
 `pathname`

 Opcjonalna. Rozdzielana średnikami lista ścieżek dla debugera do wyszukiwania symboli.

## <a name="remarks"></a>Uwagi
 Jeśli nie `pathname` jest określony, polecenie wyświetla listę bieżących ścieżek symboli.

## <a name="example"></a>Przykład
 Ten przykład dodaje dwie ścieżki do listy katalogów symboli.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example"></a>Przykład
 Ten przykład wyświetla listą rozdzielaną średnikami dla bieżących ścieżek symboli.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Zobacz też

- [Okno Polecenie](../../ide/reference/command-window.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)