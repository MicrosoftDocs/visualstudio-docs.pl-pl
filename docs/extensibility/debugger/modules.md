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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9aa0aaf7e82287c1dc2e35c524798a3480d2573e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926323"
---
# <a name="modules"></a>Moduły
W odniesieniu do architektury debugera, *modułu*:

- Jest fizycznym kontenerem kodu, takim jak plik wykonywalny lub biblioteka DLL.

- Może Załaduj ponownie symbole i opisać siebie. Opisy modułów są wyświetlane w oknie Moduły środowiska IDE.

- Jest reprezentowany przez interfejs [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) utworzony przez aparat debugowania do opisywania modułu.

## <a name="see-also"></a>Zobacz też
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
