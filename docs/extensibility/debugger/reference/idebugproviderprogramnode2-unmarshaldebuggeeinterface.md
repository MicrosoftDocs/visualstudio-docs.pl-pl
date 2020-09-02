---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3c0f6e66b6585eafde656cd7be88d0c76bbb3f37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720703"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Uzyskuje określony interfejs między granicami procesu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT UnmarshalDebuggeeInterface(
   REFIID riid,
   void** ppvObject
);
```

```csharp
int UnmarshalDebuggeeInterface(
   ref Guid   riid,
   out IntPtr ppvObject
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
