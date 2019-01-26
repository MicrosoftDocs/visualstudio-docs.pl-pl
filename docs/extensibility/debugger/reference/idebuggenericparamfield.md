---
title: IDebugGenericParamField | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e7cc68af4d5b53a36e9affc038951e2be63de90f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954621"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
Reprezentuje parametr typu ogólnego kodu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugGenericParamField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Używane do obsługi typów ogólnych.  
  
## <a name="methods"></a>Metody  
 Oprócz metod na [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu, ten interfejs implementuje następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Zwraca liczbę ograniczenia, które są skojarzone z tym parametru ogólnego.|  
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Pobiera ograniczenia, które są skojarzone z tym parametru ogólnego.|  
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Pobranie flagi dla tego parametru ogólnego.|  
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Pobiera indeks tego parametru ogólnego.|  
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Pobiera nazwę tego parametru ogólnego.|  
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Pobiera właściciela tego parametru ogólnego typu lub metody.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Sh.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll