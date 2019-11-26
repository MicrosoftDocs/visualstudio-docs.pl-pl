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
ms.openlocfilehash: 13fd54eeebf0323fcb9b8cad6a8cd8b75ae11fb3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292892"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Instrukcje: wywoływanie debugera przepływu pracy
Ogólnie rzecz biorąc, można debugować przepływy pracy, podobnie jak debugowanie programów utworzonych w innych językach programowania programu Visual Studio. Debuger przepływu pracy można uruchomić w następujący sposób:

- Wybierz opcję **Dołącz do procesu** w menu **Debuguj** , aby wybrać uruchomiony proces hosta dla wystąpienia przepływu pracy. Ta procedura jest taka sama jak dołączanie do procesu hosta w kodzie zarządzanym.

- Naciśnij klawisz **F5** , aby rozpocząć Uruchamianie wystąpienia przepływu pracy lub kontynuować działanie po trafieniu punktu przerwania.

- Używaj zdalnego debugowania. Aby uzyskać informacje na temat korzystania z debugowania zdalnego, zobacz [How to: Enable Remote Debug](https://go.microsoft.com/fwlink/?LinkId=196257).

    > [!NOTE]
    > Jeśli aplikacja przepływu pracy jest ukierunkowana na architekturę x86 i jest hostowana na maszynie z systemem 64 bitowego systemu operacyjnego, debugowanie zdalne nie będzie działać, jeśli [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] nie zostanie zainstalowana na maszynie zdalnej lub obiekt docelowy dla aplikacji przepływu pracy zostanie zmieniony na **dowolny procesor CPU**.

### <a name="stepping-through-code"></a>Krokowe przechodzenie przez kod

- **Krok w**: możesz przejść do działania przy użyciu klawisza **F11**. Debuger nie wchodzi do dowolnej procedury obsługi, który jest zdefiniowany. Jeśli żadna procedura obsługi nie jest zdefiniowany, Przekrocz działania lub za pomocą złożonych działań, które zawierają inne działania, wkroczenia do pierwszego działania wykonywania.

- **Wyjdź:** Możesz przejść do działania przy użyciu **klawisza Shift-F11**. Przechodzenie krok po kroku, poza działanie uruchamia bieżące działanie i jego element równorzędny działania ukończone. Debuger jest następnie przerywa w nadrzędnego bieżącego działania. Przy przechodzeniu od obsługi kodu, debuger przerywa na działaniu, z którą jest skojarzony program obsługi.

- **Przekroczenie: możesz**przekroczyć działanie, używając klawisza **F10**. Podczas wykonywania stopniowego działania złożonego debuger przerwie się w pierwszym pliku podrzędnym działania złożonego. Podczas wykonywania stopniowego wstawiania niezłożonego, takiego jak działanie <xref:System.Activities.Statements.Assign>, debuger wykonuje działanie i skojarzone z nim procedury obsługi oraz przerwie w następnym działaniu. Jeśli wykonywane działanie jest ostatnim działaniem podrzędnym działania złożonego, po wykonaniu debuger przerwie w działaniu nadrzędnym.

### <a name="debugging-with-f5"></a>Debugowanie za pomocą F5

- Jeśli tworzysz projekt aplikacji konsolowej przepływu pracy, po prostu naciśnij klawisz **F5** , aby rozpocząć debugowanie do aplikacji i przepływu pracy. Jeśli tworzysz bibliotekę działań samodzielnie, musisz mieć jako projekt startowy aplikację hosta wykonywalnego. Aby ustawić projekt startowy w **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu hosta i wybierz pozycję **Ustaw jako projekt startowy**.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: ustawianie punktów przerwania w](../workflow-designer/how-to-set-breakpoints-in-workflows.md) przepływach pracy debugowania dla przepływów pracy [za pomocą Projektant przepływu pracy](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)