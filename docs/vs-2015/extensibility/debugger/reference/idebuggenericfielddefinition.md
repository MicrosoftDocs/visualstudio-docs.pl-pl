---
title: IDebugGenericFieldDefinition | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 224b9a5c0e2412b9ae89c1767348b8fbd1a528be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180864"
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Reprezentuje definicję pola dla ogólnego typu kodu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugGenericFieldDefinition : IUnknown  
```  
  
## <a name="methods"></a>Metody  
 Ten interfejs implementuje następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|Tworzy wystąpienie pola z tablicą argumentów typu.|  
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|Pobiera parametry typu z określoną liczbą parametrów.|  
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|Pobiera liczbę parametrów typu skojarzonych z polem ogólnym.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
