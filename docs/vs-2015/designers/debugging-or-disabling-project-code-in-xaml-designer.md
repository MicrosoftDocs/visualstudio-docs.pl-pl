---
title: Debugowanie lub wyłączanie kodu projektu w projektant XAML | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e7de0b3985e09f61fd0c63d1764304b150503883
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657933"
---
# <a name="debugging-or-disabling-project-code-in-xaml-designer"></a>Debugowanie lub wyłączanie kodu projektu w projektancie XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W wielu przypadkach Nieobsłużone wyjątki w projektancie XAML mogą być spowodowane przez kod projektu próbujący uzyskać dostęp do właściwości lub metod, które zwracają różne wartości lub pracują na różne sposoby, gdy aplikacja jest uruchomiona w projektancie. Możesz rozwiązać te wyjątki, debugując kod projektu w innym wystąpieniu programu Visual Studio, lub tymczasowo uniemożliwiaj im, wyłączając kod projektu w projektancie.

 Kod projektu obejmuje:

- Formanty niestandardowe i kontrolki użytkownika

- Biblioteki klas

- Konwertery wartości

- Powiązania z danymi czasu projektowania generowanymi na podstawie kodu projektu

  Gdy kod projektu jest wyłączony, program Visual Studio będzie wyświetlał symbole zastępcze, takie jak nazwa właściwości dla powiązania, gdzie dane nie są już dostępne; lub symbol zastępczy kontrolki, która nie jest już uruchomiona.

  ![Okno dialogowe nieobsłużonego wyjątku](../designers/media/xaml-unhandledexception.png "XAML_UnhandledException")

#### <a name="to-determine-if-project-code-is-causing-an-exception"></a>Aby określić, czy kod projektu jest przyczyną wyjątku

1. W oknie dialogowym nieobsługiwany wyjątek wybierz **pozycję kliknij tutaj, aby ponownie załadować link projektanta** .

2. Na pasku menu wybierz **Debuguj**, **Rozpocznij debugowanie** , aby skompilować i uruchomić aplikację.

     Jeśli aplikacja zostanie pomyślnie skompilowana i uruchomiona, wyjątek czasu projektowania może być spowodowany przez kod projektu uruchomiony w projektancie.

#### <a name="to-debug-project-code-running-in-the-designer"></a>Aby debugować kod projektu uruchomiony w projektancie

1. W oknie dialogowym nieobsługiwany wyjątek wybierz **pozycję kliknij tutaj, aby wyłączyć uruchamianie kodu projektu i ponownie załaduj projektanta** .

2. W Menedżerze zadań systemu Windows wybierz przycisk **Zakończ zadanie** , aby zamknąć wszystkie wystąpienia Projektant XAML programu Visual Studio, które są obecnie uruchomione.

     ![Wystąpienia projektanta XAML w taskmanager](../designers/media/xaml-taskmanager.png "XAML_TaskManager")

3. W programie Visual Studio Otwórz stronę XAML, która zawiera kod lub kontrolkę, którą chcesz debugować.

4. Otwórz nowe wystąpienie programu Visual Studio, a następnie otwórz drugie wystąpienie projektu.

5. Ustaw punkt przerwania w kodzie projektu.

6. W nowym wystąpieniu programu Visual Studio na pasku menu wybierz **Debuguj**, **Dołącz do procesu**.

7. W oknie dialogowym **Dołącz do procesu** na liście **dostępne procesy** wybierz **XDesProc. exe**, a następnie wybierz przycisk **Dołącz** .

     ![Proces projektanta XAML](../designers/media/xaml-attach.png "XAML_Attach")

     Jest to proces projektanta XAML w pierwszym wystąpieniu programu Visual Studio.

8. W pierwszym wystąpieniu programu Visual Studio na pasku menu wybierz **Debuguj**, **Rozpocznij debugowanie**.

     Teraz możesz przejść do kodu działającego w projektancie.

#### <a name="to-disable-project-code-in-the-designer"></a>Aby wyłączyć kod projektu w projektancie

- W oknie dialogowym nieobsługiwany wyjątek wybierz **pozycję kliknij tutaj, aby wyłączyć uruchamianie kodu projektu i ponownie załaduj projektanta** .

- Alternatywnie na pasku narzędzi w projektancie XAML wybierz przycisk **Wyłącz kod projektu** .

     ![Przycisk Wyłącz kod projektu](../designers/media/xaml-disablecode.png "XAML_DisableCode")

     Można ponownie przełączyć przycisk, aby ponownie włączyć kod projektu.

    > [!NOTE]
    > W przypadku projektów przeznaczonych dla procesorów ARM lub x64 program Visual Studio nie może uruchomić kodu projektu w projektancie, dlatego przycisk **Wyłącz kod projektu** jest wyłączony w projektancie.

- Każda opcja spowoduje ponowne załadowanie projektanta, a następnie wyłączenie całego kodu dla skojarzonego projektu.

    > [!NOTE]
    > Wyłączenie kodu projektu może prowadzić do utraty danych czasu projektowania. Alternatywą jest debugowanie kodu działającego w projektancie.

## <a name="see-also"></a>Zobacz też
 [Projektowanie XAML w programach Visual Studio i Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md)
