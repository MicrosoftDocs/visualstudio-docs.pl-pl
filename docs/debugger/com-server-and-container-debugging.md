---
title: Debugowanie kontenera i serwera COM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- COM servers, debugging
- ActiveX controls, debugging
- COM [Visual Studio], debugging
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec5ed51c72ad7fd64bbdfd0135f53a13bb8c6e4b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72745679"
---
# <a name="com-server-and-container-debugging"></a>Debugowanie kontenera i serwera COM
Aplikacje COM wykonują wiele zadań poza bezpośrednią kontrolą programisty. Komunikacja między bibliotekami DLL, licznikami użycia obiektów i operacjami schowka to tylko kilka obszarów, w których może wystąpić nieoczekiwane zachowanie. W takim przypadku pierwszym krokiem jest śledzenie źródła problemu.

 Debuger programu Visual Studio obsługuje krokowe przechodzenie między kontenerami i serwerami. Obejmuje to możliwość wykonywania kroków w ramach zdalnych wywołań procedur (RPC).

## <a name="debugging-a-com-server-and-container-in-the-same-solution"></a><a name="BKMK_COMServerandContainerintheSameSolution"></a> Debugowanie serwera COM i kontenera w tym samym rozwiązaniu
 Można debugować serwer COM i kontener przy użyciu dwóch projektów w ramach tego samego rozwiązania. Ustaw odpowiednie punkty przerwania w każdym projekcie i Debuguj. Gdy kontener wykonuje wywołanie do serwera, który trafi do punktu przerwania, kontener będzie oczekiwać do momentu, aż kod serwera zwróci wartość (czyli do momentu zakończenia debugowania).

 Debugowanie kontenera COM jest podobne do debugowania programu standardowego. Jedna różnica polega na debugowaniu zdarzenia, które generuje wywołanie zwrotne (na przykład przeciąganie danych przez aplikację kontenera). W takim przypadku należy ustawić punkt przerwania w funkcji wywołania zwrotnego.

## <a name="debugging-a-server-application-without-container-information"></a><a name="BKMK_ServerApplicationWithoutContainerInformation"></a> Debugowanie aplikacji serwera bez informacji o kontenerach
 Jeśli nie masz lub nie chcesz używać informacji debugowania dla aplikacji kontenera, rozpoczęcie debugowania aplikacji serwera jest procesem dwuetapowym:

1. Rozpocznij debugowanie serwera jako zwykłej aplikacji.

2. Ustaw punkty przerwania zgodnie z potrzebami.

3. Uruchom aplikację kontenera.

## <a name="debugging-a-server-and-domain-isolation-sdi-application"></a><a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> Debugowanie aplikacji do izolacji serwera i domeny (SDI)
 W przypadku debugowania aplikacji serwera SDI należy określić `/Embedding` lub `/Automation` w właściwości **argumenty wiersza polecenia** w oknie dialogowym strony właściwości *projektu* dla projektów C/C++, C# lub Visual Basic.

 Za pomocą tych argumentów wiersza polecenia debuger może uruchomić aplikację serwera, tak jakby była uruchamiana z kontenera. Uruchomienie kontenera z Menedżera programu lub Menedżera plików spowoduje, że kontener użyje wystąpienia serwera uruchomionego w debugerze.

 Aby uzyskać dostęp do okna dialogowego strony właściwości *projektu* , kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań, a następnie wybierz polecenie Właściwości z menu skrótów. Aby znaleźć Właściwość argumenty wiersza polecenia, rozwiń kategorię właściwości konfiguracji i kliknij stronę debugowanie.

## <a name="see-also"></a>Zobacz też

- [COM i debugowanie ActiveX](../debugger/com-and-activex-debugging.md)