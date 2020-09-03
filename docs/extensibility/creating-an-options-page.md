---
title: Tworzenie strony opcji | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be826b73e28a73216ea88ceba8e23eb1e9ea457b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903818"
---
# <a name="create-an-options-page"></a>Utwórz stronę opcji

W tym instruktażu utworzono prostą stronę narzędzi/opcji, która używa siatki właściwości do badania i ustawiania właściwości.

 Aby zapisać te właściwości i przywrócić je z pliku ustawień, wykonaj następujące kroki, a następnie zobacz temat [Tworzenie kategorii ustawień](../extensibility/creating-a-settings-category.md).

 MPF udostępnia dwie klasy ułatwiające tworzenie stron opcji narzędzi, <xref:Microsoft.VisualStudio.Shell.Package> klasy i <xref:Microsoft.VisualStudio.Shell.DialogPage> klasy. Tworzysz pakietu VSPackage, aby udostępnić kontener dla tych stron przez podklasy `Package` klasy. Każdą stronę opcji narzędzi można utworzyć, wyprowadzając ją z `DialogPage` klasy.

## <a name="prerequisites"></a>Wymagania wstępne

 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tools-options-grid-page"></a>Utwórz stronę siatki opcji narzędzi

 W tej sekcji utworzysz prostą siatkę właściwości opcje. Ta siatka służy do wyświetlania i zmieniania wartości właściwości.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Aby utworzyć projekt VSIX i dodać pakietu VSPackage

1. Każde rozszerzenie programu Visual Studio rozpoczyna się od projektu wdrożenia VSIX, który będzie zawierać zasoby rozszerzenia. Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt VSIX o nazwie `MyToolsOptionsExtension` . Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt** , wyszukując frazę "VSIX".

2. Dodaj pakietu VSPackage, dodając szablon elementu pakietu programu Visual Studio o nazwie `MyToolsOptionsPackage` . W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj**  >  **nowy element**. W **oknie dialogowym Dodaj nowy element**przejdź do pozycji rozszerzalność **elementów Visual C#**  >  **Extensibility** i wybierz pozycję **pakiet programu Visual Studio**. W polu **Nazwa** w dolnej części okna dialogowego Zmień nazwę pliku na `MyToolsOptionsPackage.cs` . Aby uzyskać więcej informacji na temat tworzenia pakietu VSPackage, zobacz [Tworzenie rozszerzenia przy użyciu pakietu VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).

### <a name="to-create-the-tools-options-property-grid"></a>Aby utworzyć siatkę właściwości opcji narzędzi

1. Otwórz plik *MyToolsOptionsPackage* w edytorze kodu.

2. Dodaj następującą instrukcję using.

   ```csharp
   using System.ComponentModel;
   ```

