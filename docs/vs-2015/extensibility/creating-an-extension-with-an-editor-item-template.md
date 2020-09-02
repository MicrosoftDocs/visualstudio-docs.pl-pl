---
title: Tworzenie rozszerzenia za pomocą szablonu elementu edytora | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46ccdd87d44ee90c925992f4d7b997c9bbe09684
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64834044"
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>Tworzenie rozszerzenia za pomocą szablonu elementu edytora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą szablonów elementów zawartych w zestawie SDK programu Visual Studio można tworzyć podstawowe rozszerzenia edytora, które dodają klasyfikatory, elementy definiowania układu i marginesy do edytora. Szablony elementów edytora są dostępne dla projektów programu Visual C# lub Visual Basic VSIX.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-classifier-extension"></a>Tworzenie rozszerzenia klasyfikatora  
 Szablon elementu klasyfikatora edytora tworzy klasyfikator edytora, który koloruje odpowiedni tekst (w tym przypadku wszystko) w dowolnym pliku tekstowym.  
  
1. W oknie dialogowym **Nowy projekt** rozwiń pozycję **Visual C#** lub **Visual Basic** a następnie kliknij pozycję **rozszerzalność**. W okienku **Szablony** wybierz pozycję **Projekt VSIX**. W polu **Nazwa** wpisz `TestClassifier`. Kliknij przycisk **OK**.  
  
2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj/nowy element**. Przejdź do węzła **rozszerzalności** Visual C# i wybierz pozycję **klasyfikator edytora**. Pozostaw domyślną nazwę pliku (EditorClassifier1.cs).  
  
3. Istnieją trzy pliki kodu:  
  
    - EditorClassifier1.cs zawiera `EditorClassifier1` klasę.  
  
    - EditorClassifier1ClassificationDefinition.cs zawiera `OEditorClassifier1ClassificationDefinition` klasę.  
  
    - EditorClassifier1Format.cs zawiera `EditorClassifier1Format`  klasę.  
  
    - EditorClassifier1Provider.cs zawiera `EditorClassifier1Provider` klasę.  
  
4. Skompiluj projekt i Rozpocznij debugowanie. Pojawia się eksperymentalne wystąpienie programu Visual Studio.  
  
     Jeśli otworzysz plik tekstowy, cały tekst jest podkreślony dla fioletowego tła.  
  
## <a name="creating-a-text-relative-adornment-extension"></a>Tworzenie rozszerzenia zakończenia powiązanego z tekstem  
 Szablon szablonu zakończenia tekstu edytora tworzy powiązane z tekstem, który zdobi wszystkie wystąpienia znaku tekstowego "a" przy użyciu pola, które ma czerwony kontur i niebieskie tło. Jest to element tekstowy, ponieważ pole zawsze nakłada się na znaki "a", nawet gdy są one przenoszone lub formatowane.  
  
1. W oknie dialogowym **Nowy projekt** rozwiń pozycję **Visual C#** lub **Visual Basic** a następnie kliknij pozycję **rozszerzalność**. W okienku **Szablony** wybierz pozycję **Projekt VSIX**. W polu **Nazwa** wpisz `TestAdornment`. Kliknij przycisk **OK**.  
  
2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj/nowy element**. Przejdź do węzła **rozszerzalności** Visual C# i wybierz pozycję **Edytor tekstów edytora**. Pozostaw domyślną nazwę pliku (TextAdornment1.cs/vb).  
  
3. Istnieją dwa pliki kodu:  
  
    - TextAdornment1.cs zawiera `TextAdornment1` klasę.  
  
    - extAdornment1TextViewCreationListener.cs zawiera `TextAdornment1TextViewCreationListener` klasę.  
  
4. Skompiluj projekt i Rozpocznij debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne. Jeśli otworzysz plik tekstowy, wszystkie znaki "a" w tekście są wyróżnione czerwonym tłem.  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>Tworzenie rozszerzenia zakończenia względem okienka ekranu  
 Szablon zakończenia okienka ekranu edytora tworzy względne położenie okienka ekranu, które dodaje fioletowe pole, które ma czerwony kontur do prawego górnego rogu okienka ekranu.  
  
> [!NOTE]
> *Okienko ekranu* jest obszarem widoku tekstu, który jest aktualnie wyświetlany.  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Aby utworzyć rozszerzenie autodefiniowania okienka ekranu za pomocą edytora szablonu definiowania okienka ekranu  
  
1. W oknie dialogowym **Nowy projekt** rozwiń pozycję **Visual C#** lub **Visual Basic** a następnie kliknij pozycję **rozszerzalność**. W okienku **Szablony** wybierz pozycję **Projekt VSIX**. W polu **Nazwa** wpisz `ViewportAdornment`. Kliknij przycisk **OK**.  
  
2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj/nowy element**. Przejdź do węzła **rozszerzalności** Visual C# i wybierz pozycję **Edytor definiowania okienka ekranu edytora**. Pozostaw domyślną nazwę pliku (ViewportAdornment1.cs/vb).  
  
3. Istnieją dwa pliki kodu:  
  
    - ViewportAdornment1.cs zawiera `ViewportAdornment1` klasę.  
  
    - ViewportAdornment1TextViewCreationListener.cs zawiera `ViewportAdornment1TextViewCreationListener` klasę  
  
4. Skompiluj projekt i Rozpocznij debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne. Jeśli tworzysz nowy plik tekstowy, w prawym górnym rogu okienka ekranu zostanie wyświetlony fioletowy prostokąt z czerwonym obramowaniem.  
  
## <a name="creating-a-margin-extension"></a>Tworzenie rozszerzenia marginesu  
 Szablon marginesu edytora tworzy zielony margines, który pojawia się razem z wyrazami "Hello World!" poniżej poziomego paska przewijania.  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Aby utworzyć rozszerzenie marginesu przy użyciu szablonu marginesu edytora  
  
1. W oknie dialogowym **Nowy projekt** rozwiń pozycję **Visual C#** lub **Visual Basic** a następnie kliknij pozycję **rozszerzalność**. W okienku **Szablony** wybierz pozycję **Projekt VSIX**. W polu **Nazwa** wpisz `MarginExtension`. Kliknij przycisk **OK**.  
  
2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj/nowy element**. Przejdź do węzła **rozszerzalności** Visual C# i wybierz pozycję **Edytor definiowania okienka ekranu edytora**. Pozostaw domyślną nazwę pliku (EditorMargin1.cs/vb).  
  
3. Istnieją dwa pliki kodu:  
  
    - EditorMargin1.cs zawiera `EditorMargin1` klasę.  
  
    - EditorMargin1Factory.cs zawiera `EditorMargin1Factory` klasę.  
  
4. Kompiluj ten projekt i Rozpocznij debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne. Jeśli otworzysz plik tekstowy, zielony margines zawierający słowa "Hello EditorMargin1" jest wyświetlany poniżej poziomego paska przewijania.  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
