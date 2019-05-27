---
title: IDebugDocument2::GetName | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1e653f7f735be43f2edeb4bd3c7935d3c89a9e58
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66204755"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Pobiera nazwę dokumentu w jednym z wielu formularzy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetName( 
   GETNAME_TYPE gnType,
   BSTR*        pbstrFileName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE gnType,
   out string        pbstrFileName
);
```

## <a name="parameters"></a>Parametry
`gnType`\
[in] Wartość z zakresu od [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) wyliczenie, który określa typ nazwy do zwrócenia.

`pbstrFileName`\
[out] Zwraca ciąg zawierający nazwę dokumentu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Tej metody na przykład, można zwrócić nazwę dokumentu jako tytuł lub nazwę pliku lub nawet część nazwy pliku.

## <a name="see-also"></a>Zobacz także
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)