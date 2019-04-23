---
title: Tworzenie kontrolki przybornika WPF | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60096403"
---
# <a name="creating-a-wpf-toolbox-control"></a>Tworzenie kontrolki przybornika WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Szablon kontrolki przybornika WPF (Windows Presentation Framework) pozwala na tworzenie formantów WPF, które są automatycznie dodawane do **przybornika** po zainstalowaniu rozszerzenia. W tym temacie pokazano, jak używać szablonu do tworzenia **przybornika** formant, który można rozdystrybuować innym użytkownikom.  
  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-wpf-toolbox-control"></a>Tworzenie kontrolki przybornika WPF  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Tworzenie rozszerzenia za pomocą kontrolki przybornika WPF  
  
1. Utwórz projekt VSIX, o nazwie `MyToolboxControl`. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C# / rozszerzalności**.  
  
2. Po otwarciu projektu, Dodaj **kontrolki przybornika WPF** szablon elementu o nazwie `MyToolboxControl`. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C# / rozszerzalności** i wybierz **kontrolki przybornika WPF**. W **nazwa** u dołu okna, Zmień nazwę pliku polecenia, aby `MyToolboxControl.cs`.  
  
     Rozwiązanie zawiera teraz kontrolkę użytkownika `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> , dodaje formant aby **przybornika**i **Microsoft.VisualStudio.ToolboxControl** wpis zawartości w manifestu VSIX  wdrożenie.  
  
#### <a name="to-create-the-control-ui"></a>Aby utworzyć formant interfejsu użytkownika  
  
1. Otwórz MyToolboxControl.xaml w projektancie.  
  
     Projektant wyświetli <xref:System.Windows.Controls.Grid> kontrolkę zawierającą <xref:System.Windows.Controls.Button> kontroli.  
  
2. Rozmieść elementy w układzie siatki. Po wybraniu <xref:System.Windows.Controls.Grid> kontrolować, paskami sterowania niebieski pojawiają się na górnej i lewej krawędzi siatki. Klikając słupki, można dodać wiersze i kolumny do siatki.  
  
3. Dodaj formanty podrzędne do siatki. Można umieścić kontrolki podrzędnej, przeciągając go z **przybornika** do sekcji siatki lub przez ustawienie jego `Grid.Row` i `Grid.Column` atrybutów w XAML. Poniższy przykład dodaje dwie etykiety w górnym wierszu siatki i przycisk w drugim wierszu.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>Zmiana nazwy kontrolki  
 Domyślnie formant pojawi się w **przybornika** jako **MyToolboxControl** w grupie o nazwie **MyToolboxControl.MyToolboxControl**. Możesz zmienić te nazwy w pliku MyToolboxControl.xaml.cs.  
  
1. Otwórz MyToolboxControl.xaml.cs w widoku kodu.  
  
2. Znajdź klasy MyToolboxControl i zmień jego nazwę na TestControl. (Jest to najszybszy sposób, aby to zrobić, można zmienić nazwy klasy, następnie wybierz pozycję **Zmień nazwę** z menu kontekstowego i dokończyć procedurę. (Aby uzyskać więcej informacji na temat **Zmień nazwę** polecenia, zobacz [Refaktoryzacja zmiany nazwy (C#)](../csharp-ide/rename-refactoring-csharp.md).)  
  
3. Przejdź do `ProvideToolboxControl` atrybutu, a następnie zmień wartość pierwszy parametr **testu**. Jest to nazwa grupy, która będzie zawierać formantu w **przybornika**.  
  
     Po modyfikacji kod powinien wyglądać następująco:  
  
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
  
## <a name="building-testing-and-deployment"></a>Tworzenie, testowanie i wdrażanie  
 Podczas debugowania projektu, należy wyszukać kontroli zainstalowane w **przybornika** eksperymentalne wystąpienia programu Visual Studio.  
  
#### <a name="to-build-and-test-the-control"></a>Aby skompilować i przetestować formant  
  
1. Skompiluj ponownie projekt, a następnie rozpocząć debugowanie.  
  
2. W wystąpieniu programu Visual Studio Utwórz projekt aplikacji WPF. Upewnij się, że projektant XAML jest otwarty.  
  
3. Znajdź formant w **przybornika** i przeciągnij go do powierzchni projektowej.  
  
4. Rozpocznij debugowanie aplikacji WPF.  
  
5. Sprawdź, czy jest wyświetlany formantu.  
  
#### <a name="to-deploy-the-control"></a>Aby wdrożyć kontrolki  
  
1. Po skompilowaniu projektu przetestowane, można znaleźć plik .vsix, w folderze \bin\debug\ projektu.  
  
2. Można zainstalować go na komputerze lokalnym, klikając dwukrotnie plik .vsix i wykonując procedurę instalacji. Aby odinstalować kontrolki, przejdź do **narzędzia / rozszerzenia i aktualizacje** i poszukaj rozszerzeń kontroli, a następnie kliknij przycisk **Odinstaluj**.  
  
3. Przekaż plik .vsix, z siecią lub do witryny sieci Web.  
  
     Jeśli załadujesz plik [Visual Studio Marketplace](https://marketplace.visualstudio.com/) witryny sieci Web, można użyć w innym użytkownikom **narzędzia / rozszerzenia i aktualizacje** w programie Visual Studio można znaleźć formantu w trybie online i zainstaluj go.
