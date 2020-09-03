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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72734819"
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