---
title: Serwery (Visual Studio SDK) | Microsoft Docs
description: W tym artykule opisano definicję i rolę serwera w architekturze debugera w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 99f6c634053df9191ac419c8ee450dc99cf62c7c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902127"
---
# <a name="servers-visual-studio-sdk"></a>Serwery (zestaw SDK programu Visual Studio)
W architekturze debugera *serwer*:

- Jest kontenerem portów i dostawców portów oraz komunikuje porty i dostawców portów z menedżerem debugowania sesji (SDM) i aparatami debugowania.

- Może identyfikować się według nazwy oraz wyliczać porty i dostawców portów.

- Jest reprezentowany przez [interfejs IDebugCoreServer2,](../../extensibility/debugger/reference/idebugcoreserver2.md) który jest implementowany tylko przez Visual Studio (jedno wystąpienie serwera dla każdego wystąpienia Visual Studio uruchomionego).

## <a name="see-also"></a>Zobacz też
- [Porty](../../extensibility/debugger/ports.md)
- [Dostawcy portów](../../extensibility/debugger/port-suppliers.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
