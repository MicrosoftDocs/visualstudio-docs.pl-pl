---
title: Debugowanie kontenera i serwera COM | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- COM servers, debugging
- ActiveX controls, debugging
- COM [Visual Studio], debugging
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 631b1d35a0878bfc362b03751f35909839c7da19
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60088057"
---
# <a name="com-server-and-container-debugging"></a>Debugowanie kontenera i serwera COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikacje COM wykonywanie szeregu zadań poza programisty bezpośrednią kontrolę. Komunikacja między bibliotek DLL, liczniki użycia obiektów i operacje na schowku przedstawiono kilka obszarów, w którym mogą wystąpić nieoczekiwane zachowanie. W takim przypadku Twoim pierwszym krokiem jest śledzenie źródła problemu.  
  
 Debuger programu Visual Studio obsługuje przechodzenie między oraz kontenery i serwery. Obejmuje to możliwość krok w zdalnych wywołań procedur (RPC).  
  
## <a name="BKMK_COMServerandContainerintheSameSolution"></a> Debugowanie kontenera w tym samym rozwiązaniu i serwera COM  
 Można debugować kontenera za pomocą dwóch projektów w obrębie tego samego rozwiązania i serwera COM. Ustaw odpowiednie punkty przerwania w każdym projekcie i debugowania. Gdy kontener wywołuje do serwera, na którym trafienia punktu przerwania, kontener będzie czekał kod serwera zwraca (oznacza to, aż do zakończenia jej debugowanie).  
  
 Debugowanie kontenerów COM jest podobne do debugowania program standardowy. Jedną różnicaą jest to podczas debugowania zdarzeń, która generuje wywołanie zwrotne (na przykład przeciągnięcie danych za pośrednictwem aplikacji kontenera). W takim przypadku należy ustawić punkt przerwania w funkcji wywołania zwrotnego.  
  
## <a name="BKMK_ServerApplicationWithoutContainerInformation"></a> Debugowanie aplikacji serwera bez informacji o kontenerze  
 Jeśli nie masz, lub nie chcesz użyć informacji debugowania dla aplikacji kontenera, uruchamianie na potrzeby debugowania aplikacji serwera jest procesem trzech kroków:  
  
1. Rozpocznij debugowanie serwera jako normalna aplikacja.  
  
2. Ustaw punkty przerwania, zgodnie z potrzebami.  
  
3. Uruchom aplikację kontenera.  
  
## <a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> Debugowanie serwera i aplikacji (SDI) izolacji domeny  
 Jeśli debugujesz aplikację serwera SDI, należy określić `/Embedding` lub `/Automation` w **argumenty wiersza polecenia** właściwość *projektu* okno dialogowe strony właściwości dla C/C++, C#, lub Projekty języka Visual Basic.  
  
 Za pomocą tych argumentów wiersza polecenia debugera można uruchomić aplikacji serwera, tak, jakby zostały uruchomione z kontenera. Uruchamianie kontenera za pomocą Menedżera programu lub Menedżer plików następnie spowoduje, że kontener, aby użyć wystąpienia programu server uruchomiony w debugerze.  
  
 Aby uzyskać dostęp do *projektu* okno dialogowe strony właściwości, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, a następnie z menu skrótów wybierz polecenie Właściwości. Aby znaleźć właściwości argumenty wiersza polecenia, rozwiń kategorię właściwości konfiguracji, a następnie kliknij przycisk na stronie debugowanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji COM i kontrolek ActiveX](../debugger/com-and-activex-debugging.md)
