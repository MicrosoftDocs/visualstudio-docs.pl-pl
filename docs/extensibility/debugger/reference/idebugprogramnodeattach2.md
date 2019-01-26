---
title: IDebugProgramNodeAttach2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 85f5e63c9b41bae3066a6585a9e3e96fd9aa0ce4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54989825"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Umożliwia węzła program otrzymywać powiadomienia o próba dołączenia do skojarzonego programu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany w tej samej klasy, która implementuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interfejsu, aby otrzymać powiadomienie o operacji dołączania i zapewnienia możliwości anulowania operacji dołączania.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Uzyskanie tego interfejsu, wywołując `QueryInterface` method in Class metoda [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) obiektu. [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metoda musi zostać wywołana przed [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodę, aby nadać węzła programu szansę, aby zatrzymać proces dołączania.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 Ten interfejs implementuje następującą metodę:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Dołącza do skojarzonego programu lub procesu dołączania do odracza [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md) metody.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest preferowana alternatywa dla przestarzałego [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) metody. Wszystkie aparaty debugowania są zawsze załadowane z `CoCreateInstance` funkcji, oznacza to, są tworzone spoza przestrzeni adresowej debugowanego programu.  
  
 Jeśli poprzedniej implementacji `IDebugProgramNode2::Attach_V7` metoda po prostu ustawiał `GUID` programu debugowany, następnie tylko [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metoda musi zostać wdrożone.  
  
 Jeśli poprzedniej implementacji `IDebugProgramNode2::Attach_V7` metodę interfejs wywołania zwrotnego, która została podana, a następnie tę funkcję musi zostać przeniesione do implementacji [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md) metody i `IDebugProgramNodeAttach2` nie obsługuje interfejsu muszą być wykonywane.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)