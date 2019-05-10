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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 071dac72e39a3cce5b0b17dc9e401b9072efda6a
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65224058"
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

## <a name="parameters"></a>Parametry
 `pAddress`\

 [in] Adres obiektu reprezentowanego przez [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu.

 `pguidLanguage`\

 [out] Zwraca `GUID` , który określa język.

 `pguidLanguageVendor`\

 [out] Zwraca `GUID` określający dostawcy języka.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Aparat debugowania wywołuje tę metodę, aby uzyskać informacje potrzebne do wybrania Ewaluator wyrażeń poprawne.

## <a name="see-also"></a>Zobacz także
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)