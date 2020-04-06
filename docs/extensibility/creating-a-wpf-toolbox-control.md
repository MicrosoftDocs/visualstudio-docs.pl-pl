---
title: Tworzenie kontrolki przybornika WPF | Dokumenty firmy Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1400efb0095760bf1cee302dd33dcf6ebb90152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739569"
---
# <a name="create-a-wpf-toolbox-control"></a>Tworzenie kontrolki przybornika WPF

Szablon WPF (Windows Presentation Framework) Toolbox Control umożliwia tworzenie formantów WPF, które są automatycznie dodawane do **przybornika** po zainstalowaniu rozszerzenia. W tym przewodniku pokazano, jak użyć szablonu do utworzenia **kontrolki przybornika,** który można rozpowszechniać wśród innych użytkowników.

Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Tworzenie kontrolki przybornika

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Tworzenie rozszerzenia za pomocą kontrolki przybornika WPF

1. Utwórz projekt VSIX o nazwie `MyToolboxControl`. Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt,** wyszukując "vsix".

2. Po otwarciu projektu dodaj szablon elementu **WPF Toolbox Control** o nazwie `MyToolboxControl`. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **nowy element**. W oknie dialogowym **Dodawanie nowego elementu** przejdź do pozycji**Rozszerzalność** **programu Visual C#** > i wybierz pozycję **Formant przybornika WPF**. W polu **Nazwa** u dołu okna zmień nazwę pliku polecenia na *MyToolboxControl.cs*.

    Rozwiązanie zawiera teraz formant `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> użytkownika, a który dodaje formant do **przybornika**i **microsoft.VisualStudio.ToolboxControl** wpis zasobu w manifeście VSIX do wdrożenia.

#### <a name="to-create-the-control-ui"></a>Aby utworzyć interfejs użytkownika formantu

1. Otwórz *plik MyToolboxControl.xaml* w projektancie.

    Projektant pokazuje <xref:System.Windows.Controls.Grid> formant, <xref:System.Windows.Controls.Button> który zawiera formant.

2. Rozmieść układ siatki. Po wybraniu <xref:System.Windows.Controls.Grid> formantu niebieskie paski sterujące pojawiają się na górnych i lewej krawędziach siatki. Wiersze i kolumny można dodawać do siatki, klikając paski.

3. Dodaj formanty podrzędne do siatki. Formant podrzędny można umieścić, przeciągając go z **przybornika** do `Grid.Row` sekcji `Grid.Column` siatki lub ustawiając jego i atrybuty w kodzie XAML. Poniższy przykład dodaje dwie etykiety w górnym wierszu siatki i przycisk w drugim wierszu.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>Zmiana nazwy formantu

 Domyślnie formant pojawi się w **przyborniku** jako **MyToolboxControl** w grupie o nazwie **MyToolboxControl.MyToolboxControl**. Nazwy te można zmienić w pliku *MyToolboxControl.xaml.cs.*

1. Otwórz *MyToolboxControl.xaml.cs* w widoku kodu.

2. Znajdź `MyToolboxControl` klasę i zmień jej nazwę na TestControl. (Najszybszym sposobem, aby to zrobić, jest zmiana nazwy klasy, a następnie wybierz **Zmień nazwę** z menu kontekstowego i wykonaj kroki. (Aby uzyskać więcej informacji na temat polecenia **Zmień nazwę,** zobacz [Zmiana nazwy refaktoryzacji (C#)](../ide/reference/rename.md).)

3. Przejdź do `ProvideToolboxControl` atrybutu i zmień wartość pierwszego parametru na **Test**. Jest to nazwa grupy, która będzie zawierać formant w **przyborniku**.

    Wynikowy kod powinien wyglądać następująco:

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

## <a name="build-test-and-deployment"></a>Tworzenie, testowanie i wdrażanie

 Podczas debugowania projektu, należy znaleźć formant zainstalowany w **przyborniku** eksperymentalnego wystąpienia programu Visual Studio.

### <a name="to-build-and-test-the-control"></a>Aby zbudować i przetestować formant

1. Odbuduj projekt i rozpocznij debugowanie.

2. W nowym wystąpieniu programu Visual Studio utwórz projekt aplikacji WPF. Upewnij się, że projektant XAML jest otwarty.

3. Znajdź formant w **przyborniku** i przeciągnij go na powierzchnię projektową.

4. Rozpocznij debugowanie aplikacji WPF.

5. Sprawdź, czy formant jest wyświetlany.

### <a name="to-deploy-the-control"></a>Aby wdrożyć formant

1. Po utworzeniu testowanego projektu można znaleźć plik *.vsix* w folderze\* *\bin\debug projektu.

2. Można go zainstalować na komputerze lokalnym, klikając dwukrotnie plik *vsix* i postępując zgodnie z procedurą instalacji. Aby odinstalować formant, przejdź do**rozszerzenia i aktualizacje** **narzędzi** > i poszukaj rozszerzenia formantu, a następnie kliknij przycisk **Odinstaluj**.

3. Przekaż plik *vsix* do sieci lub witryny sieci Web.

    Jeśli przekażesz plik do witryny sieci Web [programu Visual Studio Marketplace,](https://marketplace.visualstudio.com/) inni użytkownicy mogą użyć**rozszerzeń** **narzędzi** > i aktualizacji w programie Visual Studio, aby znaleźć formant w trybie online i zainstalować go.
