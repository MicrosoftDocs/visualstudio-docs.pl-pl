---
title: Moduły | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 611d067030cd935f6957a976c8a3aa2b7d4f8ae3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091307"
---
# <a name="modules"></a>Moduły
Pod względem architektury debugera *modułu*:

- Jest kontenerem fizycznych kodu, takie jak plik wykonywalny lub bibliotekę DLL.

- Można ponownie załadować jej symboli i opisania siebie. Moduł opisy są wyświetlane w oknie moduły środowiska IDE.

- Jest reprezentowany przez [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interfejsu, utworzonych przez aparat debugowania w celu opisania modułu.

## <a name="see-also"></a>Zobacz także
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)