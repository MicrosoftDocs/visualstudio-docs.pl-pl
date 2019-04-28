---
title: IDebugMethodField::GetThis | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8fc3c4a37b30d2ce7d4f5228b60d6c411afb5c9f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872940"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Pobiera `this` (`Me` w [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]) wskaźnik obiekt zawierający metodę.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

#### <a name="parameters"></a>Parametry
 `ppClass`

 [out] Zwraca [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) obiekt reprezentujący "to" wskaźnik.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 W językach obiektowych jest zazwyczaj dorozumianych wskaźnik do bieżącego wystąpienia klasy. Jest to nazywane `this` w języku C# / C++ i `Me` w [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].

## <a name="see-also"></a>Zobacz też
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)