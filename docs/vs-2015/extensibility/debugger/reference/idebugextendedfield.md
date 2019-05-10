---
title: IDebugExtendedField | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8001ced3ba2116ec8ff76ecdac2d0789304335e3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62547250"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Rozszerza typy pól, które są dostępne, które obsługują elementy ogólne kodu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugExtendedField : IDebugField  
```  
  
## <a name="methods"></a>Metody  
 Oprócz metod na [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu, ten interfejs implementuje następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Pobiera rodzaj określone pole rozszerzonego.|  
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|Określa, czy pole reprezentuje zamkniętego typu.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Sh.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
