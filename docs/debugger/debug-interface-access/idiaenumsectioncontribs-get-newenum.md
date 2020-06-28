---
title: 'IDiaEnumSectionContribs:: get__NewEnum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::get__NewEnum method
ms.assetid: a16ee92f-3081-416a-98f6-ce6bc8288a8b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16393068ba56527abc72564b6dac1f15d53ba3d6
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468156"
---
# <a name="idiaenumsectioncontribsget__newenum"></a>IDiaEnumSectionContribs::get__NewEnum
Pobiera <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> wersję tego modułu wyliczającego.

## <a name="syntax"></a>Składnia

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Parametry
 pRetVal

określoną Zwraca `IUnknown` interfejs, który reprezentuje <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> wersję tego modułu wyliczającego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)