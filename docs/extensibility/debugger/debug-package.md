---
title: Debuguj pakiet | Microsoft Docs
description: Dowiedz się, jak działa pakiet debugowania w programie Visual Studio Shell i obsługuje interfejs użytkownika, wykorzystując interfejsy debugowania i komunikując się z menedżerem debugowania sesji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad62a487d38500617999a276aa3ae15a75089736
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914130"
---
# <a name="debug-package"></a>Debuguj pakiet
Pakiet debugowania działa w programie Visual Studio Shell i obsługuje cały interfejs użytkownika. Korzysta ona z interfejsów debugowania programu Visual Studio i komunikuje się z menedżerem debugowania sesji (SDM).

 Zdarzenia przerwania wysyłane przez model SDM przełączają debuger z trybu uruchamiania do trybu przerwania i zmieniają fokus w programie, w którym wystąpiła przerwanie. Pakiet debugowania śledzi ramkę stosu i wątek z informacji wysyłanych do niego przez zdarzenia.

 Pakiet debugowania nie ma zależności w języku ani środowisku czasu wykonywania. Nie trzeba implementować ani modyfikować pakietu debugowania.

 Pakiet debugowania jest implementowany przez *vsdebug.dll*.

## <a name="see-also"></a>Zobacz też
- [Menedżer debugowania sesji](../../extensibility/debugger/session-debug-manager.md)
- [Ramki stosu](../../extensibility/debugger/stack-frames.md)
- [Wątki](../../extensibility/debugger/threads.md)
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
