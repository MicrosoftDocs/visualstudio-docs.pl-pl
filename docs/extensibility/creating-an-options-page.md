---
title: Tworzenie strony opcji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e225f2e4c30255add5681f7c467c89be99bb4b9a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56701800"
---
# <a name="create-an-options-page"></a>Tworzenie strony opcji
Ten poradnik tworzy prostą stronę Narzędzia/Opcje korzystającą z siatki właściwości w celu zbadania i ustawić właściwości.

 Aby zapisać te właściwości, aby i przywrócić je z pliku ustawień, wykonaj następujące kroki, a następnie zobacz [Tworzenie kategorii ustawień](../extensibility/creating-a-settings-category.md).

 MPF zawiera dwie klasy ułatwiające tworzenie strony opcji narzędzi <xref:Microsoft.VisualStudio.Shell.Package> klasy i <xref:Microsoft.VisualStudio.Shell.DialogPage> klasy. Tworzenie pakietu VSPackage zapewnić kontener dla tych stron, podklasy `Package` klasy. Tworzenie każdej strony opcji narzędzi, wynikające z `DialogPage` klasy.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tools-options-grid-page"></a>Tworzenie strony opcji narzędzi siatki
 W tej sekcji utworzysz prostą siatki właściwości opcje narzędzi. Ta siatka służy do wyświetlania, a następnie zmień wartość właściwości.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Aby utworzyć projekt VSIX i dodać pakietu VSPackage

1. Każde rozszerzenie programu Visual Studio rozpoczyna się od Projekt wdrożenia VSIX, który będzie zawierać zasoby rozszerzenia. Tworzenie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu VSIX, o nazwie `MyToolsOptionsExtension`. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C#** > **rozszerzalności**.

2. Dodawanie pakietu VSPackage, dodając szablon elementu pakiet rozszerzeń Visual Studio o nazwie `MyToolsOptionsPackage`. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **nowy element**. W **okna dialogowego Dodaj nowy element**, przejdź do **elementy Visual C#** > **rozszerzalności** i wybierz **pakiet rozszerzeń Visual Studio**. W **nazwa** pola w dolnej części okna dialogowego, Zmień nazwę pliku, aby `MyToolsOptionsPackage.cs`. Aby uzyskać więcej informacji o sposobie tworzenia pakietu VSPackage, zobacz [Tworzenie rozszerzenia za pomocą pakietu VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).

### <a name="to-create-the-tools-options-property-grid"></a>Aby utworzyć siatki właściwości opcji narzędzi

1.  Otwórz *MyToolsOptionsPackage* plik w edytorze kodu.

2.  Dodaj następującą instrukcję using.

    ```csharp
    using System.ComponentModel;
    ```

3.  Zadeklaruj `OptionPageGrid` klasy i pochodzić z <xref:Microsoft.VisualStudio.Shell.DialogPage>.

    ```csharp
    public class OptionPageGrid : DialogPage
    {  }
    ```

4.  Zastosuj <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> do `VSPackage` klasy, aby przypisać do tej klasy, kategoria opcji i nazwy strony opcje dla OptionPageGrid. Wynik powinien wyglądać następująco:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5.  Dodaj `OptionInteger` właściwość `OptionPageGrid` klasy.

    -   Zastosuj <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> do przypisania do właściwości kategorii siatki właściwości.

    -   Zastosuj <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> do przypisania do właściwości name.

    -   Zastosuj <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> do przypisania do właściwości opisu.

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
    >  Domyślna implementacja klasy <xref:Microsoft.VisualStudio.Shell.DialogPage> obsługuje właściwości, które mają odpowiednie konwertery lub struktur lub tablic, które można rozszerzyć do właściwości, które mają odpowiednie konwertery. Aby uzyskać listę konwerterów zobacz <xref:System.ComponentModel> przestrzeni nazw.

6.  Skompiluj projekt, a następnie rozpocząć debugowanie.

7.  W doświadczalnym wystąpieniu programu Visual Studio na **narzędzia** kliknij menu **opcje**.

     W okienku po lewej stronie powinien zostać wyświetlony **Moje kategorii**. (Opcje kategorie są wymienione w kolejności alfabetycznej, więc powinien pojawiać się o widoczny w połowie listę w dół.) Otwórz **Moje kategorii** a następnie kliknij przycisk **Moja strona siatki**. Siatka opcji jest wyświetlana w okienku po prawej stronie. Kategoria właściwości jest **Moje opcje**, i nazwa właściwości jest **Moje opcji całkowitą**. Opis właściwości **Moje opcji całkowitą**, pojawi się u dołu okienka. Zmień wartość ze swojej wartości początkowej, 256 się czymś innym. Kliknij przycisk **OK**, a następnie ponownie otwórz **Moja strona siatki**. Aby zobaczyć, że nowa wartość będzie się powtarzać.

     Opcje strony jest również dostępna za pośrednictwem szybkiego uruchamiania programu Visual Studio. W oknie szybkiego uruchamiania w prawym górnym rogu IDE wpisz **Moje kategorii** i zostanie wyświetlony **kategorii My -> Moja strona siatki** na liście rozwijanej.

