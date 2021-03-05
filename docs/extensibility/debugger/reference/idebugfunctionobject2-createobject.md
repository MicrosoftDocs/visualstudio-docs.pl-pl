---
description: Tworzy obiekt, który używa konstruktora danego ustawienia flagi oceny i wartości limitu czasu.
title: 'IDebugFunctionObject2:: CreateObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4cd5eb81972af35b84c688e34b8cbc285c4723c2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143145"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Tworzy obiekt, który używa konstruktora danego ustawienia flagi oceny i wartości limitu czasu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CreateObject (
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject (
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   out IDebugObject**   ppObject
);
```

## <a name="parameters"></a>Parametry
`pConstructor`\
podczas Obiekt [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) , który reprezentuje konstruktora obiektu, który ma zostać utworzony.

`dwArgs`\
podczas Liczba parametrów w `pArg` tablicy. Reprezentuje liczbę parametrów przekazaną do konstruktora.

`pArgs`\
podczas Tablica obiektów [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , która reprezentuje parametry przesłane do konstruktora.

`dwEvalFlags`\
podczas Kombinacja flag z wyliczenia [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) , która określa, w jaki sposób ma być przeprowadzana Ocena.

`dwTimeout`\
podczas Maksymalny czas oczekiwania (w milisekundach) przed powrotem z tej metody. Używaj **nieskończoności** , aby czekać w nieskończoność.

`ppObject`\
określoną Zwraca **IDebugObject** reprezentujący nowo utworzony obiekt.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wywołaj tę metodę, aby utworzyć obiekt, który reprezentuje wystąpienie klasy lub inny typ złożony, który wymaga konstruktora, który jest parametrem.

## <a name="see-also"></a>Zobacz też
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
