---
title: Debugowanie lub wyłączanie kodu projektu w Projektancie XAML | Dokumentacja firmy Microsoft
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8773b9f80299c1a46b6a57506d09f9f4ca32b998
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060777"
---
# <a name="debugging-or-disabling-project-code-in-xaml-designer"></a>Debugowanie lub wyłączanie kodu projektu w Projektancie XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W wielu przypadkach nieobsługiwanych wyjątków w Projektancie XAML może być spowodowany kodu projektu, próby uzyskania dostępu do właściwości lub metody, które zwracać różne wartości i pracować na różne sposoby, gdy aplikacja jest uruchomiona w projektancie. Rozwiązania tych wyjątków dzięki możliwości debugowania kodu projektu w innym wystąpieniu programu Visual Studio lub czasowo uniemożliwić ich po wyłączeniu kodu projektu w projektancie.  
  
 Zawiera kod projektu:  
  
- Kontrolki niestandardowe i kontrolki użytkownika  
  
- Biblioteki klas  
  
- Konwertery wartości  
  
- Powiązania względem danych czasu projektowania wygenerowane z kodu projektu  
  
  Po wyłączeniu kodu projektu programu Visual Studio wyświetli symbole zastępcze takie jak nazwa właściwości do powiązania, gdzie dane nie są już dostępne. lub symbol zastępczy dla formantu, który nie jest już uruchomiony.  
  
  ![Nieobsługiwany wyjątek w oknie dialogowym](../designers/media/xaml-unhandledexception.png "XAML_UnhandledException")  
  
#### <a name="to-determine-if-project-code-is-causing-an-exception"></a>Aby określić, jeśli kod projektu powoduje wyjątek  
  
1. W oknie dialogowym nieobsługiwany wyjątek, wybierz **kliknij tutaj, aby załadować ponownie projektanta** łącza.  
  
2. Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie** Aby skompilować i uruchomić aplikację.  
  
     Jeśli aplikacja zostanie skompilowana i zostanie wykonane pomyślnie, wyjątek czasu projektowania może być spowodowane przez działanie kodu projektu w projektancie.  
  
#### <a name="to-debug-project-code-running-in-the-designer"></a>Aby debugować kod projektu w Projektancie  
  
1. W oknie dialogowym nieobsługiwany wyjątek, wybierz **kliknij tutaj, aby wyłączyć uruchamianie kodu projektu i załadować ponownie projektanta** łącza.  
  
2. W Menedżerze zadań Windows, wybierz **Zakończ zadanie** przycisk, aby zamknąć wszystkie wystąpienia projektanta XAML programu Visual Studio, które są aktualnie uruchomione.  
  
     ![Wystąpienia projektanta XAML w Menedżer zadań](../designers/media/xaml-taskmanager.png "XAML_TaskManager")  
  
3. W programie Visual Studio Otwórz stronę XAML, który zawiera kod lub formant, który chcesz debugować.  
  
4. Otwórz nowe wystąpienie programu Visual Studio, a następnie otwórz drugie wystąpienie projektu.  
  
5. Ustaw punkt przerwania w kodzie projektu.  
  
6. W wystąpieniu programu Visual Studio, na pasku menu wybierz **debugowania**, **dołączyć do procesu**.  
  
7. W **dołączyć do procesu** okna dialogowego w **dostępne procesy** , wybierz **XDesProc.exe**, a następnie wybierz **Dołącz** przycisku.  
  
     ![Proces projektanta XAML](../designers/media/xaml-attach.png "XAML_Attach")  
  
     Jest to proces projektanta XAML w pierwszym wystąpieniu programu Visual Studio.  
  
8. W pierwszym wystąpieniu programu Visual Studio, na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie**.  
  
     Możesz teraz wejść w kodzie, w którym jest uruchomiony w projektancie.  
  
#### <a name="to-disable-project-code-in-the-designer"></a>Aby wyłączyć kodu projektu w Projektancie  
  
- W oknie dialogowym nieobsługiwany wyjątek, wybierz **kliknij tutaj, aby wyłączyć uruchamianie kodu projektu i załadować ponownie projektanta** łącza.  
  
- Alternatywnie, na pasku narzędzi Projektanta XAML, należy wybrać **Wyłącz kod projektu** przycisku.  
  
     ![Przycisk Wyłącz kod projektu](../designers/media/xaml-disablecode.png "XAML_DisableCode")  
  
     Można przełączać się przycisk ponownie, aby ponownie włączyć kod projektu.  
  
    > [!NOTE]
    >  Dla projektów przeznaczonych dla ARM lub X64 procesorów, Visual Studio nie można uruchomić kod projektu w projektancie, więc **Wyłącz kod projektu** przycisk jest niedostępny w projektancie.  
  
- Jedną z opcji spowoduje, że projektanta aby załadować ponownie, a następnie spowoduje wyłączenie cały kod dla skojarzonego projektu.  
  
    > [!NOTE]
    >  Wyłączanie kodu projektu może prowadzić do utraty danych czasu projektowania. Alternatywą jest, aby debugować kod uruchomiony w projektancie.  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie XAML w programach Visual Studio i Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md)
