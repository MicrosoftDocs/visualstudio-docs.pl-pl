---
title: Moduł wyliczający kod polecenia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97b856b0c22631b3e4f9b8860f9aaba728e6944d
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315496"
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
SCC_COMMAND_GET  
Odnosi się do [SccGet](../extensibility/sccget-function.md).

SCC_COMMAND_CHECKOUT  
Odnosi się do [SccCheckout](../extensibility/scccheckout-function.md).

SCC_COMMAND_CHECKIN  
Odnosi się do [SccCheckin](../extensibility/scccheckin-function.md).

SCC_COMMAND_UNCHECKOUT  
Odnosi się do [SccUncheckout](../extensibility/sccuncheckout-function.md).

SCC_COMMAND_ADD  
Odnosi się do [SccAdd](../extensibility/sccadd-function.md).

SCC_COMMAND_REMOVE  
Odnosi się do [SccRemove](../extensibility/sccremove-function.md).

SCC_COMMAND_DIFF  
Odnosi się do [SccDiff](../extensibility/sccdiff-function.md).

SCC_COMMAND_HISTORY  
Odnosi się do [SccHistory](../extensibility/scchistory-function.md).

SCC_COMMAND_RENAME  
Odnosi się do [SccRename](../extensibility/sccrename-function.md).

SCC_COMMAND_PROPERTIES  
Odnosi się do [SccProperties](../extensibility/sccproperties-function.md).

SCC_COMMAND_OPTIONS  
Odnosi się do [SccSetOption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>Zobacz także
[Wtyczek kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)  
[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
[SccPopulateList](../extensibility/sccpopulatelist-function.md)
