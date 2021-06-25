---
title: Debugowanie pakietu | Microsoft Docs
description: Dowiedz się, jak pakiet debugowania działa w Visual Studio i obsługuje interfejs użytkownika, korzystając z interfejsów debugowania i komunikując się z menedżerem debugowania sesji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8be920ae352067a6e77593ca0a922474d68851d9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905673"
---
# <a name="debug-package"></a>Pakiet debugowania
Pakiet debugowania jest uruchamiany w Visual Studio i obsługuje cały interfejs użytkownika. Zużywa ona interfejsy Visual Studio debugowania i komunikuje się z menedżerem debugowania sesji (SDM).

 Zdarzenia przerwania wysyłane przez program SDM przełącz debuger z trybu uruchamiania na tryb przerwania i zmień fokus na program, w którym wystąpiła przerwa. Pakiet debugowania śledzi ramkę stosu i wątek z informacji wysyłanych do niego przez zdarzenia.

 Pakiet debugowania nie ma zależności między językiem ani środowiskiem uruchomieniowym. Nie jest konieczne implementowanie ani modyfikowanie pakietu debugowania.

 Pakiet debugowania jest implementowany przez *vsdebug.dll*.

## <a name="see-also"></a>Zobacz też
- [Menedżer debugowania sesji](../../extensibility/debugger/session-debug-manager.md)
- [Ramki stosu](../../extensibility/debugger/stack-frames.md)
- [Wątki](../../extensibility/debugger/threads.md)
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
