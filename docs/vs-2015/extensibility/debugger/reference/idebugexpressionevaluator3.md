---
title: IDebugExpressionEvaluator3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator3 interface
ms.assetid: c27c2a14-300b-4535-be22-767c83602f69
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: df08bdb115f29b529676e307008db7a9eac9d9d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64834296"
---
# <a name="idebugexpressionevaluator3"></a>IDebugExpressionEvaluator3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Reprezentuje ewaluatora wyrażeń (EE) z rozszerzonym drzewem analizatora składni.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugExpressionEvaluator3 : IDebugExpressionEvaluator2  
```  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ta wersja analizatora przekazuje dostawcę symboli i adres oceniania ramki.  
  
## <a name="methods"></a>Metody  
 Oprócz metod w interfejsie [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) ten interfejs implementuje następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Parse2](../../../extensibility/debugger/reference/idebugexpressionevaluator3-parse2.md)|Konwertuje ciąg wyrażenia na wyrażenie analizowane przez dostawcę symboli i adres obliczanej ramki.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: EE. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
