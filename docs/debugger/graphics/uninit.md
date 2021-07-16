---
title: UnInit | Microsoft Docs
description: Użyj metody UnInit() polecenia VsgDbg, aby sfinalizować i zamknąć plik dziennika grafiki oraz zasoby rejestrowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6bb87d210512a3f914384adb99d81695340b1ed5
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232482"
---
# <a name="uninit"></a>UnInit
Finalizuje plik dziennika grafiki, zamyka go i zamyka zasoby, które były używane podczas aktywnego rejestrowania informacji graficznych przez aplikację.

## <a name="syntax"></a>Składnia

```C++
void UnInit();
```

## <a name="remarks"></a>Uwagi
 `UnInit` jest wywoływana automatycznie, gdy wystąpienie `VsgDbg` klasy zostanie zniszczona. Jeśli wystąpienie `VsgDbg` nie było aktywnie rejestrowania informacji graficznych, nie ma to żadnego efektu.

 Po wywołaniu klasy w wystąpieniu klasy można utworzyć nowy plik dziennika grafiki przez wywołanie i sfinalizować przez `UnInit` `VsgDbg` wywołanie funkcji `Init` `UnInit` . Możesz powtarzać tę czynność tyle razy, ile chcesz użyć tego samego wystąpienia do utworzenia `VsgDbg` kilku niezależnych plików dziennika grafiki.

## <a name="see-also"></a>Zobacz też
- [Init](init.md)