---
title: Moduły | Microsoft Docs
description: W tym artykule opisano definicję i rolę modułu w architekturze debugera w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 03a3ad588b0a2e0f3aa6f04ddeb742ab66064bc9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902608"
---
# <a name="modules"></a>Moduły
Jeśli chodzi o architekturę debugera, *moduł*:

- Jest fizycznym kontenerem kodu, takim jak plik wykonywalny lub biblioteka DLL.

- Może ponownie załadować symbole i opisać siebie. Opisy modułów są wyświetlane w oknie Moduły środowiska IDE.

- Jest reprezentowany przez [interfejs IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) utworzony przez aparat debugowania w celu opisania modułu.

## <a name="see-also"></a>Zobacz też
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
