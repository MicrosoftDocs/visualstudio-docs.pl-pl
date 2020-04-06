---
title: Tworzenie rozszerzenia z szablonem elementu edytora | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ac19d99bf75c79ad011bfd0d5a56ecf3880b100
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739504"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Tworzenie rozszerzenia z szablonem elementu edytora
Za pomocą szablonów elementów, które są zawarte w visual studio SDK do tworzenia podstawowych rozszerzeń edytora, które dodają klasyfikatory, ozdoby i marginesy do edytora. Szablony elementów edytora są dostępne dla projektów Visual C# lub Visual Basic VSIX.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-classifier-extension"></a>Tworzenie rozszerzenia klasyfikatora
 Szablon elementu klasyfikatora edytora tworzy klasyfikator edytora, który koloryuje odpowiedni tekst (w tym przypadku wszystko) w dowolnym pliku tekstowym.

1. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual C#** lub **Visual Basic,** a następnie kliknij pozycję **Rozszerzalność**. W okienku **Szablony** wybierz pozycję **VSIX Project**. W polu **Nazwa** wpisz `TestClassifier`. Kliknij przycisk **OK**.

2. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **nowy element**. Przejdź do węzła **Rozszerzalność** języka Visual C# i wybierz pozycję **Klasyfikator edytora**. Pozostaw domyślną nazwę pliku (*EditorClassifier1.cs*).

3. Istnieją cztery pliki kodu, w następujący sposób:

    - *EditorClassifier1.cs* zawiera `EditorClassifier1` klasę.

    - *EditorClassifier1ClassificationDefinition.cs* zawiera `EditorClassifier1ClassificationDefinition` klasę.

    - *EditorClassifier1Format.cs* zawiera `EditorClassifier1Format` klasę.

    - *EditorClassifier1Provider.cs* zawiera `EditorClassifier1Provider` klasę.

4. Skompiluj projekt i rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie programu Visual Studio.

     Po otwarciu pliku tekstowego cały tekst zostanie podkreślony na fioletowym tle.

## <a name="create-a-text-relative-adornment-extension"></a>Tworzenie rozszerzenia ozdabiania względem tekstu
 Szablon ozdoby tekstu edytora tworzy ozdoby względne tekstu, który ozdabia wszystkie wystąpienia znaku tekstowego "a" przy użyciu pola, które ma czerwony kontur i niebieskie tło. Jest względny tekst, ponieważ pole zawsze nakłada znaki "a", nawet jeśli są one przenoszone lub sformatowane.

1. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual C#** lub **Visual Basic,** a następnie kliknij pozycję **Rozszerzalność**. W okienku **Szablony** wybierz pozycję **VSIX Project**. W polu **Nazwa** wpisz `TestAdornment`. Kliknij przycisk **OK**.

2. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **nowy element**. Przejdź do węzła **Rozszerzalność** języka Visual C# i wybierz opcję **Ozdoba tekstu edytora**. Pozostaw domyślną nazwę pliku (*TextAdornment1.cs/vb*).

3. Istnieją dwa pliki kodu, w następujący sposób:

    - *TextAdornment1.cs* zawiera `TextAdornment1` klasę.

    - *TextAdornment1TextViewCreationListener.cs* zawiera `TextAdornment1TextViewCreationListener` klasę.

4. Skompiluj projekt i rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie. Jeśli otworzysz plik tekstowy, wszystkie znaki "a" w tekście zostaną zaznaczone na niebiesko na niebieskim tle.

## <a name="create-a-viewport-relative-adornment-extension"></a>Tworzenie rozszerzenia ozdabiania względnego rzutni
 Szablon ozdoby edytora viewport tworzy ozdobę względną rzutni, która dodaje fioletowe pole z czerwonym konturem w prawym górnym rogu rzutni.

> [!NOTE]
> **Rzutnia** jest obszarem aktualnie wyświetlanego widoku tekstu.

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Aby utworzyć rozszerzenie ozdabiania rzutni przy użyciu szablonu ozdoby edytora viewport

1. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual C#** lub **Visual Basic,** a następnie kliknij pozycję **Rozszerzalność**. W okienku **Szablony** wybierz pozycję **VSIX Project**. W polu **Nazwa** wpisz `ViewportAdornment`. Kliknij przycisk **OK**.

2. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **nowy element**. Przejdź do węzła **Rozszerzalność** programu Visual C# i wybierz pozycję **Edytor Adornment .** Pozostaw domyślną nazwę pliku (*ViewportAdornment1.cs/vb*).

3. Istnieją dwa pliki kodu, w następujący sposób:

    - *ViewportAdornment1.cs* zawiera `ViewportAdornment1` klasę.

    - *ViewportAdornment1TextViewCreationListener.cs* zawiera `ViewportAdornment1TextViewCreationListener` klasę

4. Skompiluj projekt i rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie. Jeśli utworzysz nowy plik tekstowy, fioletowe pole z czerwonym konturem jest wyświetlane w prawym górnym rogu rzutni.

## <a name="create-a-margin-extension"></a>Tworzenie rozszerzenia marginesu
 Szablon Margines edytora tworzy zielony margines, który pojawia się wraz ze słowami **Hello world!* poniżej poziomego paska przewijania.

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Aby utworzyć rozszerzenie marginesu przy użyciu szablonu Margines edytora

1. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual C#** lub **Visual Basic,** a następnie kliknij pozycję **Rozszerzalność**. W okienku **Szablony** wybierz pozycję **VSIX Project**. W polu **Nazwa** wpisz `MarginExtension`. Kliknij przycisk **OK**.

2. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **nowy element**. Przejdź do węzła **Rozszerzalność** języka Visual C# i wybierz pozycję **Margines edytora**. Pozostaw domyślną nazwę pliku (EditorMargin1.cs/vb).

3. Istnieją dwa pliki kodu, w następujący sposób:

    - *EditorMargin1.cs* zawiera `EditorMargin1` klasę.

    - *EditorMargin1Factory.cs* zawiera `EditorMargin1Factory` klasę.

4. Skompiluj ten projekt i rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie. Po otwarciu pliku tekstowego poniżej poziomego paska przewijania wyświetlany jest zielony margines zawierający napis **Hello EditorMargin1.**

## <a name="see-also"></a>Zobacz też
- [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
