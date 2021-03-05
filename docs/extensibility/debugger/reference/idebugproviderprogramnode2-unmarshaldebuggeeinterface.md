---
description: Uzyskuje określony interfejs między granicami procesu.
title: 'IDebugProviderProgramNode2:: UnmarshalDebuggeeInterface | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f51484ae1e9acbb9b94fe546f8157145673e22f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167870"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Uzyskuje określony interfejs między granicami procesu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT UnmarshalDebuggeeInterface(
   REFIID riid,
   void** ppvObject
);
```

```csharp
int UnmarshalDebuggeeInterface(
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>Parametry
`riid`\
podczas Identyfikator GUID interfejsu do uzyskania.

`ppvObject`\
określoną Zwraca obiekt implementujący żądany interfejs. [C++] można to rzutować bezpośrednio na żądany typ interfejsu. [C#] Użyj <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> metody w celu uzyskania żądanego interfejsu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest używana, gdy aparat debugowania jest uruchomiony w [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] obszarze przetwarzania, a debugowany program działa we własnym obszarze procesu.

## <a name="see-also"></a>Zobacz też
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
