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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed8ec8e7f990a4a2c5d943a15a105faa5ab23572
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589386"
---
# <a name="symbol-path-command"></a>Ścieżka symboli — Polecenie
Określa listę katalogów do wyszukiwania symboli w debugerze.

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

## <a name="see-also"></a>Zobacz także

- [Okno Polecenie](../../ide/reference/command-window.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