3. Zadeklaruj `OptionPageGrid` klasę i utwórz ją z <xref:Microsoft.VisualStudio.Shell.DialogPage> .

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. Zastosuj <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> do klasy, `VSPackage` Aby przypisać do klasy opcje kategorii i opcji dla OptionPageGrid. Wynik powinien wyglądać następująco:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. Dodaj `OptionInteger` Właściwość do `OptionPageGrid` klasy.

    - Zastosuj <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> do, aby przypisać do właściwości kategorii siatka właściwości.

    - Zastosuj <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> do, aby przypisać do właściwości Nazwa.

    - Zastosuj, <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> Aby przypisać do właściwości opis.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;

        [Category("My Category")]
        [DisplayName("My Integer Option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
    }
    ```

    > [!NOTE]
    > Domyślna implementacja programu <xref:Microsoft.VisualStudio.Shell.DialogPage> obsługuje właściwości, które mają odpowiednie konwertery lub które są strukturami lub tablicami, które mogą być rozwinięte we właściwościach, które mają odpowiednie konwertery. Aby zapoznać się z listą konwerterów, zobacz <xref:System.ComponentModel> przestrzeń nazw.

6. Skompiluj projekt i Rozpocznij debugowanie.

7. W eksperymentalnym wystąpieniu programu Visual Studio, w menu **Narzędzia** kliknij pozycję **Opcje**.

     W okienku po lewej stronie powinna zostać wyświetlona **Kategoria moje kategorie**. (Kategorie opcji są wyświetlane w kolejności alfabetycznej, więc powinny być wyświetlane w połowie listy). Otwórz **moją kategorię** , a następnie kliknij pozycję **moja strona siatki**. Siatka opcji zostanie wyświetlona w okienku po prawej stronie. Kategoria właściwości to **Moje opcje**, a nazwa właściwości jest **opcją my Integer**. Opcja opis właściwości, **My Integer**pojawia się u dołu okienka. Zmień wartość z jej początkowej wartości 256 na inną. Kliknij przycisk **OK**, a następnie ponownie Otwórz **stronę Moje siatki**. Można zobaczyć, że nowa wartość będzie się utrzymywała.

     Strona opcji jest również dostępna za poorednictwem pola wyszukiwania programu Visual Studio. W polu wyszukiwania w górnej części środowiska IDE wpisz **moją kategorię** , a na liście wyników zobaczysz moją **kategorię — > stronie Moje siatki** .

## <a name="create-a-tools-options-custom-page"></a>Utwórz stronę niestandardową opcji narzędzi

 W tej sekcji utworzysz stronę opcji narzędzi z niestandardowym interfejsem użytkownika. Ta strona służy do wyświetlania i zmieniania wartości właściwości.

1. Otwórz plik *MyToolsOptionsPackage* w edytorze kodu.

2. Dodaj następującą instrukcję using.

    ```csharp
    using System.Windows.Forms;
    ```

3. Dodaj `OptionPageCustom` klasę bezpośrednio przed `OptionPageGrid` klasą. Utwórz nową klasę z `DialogPage` .

    ```csharp
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

4. Dodaj atrybut GUID. Dodaj właściwość OptionString:

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

5. Zastosuj sekundę <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> do klasy pakietu VSPackage. Ten atrybut służy do przypisywania klasy kategorii opcji i opcji Nazwa strony.

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    [ProvideOptionPage(typeof(OptionPageCustom),
        "My Category", "My Custom Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

6. Dodaj nową **kontrolkę użytkownika** o nazwie UserControl do projektu.

7. Dodaj kontrolkę **TextBox** do kontrolki użytkownika.

     W oknie **Właściwości** , na pasku narzędzi kliknij przycisk **zdarzenia** , a następnie kliknij dwukrotnie zdarzenie **opuszczenia** . Nowy program obsługi zdarzeń pojawi się w kodzie *MyUserControl.cs* .

8. Dodaj pole publiczne `OptionsPage` , `Initialize` metodę do klasy Control i zaktualizuj procedurę obsługi zdarzeń, aby ustawić wartość opcji na zawartość pola tekstowego:

    ```csharp
    public partial class MyUserControl : UserControl
    {
        public MyUserControl()
        {
            InitializeComponent();
        }

        internal OptionPageCustom optionsPage;

        public void Initialize()
        {
            textBox1.Text = optionsPage.OptionString;
        }

        private void textBox1_Leave(object sender, EventArgs e)
        {
            optionsPage.OptionString = textBox1.Text;
        }
    }
    ```

     `optionsPage`Pole zawiera odwołanie do `OptionPageCustom` wystąpienia nadrzędnego. `Initialize`Metoda zostanie wyświetlona `OptionString` w polu **tekstowym**. Program obsługi zdarzeń zapisuje bieżącą wartość **pola tekstowego** w `OptionString` momencie, gdy fokus opuszcza **pole tekstowe**.

9. W pliku kodu pakietu Dodaj przesłonięcie dla `OptionPageCustom.Window` właściwości do `OptionPageCustom` klasy, aby utworzyć, zainicjować i zwrócić wystąpienie `MyUserControl` . Klasa powinna teraz wyglądać następująco:

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }

        protected override IWin32Window Window
        {
            get
            {
                MyUserControl page = new MyUserControl();
                page.optionsPage = this;
                page.Initialize();
                return page;
            }
        }
    }
    ```

10. Skompiluj i Uruchom projekt.

11. W eksperymentalnym wystąpieniu kliknij pozycję **Narzędzia**  >  **Opcje**.

12. Znajdź **moją kategorię** , a następnie **stronę niestandardową**.

13. Zmień wartość **OptionString**. Kliknij przycisk **OK**, a następnie ponownie Otwórz **moją stronę niestandardową**. Można zobaczyć, że nowa wartość jest utrwalona.

## <a name="access-options"></a>Opcje dostępu

 W tej sekcji uzyskasz wartość opcji z pakietu VSPackage, która zawiera skojarzone Opcje narzędzi. Ta sama technika może służyć do uzyskania wartości każdej właściwości publicznej.

1. W pliku kodu pakietu Dodaj publiczną właściwość o nazwie **OptionInteger** do klasy **MyToolsOptionsPackage** .

    ```csharp
    public int OptionInteger
    {
        get
        {
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));
            return page.OptionInteger;
        }
    }

    ```

     Ten kod wywołuje, <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> Aby utworzyć lub pobrać `OptionPageGrid` wystąpienie. `OptionPageGrid` wywołania <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> do załadowania swoich opcji, które są właściwościami publicznymi.

2. Teraz Dodaj niestandardowy szablon elementu polecenia o nazwie **MyToolsOptionsCommand** , aby wyświetlić tę wartość. W oknie dialogowym **Dodaj nowy element** przejdź do rozszerzalności **Visual C#**  >  **Extensibility** i wybierz **polecenie niestandardowe**. W polu **Nazwa** w dolnej części okna Zmień nazwę pliku polecenia na *MyToolsOptionsCommand.cs*.

3. W pliku *MyToolsOptionsCommand* Zastąp treść `ShowMessageBox` metody polecenia następującym:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. Skompiluj projekt i Rozpocznij debugowanie.

5. W eksperymentalnym wystąpieniu, w menu **Narzędzia** kliknij polecenie **Wywołaj MyToolsOptionsCommand**.

     Zostanie wyświetlone okno komunikatu z bieżącą wartością `OptionInteger` .

## <a name="see-also"></a>Zobacz też

- [Opcje i strony opcji](../extensibility/internals/options-and-options-pages.md)
