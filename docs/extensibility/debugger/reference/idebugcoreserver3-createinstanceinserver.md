---
title: IDebugCoreServer3::CreateInstanceInServer | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7e74ea66f5b8ecd04acfbc2617f91bcaf0f7ecbd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332411"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Tworzy wystąpienie aparatu debugowania na serwerze.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CreateInstanceInServer(
   LPCWSTR  szDll,
   WORD     wLangId,
   REFCLSID clsidObject,
   REFIID   riid,
   void**   ppvObject
);
```

```csharp
int CreateInstanceInServer(
   string     szDll,
   ushort     wLangID,
   ref Guid   clsidObject,
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>Parametry
`szDll`\
[in] Ścieżka do biblioteki dll, która implementuje CLSID określone w `clsidObject` parametru. Jeśli jest to `NULL`, następnie modelu COM `CoCreateInstance` funkcja jest wywoływana.

`wLangId`\
[in] Ustawienia regionalne aparatu debugowania. Może to być 0, jeśli [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) nie powinna być wywoływana metoda.

`clsidObject`\
[in] Identyfikator CLSID aparat debugowania do utworzenia.

`riid`\
[in] Identyfikator interfejsu określonego interfejsu, aby pobrać z obiektu klasy.

`ppvObject`\
[out] `IUnknown` interfejsu z wystąpieniami obiektu. Rzutowanie lub kierować się ten obiekt do żądanego interfejsu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)