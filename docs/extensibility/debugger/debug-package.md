---
title: Pakiet debugowania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ba784f3a544b2f66f1f2c9c229f85477bf6c782
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705877"
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