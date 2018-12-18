---
title: IDebugSourceServerModule | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1fefd8abd0693ae0ab1150365bd41aab04e6a0fe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817103"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Reprezentuje informacji o serwerze źródłowym, który jest zawarty w pliku PDB.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugSourceServerModule : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez debugera aparatów i wykorzystana przez debugera interfejsu użytkownika.  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `IDebugSourceServerModule`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetSourceServerData, metoda](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Pobiera tablicę informacji o serwerze źródłowym.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

