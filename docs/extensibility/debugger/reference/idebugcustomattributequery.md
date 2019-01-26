---
title: IDebugCustomAttributeQuery | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
ms.assetid: b804b619-70eb-4c38-80d9-c8b32b65ed3e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f035441a05f711438fd19eaa54e6c6b2a3aab7a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997939"
---
# <a name="idebugcustomattributequery"></a>IDebugCustomAttributeQuery
Reprezentuje zapytanie, w przypadku niestandardowych atrybutów na metody lub typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugCustomAttributeQuery : IUnknown  
```  
  
## <a name="methods"></a>Metody  
 Ten interfejs implementuje następujących metod:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery-getcustomattributebyname.md)|Pobiera atrybut niestandardowy nadać jej nazwę.|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery-iscustomattributedefined.md)|Określa, w określonym zdefiniowano atrybutu niestandardowego.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Sh.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll