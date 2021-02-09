---
title: IDiaStackWalkHelper::p ut_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7dd354553568ec517f6816f5b279ccbe214f101c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854760"
---
# <a name="idiastackwalkhelperput_registervalue"></a>IDiaStackWalkHelper::put_registerValue
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

podczas Wartość z wyliczenia [CV_HREG_e wyliczeniem](../../debugger/debug-interface-access/cv-hreg-e.md) określająca rejestrację, w której ma zostać zapisany.

 `NewVal`

podczas Nowa wartość rejestru.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Pomimo rozmiaru wartości implementacja powinna przechowywać tylko te dane, które są zwykle przechowywane w rejestrze. Na przykład rejestr 8-bitowy będzie zawierał tylko najmniejsze 8 bitów danej wartości.

## <a name="see-also"></a>Zobacz też
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e, wyliczenie](../../debugger/debug-interface-access/cv-hreg-e.md)