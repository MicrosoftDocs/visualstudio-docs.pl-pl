---
description: Tworzy wystąpienie aparatu debugowania na serwerze.
title: 'IDebugCoreServer3:: CreateInstanceInServer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3511e67300725dc46e6d0e3978b2cb034b92d84e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058693"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Tworzy wystąpienie aparatu debugowania na serwerze.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CreateInstanceInServer(
   LPCWSTR  szDll,
   WORD     wLangId,
   REFCLSID clsidObject,
   REFIID   riid,
   void**   ppvObject
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
podczas Ścieżka do biblioteki DLL implementującej identyfikator CLSID określony w `clsidObject` parametrze. Jeśli tak jest `NULL` , `CoCreateInstance` Funkcja com jest wywoływana.

`wLangId`\
podczas Ustawienia regionalne aparatu debugowania. Może to być wartość 0, jeśli metoda [setlocal](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) nie powinna być wywoływana.

`clsidObject`\
podczas Identyfikator CLSID aparatu debugowania do utworzenia.

`riid`\
podczas Identyfikator interfejsu określonego interfejsu, który ma zostać pobrany z obiektu klasy.

`ppvObject`\
[out] `IUnknown` Interfejs z obiektu skonkretyzowany. Rzutowanie lub kierowanie tego obiektu do żądanego interfejsu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
