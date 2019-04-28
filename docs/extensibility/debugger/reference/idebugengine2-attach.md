---
title: IDebugEngine2::Attach | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab1ea05511369d36b881afcaf7c161f796fd4925
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875317"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Dołącza aparat debugowania (DE), programów lub programu. Wywoływane przez Menedżer debugowania sesji (SDM), gdy DE jest uruchomiona wewnątrz procesu SDM.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Attach( 
   IDebugProgram2**      pProgram,
   IDebugProgramNode2**  rgpProgramNodes,
   DWORD                 celtPrograms,
   IDebugEventCallback2* pCallback,
   ATTACH_REASON         dwReason
);
```

```csharp
int Attach( 
   IDebugProgram2[]     pProgram,
   IDebugProgramNode2[] rgpProgramNodes,
   uint                 celtPrograms,
   IDebugEventCallback2 pCallback,
   Enum_ATTACH_REASON   dwReason
);
```

#### <a name="parameters"></a>Parametry
 `pProgram`

 [in] Tablica [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekty reprezentujące programy do podłączenia do. Są to programy portu.

 `rgpProgramNodes`

 [in] Tablica [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) obiekty reprezentujące program węzłów, jednej dla każdego programu. Węzły programu w tej tablicy reprezentują te same programy, podobnie jak w `pProgram`. Węzły programu podane są tak, aby DE można zidentyfikować te programy można dołączyć do.

 `celtPrograms`

 [in] Liczba programów i/lub węzły programu w `pProgram` i `rgpProgramNodes` tablic.

 `pCallback`

 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) obiekt ma być używany do wysyłania zdarzeń debugowania do SDM.

 `dwReason`

 [in] Wartość z zakresu od [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) wyliczenie, które określa przyczyny dołączenie tych programów. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Istnieją trzy powody dołączanie do programu, w następujący sposób:

- `ATTACH_REASON_LAUNCH` Wskazuje, że DE jest dołączanie do programu, ponieważ użytkownik uruchomił proces, który go zawiera.

- `ATTACH_REASON_USER` Wskazuje, że użytkownik zażądał jawnie DE można dołączyć do programu (lub proces, który zawiera program).

- `ATTACH_REASON_AUTO` Wskazuje, że Niemcy jest dołączenie do określonego programu, ponieważ on już trwa debugowanie innych programów w danym procesie. Jest to również automatyczne dołączanie.

  Gdy ta metoda jest wywoływana, DE musi wysłać tych zdarzeń w sekwencji:

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (jeśli go nie już zostało wysłane do konkretnego wystąpienia aparatu debugowania)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   Ponadto, jeśli jest przyczyna dołączanie `ATTACH_REASON_LAUNCH`, DE musi wysyłać [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) zdarzeń.

   Gdy pobiera DE [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) obiekt odpowiadający debugowanego, może być badana dla dowolnego prywatny interfejsu.

   Przed wywołaniem metody węzła programu w tablicy, biorąc pod uwagę przy `pProgram` lub `rgpProgramNodes`, personifikacji, jeśli jest to wymagane, powinna być włączona na `IDebugProgram2` interfejs, który reprezentuje węzeł program. Zwykle jednak ten krok nie jest konieczne. Aby uzyskać więcej informacji, zobacz [problemy z zabezpieczeniami](../../../extensibility/debugger/security-issues.md).

## <a name="see-also"></a>Zobacz też
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)