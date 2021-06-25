---
title: Moduł wyliczający kod | Microsoft Docs
description: Moduł wyliczający kod polecenia jest używany w opcjach SccGetCommandOptions i SccPopulateListto, aby wskazać polecenie, dla którego określono opcje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b97d5083c4f262ae2d86aeef5ee2627fdc854bcb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901386"
---
# <a name="command-code-enumerator"></a>Moduł wyliczający kod polecenia
Ten moduł wyliczający jest używany w opcjach [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) i [SccPopulateList,](../extensibility/sccpopulatelist-function.md)aby wskazać polecenie, dla którego określono opcje.

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
SCC_COMMAND_GET odpowiada [sccGet](../extensibility/sccget-function.md).

SCC_COMMAND_CHECKOUT odpowiada [sccCheckout](../extensibility/scccheckout-function.md).

SCC_COMMAND_CHECKIN odpowiada [sccCheckin](../extensibility/scccheckin-function.md).

SCC_COMMAND_UNCHECKOUT odpowiada [sccUncheckout](../extensibility/sccuncheckout-function.md).

SCC_COMMAND_ADD odpowiada [sccAdd](../extensibility/sccadd-function.md).

SCC_COMMAND_REMOVE odpowiada [SccRemove](../extensibility/sccremove-function.md).

SCC_COMMAND_DIFF odpowiada [sccDiff](../extensibility/sccdiff-function.md).

SCC_COMMAND_HISTORY odpowiada [sccHistory](../extensibility/scchistory-function.md).

SCC_COMMAND_RENAME odpowiada nazwie [SccRename.](../extensibility/sccrename-function.md)

SCC_COMMAND_PROPERTIES odpowiada [właściwościom SccProperties.](../extensibility/sccproperties-function.md)

SCC_COMMAND_OPTIONS odpowiada [sccSetOption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
