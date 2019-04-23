---
title: 'Instrukcje: Tworzenie kontrolki przybornika, który używa formularzy Windows | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Toolbox control
- winforms
- toolbox
ms.assetid: abbd3c3c-3a6e-4539-bd6c-a5891dead234
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: a2b51b8f07a1cc049e4761001bfea754b6ca1819
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105646"
---
# <a name="how-to-create-a-toolbox-control-that-uses-windows-forms"></a>Instrukcje: Tworzenie kontrolki przybornika korzystającej z Windows Forms
Szablon kontrolki formularzy Windows Forms przybornika, który znajduje się w [!INCLUDE[vssdk_dev11_long](../includes/vssdk-dev11-long-md.md)] umożliwia tworzenie formantów Windows Forms, które są automatycznie dodawane do **przybornika** po zainstalowaniu rozszerzenia. W tym temacie pokazano, jak używać szablonu do tworzenia **przybornika** formant, który można rozdystrybuować innym użytkownikom...  
  
> [!NOTE]
>  Aby dowiedzieć się, jak pobrać zestawu SDK programu Visual Studio, zobacz [Centrum deweloperów programu Visual Studio Extensibility](http://go.microsoft.com/fwlink/?linkid=121964) w witrynie MSDN w sieci Web.  
  
## <a name="creating-a-toolbox-control"></a>Tworzenie kontrolki przybornika  
 Użyj szablonu kontrolki Przybornika formularzy Windows, aby utworzyć projekt, a następnie utworzyć interfejs użytkownika (UI), w projektancie.  
  
#### <a name="to-create-a-windows-forms-toolbox-control-project"></a>Aby utworzyć projekt kontrolki formularzy Windows Forms przybornika  
  
1. Na **pliku** menu, kliknij przycisk **New**, a następnie kliknij przycisk **projektu**.  
  
2. W **nowy projekt** dialogowego **zainstalowane szablony**, kliknij węzeł preferowanego języka programowania, a następnie kliknij przycisk **rozszerzalności**. Na liście typów projektów wybierz **kontrolki formularzy Windows Forms przybornika**.  
  
3. W **nazwa** wpisz nazwę, którego chcesz użyć dla projektu. Kliknij przycisk **OK**.  
  
     Program Visual Studio tworzy rozwiązanie, które zawiera kontrolkę użytkownika, atrybut należy umieścić formant w **przybornika**, i VSIX manifestu wdrożenia.  
  
#### <a name="to-build-the-control-ui"></a>Tworzenie kontrolki interfejsu użytkownika  
  
1. W **Eksploratora rozwiązań**, kliknij dwukrotnie ToolboxControl.cs, aby otworzyć go w projektancie.  
  
2. Z **przybornika**, przeciągnij formanty mają powierzchnię projektową i rozmieść je zgodnie z projektem.  
  
3. W **właściwości** oknie ustawienie właściwości publiczne w kontrolce użytkownika, a w elemencie podrzędnym kontroli.  
  
## <a name="coding-the-control"></a>Kodowanie kontrolki  
 Domyślnie formant pojawi się w **przybornika** jako **ToolboxControl1** w **przybornika** grupy elementów, który ma taką samą nazwę jak rozwiązania. Możesz zmienić te nazwy w pliku ToolboxControl.cs.  
  
#### <a name="to-code-the-control"></a>Do kodu kontrolki  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy ToolboxControl.cs, a następnie kliknij przycisk **Wyświetl kod** aby otworzyć go w widoku kodu.  
  
2. W definicji klasy częściowej, który implementuje kontrolkę, kliknij prawym przyciskiem myszy nazwę klasy, kliknij przycisk **Refaktoryzuj**, a następnie kliknij przycisk **Zmień nazwę**. Zmień nazwę klasy na nazwę, która ma być wyświetlana w **przybornika** , gdy kontrolka jest zainstalowany.  
  
3. Bezpośrednio nad definicji klasy w `ProvideToolboxControl` atrybutu deklaracji, zmień wartość pierwszego parametru do nazwy grupy elementów, który będzie obsługiwać formant w **przybornika**.  
  
     W poniższym przykładzie przedstawiono `ProvideToolboxControl` atrybut i definicję klasy skorygowany kontrolki o nazwie `Counter` w `General` grupy elementów.  
  
     [!code-csharp[ToolboxControlWinForms#07](../snippets/csharp/VS_Snippets_VSSDK/toolboxcontrolwinforms/cs/toolboxcontrol.cs#07)]  
  
4. Implementuje właściwości, metod i zdarzeń dla formantu.  
  
## <a name="building-testing-and-deployment"></a>Tworzenie, testowanie i wdrażanie  
 Naciśnięcie klawisza F5 kompilacji projektu, który zawiera plik .vsix wdrożenia i otwiera drugie wystąpienie programu Visual Studio ma kontrolę zainstalowane w **przybornika**.  
  
#### <a name="to-build-and-test-the-control"></a>Aby skompilować i przetestować formant  
  
1. Naciśnij F5.  
  
2. W wystąpieniu programu Visual Studio Utwórz projekt Windows Forms aplikacji.  
  
3. Znajdź formant w **przybornika** i przeciągnij go do powierzchni projektowej.  
  
4. W **właściwości** okna, sprawdź, czy właściwości są wyświetlane zgodnie z oczekiwaniami.  
  
5. Dodaj kod lub dodatkowe formanty, które są wymagane do przetestowania Twojej metody i zdarzenia.  
  
6. Naciśnij klawisz F5, aby otworzyć aplikację Windows Forms.  
  
7. Upewnij się, że właściwości, metod i zdarzeń formantu zachowują się zgodnie z oczekiwaniami.  
  
#### <a name="to-deploy-the-control"></a>Aby wdrożyć kontrolki  
  
1. Po skompilowaniu projektu przetestowane, otwórz folder \bin\debug\ projektu w Eksploratorze plików, a następnie zlokalizuj plik .vsix.  
  
2. Przekaż plik .vsix, z siecią lub do witryny sieci Web.  
  
     Jeśli załadujesz plik [Visual Studio Marketplace](https://marketplace.visualstudio.com/) witryny sieci Web, można użyć w innym użytkownikom **Menedżera rozszerzeń** w programie Visual Studio można znaleźć formantu i zainstaluj go.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie kontrolki przybornika WPF](../extensibility/creating-a-wpf-toolbox-control.md)