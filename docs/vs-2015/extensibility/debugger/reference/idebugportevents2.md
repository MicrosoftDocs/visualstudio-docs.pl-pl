---
title: IDebugPortEvents2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f47877b5bea1a65961ae7be6d7018e18fb03cd8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748437"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs powiadamia słuchacz (zazwyczaj Menedżer debugowania sesji [SDM] lub aparat debugowania) proces i program tworzenia i niszczenia na określonym porcie. Te informacje mogą służyć do przedstawiać w czasie rzeczywistym procesów i programy uruchomione na porcie.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Program Visual Studio zazwyczaj implementują ten interfejs, aby otrzymywać powiadomienia o programu, tworzenia i niszczenia. Aparat debugowania mogą także implementować ten interfejs do nasłuchiwania zdarzeń tych portów.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wszystkie [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfejsów można wykonywać zapytania dla <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfejsu. A następnie <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> metodę `IDebugPortEvents2` jest wywoływana w <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfejsu, aby uzyskać <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfejsu. Na koniec <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> method in Class metoda <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> wywoływany jest interfejs do wysyłania zdarzeń za pomocą [zdarzeń](../../../extensibility/debugger/reference/idebugportevents2-event.md) metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugPortEvents2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Wysyła zdarzenia, opisujące, tworzenia i niszczenia, procesów i programy na porcie.|  
  
## <a name="remarks"></a>Uwagi  
 `IDebugPortEvents2` Umożliwia również przez SDM debugowanie programów, które są uruchamiane w ramach procesu, który jest już debugowany.  
  
 Port zdarzenia są przekazywane do SDM według tego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)

