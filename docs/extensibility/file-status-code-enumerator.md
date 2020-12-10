---
title: Moduł wyliczający kod stanu pliku | Microsoft Docs
description: Moduł wyliczający SccStatus zawiera wartości stałe, które określają stan pliku w systemie kontroli źródła i jest używany przez SccQueryInfo i POPLISTFUNC.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 0093e3a79a5a9caf9846c4b418226568e37828f0
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994488"
---
# <a name="file-status-code-enumerator"></a>Moduł wyliczający kod stanu pliku
`SccStatus`Moduł wyliczający zawiera nazwane wartości stałe, które określają stan pliku w systemie kontroli źródła. To wyliczenie jest używane przez [SccQueryInfo](../extensibility/sccqueryinfo-function.md) i `POPLISTFUNC` funkcję wywołania zwrotnego (zobacz [POPLISTFUNC](../extensibility/poplistfunc.md) , aby uzyskać szczegółowe informacje).

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
 Nie można uzyskać stanu SCC_STATUS_INVALID; nie należy polegać na nim.

 Plik SCC_STATUS_NOTCONTROLLED nie znajduje się pod kontrolą źródła.

 Plik SCC_STATUS_CONTROLLED jest pod kontrolą źródła.

 SCC_STATUS_CHECKEDOUT wyewidencjonowany przez bieżącego użytkownika na dysku lokalnym.

 Plik SCC_STATUS_OUTOTHER został wyewidencjonowany przez innego użytkownika.

 Plik SCC_STATUS_OUTEXCLUSIVE jest wyewidencjonowany na wyłączność.

 Plik SCC_STATUS_OUTMULTIPLE został wyewidencjonowany przez więcej niż jednego użytkownika.

 SCC_STATUS_OUTOFDATE plik nie jest najnowszy.

 Plik SCC_STATUS_DELETED został usunięty z projektu.

 Plik SCC_STATUS_LOCKED jest zablokowany; nie ma więcej wersji.

 Plik SCC_STATUS_MERGED został scalony, ale nie został jeszcze ustalony/zweryfikowany.

 Plik SCC_STATUS_SHARED jest współużytkowany między projektami.

 Plik SCC_STATUS_PINNED jest udostępniany w wersji jawnej.

 Plik SCC_STATUS_MODIFIED został zmodyfikowany/złamany/naruszony.

 Plik SCC_STATUS_OUTBYUSER został wyewidencjonowany przez bieżącego użytkownika.

 Plik SCC_STATUS_NOMERGE nigdy nie może zostać scalony z i nie musi być zapisany przed GET.

 SCC_STATUS_RESERVED_1 zarezerwowane do użytku wewnętrznego.

 SCC_STATUS_RESERVED_2 zarezerwowane do użytku wewnętrznego.

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
