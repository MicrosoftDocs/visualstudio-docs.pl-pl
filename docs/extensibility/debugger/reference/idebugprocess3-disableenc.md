---
description: Ta metoda jawnie wyłącza funkcję Edytuj i Kontynuuj dla tego procesu (oraz wszystkich programów, które zawiera).
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
ms.openlocfilehash: ffedebd14f720e006c0bec2044afe80901762b52
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158491"
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
