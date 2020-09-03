---
title: Serwery (Visual Studio SDK) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712895"
---
# <a name="servers-visual-studio-sdk"></a>Serwery (zestaw SDK programu Visual Studio)
W architekturze debugera *serwer*programu:

- Jest kontenerem portów i dostawców portów, który komunikuje porty i dostawcy portów z menedżerem debugowania sesji (SDM) i aparatami debugowania.

- Może identyfikować siebie według nazwy i wyliczać jej porty i dostawców portów.

- Jest reprezentowany przez interfejs [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) , który jest implementowany tylko przez program Visual Studio (jedno wystąpienie serwera dla każdego wystąpienia programu Visual Studio uruchomionego).

## <a name="see-also"></a>Zobacz też
- [Porty](../../extensibility/debugger/ports.md)
- [Dostawcy portów](../../extensibility/debugger/port-suppliers.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
