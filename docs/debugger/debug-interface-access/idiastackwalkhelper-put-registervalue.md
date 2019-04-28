---
title: IDiaStackWalkHelper::put_registerValue | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59d076781e0f67ad9a2f2af02e7dc937042b0e71
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837930"
---
# <a name="idiastackwalkhelperputregistervalue"></a>IDiaStackWalkHelper::put_registerValue
Ustawia wartość rejestru.

## <a name="syntax"></a>Składnia

```C++
HRESULT put_registerValue ( 
   DWORD     index,
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Parametry
 `index`

[in] Wartość z zakresu od [cv_hreg_e — wyliczenie](../../debugger/debug-interface-access/cv-hreg-e.md) wyliczenie opisujące rejestru do zapisu.

 `NewVal`

[in] Nowa wartość rejestru.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Niezależnie od rozmiaru wartość należy przechowywać implementację, co rejestru zwykle zawiera tylko. Na przykład rejestr 8-bitowy będzie przechowywało tylko najniższy 8 bitów danej wartości.

## <a name="see-also"></a>Zobacz też
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e, wyliczenie](../../debugger/debug-interface-access/cv-hreg-e.md)