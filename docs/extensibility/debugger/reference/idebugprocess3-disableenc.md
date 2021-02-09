---
title: IDebugProcess3::D isableENC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5cfd425e6b992d8d933edd45f27d6fb4c8161a1a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891049"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Ta metoda jawnie wyłącza funkcję Edytuj i Kontynuuj dla tego procesu (oraz wszystkich programów, które zawiera). Niestandardowy dostawca portu zawsze powinien zwrócić `E_NOTIMPL` .

## <a name="syntax"></a>Składnia

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>Parametry
`reason`\
podczas Wartość z wyliczenia [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

> [!NOTE]
> Niestandardowy dostawca portu zawsze powinien zwrócić `E_NOTIMPL` .

## <a name="remarks"></a>Uwagi
 Gdy funkcja Edytuj i Kontynuuj jest wyłączona dla procesu, można ją ponownie włączyć tylko przez ponowne uruchomienie procesu.

## <a name="see-also"></a>Zobacz też
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
