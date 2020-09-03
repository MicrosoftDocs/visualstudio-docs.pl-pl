---
title: 'IDebugProgram2:: GetENCUpdate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e90ff9f8a7a80913aec72b9fe2bb6fe470013d51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722837"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Ta metoda pobiera aktualizację Edytuj i Kontynuuj (ENC) dla tego programu. Niestandardowy aparat debugowania zawsze zwraca wartość `E_NOTIMPL` .

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetENCUpdate( 
   IUnknown** ppUpdate
);
```

```csharp
int GetENCUpdate(
   out object ppUpdate
);
```

## <a name="parameters"></a>Parametry
`ppUpdate`\
określoną Zwraca wewnętrzny interfejs, którego można użyć do zaktualizowania tego programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

> [!NOTE]
> Niestandardowy aparat debugowania powinien zawsze zwrócić `E_NOTIMPL` .

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
