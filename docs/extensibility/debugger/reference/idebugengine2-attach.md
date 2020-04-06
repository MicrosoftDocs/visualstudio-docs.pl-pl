---
title: IDebugEngine2::Dołącz | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93890885dbbdfd3cc26984590955681487977200
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731205"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Dołącza aparat debugowania (DE) do programu lub programów. Wywoływane przez menedżera debugowania sesji (SDM), gdy DE jest uruchomiony w procesie do SDM.

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

## <a name="parameters"></a>Parametry
`pProgram`\
[w] Tablica [obiektów IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) które reprezentują programy, do których należy dołączyć. Są to programy portowe.

`rgpProgramNodes`\
[w] Tablica [obiektów IDebugProgramNode2,](../../../extensibility/debugger/reference/idebugprogramnode2.md) które reprezentują węzły programu, po jednym dla każdego programu. Węzły programu w tej tablicy reprezentują `pProgram`te same programy, co w programie . Węzły programu są podane tak, że DE można zidentyfikować programy do przyłączenia do.

`celtPrograms`\
[w] Liczba programów i/lub węzłów `pProgram` programu `rgpProgramNodes` w tablicach i.

`pCallback`\
[w] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) obiekt, który ma być używany do wysyłania zdarzeń debugowania do SDM.

`dwReason`\
[w] Wartość z [wyliczenia ATTACH_REASON,](../../../extensibility/debugger/reference/attach-reason.md) która określa przyczynę dołączania tych programów. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Istnieją trzy powody dołączania do programu, w następujący sposób:

- `ATTACH_REASON_LAUNCH`wskazuje, że DE jest dołączanie do programu, ponieważ użytkownik uruchomił proces, który go zawiera.

- `ATTACH_REASON_USER`wskazuje, że użytkownik jawnie zażądał DE do dołączenia do programu (lub procesu, który zawiera program).

- `ATTACH_REASON_AUTO`wskazuje, że DE jest dołączanie do określonego programu, ponieważ jest już debugowanie innych programów w określonym procesie. Jest to również nazywane auto-attach.

  Gdy ta metoda jest wywoływana, DE musi wysłać te zdarzenia w kolejności:

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (jeśli nie został jeszcze wysłany dla określonego wystąpienia aparatu debugowania)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   Ponadto, jeśli powodem dołączania `ATTACH_REASON_LAUNCH`jest , DE musi wysłać [zdarzenie IDebugEntryPointEvent2.](../../../extensibility/debugger/reference/idebugentrypointevent2.md)

   Gdy DE pobiera [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) obiekt odpowiadający program jest debugowany, może być wyszukiwane dla dowolnego interfejsu prywatnego.

   Przed wywołaniem metod węzła programu w `pProgram` `rgpProgramNodes`tablicy podanej przez lub personifikacji, jeśli jest to wymagane, powinny być włączone w interfejsie, `IDebugProgram2` który reprezentuje węzeł programu. Zwykle jednak ten krok nie jest konieczny. Aby uzyskać więcej informacji, zobacz [Problemy z zabezpieczeniami](../../../extensibility/debugger/security-issues.md).

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
