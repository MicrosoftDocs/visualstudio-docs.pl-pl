---
title: Pakiet debugowania | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739018"
---
# <a name="debug-package"></a>Pakiet debugowania
Pakiet debugowania jest uruchamiany w powłoce programu Visual Studio i obsługuje cały interfejs użytkownika. Zużywa interfejsy debugowania programu Visual Studio i komunikuje się z menedżerem debugowania sesji (SDM).

 Przerwij zdarzenia wysyłane za pośrednictwem SDM przełączyć debugera z trybu uruchamiania do trybu przerwania i zmienić fokus do programu, w którym wystąpił przerwa. Pakiet debugowania śledzi ramki stosu i wątku z informacji wysyłanych do niego przez zdarzenia.

 Pakiet debugowania nie ma zależności w języku ani środowisku wykonywania. Nie jest konieczne implementowanie lub modyfikowanie pakietu debugowania.

 Pakiet debugowania jest implementowany przez *plik vsdebug.dll*.

## <a name="see-also"></a>Zobacz też
- [Menedżer debugowania sesji](../../extensibility/debugger/session-debug-manager.md)
- [Ramki stosu](../../extensibility/debugger/stack-frames.md)
- [Wątki](../../extensibility/debugger/threads.md)
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
