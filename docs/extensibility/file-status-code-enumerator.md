---
title: Wyliczacz kodu stanu pliku | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 184c8686ea184aea2cbd0a64873718cbe72f7615
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711450"
---
# <a name="file-status-code-enumerator"></a>Wyliczacz kodu stanu pliku
Wyliczacz `SccStatus` zawiera nazwane wartości stałe, które określają stan pliku w systemie kontroli źródła. To wyliczenie jest używane przez [SccQueryInfo](../extensibility/sccqueryinfo-function.md) i funkcji wywołania zwrotnego `POPLISTFUNC` (zobacz [POPLISTFUNC](../extensibility/poplistfunc.md) szczegóły).

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
 nie można było uzyskać statusu SCC_STATUS_INVALID; nie polegaj na nim.

 SCC_STATUS_NOTCONTROLLED Plik nie jest pod kontrolą źródła.

 SCC_STATUS_CONTROLLED Plik jest pod kontrolą źródła.

 SCC_STATUS_CHECKEDOUT Wyewidencjonowany przez bieżącego użytkownika na dysku lokalnym.

 SCC_STATUS_OUTOTHER Plik jest wyewidencjonowany przez innego użytkownika.

 SCC_STATUS_OUTEXCLUSIVE Plik jest wyłącznie wyewidencjonowany.

 SCC_STATUS_OUTMULTIPLE plik jest wyewidencjonowany przez więcej niż jednego użytkownika.

 SCC_STATUS_OUTOFDATE Plik nie jest najnowszy.

 SCC_STATUS_DELETED Plik został usunięty z projektu.

 SCC_STATUS_LOCKED plik jest zablokowany; nie więcej wersji dozwolone.

 SCC_STATUS_MERGED Plik został scalony, ale nie został jeszcze naprawiony/zweryfikowany.

 SCC_STATUS_SHARED Plik jest współużytkowana między projektami.

 SCC_STATUS_PINNED Plik jest współużytkowana w wersji jawnej.

 SCC_STATUS_MODIFIED Plik został zmodyfikowany/uszkodzony/naruszony.

 SCC_STATUS_OUTBYUSER Plik jest wyewidencjonowany przez bieżącego użytkownika.

 SCC_STATUS_NOMERGE plik nigdy nie może być scalany z i nie muszą być zapisywane przed GET.

 SCC_STATUS_RESERVED_1 zarezerwowane do użytku wewnętrznego.

 SCC_STATUS_RESERVED_2 zarezerwowane do użytku wewnętrznego.

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
