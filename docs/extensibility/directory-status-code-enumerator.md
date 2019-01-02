---
title: Moduł wyliczający kod stanu katalogu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a8d6a541415e42e8d35dc4f3ab814c89cf939beb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927613"
---
# <a name="directory-status-code-enumerator"></a>Moduł wyliczający kod stanu katalogu
`SccDirStatus` Modułu wyliczającego zawiera nazwanych stałych, określające stan katalogu w systemie kontroli źródła. To wyliczenie jest używane przez [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). To została wprowadzona w wersji 1.2 API wtyczki kontroli źródła.  
  
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
 Nie można uzyskać stanu; nie należy polegać na niej.  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 Katalog nie jest pod kontrolą źródła.  
  
 SCC_DIRSTATUS_CONTROLLED  
 Katalog jest pod kontrolą źródła.  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 Projekt odpowiadający ten katalog jest pusty.  
  
## <a name="see-also"></a>Zobacz także  
 [Wtyczek kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)