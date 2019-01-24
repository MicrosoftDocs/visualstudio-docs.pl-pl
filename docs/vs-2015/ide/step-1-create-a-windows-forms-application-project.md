---
title: Krok 1. Utwórz projekt aplikacji Windows Forms | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: add477fd77731f81da4cc0ee94f7f7d0c7a09cb6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780472"
---
# <a name="step-1-create-a-windows-forms-application-project"></a>Krok 1. Tworzenie projektu aplikacji Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kiedy tworzysz przeglądarki obrazów, pierwszym krokiem jest utworzenie projektu aplikacji formularzy Windows.  
  
 ![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo")wersja wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic – wideo 1](http://go.microsoft.com/fwlink/?LinkId=205209) lub [samouczek 1: Tworzenie przeglądarki obrazów w C# — wideo 1](http://go.microsoft.com/fwlink/?LinkId=205199). W tych filmach wideo użyj wcześniejszej wersji programu Visual Studio, więc istnieją drobne różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednakże pojęcia i procedury działają podobnie w bieżącej wersji programu Visual Studio.  
  
### <a name="to-create-a-windows-forms-application-project"></a>Aby utworzyć projekt aplikacja interfejsu Windows Forms  
  
1.  Na pasku menu wybierz **pliku**, **New**, **projektu**. Okno dialogowe powinno wyglądać następująco.  
  
     ![Okno dialogowe nowego projektu](../ide/media/newprojectdialogcallouts.png "NewProjectDialogCallouts")  
Okno dialogowe Nowy projekt  
  
2.  Wybierz opcję **Visual C#** lub **języka Visual Basic** w **zainstalowane szablony** listy.  
  
3.  Na liście szablonów wybierz **aplikacja interfejsu Windows Forms** ikony. Nazwij nowy formularz **PictureViewer**, a następnie wybierz **OK** przycisku.  
  
     Program Visual Studio tworzy rozwiązanie dla Twojego programu. To rozwiązanie działa jako kontener dla wszystkich projektów i plików wymaganych przez program. Te zwroty zostaną wyjaśnione bardziej szczegółowo w dalszej części tego samouczka.  
  
4.  Poniższa ilustracja przedstawia, co powinien zostać wyświetlony w interfejsie programu Visual Studio.  
  
    > [!NOTE]
    >  Twój układ okna może nie wyglądać dokładnie tak samo jak na ilustracji. Dokładny układ okna zależy od wersji programu Visual Studio, język programowania, którego używasz i innych czynników. Należy jednak sprawdzić, czy są wyświetlane wszystkie trzy okna.  
  
     ![Okno IDE](../ide/media/express-ideoverview-visio.png "Express_IDEOverview_Visio")  
Okno IDE  
  
     Interfejs zawiera trzy okna: główne okno **Eksploratora rozwiązań**i **właściwości** okna.  
  
     Jeśli brakuje któregokolwiek z tych okien, Przywróć domyślny układ okna, na pasku menu, wybierając **okna**, **Zresetuj układ okna**. Można również wyświetlić okna przy użyciu poleceń menu. Na pasku menu wybierz **widoku**, **okno właściwości** lub **Eksploratora rozwiązań**. Jeśli inne okna są otwarte, zamknij je, wybierając **Zamknij** (przycisku w ich prawym górnym rogu x).  
  
5.  Na ilustracji przedstawiono w następujących oknach (zgodnie z ruchem wskazówek zegara od lewego górnego rogu):  
  
    -   **Okno główne** w tym oknie wykonasz większość swojej pracy, takich jak praca z formularzami i Edycja kodu. Na ilustracji okno przedstawia formularz w edytorze formularzy. W górnej części okna **strona startowa** kartę i **Form1.cs [projekt]** karty są wyświetlane. (Kończy w języku Visual Basic, .vb, zamiast nazwy karty. cs.)  
  
    -   **Okno Eksploratora rozwiązań** w tym oknie można przeglądać i nawigować do wszystkich elementów w rozwiązaniu. Po wybraniu pliku, zawartość **właściwości** okna zmiany. Jeśli otworzysz plik kodu (końcówka .cs w środowisku Visual C# i .vb w języku Visual Basic), zostanie wyświetlony plik kodu lub Projektant pliku kodu. Projektant jest powierzchnią wizualną, na którym można dodać formanty, takie jak przyciski i listy. Formularzy programu Visual Studio Projektant nazywa Windows Forms Designer.  
  
    -   **Okno właściwości** w tym oknie można zmienić właściwości elementów, które wybrano w innych oknach. Na przykład, jeśli wybierzesz Form1, możesz zmienić jego tytuł przez ustawienie **tekstu** właściwości, na które można zmienić kolor tła, ustawiając **Backcolor** właściwości.  
  
    > [!NOTE]
    >  W pierwszym wierszu **Eksploratora rozwiązań** pokazuje **rozwiązanie "PictureViewer" (1 projekt)**, co oznacza, że tworzone rozwiązanie programu Visual Studio. To rozwiązanie może zawierać więcej niż jeden projekt, ale na razie będziesz pracować z rozwiązaniami, które zawierają tylko jeden projekt.  
  
6.  Na pasku menu wybierz **pliku**, **Zapisz wszystko**.  
  
     Jako alternatywę, wybierz **Zapisz wszystko** przycisk na pasku narzędzi na następującej ilustracji pokazano.  
  
     ![Zapisz wszystkie przyciski paska narzędzi](../ide/media/express-iconsaveall.png "Express_IconSaveAll")  
Zapisz wszystkie przyciski paska narzędzi  
  
     Program Visual Studio automatycznie wypełnia nazwę folderu i nazwę projektu, a następnie zapisuje projekt w Twoim folderze projektów.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 2: Uruchom Program](../ide/step-2-run-your-program.md).  
  
-   Aby powrócić do tematu przeglądu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów](../ide/tutorial-1-create-a-picture-viewer.md).
