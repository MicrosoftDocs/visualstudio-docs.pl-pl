---
title: Moduł wyliczający kod stanu pliku | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1b6e74caa9eedd42e25339d62f5837ccfe82d001
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54755517"
---
# <a name="file-status-code-enumerator"></a>Moduł wyliczający kod stanu pliku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`SccStatus` Modułu wyliczającego zawiera nazwanych stałych, określające stan pliku w systemie kontroli źródła. To wyliczenie jest używane przez [SccQueryInfo](../extensibility/sccqueryinfo-function.md) i `POPLISTFUNC` funkcji wywołania zwrotnego (zobacz [POPLISTFUNC](../extensibility/poplistfunc.md) Aby uzyskać szczegółowe informacje).  
  
## <a name="syntax"></a>Składnia  
  
```  
enum SccStatus {  
   SCC_STATUS_INVALID          = -1L,  
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,  
   SCC_STATUS_CONTROLLED       = 0x0001L,  
   SCC_STATUS_CHECKEDOUT       = 0x0002L,  
   SCC_STATUS_OUTOTHER         = 0x0004L,  
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,  
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,  
   SCC_STATUS_OUTOFDATE        = 0x0020L,  
   SCC_STATUS_DELETED          = 0x0040L,  
   SCC_STATUS_LOCKED           = 0x0080L,  
   SCC_STATUS_MERGED           = 0x0100L,  
   SCC_STATUS_SHARED           = 0x0200L,  
   SCC_STATUS_PINNED           = 0x0400L,  
   SCC_STATUS_MODIFIED         = 0x0800L,  
   SCC_STATUS_OUTBYUSER        = 0x1000L  
   SCC_STATUS_NOMERGE          = 0x2000L  
   SCC_STATUS_RESERVED_1       = 0x4000L  
   SCC_STATUS_RESERVED_2       = 0x8000L  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 SCC_STATUS_INVALID  
 Nie można uzyskać stanu; nie należy polegać na niej.  
  
 SCC_STATUS_NOTCONTROLLED  
 Plik nie jest pod kontrolą źródła.  
  
 SCC_STATUS_CONTROLLED  
 Plik jest pod kontrolą źródła.  
  
 SCC_STATUS_CHECKEDOUT  
 Wyewidencjonowany przez bieżącego użytkownika na dysku lokalnym.  
  
 SCC_STATUS_OUTOTHER  
 Plik jest wyewidencjonowany przez innego użytkownika.  
  
 SCC_STATUS_OUTEXCLUSIVE  
 Plik jest wyewidencjonowany.  
  
 SCC_STATUS_OUTMULTIPLE  
 Plik jest wyewidencjonowany przez więcej niż jednego użytkownika.  
  
 SCC_STATUS_OUTOFDATE  
 Plik nie jest najnowsza.  
  
 SCC_STATUS_DELETED  
 Plik został usunięty z projektu.  
  
 SCC_STATUS_LOCKED  
 Plik jest zablokowany; nie dozwolone więcej wersji.  
  
 SCC_STATUS_MERGED  
 Plik został połączony, ale nie zostały jeszcze rozwiązane/weryfikacji.  
  
 SCC_STATUS_SHARED  
 Plik jest udostępniony między projektami.  
  
 SCC_STATUS_PINNED  
 Plik jest udostępniony do jawnego wersji.  
  
 SCC_STATUS_MODIFIED  
 Plik został zmodyfikowany/uszkodzony/naruszone.  
  
 SCC_STATUS_OUTBYUSER  
 Plik jest wyewidencjonowany przez bieżącego użytkownika.  
  
 SCC_STATUS_NOMERGE  
 Plik nigdy nie mogą zostać scalone z i nie muszą zostać zapisane przed GET.  
  
 SCC_STATUS_RESERVED_1  
 Zarezerwowane do użytku wewnętrznego.  
  
 SCC_STATUS_RESERVED_2  
 Zarezerwowane do użytku wewnętrznego.  
  
## <a name="see-also"></a>Zobacz też  
 [Wtyczek kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)
