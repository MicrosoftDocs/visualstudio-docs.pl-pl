---
title: Tworzenie kontrolki przybornika WPF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 768d9747635f2106d16f755db6799e356c890838
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197435"
---
# <a name="creating-a-wpf-toolbox-control"></a>Tworzenie kontrolki przybornika WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Szablon kontrolki przybornika WPF (Windows Presentation Framework) umożliwia tworzenie formantów WPF, które są automatycznie dodawane do **przybornika** po zainstalowaniu rozszerzenia. W tym temacie pokazano, jak za pomocą szablonu utworzyć formant **przybornika** , który można dystrybuować do innych użytkowników.  
  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-wpf-toolbox-control"></a>Tworzenie kontrolki przybornika WPF  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Tworzenie rozszerzenia za pomocą kontrolki przybornika WPF  
  
1. Utwórz projekt VSIX o nazwie `MyToolboxControl` . Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt** w obszarze **Visual C#/rozszerzalność**.  
  
2. Po otwarciu projektu Dodaj szablon elementu **kontrolki przybornika WPF** o nazwie `MyToolboxControl` . W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj/nowy element**. W oknie dialogowym **Dodaj nowy element** przejdź do pozycji **Visual C#/rozszerzalność** i wybierz **formant przybornik WPF**. W polu **Nazwa** w dolnej części okna Zmień nazwę pliku polecenia na `MyToolboxControl.cs` .  
  
     Rozwiązanie zawiera teraz kontrolkę użytkownika, `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> która dodaje formant do **przybornika**i wpis zasobu **Microsoft. VISUALSTUDIO. ToolboxControl** w manifeście VSIX dla wdrożenia.  
  
#### <a name="to-create-the-control-ui"></a>Aby utworzyć interfejs użytkownika kontrolki  
  
1. Otwórz MyToolboxControl. XAML w projektancie.  
  
     Projektant pokazuje <xref:System.Windows.Controls.Grid> formant, który zawiera <xref:System.Windows.Controls.Button> kontrolkę.  
  
2. Rozmieść układ siatki. Po wybraniu <xref:System.Windows.Controls.Grid> kontrolki niebieskie paski sterowania pojawiają się na górnej i lewej krawędzi siatki. Możesz dodać wiersze i kolumny do siatki, klikając słupki.  
  
3. Dodaj kontrolki podrzędne do siatki. Formant podrzędny można ustawić, przeciągając go z **przybornika** do sekcji siatki lub ustawiając jego `Grid.Row` `Grid.Column` atrybuty i w kodzie XAML. Poniższy przykład dodaje dwie etykiety w górnym wierszu siatki i przycisk w drugim wierszu.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>Zmiana nazwy kontrolki  
 Domyślnie kontrolka będzie wyświetlana w **przyborniku** jako **MyToolboxControl** w grupie o nazwie **MyToolboxControl. MyToolboxControl**. Te nazwy można zmienić w pliku MyToolboxControl.xaml.cs.  
  
1. Otwórz MyToolboxControl.xaml.cs w widoku kodu.  
  
2. Znajdź klasę MyToolboxControl i zmień jej nazwę na TestControl. (Najszybszym sposobem wykonania tej czynności jest zmiana nazwy klasy, a następnie wybranie opcji **Zmień nazwę** z menu kontekstowego i wykonanie kroków. (Aby uzyskać więcej informacji na temat **zmiany nazwy** , zobacz [Refaktoryzacja zmiany nazwy (C#)](../csharp-ide/rename-refactoring-csharp.md).)  
  
3. Przejdź do `ProvideToolboxControl` atrybutu i zmień wartość pierwszego parametru do **przetestowania**. To jest nazwa grupy, która będzie zawierać formant w **przyborniku**.  
  
     Otrzymany kod powinien wyglądać następująco:  
  
    ```csharp  
    [ProvideToolboxControl("Test", true)]  
    public partial class TestControl : UserControl  
    {  
        public TestControl()  
        {  
            InitializeComponent();  
        }  
    }  
    ```  
  
## <a name="building-testing-and-deployment"></a>Kompilowanie, testowanie i wdrażanie  
 Podczas debugowania projektu, należy znaleźć formant zainstalowany w **przyborniku** eksperymentalnego wystąpienia programu Visual Studio.  
  
#### <a name="to-build-and-test-the-control"></a>Aby skompilować i przetestować kontrolkę  
  
1. Skompiluj ponownie projekt i Rozpocznij debugowanie.  
  
2. W nowym wystąpieniu programu Visual Studio Utwórz projekt aplikacji WPF. Upewnij się, że projektant XAML jest otwarty.  
  
3. Znajdź swój formant w **przyborniku** i przeciągnij go na powierzchnię projektu.  
  
4. Rozpocznij debugowanie aplikacji WPF.  
  
5. Sprawdź, czy kontrolka jest widoczna.  
  
#### <a name="to-deploy-the-control"></a>Aby wdrożyć formant  
  
1. Po skompilowaniu przetestowanego projektu można znaleźć plik. vsix w folderze \bin\debug\ projektu.  
  
2. Można go zainstalować na komputerze lokalnym, klikając dwukrotnie plik. vsix i postępując zgodnie z procedurą instalacji. Aby odinstalować formant, przejdź do pozycji **Narzędzia/rozszerzenia i aktualizacje** , a następnie kliknij przycisk **Odinstaluj**.  
  
3. Przekaż plik VSIX do sieci lub witryny sieci Web.  
  
     Jeśli przekażesz plik do witryny sieci Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) , inni użytkownicy będą mogli użyć **narzędzi/rozszerzeń i aktualizacji** w programie Visual Studio, aby znaleźć formant online i zainstalować go.
