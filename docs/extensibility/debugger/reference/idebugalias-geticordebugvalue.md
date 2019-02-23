---
title: IDebugAlias::GetICorDebugValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59506af5ad48bd18c454f4c59367921eed1e679a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707916"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Pobiera interfejs kodu zarządzanego, który reprezentuje wartość skojarzoną z tego aliasu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

#### <a name="parameters"></a>Parametry
 `ppUnk`

 [out] `IUnknown` interfejs, który reprezentuje wartość skojarzoną z tego aliasu. Ten interfejs może być odpytywany dla `ICorDebugValue` interfejsu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda ma zastosowanie tylko do zarządzanych wartości ( `ICorDebugValue` jest dostępny w interfejsie [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] i jest definiowany w [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] zestawu SDK w pliku cordebug.idl).

## <a name="see-also"></a>Zobacz też
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)