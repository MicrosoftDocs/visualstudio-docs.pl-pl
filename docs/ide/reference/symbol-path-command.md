---
title: Ścieżka symboli — Polecenie
description: Dowiedz się więcej o ścieżce symboli polecenia i sposobie ustawiania listy katalogów dla debugera, aby wyszukać symbole.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 72e69300e9dc621ea346c05923168c33bc7065c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967166"
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
Jeśli wartość nie `pathname` jest określona, polecenie wyświetla listę bieżących ścieżek symboli.

## <a name="example-1"></a>Przykład 1
Ten przykład dodaje dwie ścieżki do listy katalogów symboli.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example-2"></a>Przykład 2
Ten przykład wyświetla listę rozdzielonych średnikami dla bieżących ścieżek symboli.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Zobacz też

- [Okno polecenia](../../ide/reference/command-window.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
