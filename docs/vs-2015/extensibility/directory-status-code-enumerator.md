---
title: Moduł wyliczający kod stanu katalogu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e082a691a389d5cb9a8fa307a627b11911e0db78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185256"
---
# <a name="directory-status-code-enumerator"></a>Moduł wyliczający kod stanu katalogu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`SccDirStatus`Moduł wyliczający zawiera nazwane wartości stałe, które określają stan katalogu w systemie kontroli źródła. To wyliczenie jest używane przez [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Została wprowadzona w wersji 1,2 interfejsu API dodatku plug-in kontroli źródła.  
  
## <a name="syntax"></a>Składnia  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 SCC_DIRSTATUS_INVALID  
 Nie można uzyskać stanu. nie należy polegać na nim.  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 Katalog nie znajduje się pod kontrolą źródła.  
  
 SCC_DIRSTATUS_CONTROLLED  
 Katalog jest pod kontrolą źródła.  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 Projekt odpowiadający temu katalogowi jest pusty.  
  
## <a name="see-also"></a>Zobacz też  
 [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
