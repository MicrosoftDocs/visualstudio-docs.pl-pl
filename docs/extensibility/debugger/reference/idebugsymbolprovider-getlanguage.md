---
title: IDebugSymbolProvider::GetLanguage | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b20222db9b007fbeee6daf0df1921e4c56744818
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56699629"
---
# <a name="idebugsymbolprovidergetlanguage"></a>IDebugSymbolProvider::GetLanguage
Ta metoda pobiera języka, który został użyty do kompilowania kodu pod adresem debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetLanguage( 
   IDebugAddress* pAddress,
   GUID*          pguidLanguage,
   GUID*          pguidLanguageVendor
);
```

```csharp
int GetLanguage(
   IDebugAddress pAddress,
   out Guid      pguidLanguage,
   out Guid      pguidLanguageVendor
);
```

#### <a name="parameters"></a>Parametry
 `pAddress`

 [in] Adres obiektu reprezentowanego przez [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu.

 `pguidLanguage`

 [out] Zwraca `GUID` , który określa język.

 `pguidLanguageVendor`

 [out] Zwraca `GUID` określający dostawcy języka.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Aparat debugowania wywołuje tę metodę, aby uzyskać informacje potrzebne do wybrania Ewaluator wyrażeń poprawne.

## <a name="see-also"></a>Zobacz też
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)