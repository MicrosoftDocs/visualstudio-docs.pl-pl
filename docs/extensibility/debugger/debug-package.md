---
title: Pakiet debugowania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb1af813fabb1245d85fe18629d77a45f6acca3f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345909"
---
# <a name="debug-package"></a>Pakiet debugowania
Pakiet debugowania jest uruchamiane w powłoce programu Visual Studio i obsługuje cały interfejs użytkownika. On wykorzystuje interfejsy debugowania programu Visual Studio i komunikuje się z usługą Menedżer debugowania sesji (SDM).

 Zdarzenia przerwania wysyłane za pośrednictwem SDM Przełącz debugera w trybie uruchamiania tryb przerwania i zmianie fokusu do programu, w którym wystąpiło przerwanie. Debugowanie pakietu śledzi ramki stosu i wątku z informacje wysyłane do niej przez zdarzenia.

 Debugowanie pakietu nie ma języka lub zależności środowiska uruchomieniowego. Nie jest niezbędne do wdrożenia lub zmodyfikować pakiet debugowania.

 Debugowanie pakietu jest implementowany przez *vsdebug.dll*.

## <a name="see-also"></a>Zobacz także
- [Menedżer debugowania sesji](../../extensibility/debugger/session-debug-manager.md)
- [Ramki stosu](../../extensibility/debugger/stack-frames.md)
- [Wątki](../../extensibility/debugger/threads.md)
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)