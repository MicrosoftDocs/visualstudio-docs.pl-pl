---
title: IDebugModuleLoadEvent2::GetModule | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b17636d5f346475018e27c72562807b44b39460c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872901"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Pobiera moduł, który jest załadowany lub zwolnione.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetModule( 
   IDebugModule2** pModule,
   BSTR*           pbstrDebugMessage,
   BOOL*           pbLoad
);
```

```csharp
int GetModule( 
   out IDebugModule2 pModule,
   ref string        pbstrDebugMessage,
   ref int           pbLoad
);
```

#### <a name="parameters"></a>Parametry
 `pModule`

 [out] Zwraca [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) obiekt, który reprezentuje ładowanie lub zwalnianie modułu.

 `pbstrDebugMessage`

 [out w] Zwraca wartość opcjonalną wiadomość, zawierająca opis tego zdarzenia. Jeśli ten parametr ma wartość null, jest wymagany żaden komunikat.

 `pbLoad`

 [out w] Wartość różną od zera (`TRUE`) Jeśli moduł jest ładowanie i zero (`FALSE`) Jeśli Trwa zwalnianie modułu. Jeśli ten parametr ma wartość null, wymagane jest Brak stanu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)