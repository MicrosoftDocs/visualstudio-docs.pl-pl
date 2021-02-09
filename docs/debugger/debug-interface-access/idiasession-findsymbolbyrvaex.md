---
title: 'IDiaSession:: findSymbolByRVAEx | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByRVAEx method
ms.assetid: 61344966-fed4-4c02-9e27-20356ec2ef7c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fd3290afb5116661f62983ce3a6fae8653312f24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864132"
---
# <a name="idiasessionfindsymbolbyrvaex"></a>IDiaSession::findSymbolByRVAEx
Pobiera określony typ symbolu, który zawiera lub jest najbliższy do, określony względny adres wirtualny (RVA) i przesunięcie.

## <a name="syntax"></a>Składnia

```C++
HRESULT findSymbolByRVAEx ( 
   DWORD        rva,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol,
   LONG*        displacement
);
```

#### <a name="parameters"></a>Parametry
 `rva`

podczas Określa adres RVA.

 `symtag`

podczas Typ symbolu, który ma zostać znaleziony. Wartości są pobierane z wyliczenia [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) .

 `ppSymbol`

określoną Zwraca obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , który reprezentuje pobrany symbol.

 `displacement`

określoną Zwraca wartość określającą przesunięcie względem względnego adresu wirtualnego określonego w `rva` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład

```C++
IDiaSymbol* pFunc;
LONG disp = 0;
pSession->findSymbolByRVAEx( rva, SymTagFunction, &pFunc, &disp );
```

## <a name="see-also"></a>Zobacz także
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)