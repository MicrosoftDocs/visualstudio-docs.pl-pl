---
title: 'IDebugSymbolProviderDirect:: GetMethodFromAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a062056f4a61521966417e9923a17f6d85b991a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718940"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
Pobiera informacje o metodzie pod określonym adresem debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetMethodFromAddress(
   IDebugAddress* pAddress,
   GUID*          pGuid,
   DWORD*         pAppID,
   _mdToken*      pTokenClass,
   _mdToken*      pTokenMethod,
   DWORD*         pdwOffset,
   DWORD*         pdwVersion
);
```

```csharp
int GetMethodFromAddress(
   IDebugAddress pAddress,
   out Guid      pGuid,
   out uint      pAppID,
   out uint      pTokenClass,
   out uint      pTokenMethod,
   out uint      pdwOffset,
   out uint      pdwVersion
);
```

## <a name="parameters"></a>Parametry
`pAddress`\
podczas Adres debugowania reprezentowany przez interfejs [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`pGuid`\
określoną Unikatowy identyfikator modułu.

`pAppID`\
określoną Identyfikator domeny aplikacji.

`pTokenClass`\
określoną Token, który reprezentuje klasę zawierającą.

`pTokenMethod`\
określoną Token, który reprezentuje moduł.

`pdwOffset`\
określoną Przesunięcie w bajtach od początku `pAddress` parametru.

`pdwVersion`\
określoną Numer wersji metody.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
