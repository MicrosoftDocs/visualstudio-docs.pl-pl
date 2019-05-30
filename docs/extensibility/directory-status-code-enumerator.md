---
title: Moduł wyliczający kod stanu katalogu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b6e113949c9e87605895bbb43aa1ae4b4df0496
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348034"
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
 Nie można uzyskać stanu SCC_DIRSTATUS_INVALID; nie należy polegać na niej.

 Katalog SCC_DIRSTATUS_NOTCONTROLLED jest pod kontrolą źródła.

 Katalog SCC_DIRSTATUS_CONTROLLED jest pod kontrolą źródła.

 Projekt SCC_DIRSTATUS_EMPTYPROJ odpowiadający ten katalog jest pusty.

## <a name="see-also"></a>Zobacz także
- [Wtyczek kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)