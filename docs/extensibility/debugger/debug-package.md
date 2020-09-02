---
title: Debuguj pakiet | Microsoft Docs
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
ms.openlocfilehash: de6240ea5d938d02f8415009203962e124ff049e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739018"
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
