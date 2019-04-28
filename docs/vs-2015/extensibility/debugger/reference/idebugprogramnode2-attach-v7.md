---
title: IDebugProgramNode2::Attach_V7 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
ms.assetid: b5ffc736-efc7-4ca8-964d-5536ff891b0e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08028f2b03f3ea36cc72172ca8f9de31740b49f3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63417909"
---
# <a name="idebugprogramnode2attachv7"></a>IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

PRZESTARZAŁE. NIE NALEŻY UŻYWAĆ.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Attach_V7 (   
   IDebugProgram2*       pMDMProgram,  
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason  
);  
```  
  
```csharp  
int Attach_V7 (   
   IDebugProgram2       pMDMProgram,  
   IDebugEventCallback2 pCallback,  
   uint                 dwReason  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pMDMProgram`  
 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejs, który reprezentuje program, który można dołączyć do.  
  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) interfejs służący do wysyłania zdarzeń debugowania do SDM.  
  
 `dwReason`  
 [in] Wartość z zakresu od [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) wyliczenie, które określa przyczynę dołączania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja zawsze powinna zwrócić `E_NOTIMPL`.  
  
## <a name="remarks"></a>Uwagi  
  
> [!WARNING]
> Począwszy od programu [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], ta metoda nie jest już używany i powinien zawsze zwracają `E_NOTIMPL`. Zobacz [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfejs dla alternatywne podejście, jeśli węzeł program musi wskazywać, nie można dołączyć do lub węzeł program po prostu ustawia program `GUID`. W przeciwnym razie zaimplementować [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md) metody.  
  
## <a name="prior-to-visual-studio-2005"></a>Prior to Visual Studio 2005  
 Ta metoda musi zaimplementować tylko wtedy, gdy DE działa w przestrzeni adresowej debugowanego programu. W przeciwnym razie ta metoda powinna zwracać `S_FALSE`.  
  
 Gdy ta metoda jest wywoływana, DE musi wysłać [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) obiektu zdarzenia, jeśli go nie ma już wysłane dla tego wystąpienia [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfejsu, jak również [ IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) i [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) obiekty zdarzeń. [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) obiektu zdarzenia jest następnie wysyłana, gdy `dwReason` parametr `ATTACH_REASON_LAUNCH`.  
  
 DE musi wywołać [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metody [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) dostarczonych przez obiekt [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zdarzenia obiektu, a musi być przechowywany identyfikator GUID tego programu w danych wystąpienia dla `IDebugProgram2` implementowany przez DE obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
