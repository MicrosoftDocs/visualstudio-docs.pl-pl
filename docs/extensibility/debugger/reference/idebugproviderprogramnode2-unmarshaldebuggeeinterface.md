---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720703"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Uzyskuje określony interfejs w granicach procesu.

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
[w] Identyfikator GUID interfejsu do uzyskania.

`ppvObject`\
[na zewnątrz] Zwraca obiekt implementujący żądany interfejs. [C++] można go rzutować bezpośrednio do żądanego typu interfejsu. [C#] użyj <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> metody, aby uzyskać żądany interfejs.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest używana, gdy aparat [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugowania jest uruchomiony w przestrzeni procesu i program debugowany jest uruchomiony we własnym miejscu procesu.

## <a name="see-also"></a>Zobacz też
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
