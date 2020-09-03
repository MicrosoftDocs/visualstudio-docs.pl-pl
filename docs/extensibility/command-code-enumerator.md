---
title: Moduł wyliczający kod polecenia | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739789"
---
# <a name="command-code-enumerator"></a>Moduł wyliczający kod polecenia
Ten moduł wyliczający jest używany w opcjach dla [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) i [SccPopulateList](../extensibility/sccpopulatelist-function.md), aby wskazać polecenie, dla którego są określone opcje.

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
SCC_COMMAND_GET odnosi się do [SccGet](../extensibility/sccget-function.md).

SCC_COMMAND_CHECKOUT odnosi się do [SccCheckout](../extensibility/scccheckout-function.md).

SCC_COMMAND_CHECKIN odnosi się do [SccCheckin](../extensibility/scccheckin-function.md).

SCC_COMMAND_UNCHECKOUT odnosi się do [SccUncheckout](../extensibility/sccuncheckout-function.md).

SCC_COMMAND_ADD odnosi się do [SccAdd](../extensibility/sccadd-function.md).

SCC_COMMAND_REMOVE odnosi się do [SccRemove](../extensibility/sccremove-function.md).

SCC_COMMAND_DIFF odnosi się do [SccDiff](../extensibility/sccdiff-function.md).

SCC_COMMAND_HISTORY odnosi się do [SccHistory](../extensibility/scchistory-function.md).

SCC_COMMAND_RENAME odnosi się do [SccRename](../extensibility/sccrename-function.md).

SCC_COMMAND_PROPERTIES odnosi się do [SccProperties](../extensibility/sccproperties-function.md).

SCC_COMMAND_OPTIONS odnosi się do [SccSetOption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
