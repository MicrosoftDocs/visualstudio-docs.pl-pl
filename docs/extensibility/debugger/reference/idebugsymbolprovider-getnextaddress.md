---
title: IDebugSymbolProvider::GetNextAddress | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 574111db390388ee1d0c572a3a8825c3a2ae9469
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915673"
---
# <a name="idebugsymbolprovidergetnextaddress"></a>IDebugSymbolProvider::GetNextAddress
Pobiera adres debugowania, występującego z adresu podanego debugowania w metodzie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetNextAddress( 
   IDebugAddress*  pAddress,
   BOOL            fStatementOnly,
   IDebugAddress** ppAddress
);
```

```csharp
int GetNextAddress( 
   IDebugAddress     pAddress,
   bool              fStatementOnly,
   out IDebugAddress ppAddress
);
```

#### <a name="parameters"></a>Parametry
 `pAddress`

 [in] Podany adres debugowania.

 `fStatementOnly`

 [in] W przypadku opcji TRUE ogranicza adresy debugowania do pojedynczej instrukcji.

 `ppAddress`

 [out] Zwraca następny adres debugowania.

## <a name="return-value"></a>Wartość zwracana
 Zwraca prawidłową `HRESULT`, zazwyczaj S_OK.

## <a name="see-also"></a>Zobacz też
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)