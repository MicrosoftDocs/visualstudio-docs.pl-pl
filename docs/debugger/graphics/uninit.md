---
title: Odinicjuj inicjowanie | Microsoft Docs
description: Użyj metody UnInit () elementu VsgDbg, aby sfinalizować i zamknąć plik dziennika grafiki i zwolnić zasoby rejestrowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f79b39ced4f3285815412b9b231692868e5e00f
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996061"
---
# <a name="uninit"></a>UnInit
Kończy plik dziennika grafiki, zamyka go i zwalnia zasoby, które były używane podczas aktywnie rejestrowania informacji graficznych przez aplikację.

## <a name="syntax"></a>Składnia

```C++
void UnInit();
```

## <a name="remarks"></a>Uwagi
 `UnInit` jest wywoływana automatycznie, gdy wystąpienie `VsgDbg` klasy zostanie zniszczone. Jeśli `VsgDbg` wystąpienie nie było aktywnie rejestrować informacji graficznych, nie ma to wpływu.

 Po `UnInit` wywołaniu w wystąpieniu `VsgDbg` klasy nowy plik dziennika grafiki można utworzyć, wywołując `Init` i finaljąc wywołując metodę `UnInit` . Możesz powtórzyć tyle razy, ile chcesz używać tego samego `VsgDbg` wystąpienia do tworzenia kilku niezależnych plików dziennika grafiki.

## <a name="see-also"></a>Zobacz też
- [Init](init.md)