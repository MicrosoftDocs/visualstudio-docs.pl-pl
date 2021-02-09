---
title: 'IDiaStackWalkHelper:: frameForVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::frameForVA method
ms.assetid: f35fc61b-f8dd-473a-b583-82c304059422
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8d5d053e7f3d185f3685ff9b0bf775711115abad
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854781"
---
# <a name="idiastackwalkhelperframeforva"></a>IDiaStackWalkHelper::frameForVA
Pobiera ramkę stosu, która zawiera określony adres wirtualny.

## <a name="syntax"></a>Składnia

```C++
HRESULT frameForVA( 
   ULONGLONG        va,
   IDiaFrameData**  ppFrame
);
```

#### <a name="parameters"></a>Parametry
 `va`

podczas Adres wirtualny dla danych ramek.

 `ppFrame`

określoną Obiekt [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) , który reprezentuje ramkę stosu o określonym adresie.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)