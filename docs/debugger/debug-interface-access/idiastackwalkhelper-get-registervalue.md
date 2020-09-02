---
title: 'IDiaStackWalkHelper:: get_registerValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fb78b4cbdfa2130731e3847b1a3325ab4cb3eac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464724"
---
# <a name="idiastackwalkhelperget_registervalue"></a>IDiaStackWalkHelper::get_registerValue
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

podczas Wartość z wyliczenia [CV_HREG_e wyliczeniem](../../debugger/debug-interface-access/cv-hreg-e.md) określająca, z którego rejestru pobrać wartość.

 `pRetVal`

określoną Zwraca bieżącą wartość rejestru.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Pomimo rozmiaru `pRetVal` parametru implementacja powinna przechowywać tylko te dane, które są zwykle przechowywane w rejestrze. Na przykład rejestr 8-bitowy zawiera tylko najmniejsze 8 bitów danej wartości. Ta wartość 8-bitowa jest rozwinięta do 64-bitów, gdy zwracana jest z tej metody.

## <a name="see-also"></a>Zobacz też
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e, wyliczenie](../../debugger/debug-interface-access/cv-hreg-e.md)