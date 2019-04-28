---
title: Moduł wyliczający kod stanu pliku | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 50312caddf0ce2b5c64d1ec83e1707e2e0ee086e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62863067"
---
# <a name="file-status-code-enumerator"></a>Moduł wyliczający kod stanu pliku
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
 Nie można uzyskać stanu SCC_STATUS_INVALID; nie należy polegać na niej.

 Plik SCC_STATUS_NOTCONTROLLED nie jest pod kontrolą źródła.

 Plik SCC_STATUS_CONTROLLED jest pod kontrolą źródła.

 SCC_STATUS_CHECKEDOUT sprawdzane przez bieżącego użytkownika na dysku lokalnym.

 SCC_STATUS_OUTOTHER plik jest wyewidencjonowany przez innego użytkownika.

 SCC_STATUS_OUTEXCLUSIVE plik jest wyewidencjonowany.

 SCC_STATUS_OUTMULTIPLE plik jest wyewidencjonowany przez więcej niż jednego użytkownika.

 SCC_STATUS_OUTOFDATE pliku nie jest najnowsza.

 Plik SCC_STATUS_DELETED został usunięty z projektu.

 SCC_STATUS_LOCKED plik jest zablokowany; nie dozwolone więcej wersji.

 Plik SCC_STATUS_MERGED została scalona, ale nie zostały jeszcze rozwiązane/weryfikacji.

 SCC_STATUS_SHARED plik jest udostępniony między projektami.

 SCC_STATUS_PINNED plik jest udostępniony do jawnego wersji.

 SCC_STATUS_MODIFIED plik został zmodyfikowany/uszkodzony/naruszono.

 SCC_STATUS_OUTBYUSER plik jest wyewidencjonowany przez bieżącego użytkownika.

 Plik SCC_STATUS_NOMERGE nigdy nie mogą zostać scalone z i nie muszą zostać zapisane przed GET.

 SCC_STATUS_RESERVED_1 zarezerwowane do użytku wewnętrznego.

 SCC_STATUS_RESERVED_2 zarezerwowane do użytku wewnętrznego.

## <a name="see-also"></a>Zobacz także
- [Wtyczek kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)