---
title: Krok 1. Tworzenie projektu aplikacji Windows Forms | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9cf0177efe373933f8c34e1600658160f489a64
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667352"
---
# <a name="step-1-create-a-windows-forms-application-project"></a>Krok 1. Utworzenie projektu aplikacji Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas tworzenia przeglądarki obrazów pierwszym krokiem jest utworzenie projektu aplikacji Windows Forms.

 ![link do wideo](../data-tools/media/playvideo.gif "PlayVideo") Aby uzyskać wersję wideo tego tematu, zobacz [Samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic — wideo 1](http://go.microsoft.com/fwlink/?LinkId=205209) lub [Samouczek 1: Tworzenie przeglądarki obrazów w C# wideo 1](http://go.microsoft.com/fwlink/?LinkId=205199). Te filmy wideo korzystają ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

### <a name="to-create-a-windows-forms-application-project"></a>Aby utworzyć projekt aplikacji Windows Forms

1. Na pasku menu wybierz **plik**, **Nowy**, **projekt**. Okno dialogowe powinno wyglądać następująco.

     ![Okno dialogowe Nowy projekt](../ide/media/newprojectdialogcallouts.png "NewProjectDialogCallouts") Nowy projekt — okno dialogowe

2. Wybierz **wizualizację C#**  lub **Visual Basic** na liście **zainstalowane szablony** .

3. Na liście szablony wybierz ikonę **Windows Forms aplikacji** . Nazwij nowy formularz **PictureViewer**, a następnie wybierz przycisk **OK** .

     Program Visual Studio tworzy rozwiązanie dla Twojego programu. Rozwiązanie pełni rolę kontenera dla wszystkich projektów i plików wymaganych przez program. Te warunki zostaną omówione bardziej szczegółowo w dalszej części tego samouczka.

4. Na poniższej ilustracji przedstawiono elementy, które powinny być widoczne w interfejsie programu Visual Studio.

    > [!NOTE]
    > Układ okna może nie wyglądać dokładnie tak, jak na poniższej ilustracji. Dokładny układ okna zależy od wersji programu Visual Studio, używanego języka programowania i innych czynników. Należy jednak sprawdzić, czy wszystkie trzy okna są widoczne.

     ![Okno środowiska IDE](../ide/media/express-ideoverview-visio.png "Express_IDEOverview_Visio") Okno środowiska IDE

     Interfejs zawiera trzy okna: okno główne, **Eksplorator rozwiązań**i okno **Właściwości** .

     Jeśli brakuje któregoś z tych okien, Przywróć domyślny układ okna przez, na pasku menu, wybierając **okno**, **Zresetuj układ okna**. Możesz również wyświetlić okna przy użyciu poleceń menu. Na pasku menu wybierz **Widok**, **okno właściwości** lub **Eksplorator rozwiązań**. Jeśli jakiekolwiek inne okna są otwarte, zamknij je, wybierając przycisk **Zamknij** (x) w prawym górnym rogu.

5. Na ilustracji przedstawiono następujące okna (zgodnie z ruchem wskazówek zegara od lewego górnego rogu):

    - **Okno główne** W tym oknie można wykonywać większość prac, takich jak praca z formularzami i edytowanie kodu. Na ilustracji okno zawiera formularz w edytorze formularzy. W górnej części okna zostanie wyświetlona karta **Strona początkowa** i karta **Form1.cs [Design]** . (W Visual Basic Nazwa karty zostanie zakończona z. vb zamiast. cs).

    - **Okno Eksplorator rozwiązań** W tym oknie można wyświetlać wszystkie elementy w rozwiązaniu i przechodzić do nich. W przypadku wybrania pliku zawartość okna **Właściwości** zostanie zmieniona. Jeśli otworzysz plik kodu (który zostaje zakończony w. cs w wizualizacji C# i. vb w Visual Basic), zostanie wyświetlony plik kodu lub Projektant pliku kodu. Projektant jest powierzchnią wizualną, na której można dodawać kontrolki, takie jak przyciski i listy. W przypadku formularzy programu Visual Studio Projektant jest nazywany Projektant formularzy systemu Windows.

    - **Okno właściwości** W tym oknie można zmienić właściwości elementów wybranych w innych oknach. Na przykład po wybraniu formularza Form1 można zmienić jego tytuł przez ustawienie właściwości **Text** i zmienić kolor tła, ustawiając właściwość **BackColor** .

    > [!NOTE]
    > W górnym wierszu **Eksplorator rozwiązań** przedstawiono **rozwiązanie "PictureViewer" (1 projekt)** , co oznacza, że program Visual Studio utworzył rozwiązanie. Rozwiązanie może zawierać więcej niż jeden projekt, ale teraz będzie można korzystać z rozwiązań, które zawierają tylko jeden projekt.

6. Na pasku menu wybierz **plik**, **Zapisz wszystko**.

     Alternatywnie wybierz przycisk **Zapisz wszystko** na pasku narzędzi, który pokazuje poniższą ilustrację.

     ![Przycisk Zapisz wszystkie paski narzędzi](../ide/media/express-iconsaveall.png "Express_IconSaveAll") Przycisk Zapisz wszystkie paski narzędzi

     Program Visual Studio automatycznie wypełnia nazwę folderu i nazwę projektu, a następnie zapisuje projekt w folderze projektów.

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 2. Uruchamianie programu](../ide/step-2-run-your-program.md).

- Aby powrócić do tematu przeglądu, zobacz [Samouczek 1: Tworzenie przeglądarki obrazów](../ide/tutorial-1-create-a-picture-viewer.md).
