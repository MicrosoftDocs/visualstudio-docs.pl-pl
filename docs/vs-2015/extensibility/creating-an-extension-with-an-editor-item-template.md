---
title: Tworzenie rozszerzenia za pomocą szablonu elementu edytora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab22549550c0564f7e27b88adae4627f24ab9acc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772745"
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>Tworzenie rozszerzenia za pomocą szablonu elementu edytora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można użyć szablonów elementów, które znajdują się w Visual Studio SDK do tworzenia Edytor języka basic rozszerzeń klasyfikatorów, zakończeń oraz marginesy do edytora. Edytor szablonów elementów są dostępne dla projektów języka Visual C# lub Visual Basic VSIX.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-classifier-extension"></a>Tworzenie rozszerzenia klasyfikatora  
 Szablon elementu klasyfikatora Edytor umożliwia utworzenie klasyfikatora edytor, który kolory odpowiedni tekst (w tym przypadku wszystko) w dowolnym pliku tekstowego.  
  
1.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** a następnie kliknij przycisk **rozszerzalności**. W **szablony** okienku wybierz **projekt VSIX**. W **nazwa** wpisz `TestClassifier`. Kliknij przycisk **OK**.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. Przejdź do programu Visual C# **rozszerzalności** a następnie wybierz węzeł **klasyfikatora edytora**. Pozostaw domyślną nazwę pliku (EditorClassifier1.cs).  
  
3.  Istnieją trzy pliki kodu, w następujący sposób:  
  
    -   Zawiera EditorClassifier1.cs `EditorClassifier1` klasy.  
  
    -   Zawiera EditorClassifier1ClassificationDefinition.cs `OEditorClassifier1ClassificationDefinition` klasy.  
  
    -   Zawiera EditorClassifier1Format.cs `EditorClassifier1Format` klasy.  
  
    -   Zawiera EditorClassifier1Provider.cs `EditorClassifier1Provider` klasy.  
  
4.  Skompiluj projekt, a następnie rozpocząć debugowanie. Pojawi się doświadczalnym wystąpieniu programu Visual Studio.  
  
     Jeśli otworzysz plik tekstowy, cały tekst jest podkreślony przeciwko fioletowy tła.  
  
## <a name="creating-a-text-relative-adornment-extension"></a>Tworzenie rozszerzenia zakończeń względem tekstu  
 Szablon edytora tekstu zakończeń tworzy zakończeń tekstu powiązane z wątkiem, który rozszerza wszystkie wystąpienia tekstu znaku "" przy użyciu pola, czerwone obramowanie i niebieskim tłem. Jest powiązane z wątkiem tekstu ponieważ pole zawsze nakładki "" znaków, nawet wtedy, gdy są one przenoszone lub ponownie sformatowany.  
  
1.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** a następnie kliknij przycisk **rozszerzalności**. W **szablony** okienku wybierz **projekt VSIX**. W **nazwa** wpisz `TestAdornment`. Kliknij przycisk **OK**.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. Przejdź do programu Visual C# **rozszerzalności** a następnie wybierz węzeł **edytora tekstu zakończeń**. Pozostaw domyślną nazwę pliku (TextAdornment1.cs/vb).  
  
3.  Istnieją dwa pliki kodu, w następujący sposób:  
  
    -   Zawiera TextAdornment1.cs `TextAdornment1` klasy.  
  
    -   zawiera extAdornment1TextViewCreationListener.cs `TextAdornment1TextViewCreationListener` klasy.  
  
4.  Skompiluj projekt, a następnie rozpocząć debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne. Jeśli otworzysz plik tekstowy, '' znaków w tekście są opisane w kolorze czerwonym na niebieskim tle.  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>Tworzenie rozszerzenia zakończeń względem okienka ekranu  
 Szablon zakończeń okienka ekranu edytora tworzy zakończeń względem okienka ekranu, dodającego fioletowe pole, które ma czerwone obramowanie na prawym górnym rogu okienka ekranu.  
  
> [!NOTE]
>  *Okienka ekranu* jest obszar widoku tekstu, który jest aktualnie wyświetlany.  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Aby utworzyć rozszerzenie zakończeń okienka ekranu przy użyciu szablonu zakończeń okienka ekranu edytora  
  
1.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** a następnie kliknij przycisk **rozszerzalności**. W **szablony** okienku wybierz **projekt VSIX**. W **nazwa** wpisz `ViewportAdornment`. Kliknij przycisk **OK**.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. Przejdź do programu Visual C# **rozszerzalności** a następnie wybierz węzeł **zakończeń okienka ekranu edytora**. Pozostaw domyślną nazwę pliku (ViewportAdornment1.cs/vb).  
  
3.  Istnieją dwa pliki kodu, w następujący sposób:  
  
    -   Zawiera ViewportAdornment1.cs `ViewportAdornment1` klasy.  
  
    -   Zawiera ViewportAdornment1TextViewCreationListener.cs `ViewportAdornment1TextViewCreationListener` klasy  
  
4.  Skompiluj projekt, a następnie rozpocząć debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne. Jeśli tworzysz nowy plik tekstowy, fioletowy pole, które ma czerwone obramowanie jest wyświetlany w prawym górnym rogu okienka ekranu.  
  
## <a name="creating-a-margin-extension"></a>Tworzenie rozszerzenia margines  
 Szablon marginesu edytora tworzy zielony marginesie, na którym jest wyświetlana wraz z słowa "Hello world!" Poniższe poziomy pasek przewijania.  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Aby utworzyć rozszerzenie margines przy użyciu szablonu marginesu edytora  
  
1.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** a następnie kliknij przycisk **rozszerzalności**. W **szablony** okienku wybierz **projekt VSIX**. W **nazwa** wpisz `MarginExtension`. Kliknij przycisk **OK**.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. Przejdź do programu Visual C# **rozszerzalności** a następnie wybierz węzeł **zakończeń okienka ekranu edytora**. Pozostaw domyślną nazwę pliku (EditorMargin1.cs/vb).  
  
3.  Istnieją dwa pliki kodu, w następujący sposób:  
  
    -   Zawiera EditorMargin1.cs `EditorMargin1` klasy.  
  
    -   Zawiera EditorMargin1Factory.cs `EditorMargin1Factory` klasy.  
  
4.  Tworzenie tego projektu, a następnie rozpocząć debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne. Jeśli otworzysz plik tekstowy, zielony margines, który zawiera słowa "Hello EditorMargin1" jest wyświetlana poniżej poziomy pasek przewijania.  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)

