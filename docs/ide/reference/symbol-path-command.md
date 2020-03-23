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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589386"
---
# <a name="symbol-path-command"></a>Ścieżka symboli — Polecenie
Ustawia listę katalogów debugera do wyszukiwania symboli.

## <a name="syntax"></a>Składnia

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Argumenty
`pathname`

Element opcjonalny. Średnik rozdzielona lista ścieżek debugera do wyszukiwania symboli.

## <a name="remarks"></a>Uwagi
Jeśli `pathname` nie zostanie określony, polecenie wyświetla bieżące ścieżki symboli.

## <a name="example"></a>Przykład
W tym przykładzie dodaje dwie ścieżki do listy katalogów symboli.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example"></a>Przykład
W tym przykładzie jest wyświetlana lista rozdzielanych średników bieżących ścieżek symboli.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Zobacz też

- [Okno polecenia](../../ide/reference/command-window.md)
- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
