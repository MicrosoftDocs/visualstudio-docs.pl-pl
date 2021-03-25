---
description: Pobiera nazwę dokumentu w jednym z kilku formularzy.
title: 'IDebugDocument2:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 49c9a2b4fd95fbb24b28b69003c8e462b09be38b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066818"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Pobiera nazwę dokumentu w jednym z kilku formularzy.

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
podczas Wartość z wyliczenia [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) , która określa typ nazwy do zwrócenia.

`pbstrFileName`\
określoną Zwraca ciąg zawierający nazwę dokumentu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda może na przykład zwrócić nazwę dokumentu jako tytuł lub nazwę pliku lub parzystą część nazwy pliku.

## <a name="see-also"></a>Zobacz też
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
