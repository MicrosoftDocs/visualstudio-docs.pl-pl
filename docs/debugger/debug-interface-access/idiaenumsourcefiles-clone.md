---
title: 'IDiaEnumSourceFiles:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Clone method
ms.assetid: 87a9a9b6-3927-4131-927c-ad95f8f098b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5e18d9ba518580d21874b49a7c910268aab36d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85467940"
---
# <a name="idiaenumsourcefilesclone"></a>IDiaEnumSourceFiles::Clone
Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.

## <a name="syntax"></a>Składnia

```C++
HRESULT Clone ( 
   IDiaEnumSourceFiles** ppenum
);
```

#### <a name="parameters"></a>Parametry
 ppenum

określoną Zwraca obiekt [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) , który zawiera duplikat modułu wyliczającego. Pliki źródłowe nie są duplikowane, tylko moduł wyliczający.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)