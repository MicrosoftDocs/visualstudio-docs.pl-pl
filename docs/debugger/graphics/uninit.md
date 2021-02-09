---
title: Odinicjuj inicjowanie | Microsoft Docs
description: Użyj metody UnInit () elementu VsgDbg, aby sfinalizować i zamknąć plik dziennika grafiki i zwolnić zasoby rejestrowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7cead2d7c1c98e4f481e6057c9ab79c8dc908683
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905020"
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