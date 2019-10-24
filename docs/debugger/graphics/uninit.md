---
title: Odinicjuj inicjowanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef809b646a0af58e46b8c68dc5a8cf7633692bcc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734819"
---
# <a name="uninit"></a>UnInit
Kończy plik dziennika grafiki, zamyka go i zwalnia zasoby, które były używane podczas aktywnie rejestrowania informacji graficznych przez aplikację.

## <a name="syntax"></a>Składnia

```C++
void UnInit();
```

## <a name="remarks"></a>Uwagi
 `UnInit` jest wywoływana automatycznie, gdy wystąpienie klasy `VsgDbg` jest niszczone. Jeśli wystąpienie `VsgDbg` nie było aktywnie rejestrować informacji graficznych, nie ma to żadnego efektu.

 Po wywołaniu `UnInit` na wystąpieniu klasy `VsgDbg` można utworzyć nowy plik dziennika grafiki, wywołując `Init` i finaljąc wywołując `UnInit`. Możesz powtórzyć tyle razy, ile chcesz użyć tego samego wystąpienia `VsgDbg`, aby utworzyć kilka niezależnych plików dziennika grafiki.

## <a name="see-also"></a>Zobacz także
- [Init](init.md)