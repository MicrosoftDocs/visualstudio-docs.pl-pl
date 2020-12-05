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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 57202231c1bbfc7712d322b8cc7a30e3f64c87af
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606648"
---
# <a name="modules"></a>Moduły
W odniesieniu do architektury debugera, *modułu*:

- Jest fizycznym kontenerem kodu, takim jak plik wykonywalny lub biblioteka DLL.

- Może Załaduj ponownie symbole i opisać siebie. Opisy modułów są wyświetlane w oknie Moduły środowiska IDE.

- Jest reprezentowany przez interfejs [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) utworzony przez aparat debugowania do opisywania modułu.

## <a name="see-also"></a>Zobacz także
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
