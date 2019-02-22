---
title: IDebugProgramPublisher2::UnpublishProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f633b7cd41a9e19179ba5daf22fdd66e9749ad5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698654"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Sprawia, że program jest niedostępny do debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT UnpublishProgram(
   IUnknown* pDebuggeeInterface
);
```

```csharp
int UnpublishProgram(
   object pDebuggeeInterface
);
```

#### <a name="parameters"></a>Parametry
 `pDebuggeeInterface`

 [in] `IUnknown` Interfejsu do programu. To jest taka sama wartość przekazana do [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) metody i jednoznacznie identyfikuje programu usuwany (oznacza to, że jest ona używana jako plik cookie).

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Aby udostępnić program aparaty debugowania i Menedżer debugowania sesji, należy użyć [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) metody.

## <a name="see-also"></a>Zobacz też
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)