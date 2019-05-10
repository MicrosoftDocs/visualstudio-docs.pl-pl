---
title: IDebugArrayObject2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d68b0db20150bd81a9b2b4aef29c78701a6bc8ee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440701"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Reprezentuje obiekt tablicy zarządzanej i pozwala ewaluatora wyrażeń (EE), aby określić podstawowy indeks tablicy (dolne granice).  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugArrayObject2 : IDebugArrayObject  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 To jest implementowany przez aparat debugowania zarządzanego (DE).  
  
## <a name="methods"></a>Metody  
 Oprócz metod na [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) interfejsu, ten interfejs implementuje następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Pobiera podstawowy indeksów (dolne granice) dla każdego indeksu, biorąc pod uwagę liczbę wymiarów w tablicy.|  
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Określa, czy tablica ma podstawowy indeksów (dolne granice) zdefiniowany.|  
  
## <a name="remarks"></a>Uwagi  
 Ewaluatora wyrażeń używa tego interfejsu, który reprezentuje zarządzanych tablic w drzewie analizy.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: EE.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
