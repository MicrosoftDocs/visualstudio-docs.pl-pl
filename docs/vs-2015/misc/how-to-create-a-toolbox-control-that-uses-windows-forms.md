---
title: 'Instrukcje: Tworzenie kontrolki przybornika korzystającej z Windows Forms | Microsoft Docs'
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
ms.openlocfilehash: 1f3b0c173d5d1f4b3642bf61d2cca9fb6fd231e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850322"
---
# <a name="how-to-create-a-toolbox-control-that-uses-windows-forms"></a>Instrukcje: Tworzenie kontrolki przybornika korzystającej z Windows Forms
Szablon kontrolki przybornika Windows Forms, który jest zawarty w programie [!INCLUDE[vssdk_dev11_long](../includes/vssdk-dev11-long-md.md)] umożliwia tworzenie Windows Forms formantów, które są automatycznie dodawane do **przybornika** po zainstalowaniu rozszerzenia. W tym temacie pokazano, jak za pomocą szablonu utworzyć formant **przybornika** , który można dystrybuować do innych użytkowników.  
  
> [!NOTE]
> Aby dowiedzieć się, jak pobrać zestaw Visual Studio SDK, zobacz [Centrum deweloperów rozszerzeń programu Visual Studio](https://msdn.microsoft.com/vsx/default.aspx) w witrynie MSDN w sieci Web.  
  
## <a name="creating-a-toolbox-control"></a>Tworzenie kontrolki przybornika  
 Użyj szablonu kontrolki przybornika Windows Forms, aby utworzyć projekt, a następnie Skompiluj interfejs użytkownika w projektancie.  
  
#### <a name="to-create-a-windows-forms-toolbox-control-project"></a>Aby utworzyć projekt kontrolki przybornika Windows Forms  
  
1. W menu **Plik** kliknij pozycję **Nowy**, a następnie kliknij pozycję **Projekt**.  
  
2. W oknie dialogowym **Nowy projekt** w obszarze **zainstalowane szablony**kliknij węzeł preferowanego języka programowania, a następnie kliknij pozycję **rozszerzalność**. Na liście typów projektów wybierz pozycję **formant przybornika Windows Forms**.  
  
3. W polu **Nazwa** wpisz nazwę, której chcesz użyć dla projektu. Kliknij przycisk **OK**.  
  
     Program Visual Studio tworzy rozwiązanie, które zawiera kontrolkę użytkownika, atrybut służący do umieszczania kontrolki w **przyborniku**i manifest VSIX dla wdrożenia.  
  
#### <a name="to-build-the-control-ui"></a>Aby skompilować interfejs użytkownika kontrolki  
  
1. W **Eksplorator rozwiązań**kliknij dwukrotnie pozycję ToolboxControl.cs, aby otworzyć ją w projektancie.  
  
2. Z **przybornika**przeciągnij wszystkie kontrolki do powierzchni projektowej i rozmieść je zgodnie z projektem.  
  
3. W oknie **Właściwości** ustaw właściwości publiczne na kontrolce użytkownika i w kontrolkach podrzędnych.  
  
## <a name="coding-the-control"></a>Kodowanie formantu  
 Domyślnie kontrolka będzie wyświetlana w **przyborniku** jako **ToolboxControl1** w grupie elementów **przybornika** , która ma taką samą nazwę jak rozwiązanie. Te nazwy można zmienić w pliku ToolboxControl.cs.  
  
#### <a name="to-code-the-control"></a>Aby zakodować formant  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję ToolboxControl.cs, a następnie kliknij pozycję **Wyświetl kod** , aby otworzyć plik w widoku kodu.  
  
2. W definicji klasy częściowej, która implementuje formant, kliknij prawym przyciskiem myszy nazwę klasy, kliknij pozycję **Refaktoryzacja**, a następnie kliknij polecenie **Zmień nazwę**. Zmień nazwę klasy na nazwę, która ma być wyświetlana w **przyborniku** , gdy kontrolka jest zainstalowana.  
  
3. Bezpośrednio powyżej definicji klasy, w `ProvideToolboxControl` deklaracji atrybutu, Zmień wartość pierwszego parametru na nazwę grupy elementów, która będzie hostować formant w **przyborniku**.  
  
     Poniższy przykład pokazuje `ProvideToolboxControl` atrybut i dostosowaną definicję klasy dla kontrolki o nazwie `Counter` w `General` grupie elementów.  
  
     [!code-csharp[ToolboxControlWinForms#07](../snippets/csharp/VS_Snippets_VSSDK/toolboxcontrolwinforms/cs/toolboxcontrol.cs#07)]  
  
4. Zaimplementuj właściwości, metody i zdarzenia dla kontrolki.  
  
## <a name="building-testing-and-deployment"></a>Kompilowanie, testowanie i wdrażanie  
 Naciśnięcie klawisza F5 kompiluje projekt, który obejmuje plik wdrożenia. vsix, i otwiera drugie wystąpienie programu Visual Studio, które ma kontrolkę zainstalowaną w **przyborniku**.  
  
#### <a name="to-build-and-test-the-control"></a>Aby skompilować i przetestować kontrolkę  
  
1. Naciśnij F5.  
  
2. W nowym wystąpieniu programu Visual Studio Utwórz projekt aplikacji Windows Forms.  
  
3. Znajdź swój formant w **przyborniku** i przeciągnij go na powierzchnię projektu.  
  
4. W oknie **Właściwości** Sprawdź, czy właściwości są wyświetlane zgodnie z oczekiwaniami.  
  
5. Dodaj dowolny kod lub dodatkowe kontrolki, które są wymagane do testowania metod i zdarzeń.  
  
6. Naciśnij klawisz F5, aby otworzyć aplikację Windows Forms.  
  
7. Sprawdź, czy właściwości, metody i zdarzenia kontrolki działają zgodnie z oczekiwaniami.  
  
#### <a name="to-deploy-the-control"></a>Aby wdrożyć formant  
  
1. Po skompilowaniu przetestowanego projektu Otwórz folder \bin\debug\ projektu w Eksploratorze plików i Znajdź plik. VSIX.  
  
2. Przekaż plik VSIX do sieci lub witryny sieci Web.  
  
     W przypadku przekazania pliku do witryny sieci Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) inni użytkownicy mogą użyć **Menedżera rozszerzeń** w programie Visual Studio, aby znaleźć formant i zainstalować go.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie kontrolki przybornika WPF](../extensibility/creating-a-wpf-toolbox-control.md)
