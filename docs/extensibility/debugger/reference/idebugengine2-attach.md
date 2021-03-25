---
description: Dołącza aparat debugowania (DE) do programu lub programów.
title: 'IDebugEngine2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38275cc623fcb8b30646c9d84ef194f584369ef2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093915"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Dołącza aparat debugowania (DE) do programu lub programów. Wywoływane przez Menedżera debugowania sesji (SDM), gdy jest uruchomiona w procesie do modelu SDM.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Attach( 
   IDebugProgram2**      pProgram,
   IDebugProgramNode2**  rgpProgramNodes,
   DWORD                 celtPrograms,
   IDebugEventCallback2* pCallback,
   ATTACH_REASON         dwReason
);
```

```csharp
int Attach( 
   IDebugProgram2[]     pProgram,
   IDebugProgramNode2[] rgpProgramNodes,
   uint                 celtPrograms,
   IDebugEventCallback2 pCallback,
   Enum_ATTACH_REASON   dwReason
);
```

## <a name="parameters"></a>Parametry
`pProgram`\
podczas Tablica obiektów [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , które reprezentują programy do dołączenia. Są to programy portów.

`rgpProgramNodes`\
podczas Tablica obiektów [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) reprezentujących węzły programu, po jednym dla każdego programu. Węzły programu w tej tablicy reprezentują te same programy jak w programie `pProgram` . Węzły programu są podawane, aby można było zidentyfikować programy do dołączenia.

`celtPrograms`\
podczas Liczba programów i/lub węzłów programu w `pProgram` `rgpProgramNodes` tablicach i.

`pCallback`\
podczas Obiekt [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , który ma być używany do wysyłania zdarzeń debugowania do modelu SDM.

`dwReason`\
podczas Wartość z wyliczenia [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) , która określa przyczynę dołączenia tych programów. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Istnieją trzy powody dołączenia do programu w następujący sposób:

- `ATTACH_REASON_LAUNCH` wskazuje, że element DE jest dołączany do programu, ponieważ użytkownik uruchomił proces, który go zawiera.

- `ATTACH_REASON_USER` oznacza, że użytkownik jawnie zażądał dołączenia do programu (lub procesu, który zawiera program).

- `ATTACH_REASON_AUTO` wskazuje, że element DE jest dołączany do określonego programu, ponieważ jest już debugowany w innych programach w konkretnym procesie. Ta funkcja jest również nazywana AutoAttach.

  W przypadku wywołania tej metody DE musi wysłać te zdarzenia w sekwencji:

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (jeśli nie został jeszcze wysłany do określonego wystąpienia aparatu debugowania)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   Ponadto, jeśli powodem dołączenia jest `ATTACH_REASON_LAUNCH` , nie musi wysłać zdarzenia [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) .

   Po usunięciu obiektu [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) odpowiadającego debugowanemu programowi można wykonać zapytanie dotyczące dowolnego interfejsu prywatnego.

   Przed wywołaniem metod węzła programu w tablicy podanym przez `pProgram` lub `rgpProgramNodes` , personifikacji, jeśli jest to wymagane, należy włączyć w `IDebugProgram2` interfejsie, który reprezentuje węzeł programu. Zwykle jednak ten krok nie jest konieczny. Aby uzyskać więcej informacji, zobacz [problemy z zabezpieczeniami](../../../extensibility/debugger/security-issues.md).

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
