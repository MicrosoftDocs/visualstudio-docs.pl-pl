---
title: IDiaStackWalker::getEnumFrames2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35886ea0456426c30c44d5fd8e90399d4a2143ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837943"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
Pobiera moduł wyliczający ramek stosu dla typu określonej platformy.

## <a name="syntax"></a>Składnia

```C++

      HRESULT getEnumFrames2( 
   enum  CV_CPU_TYPE_e    cpuid,
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>Parametry
 `cpuid`

[in] Wartość z zakresu od [cv_cpu_type_e — wyliczenie](../../debugger/debug-interface-access/cv-cpu-type-e.md) wyliczenia, określając typ platformy.

 `pHelper`

[in] Pomocnik [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) obiektu.

 `ppEnum`

[out] Zwraca [idiaenumstackframes —](../../debugger/debug-interface-access/idiaenumstackframes.md) obiektu zawierającego listę [idiastackframe —](../../debugger/debug-interface-access/idiastackframe.md) obiektów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Aby uzyskać listę ramek stosu dla właśnie x86 platforma, wywołanie [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) metody.

## <a name="see-also"></a>Zobacz też
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [CV_CPU_TYPE_e, wyliczenie](../../debugger/debug-interface-access/cv-cpu-type-e.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)