---
title: Tworzenie rozszerzenia za pomocą szablonu elementu edytora | Microsoft Docs
description: Dowiedz się, jak używać szablonów elementów w zestawie SDK programu Visual Studio, aby tworzyć podstawowe rozszerzenia edytora, które dodają klasyfikatory, elementy definiowania układu i marginesy do edytora.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 06c3fbfabb4eccc08e528aef913e1c1ba502cbf1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089137"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Tworzenie rozszerzenia z szablonem elementu edytora
Za pomocą szablonów elementów zawartych w zestawie SDK programu Visual Studio można tworzyć podstawowe rozszerzenia edytora, które dodają klasyfikatory, elementy definiowania układu i marginesy do edytora. Szablony elementów edytora są dostępne dla projektów programu Visual C# lub Visual Basic VSIX.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-classifier-extension"></a>Utwórz rozszerzenie klasyfikatora
 Szablon elementu klasyfikatora edytora tworzy klasyfikator edytora, który koloruje odpowiedni tekst (w tym przypadku wszystko) w dowolnym pliku tekstowym.

1. W oknie dialogowym **Nowy projekt** rozwiń pozycję **Visual C#** lub **Visual Basic** a następnie kliknij pozycję **rozszerzalność**. W okienku **Szablony** wybierz pozycję **Projekt VSIX**. W polu **Nazwa** wpisz `TestClassifier`. Kliknij przycisk **OK**.

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj**  >  **nowy element**. Przejdź do węzła **rozszerzalności** Visual C# i wybierz pozycję **klasyfikator edytora**. Pozostaw domyślną nazwę pliku (*EditorClassifier1. cs*).

3. Istnieją cztery pliki kodu:

    - *EditorClassifier1. cs* zawiera `EditorClassifier1` klasę.

    - *EditorClassifier1ClassificationDefinition. cs* zawiera `EditorClassifier1ClassificationDefinition` klasę.

    - *EditorClassifier1Format. cs* zawiera `EditorClassifier1Format`  klasę.

    - *EditorClassifier1Provider. cs* zawiera `EditorClassifier1Provider` klasę.

4. Skompiluj projekt i Rozpocznij debugowanie. Pojawia się eksperymentalne wystąpienie programu Visual Studio.

     Jeśli otworzysz plik tekstowy, cały tekst jest podkreślony dla fioletowego tła.

## <a name="create-a-text-relative-adornment-extension"></a>Utwórz rozszerzenie zakończenia powiązane z tekstem
 Szablon szablonu zakończenia tekstu edytora tworzy powiązane z tekstem, który zdobi wszystkie wystąpienia znaku tekstowego "a" przy użyciu pola, które ma czerwony kontur i niebieskie tło. Jest to element tekstowy, ponieważ pole zawsze nakłada się na znaki "a", nawet gdy są one przenoszone lub formatowane.

1. W oknie dialogowym **Nowy projekt** rozwiń pozycję **Visual C#** lub **Visual Basic** a następnie kliknij pozycję **rozszerzalność**. W okienku **Szablony** wybierz pozycję **Projekt VSIX**. W polu **Nazwa** wpisz `TestAdornment`. Kliknij przycisk **OK**.

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj**  >  **nowy element**. Przejdź do węzła **rozszerzalności** Visual C# i wybierz pozycję **Edytor tekstów edytora**. Pozostaw domyślną nazwę pliku (*TextAdornment1. cs/VB*).

3. Istnieją dwa pliki kodu:

    - *TextAdornment1. cs* zawiera `TextAdornment1` klasę.

    - *TextAdornment1TextViewCreationListener. cs* zawiera `TextAdornment1TextViewCreationListener` klasę.

4. Skompiluj projekt i Rozpocznij debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne. Jeśli otworzysz plik tekstowy, wszystkie znaki "a" w tekście są wyróżnione czerwonym tłem.

## <a name="create-a-viewport-relative-adornment-extension"></a>Utwórz rozszerzenie zakończenia względem okienka ekranu
 Szablon zakończenia okienka ekranu edytora tworzy względne położenie okienka ekranu, które dodaje fioletowe pole, które ma czerwony kontur do prawego górnego rogu okienka ekranu.

> [!NOTE]
> **Okienko ekranu** jest obszarem widoku tekstu, który jest aktualnie wyświetlany.

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Aby utworzyć rozszerzenie autodefiniowania okienka ekranu za pomocą edytora szablonu definiowania okienka ekranu

1. W oknie dialogowym **Nowy projekt** rozwiń pozycję **Visual C#** lub **Visual Basic** a następnie kliknij pozycję **rozszerzalność**. W okienku **Szablony** wybierz pozycję **Projekt VSIX**. W polu **Nazwa** wpisz `ViewportAdornment`. Kliknij przycisk **OK**.

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj**  >  **nowy element**. Przejdź do węzła **rozszerzalności** Visual C# i wybierz pozycję **Edytor definiowania okienka ekranu edytora**. Pozostaw domyślną nazwę pliku (*ViewportAdornment1. cs/VB*).

3. Istnieją dwa pliki kodu:

    - *ViewportAdornment1. cs* zawiera `ViewportAdornment1` klasę.

    - *ViewportAdornment1TextViewCreationListener. cs* zawiera `ViewportAdornment1TextViewCreationListener` klasę

4. Skompiluj projekt i Rozpocznij debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne. Jeśli tworzysz nowy plik tekstowy, w prawym górnym rogu okienka ekranu zostanie wyświetlony fioletowy prostokąt z czerwonym obramowaniem.

## <a name="create-a-margin-extension"></a>Utwórz rozszerzenie marginesu
 Szablon marginesu edytora tworzy zielony margines, który pojawia się razem z wyrazami **Hello World!* poniżej poziomego paska przewijania.

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Aby utworzyć rozszerzenie marginesu przy użyciu szablonu marginesu edytora

1. W oknie dialogowym **Nowy projekt** rozwiń pozycję **Visual C#** lub **Visual Basic** a następnie kliknij pozycję **rozszerzalność**. W okienku **Szablony** wybierz pozycję **Projekt VSIX**. W polu **Nazwa** wpisz `MarginExtension`. Kliknij przycisk **OK**.

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj**  >  **nowy element**. Przejdź do węzła **rozszerzalności** Visual C# i wybierz pozycję **margines edytora**. Pozostaw domyślną nazwę pliku (EditorMargin1. cs/VB).

3. Istnieją dwa pliki kodu:

    - *EditorMargin1. cs* zawiera `EditorMargin1` klasę.

    - *EditorMargin1Factory. cs* zawiera `EditorMargin1Factory` klasę.

4. Kompiluj ten projekt i Rozpocznij debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne. Jeśli otworzysz plik tekstowy, zielony margines zawierający słowa **Hello EditorMargin1** jest wyświetlany poniżej poziomego paska przewijania.

## <a name="see-also"></a>Zobacz też
- [Punkty rozszerzenia usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
