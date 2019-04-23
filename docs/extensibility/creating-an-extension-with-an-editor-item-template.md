---
title: Tworzenie rozszerzenia za pomocą szablonu elementu edytora | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e87429c38d5b456eca08daa6675edcb0bd3f056
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079814"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Tworzenie rozszerzenia za pomocą szablonu elementu edytora
Można użyć szablonów elementów, które znajdują się w Visual Studio SDK do tworzenia Edytor języka basic rozszerzeń klasyfikatorów, zakończeń oraz marginesy do edytora. Edytor szablonów elementów są dostępne dla projektów języka Visual C# lub Visual Basic VSIX.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-classifier-extension"></a>Tworzenie rozszerzenia klasyfikatora
 Szablon elementu klasyfikatora Edytor umożliwia utworzenie klasyfikatora edytor, który kolory odpowiedni tekst (w tym przypadku wszystko) w dowolnym pliku tekstowego.

1. W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** a następnie kliknij przycisk **rozszerzalności**. W **szablony** okienku wybierz **projekt VSIX**. W **nazwa** wpisz `TestClassifier`. Kliknij przycisk **OK**.

2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **nowy element**. Przejdź do programu Visual C# **rozszerzalności** a następnie wybierz węzeł **klasyfikatora edytora**. Pozostaw domyślną nazwę pliku (*EditorClassifier1.cs*).

3. Istnieją cztery pliki kodu, w następujący sposób:

    - *EditorClassifier1.cs* zawiera `EditorClassifier1` klasy.

    - *EditorClassifier1ClassificationDefinition.cs* zawiera `EditorClassifier1ClassificationDefinition` klasy.

    - *EditorClassifier1Format.cs* zawiera `EditorClassifier1Format` klasy.

    - *EditorClassifier1Provider.cs* zawiera `EditorClassifier1Provider` klasy.

4. Skompiluj projekt, a następnie rozpocząć debugowanie. Pojawi się doświadczalnym wystąpieniu programu Visual Studio.

     Jeśli otworzysz plik tekstowy, cały tekst jest podkreślony przeciwko fioletowy tła.

## <a name="create-a-text-relative-adornment-extension"></a>Tworzenie rozszerzenia zakończeń względem tekstu
 Szablon edytora tekstu zakończeń tworzy zakończeń tekstu powiązane z wątkiem, który rozszerza wszystkie wystąpienia tekstu znaku "" przy użyciu pola, czerwone obramowanie i niebieskim tłem. Jest powiązane z wątkiem tekstu ponieważ pole zawsze nakładki "" znaków, nawet wtedy, gdy są one przenoszone lub ponownie sformatowany.

1. W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** a następnie kliknij przycisk **rozszerzalności**. W **szablony** okienku wybierz **projekt VSIX**. W **nazwa** wpisz `TestAdornment`. Kliknij przycisk **OK**.

2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **nowy element**. Przejdź do programu Visual C# **rozszerzalności** a następnie wybierz węzeł **edytora tekstu zakończeń**. Pozostaw domyślną nazwę pliku (*TextAdornment1.cs/vb*).

3. Istnieją dwa pliki kodu, w następujący sposób:

    - *TextAdornment1.cs* zawiera `TextAdornment1` klasy.

    - *TextAdornment1TextViewCreationListener.cs* zawiera `TextAdornment1TextViewCreationListener` klasy.

4. Skompiluj projekt, a następnie rozpocząć debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne. Jeśli otworzysz plik tekstowy, '' znaków w tekście są opisane w kolorze czerwonym na niebieskim tle.

## <a name="create-a-viewport-relative-adornment-extension"></a>Tworzenie rozszerzenia zakończeń względem okienka ekranu
 Szablon zakończeń okienka ekranu edytora tworzy zakończeń względem okienka ekranu, dodającego fioletowe pole, które ma czerwone obramowanie na prawym górnym rogu okienka ekranu.

> [!NOTE]
>  **Okienka ekranu** jest obszar widoku tekstu, który jest aktualnie wyświetlany.

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Aby utworzyć rozszerzenie zakończeń okienka ekranu przy użyciu szablonu zakończeń okienka ekranu edytora

1. W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** a następnie kliknij przycisk **rozszerzalności**. W **szablony** okienku wybierz **projekt VSIX**. W **nazwa** wpisz `ViewportAdornment`. Kliknij przycisk **OK**.

2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **nowy element**. Przejdź do programu Visual C# **rozszerzalności** a następnie wybierz węzeł **zakończeń okienka ekranu edytora**. Pozostaw domyślną nazwę pliku (*ViewportAdornment1.cs/vb*).

3. Istnieją dwa pliki kodu, w następujący sposób:

    - *ViewportAdornment1.cs* zawiera `ViewportAdornment1` klasy.

    - *ViewportAdornment1TextViewCreationListener.cs* zawiera `ViewportAdornment1TextViewCreationListener` klasy

4. Skompiluj projekt, a następnie rozpocząć debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne. Jeśli tworzysz nowy plik tekstowy, fioletowy pole, które ma czerwone obramowanie jest wyświetlany w prawym górnym rogu okienka ekranu.

## <a name="create-a-margin-extension"></a>Tworzenie rozszerzenia margines
 Szablon marginesu edytora tworzy zielony marginesie, na którym jest wyświetlana wraz z wyrazy **Witaj świecie!* poniżej paska przewijania w poziomie.

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Aby utworzyć rozszerzenie margines przy użyciu szablonu marginesu edytora

1. W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** a następnie kliknij przycisk **rozszerzalności**. W **szablony** okienku wybierz **projekt VSIX**. W **nazwa** wpisz `MarginExtension`. Kliknij przycisk **OK**.

2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **nowy element**. Przejdź do programu Visual C# **rozszerzalności** a następnie wybierz węzeł **marginesu edytora**. Pozostaw domyślną nazwę pliku (EditorMargin1.cs/vb).

3. Istnieją dwa pliki kodu, w następujący sposób:

    - *EditorMargin1.cs* zawiera `EditorMargin1` klasy.

    - *EditorMargin1Factory.cs* zawiera `EditorMargin1Factory` klasy.

4. Tworzenie tego projektu, a następnie rozpocząć debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne. Jeśli otworzysz plik tekstowy, zielony margines, który zawiera wyrazy **Hello EditorMargin1** jest wyświetlana poniżej paska przewijania w poziomie.

## <a name="see-also"></a>Zobacz także
- [Punkty rozszerzenia usługi oraz edytora języka](../extensibility/language-service-and-editor-extension-points.md)
