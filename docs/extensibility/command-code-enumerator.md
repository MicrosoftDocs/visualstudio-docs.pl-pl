---
title: Wyliczacz kodu polecenia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15916d26ac0120417205af0bb9117a45ec0397c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739789"
---
# <a name="command-code-enumerator"></a>Wyliczacz kodu polecenia
Ten wyliczyć jest używany w opcjach [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) i [SccPopulateList,](../extensibility/sccpopulatelist-function.md)aby wskazać polecenie, dla którego opcje są określone.

## <a name="syntax"></a>Składnia

```
enum SCCCOMMAND {
   SCC_COMMAND_GET,
   SCC_COMMAND_CHECKOUT,
   SCC_COMMAND_CHECKIN,
   SCC_COMMAND_UNCHECKOUT,
   SCC_COMMAND_ADD,
   SCC_COMMAND_REMOVE,
   SCC_COMMAND_DIFF,
   SCC_COMMAND_HISTORY,
   SCC_COMMAND_RENAME,
   SCC_COMMAND_PROPERTIES,
   SCC_COMMAND_OPTIONS
};
```

## <a name="members"></a>Elementy członkowskie
SCC_COMMAND_GET odpowiada [SccGet](../extensibility/sccget-function.md).

SCC_COMMAND_CHECKOUT odpowiada [SccCheckout](../extensibility/scccheckout-function.md).

SCC_COMMAND_CHECKIN odpowiada [SccCheckin](../extensibility/scccheckin-function.md).

SCC_COMMAND_UNCHECKOUT odpowiada [SccUncheckout](../extensibility/sccuncheckout-function.md).

SCC_COMMAND_ADD odpowiada [SccAdd](../extensibility/sccadd-function.md).

SCC_COMMAND_REMOVE odpowiada [SccRemove](../extensibility/sccremove-function.md).

SCC_COMMAND_DIFF odpowiada [SccDiff](../extensibility/sccdiff-function.md).

SCC_COMMAND_HISTORY odpowiada [SccHistory](../extensibility/scchistory-function.md).

SCC_COMMAND_RENAME odpowiada [SccRename](../extensibility/sccrename-function.md).

SCC_COMMAND_PROPERTIES odpowiada [właściwościom SccProperties](../extensibility/sccproperties-function.md).

SCC_COMMAND_OPTIONS odpowiada [SccSetOption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
