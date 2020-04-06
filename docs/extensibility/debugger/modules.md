---
title: Moduły | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738350"
---
# <a name="modules"></a>Moduły
Jeśli chodzi o architekturę debugera, *moduł:*

- Jest fizycznym kontenerem kodu, takim jak plik wykonywalny lub biblioteka DLL.

- Może przeładować swoje symbole i opisać siebie. Opisy modułów są wyświetlane w oknie Moduły IDE.

- Jest reprezentowany przez interfejs [IDebugModule2,](../../extensibility/debugger/reference/idebugmodule2.md) utworzony przez aparat debugowania do opisania modułu.

## <a name="see-also"></a>Zobacz też
- [Pojęcia debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