## <a name="create-a-tools-options-custom-page"></a>Tworzenie niestandardowej strony opcji narzędzi
 W tej sekcji utworzysz strony Opcje narzędzi z niestandardowego interfejsu użytkownika. Ta strona umożliwia wyświetlanie i zmień wartość właściwości.

1.  Otwórz *MyToolsOptionsPackage* plik w edytorze kodu.

2.  Dodaj następującą instrukcję using.

    ```csharp
    using System.Windows.Forms;
    ```

3.  Dodaj `OptionPageCustom` klasy tuż przed `OptionPageGrid` klasy. Pochodzić nowa klasa z `DialogPage`.

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

4.  Dodaj atrybut GUID. Dodaj właściwość właściwości OptionString:

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

5.  Zastosuj drugi <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> do klasy pakietu VSPackage. Ten atrybut przypisuje klasy opcji kategorii i nazwy strony opcje.

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

6.  Dodaj nową **kontrolki użytkownika** o nazwie MyUserControl do projektu.

7.  Dodaj **TextBox** kontrolki do kontrolki użytkownika.

     W **właściwości** okna, na pasku narzędzi kliknij polecenie **zdarzenia** przycisk, a następnie kliknij dwukrotnie **pozostaw** zdarzeń. Nowy program obsługi zdarzeń jest wyświetlana w *MyUserControl.cs* kodu.

8.  Dodaj publiczny `OptionsPage` pola `Initialize` metodę do klasy formantu i aktualizacji programu obsługi zdarzeń, aby ustawić opcję wartość zawartości pola tekstowego:

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

     `optionsPage` Pole zawiera odwołanie do elementu nadrzędnego `OptionPageCustom` wystąpienia. `Initialize` Metoda Wyświetla `OptionString` w **TextBox**. Program obsługi zdarzeń zapisuje bieżącą wartość **TextBox** do `OptionString` po skupić się pozostawia **TextBox**.

9. W pliku pakietu kodu, Dodaj zastąpienie `OptionPageCustom.Window` właściwości `OptionPageCustom` klasy w celu tworzenie, inicjowanie i zwrócenia wystąpienia `MyUserControl`. Klasa powinna teraz wyglądać następująco:

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

10. Skompiluj i uruchom projekt.

11. W doświadczalnym wystąpieniu kliknij **narzędzia** > **opcje**.

12. Znajdź **Moje kategorii** i następnie **Moje niestandardowe strony**.

13. Zmień wartość właściwości **właściwości OptionString**. Kliknij przycisk **OK**, a następnie ponownie otwórz **Moje niestandardowe strony**. Aby zobaczyć, trwałość nową wartość.

## <a name="access-options"></a>Opcje dostępu
 W tej sekcji można uzyskać wartość opcji od pakietu VSPackage, który jest hostem skojarzonej strony opcji narzędzi. Tej samej techniki, może służyć do uzyskania wartości dowolnej właściwości publicznych.

1.  W pliku kodu pakiet, należy dodać publiczny właściwość o nazwie **OptionInteger** do **MyToolsOptionsPackage** klasy.

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

     Ten kod wywołuje <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> można utworzyć lub pobrać `OptionPageGrid` wystąpienia. `OptionPageGrid` wywołania <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> załadować jego opcji, które są właściwości publiczne.

2.  Teraz Dodaj polecenie niestandardowe szablon elementu o nazwie **MyToolsOptionsCommand** do wyświetlania wartości. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C#** > **rozszerzalności** i wybierz **polecenia niestandardowego**. W **nazwa** u dołu okna, Zmień nazwę pliku polecenia, aby *MyToolsOptionsCommand.cs*.

3.  W *MyToolsOptionsCommand* pliku, Zastąp treść metody polecenia `ShowMessageBox` metoda następującym kodem:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4.  Skompiluj projekt, a następnie rozpocząć debugowanie.

5.  W doświadczalnym wystąpieniu na **narzędzia** menu, kliknij przycisk **wywołania MyToolsOptionsCommand**.

     Okno komunikatu Wyświetla bieżącą wartość `OptionInteger`.

## <a name="see-also"></a>Zobacz także
- [Opcje i strony opcji](../extensibility/internals/options-and-options-pages.md)
