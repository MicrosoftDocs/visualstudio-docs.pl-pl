---
title: IDebugSymbolProviderDirect::GetCurrentModulesInfo | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetCurrentModulesInfo
- GetCurrentModulesInfo
ms.assetid: b3b45ed2-ea4e-4389-b78a-11fc9796a6c1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95dc42b0e65ad0f849dd95e0ffead122e4cd1ebf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915702"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesinfo"></a>IDebugSymbolProviderDirect::GetCurrentModulesInfo
Pobiera informacje o modułach w grupie symboli.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetCurrentModulesInfo(
   unsigned long * pCount,
   GUID *          ppGuids,
   DWORD *         pADIds,
   DWORD *         pCurrentState,
   IUnknown **     ppCDModItfs
);
```

```csharp
int GetCurrentModulesInfo(
   uint       pCount,
   Guid       ppGuids,
   uint       pADIds,
   uint       pCurrentState,
   out object ppCDModItfs
);
```

#### <a name="parameters"></a>Parametry
 `pCount`

 [in] Liczba modułów w `ppGuids` tablicy.

 `ppGuids`

 [in] Tablica, która zawiera unikatowe identyfikatory dla modułów.

 `pADIds`

 [in] Identyfikatory domen aplikacji.

 `pCurrentState`

 [in] Bieżący stan grupy symboli.

 `ppCDModItfs`

 [out] Zwraca obiekt, który zawiera moduły w grupie symboli.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)