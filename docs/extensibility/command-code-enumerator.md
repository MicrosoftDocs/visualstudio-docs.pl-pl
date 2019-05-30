---
title: Moduł wyliczający kod polecenia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4ec14c15bbd0aa6340e30e3156e714ba5f9e074
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334968"
---
# <a name="command-code-enumerator"></a>Moduł wyliczający kod polecenia
Ten moduł wyliczający jest używany w opcji [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) i [SccPopulateList](../extensibility/sccpopulatelist-function.md)aby wskazać polecenie, dla której są określone opcje.

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
Odpowiada SCC_COMMAND_GET [SccGet](../extensibility/sccget-function.md).

Odpowiada SCC_COMMAND_CHECKOUT [SccCheckout](../extensibility/scccheckout-function.md).

Odpowiada SCC_COMMAND_CHECKIN [SccCheckin](../extensibility/scccheckin-function.md).

Odpowiada SCC_COMMAND_UNCHECKOUT [SccUncheckout](../extensibility/sccuncheckout-function.md).

Odpowiada SCC_COMMAND_ADD [SccAdd](../extensibility/sccadd-function.md).

Odpowiada SCC_COMMAND_REMOVE [SccRemove](../extensibility/sccremove-function.md).

Odpowiada SCC_COMMAND_DIFF [SccDiff](../extensibility/sccdiff-function.md).

Odpowiada SCC_COMMAND_HISTORY [SccHistory](../extensibility/scchistory-function.md).

Odpowiada SCC_COMMAND_RENAME [SccRename](../extensibility/sccrename-function.md).

Odpowiada SCC_COMMAND_PROPERTIES [SccProperties](../extensibility/sccproperties-function.md).

Odpowiada SCC_COMMAND_OPTIONS [SccSetOption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>Zobacz także
- [Wtyczek kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
