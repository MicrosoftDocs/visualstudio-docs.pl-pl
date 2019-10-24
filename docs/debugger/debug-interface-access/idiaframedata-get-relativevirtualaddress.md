---
title: 'IDiaFrameData:: get_relativeVirtualAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_relativeVirtualAddress method
ms.assetid: de070ef4-6c9d-43ca-911c-5245cbcb8dbe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be44c7a4136629c6b8d86b4e60a509842734131d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743508"
---
# <a name="idiaframedataget_relativevirtualaddress"></a>IDiaFrameData::get_relativeVirtualAddress
Pobiera względny adres wirtualny (RVA) kodu dla ramki.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_relativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca względny adres wirtualny kodu dla ramki.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`. Zwraca `S_FALSE`, jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)