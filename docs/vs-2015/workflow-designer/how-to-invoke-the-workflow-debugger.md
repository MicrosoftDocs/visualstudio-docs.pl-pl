---
title: 'Instrukcje: wywoływanie debugera przepływu pracy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e702b402d5350641aa01d341106634efe5f6c6c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849266"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Instrukcje: Wywoływanie debugera przepływu pracy
Ogólnie rzecz biorąc, można debugować przepływy pracy, podobnie jak debugowanie programów utworzonych w innych językach programowania programu Visual Studio. Debuger przepływu pracy można uruchomić w następujący sposób:

- Wybierz opcję **Dołącz do procesu** w menu **Debuguj** , aby wybrać uruchomiony proces hosta dla wystąpienia przepływu pracy. Ta procedura jest taka sama jak dołączanie do procesu hosta w kodzie zarządzanym.

- Naciśnij klawisz **F5** , aby rozpocząć Uruchamianie wystąpienia przepływu pracy lub kontynuować działanie po trafieniu punktu przerwania.

- Używaj zdalnego debugowania. Aby uzyskać informacje na temat korzystania z debugowania zdalnego, zobacz [How to: Enable Remote Debug](https://msdn.microsoft.com/library/febz73k0.aspx).

    > [!NOTE]
    > Jeśli aplikacja przepływu pracy jest ukierunkowana na architekturę x86 i jest hostowana na maszynie z systemem 64 bitowego systemu operacyjnego, debugowanie zdalne nie będzie działać, jeśli nie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] zostanie zainstalowane na maszynie zdalnej lub obiekt docelowy dla aplikacji przepływu pracy zostanie zmieniony na **dowolny procesor CPU**.

### <a name="stepping-through-code"></a>Krokowe przechodzenie przez kod

- **Krok w**: możesz przejść do działania przy użyciu klawisza **F11**. Debuger kroków do dowolnej zdefiniowanej procedury obsługi. Jeśli nie zdefiniowano programu obsługi, przekroczę działanie lub z działaniami złożonymi, które zawierają inne działania, możesz przejść do pierwszego wykonywanego działania.

- **Wyjdź:** Możesz przejść do działania przy użyciu **klawisza Shift-F11**. Wychodzenie z działania powoduje uruchomienie bieżącego działania i wszystkich jego elementów równorzędnych do ukończenia. Debuger następnie przerwie w elemencie nadrzędnym bieżącego działania. Podczas wykonywania kroków z programu obsługi kodu debuger przerwie się w działaniu, z którym jest skojarzona procedura obsługi.

- **Przekroczenie: możesz**przekroczyć działanie, używając klawisza **F10**. Podczas wykonywania stopniowego działania złożonego debuger przerwie się w pierwszym pliku podrzędnym działania złożonego. Podczas przechodzenia przez nie złożone elementy, takie jak <xref:System.Activities.Statements.Assign> działanie, debuger wykonuje działanie i skojarzone z nim procedury obsługi oraz przerwanie w następnym działaniu. Jeśli wykonywane działanie jest ostatnim działaniem podrzędnym działania złożonego, po wykonaniu debuger przerwie w działaniu nadrzędnym.

### <a name="debugging-with-f5"></a>Debugowanie za pomocą klawisza F5

- Jeśli tworzysz projekt aplikacji konsolowej przepływu pracy, po prostu naciśnij klawisz **F5** , aby rozpocząć debugowanie do aplikacji i przepływu pracy. Jeśli tworzysz bibliotekę działań samodzielnie, musisz mieć jako projekt startowy aplikację hosta wykonywalnego. Aby ustawić projekt startowy w **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu hosta i wybierz pozycję **Ustaw jako projekt startowy**.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: ustawianie punktów przerwania w](../workflow-designer/how-to-set-breakpoints-in-workflows.md) przepływach pracy debugowania dla przepływów pracy [za pomocą Projektant przepływu pracy](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
