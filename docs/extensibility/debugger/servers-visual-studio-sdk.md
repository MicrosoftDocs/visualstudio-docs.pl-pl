---
title: Serwery (Visual Studio SDK) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32fdbb5afca40c3b4fced468d2f9ef0ea5226c00
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712895"
---
# <a name="servers-visual-studio-sdk"></a>Serwery (zestaw SDK programu Visual Studio)
W architekturze debugera *serwer:*

- Jest kontenerem portów i dostawców portów i komunikuje porty i dostawców portów do menedżera debugowania sesji (SDM) i aparatów debugowania.

- Można zidentyfikować się według nazwy i wyliczyć jego portów i dostawców portów.

- Jest reprezentowany przez interfejs [IDebugCoreServer2,](../../extensibility/debugger/reference/idebugcoreserver2.md) który jest implementowany tylko przez program Visual Studio (jedno wystąpienie serwera dla każdego wystąpienia programu Visual Studio uruchomione).

## <a name="see-also"></a>Zobacz też
- [Porty](../../extensibility/debugger/ports.md)
- [Dostawcy portów](../../extensibility/debugger/port-suppliers.md)
- [Pojęcia debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
