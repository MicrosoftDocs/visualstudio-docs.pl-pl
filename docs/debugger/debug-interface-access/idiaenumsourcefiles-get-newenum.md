---
title: 'IDiaEnumSourceFiles:: get__NewEnum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::get__NewEnum method
ms.assetid: 8405966c-64b4-4743-9a83-0e27ca2047c7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04ebf4e1338d83a62fd6167cdba9d6f18a011c1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85467926"
---
# <a name="idiaenumsourcefilesget__newenum"></a>IDiaEnumSourceFiles::get__NewEnum
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
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)