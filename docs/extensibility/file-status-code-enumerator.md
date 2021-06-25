---
title: Moduł wyliczający kod stanu | Microsoft Docs
description: Moduł wyliczający SccStatus zawiera wartości stałe, które określają stan pliku w systemie kontroli źródła i są używane przez SccQueryInfo i POPLISTFUNC.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 95de8a29efcd56880cdaf452c9f21b90bba1c5c9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900970"
---
# <a name="file-status-code-enumerator"></a>Moduł wyliczający kod stanu pliku
Moduł `SccStatus` wyliczający zawiera nazwane wartości stałe, które określają stan pliku w systemie kontroli źródła. To wyliczenie jest używane przez [funkcję SccQueryInfo](../extensibility/sccqueryinfo-function.md) i funkcję `POPLISTFUNC` wywołania zwrotnego (zobacz [POPLISTFUNC,](../extensibility/poplistfunc.md) aby uzyskać szczegółowe informacje).

## <a name="syntax"></a>Składnia

```
enum SccStatus {
   SCC_STATUS_INVALID          = -1L,
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,
   SCC_STATUS_CONTROLLED       = 0x0001L,
   SCC_STATUS_CHECKEDOUT       = 0x0002L,
   SCC_STATUS_OUTOTHER         = 0x0004L,
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,
   SCC_STATUS_OUTOFDATE        = 0x0020L,
   SCC_STATUS_DELETED          = 0x0040L,
   SCC_STATUS_LOCKED           = 0x0080L,
   SCC_STATUS_MERGED           = 0x0100L,
   SCC_STATUS_SHARED           = 0x0200L,
   SCC_STATUS_PINNED           = 0x0400L,
   SCC_STATUS_MODIFIED         = 0x0800L,
   SCC_STATUS_OUTBYUSER        = 0x1000L
   SCC_STATUS_NOMERGE          = 0x2000L
   SCC_STATUS_RESERVED_1       = 0x4000L
   SCC_STATUS_RESERVED_2       = 0x8000L
};
```

## <a name="members"></a>Elementy członkowskie
 SCC_STATUS_INVALID nie można uzyskać stanu; Nie należy polegać na tym.

 SCC_STATUS_NOTCONTROLLED nie jest pod kontrolą źródła.

 SCC_STATUS_CONTROLLED znajduje się pod kontrolą źródła.

 SCC_STATUS_CHECKEDOUT wyewidencjonowane przez bieżącego użytkownika na dysku lokalnym.

 SCC_STATUS_OUTOTHER jest wyewidencjonowany przez innego użytkownika.

 SCC_STATUS_OUTEXCLUSIVE plik jest wyewidencjonowany wyłącznie.

 SCC_STATUS_OUTMULTIPLE jest wyewidencjonowany przez więcej niż jednego użytkownika.

 SCC_STATUS_OUTOFDATE Plik nie jest najnowszy.

 SCC_STATUS_DELETED plik został usunięty z projektu.

 SCC_STATUS_LOCKED jest zablokowany; nie są dozwolone żadne kolejne wersje.

 SCC_STATUS_MERGED plik został scalony, ale nie został jeszcze naprawiony/zweryfikowany.

 SCC_STATUS_SHARED plik jest współużytkowywny między projektami.

 SCC_STATUS_PINNED plik jest udostępniany jawnie w wersji.

 SCC_STATUS_MODIFIED plik został zmodyfikowany/uszkodzony/naruszony.

 SCC_STATUS_OUTBYUSER jest wyewidencjonowany przez bieżącego użytkownika.

 SCC_STATUS_NOMERGE nigdy nie można scalić z plikiem i nie trzeba go zapisywać przed get.

 SCC_STATUS_RESERVED_1 zarezerwowane do użytku wewnętrznego.

 SCC_STATUS_RESERVED_2 zarezerwowane do użytku wewnętrznego.

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
