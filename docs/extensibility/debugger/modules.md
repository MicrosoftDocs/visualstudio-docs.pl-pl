---
title: Moduły | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: abdf76c7f5f031d2ef7f3bcac2bae8a2c508b783
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738350"
---
# <a name="modules"></a>Moduły
W odniesieniu do architektury debugera, *modułu*:

- Jest fizycznym kontenerem kodu, takim jak plik wykonywalny lub biblioteka DLL.

- Może Załaduj ponownie symbole i opisać siebie. Opisy modułów są wyświetlane w oknie Moduły środowiska IDE.

- Jest reprezentowany przez interfejs [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) utworzony przez aparat debugowania do opisywania modułu.

## <a name="see-also"></a>Zobacz też
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
