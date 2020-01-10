---
title: Krok 11. Uruchamianie programu i wypróbuj inne funkcje | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bff0467cfe9447b1cc7814d471f56ab323bb853d
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851578"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>Krok 11. Uruchamianie programu i wypróbowanie innych funkcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program jest gotowy i gotowy do uruchomienia. Można uruchomić program i ustawić kolor tła elementu PictureBox. Aby dowiedzieć się więcej, spróbuj poprawić program, zmieniając kolor formularza, dostosowując przyciski i pole wyboru i zmieniając właściwości formularza.

 ![link do wideo](../data-tools/media/playvideo.gif "PlayVideo") Aby uzyskać wersję wideo tego tematu, zobacz [Samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic — wideo 5](https://msdn.microsoft.com/vbasic/gg315356.aspx) lub [Samouczek 1: Tworzenie przeglądarki obrazów w C# pliku wideo 5](https://msdn.microsoft.com/vcsharp/gg278413.aspx). Te filmy wideo korzystają ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

### <a name="to-run-your-program-and-set-the-background-color"></a>Aby uruchomić program i ustawić kolor tła

1. Wybierz F5 lub na pasku menu wybierz **Debuguj**, **Rozpocznij debugowanie**.

2. Przed otwarciem obrazu wybierz przycisk **Ustaw kolor tła** . Zostanie otwarte okno dialogowe **koloru** .

     Okno ![dialogowe koloru](../ide/media/express-colordialog.png "Express_ColorDialog") Okno dialogowe koloru

3. Wybierz kolor, aby ustawić kolor tła PictureBox. Dokładnie obejrzyj metodę `backgroundButton_Click()`, aby zrozumieć, jak to działa.

    > [!NOTE]
    > Możesz załadować obraz z Internetu, wklejając jego adres URL do okna dialogowego **Otwórz plik** . Spróbuj znaleźć obraz z przezroczystym tłem, aby wyświetlić kolor tła.

4. Wybierz przycisk **Wyczyść obraz** , aby upewnić się, że został wyczyszczony. Następnie zamknij program, wybierając przycisk **Zamknij** .

### <a name="to-try-other-features"></a>Aby wypróbować inne funkcje

- Zmień kolor formularza i przycisków przy użyciu właściwości **BackColor** .

- Dostosuj przyciski i pola wyboru przy użyciu właściwości **Font** i **ForeColor** .

- Zmień właściwości **FormBorderStyle** i **ControlBox** formularza.

- Użyj właściwości **AcceptButton** i **CancelButton** formularza, aby przyciski były wybierane automatycznie, gdy użytkownik wybierze klawisz ENTER lub Esc. Uruchom okno dialogowe **Otwórz plik** , gdy użytkownik wybierze klawisz ENTER i zamknie pole, gdy użytkownik wybierze klawisz ESC.

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby dowiedzieć się więcej na temat programowania w programie Visual Studio, zobacz [pojęcia związane z programowaniem](https://msdn.microsoft.com/library/65c12cca-af4f-4017-886e-2dbc00a189d6).

- Aby dowiedzieć się więcej na temat Visual Basic, zobacz [Tworzenie aplikacji przy użyciu Visual Basic](https://msdn.microsoft.com/library/1e1c0c81-6d95-4167-a98b-44b1efb6d25f).

- Aby dowiedzieć się więcej C#na temat wizualizacji, zobacz [wprowadzenie do C# języka i .NET Framework](https://msdn.microsoft.com/library/0a2dff4e-cd84-42ff-8141-e89889b24081).

- Aby przejść do następnego samouczka, zobacz [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 10. Pisanie kodu dla dodatkowych przycisków i pola wyboru](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).
