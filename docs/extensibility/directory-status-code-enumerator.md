---
title: Moduł wyliczający kod stanu katalogu | Microsoft Docs
description: Moduł wyliczający SccDirStatus zawiera nazwane wartości stałych, które określają stan katalogu w systemie kontroli źródła i są używane przez SccDirQueryInfo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a504c6c080c34b4506cf4078b64465a3bd6c7d97
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904233"
---
# <a name="directory-status-code-enumerator"></a>Moduł wyliczający kod stanu katalogu
Moduł `SccDirStatus` wyliczający zawiera nazwane wartości stałych, które określają stan katalogu w systemie kontroli źródła. To wyliczenie jest używane przez [SccDirQueryInfo.](../extensibility/sccdirqueryinfo-function.md) Zostało to wprowadzone w wersji 1.2 interfejsu API wtyczki kontroli kodu źródłowego.

## <a name="syntax"></a>Składnia

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>Elementy członkowskie
 SCC_DIRSTATUS_INVALID nie można uzyskać stanu; Nie należy polegać na tym.

 SCC_DIRSTATUS_NOTCONTROLLED Directory nie jest pod kontrolą źródła.

 SCC_DIRSTATUS_CONTROLLED Directory jest pod kontrolą źródła.

 SCC_DIRSTATUS_EMPTYPROJ Project odpowiadający temu katalogowi jest pusty.

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
