---
title: Moduły | Microsoft Docs
description: W tym artykule opisano definicje i rolę modułu w architekturze debugera w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f40cb7d0c65822fcb6ba4d4ca0132147f62d9286
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054767"
---
# <a name="modules"></a>Moduły
W odniesieniu do architektury debugera, *modułu*:

- Jest fizycznym kontenerem kodu, takim jak plik wykonywalny lub biblioteka DLL.

- Może Załaduj ponownie symbole i opisać siebie. Opisy modułów są wyświetlane w oknie Moduły środowiska IDE.

- Jest reprezentowany przez interfejs [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) utworzony przez aparat debugowania do opisywania modułu.

## <a name="see-also"></a>Zobacz też
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
