---
title: IDebugPointerObject3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugPointerObject3 interface
ms.assetid: 11d26af4-1079-435e-96fa-d5269cbea8eb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e5d6707a84e3a9a019b427ee5f1289af9425b941
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54934221"
---
# <a name="idebugpointerobject3"></a>IDebugPointerObject3
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Reprezentuje wskaźnik w drzewie analizy i rozszerza **IDebugPointerObject** interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPointerObject3 : IDebugPointerObject  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ewaluatora wyrażeń (EE) implementuje ten interfejs.  
  
## <a name="methods"></a>Metody  
 Oprócz metod na [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) interfejsu, ten interfejs implementuje następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetPointerAddress](../../../extensibility/debugger/reference/idebugpointerobject3-getpointeraddress.md)|Pobiera adres wskaźnika.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: EE.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll