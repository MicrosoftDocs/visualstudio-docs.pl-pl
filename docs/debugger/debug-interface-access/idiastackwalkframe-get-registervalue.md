---
title: Idiastackwalkframe::get_registervalue — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::get_registerValue method
ms.assetid: ca3c20a9-934a-4b2c-a7f6-7d06e8611ff2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d60fa2ebefb7e1e4eefccce866a1059fdbc78a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837982"
---
# <a name="idiastackwalkframegetregistervalue"></a>IDiaStackWalkFrame::get_registerValue
Pobiera wartość rejestru.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_registerValue ( 
   DWORD      index,
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `index`

[in] Wartość z zakresu od [cv_hreg_e — wyliczenie](../../debugger/debug-interface-access/cv-hreg-e.md) wyliczenie opisujące Zarejestruj, aby uzyskać wartość.

 `pRetVal`

[out] Zwraca bieżącą wartość rejestru.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [CV_HREG_e, wyliczenie](../../debugger/debug-interface-access/cv-hreg-e.md)