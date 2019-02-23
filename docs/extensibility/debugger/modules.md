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
ms.openlocfilehash: 1f31e3760a0697be8c9fc80eb811c99df79d32b1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718914"
---
# <a name="modules"></a>Moduły
Pod względem architektury debugera *modułu*:

-   Jest kontenerem fizycznych kodu, takie jak plik wykonywalny lub bibliotekę DLL.

-   Można ponownie załadować jej symboli i opisania siebie. Moduł opisy są wyświetlane w oknie moduły środowiska IDE.

-   Jest reprezentowany przez [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interfejsu, utworzonych przez aparat debugowania w celu opisania modułu.

## <a name="see-also"></a>Zobacz także
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)