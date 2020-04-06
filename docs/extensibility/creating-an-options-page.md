---
title: Tworzenie strony z opcjami | Dokumenty firmy Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1607af2a6f68bd5593f9a185188b25b364926fe4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739514"
---
# <a name="create-an-options-page"></a>Tworzenie strony z opcjami

W tym instruktażu utworzy się prostą stronę Narzędzia/Opcje, która używa siatki właściwości do badania i ustawiania właściwości.

 Aby zapisać te właściwości i przywrócić je z pliku ustawień, wykonaj następujące kroki, a następnie zobacz [Tworzenie kategorii ustawień](../extensibility/creating-a-settings-category.md).

 MPF udostępnia dwie klasy, które ułatwią <xref:Microsoft.VisualStudio.Shell.Package> tworzenie stron <xref:Microsoft.VisualStudio.Shell.DialogPage> Opcje narzędzi, klasy i klasy. Tworzenie VSPackage, aby zapewnić kontener dla tych stron `Package` przez podklasy klasy. Każdej stronie opcji narzędzi można utworzyć, wywodząc się `DialogPage` z klasy.

## <a name="prerequisites"></a>Wymagania wstępne

 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tools-options-grid-page"></a>Tworzenie strony siatki Opcje narzędzi

 W tej sekcji utworzysz prostą siatkę właściwości Opcje narzędzi. Ta siatka służy do wyświetlania i zmieniania wartości właściwości.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Aby utworzyć projekt VSIX i dodać vspackage

1. Każde rozszerzenie programu Visual Studio rozpoczyna się od projektu wdrożenia VSIX, który będzie zawierał zasoby rozszerzenia. Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt VSIX o nazwie `MyToolsOptionsExtension`. Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt,** wyszukując "vsix".

2. Dodaj pakiet VSPackage, dodając szablon elementu `MyToolsOptionsPackage`pakietu programu Visual Studio o nazwie . W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **nowy element**. W **oknie dialogowym Dodawanie nowego elementu**przejdź do pozycji**Rozszerzalność** **elementów** > programu Visual C# i wybierz pozycję **Pakiet programu Visual Studio**. W polu **Nazwa** u dołu okna dialogowego `MyToolsOptionsPackage.cs`zmień nazwę pliku na . Aby uzyskać więcej informacji na temat tworzenia pakietu VSPackage, zobacz [Tworzenie rozszerzenia za pomocą programu VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).

### <a name="to-create-the-tools-options-property-grid"></a>Aby utworzyć siatkę właściwości Opcje narzędzi

1. Otwórz plik *MyToolsOptionsPackage* w edytorze kodu.

2. Dodaj następującą instrukcję za pomocą.

   ```csharp
   using System.ComponentModel;
   ```

3. Deklaruj `OptionPageGrid` klasę <xref:Microsoft.VisualStudio.Shell.DialogPage>i wywodź ją z .

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. Zastosuj <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> a `VSPackage` do klasy, aby przypisać do klasy kategorię opcji i nazwę strony opcji dla OptionPageGrid. Wynik powinien wyglądać następująco:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. Dodaj `OptionInteger` właściwość `OptionPageGrid` do klasy.

    - Zastosuj <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> a, aby przypisać do właściwości kategorię siatki właściwości.

    - Zastosuj <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> a, aby przypisać do właściwości nazwę.

    - Zastosuj <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> a, aby przypisać do właściwości opis.

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
    > Domyślna implementacja <xref:Microsoft.VisualStudio.Shell.DialogPage> obsługuje właściwości, które mają odpowiednie konwertery lub które są struktury lub tablice, które można rozwinąć do właściwości, które mają odpowiednie konwertery. Aby uzyskać listę konwerterów, zobacz obszar <xref:System.ComponentModel> nazw.

6. Skompiluj projekt i rozpocznij debugowanie.

7. W eksperymentalnym wystąpieniu programu Visual Studio w menu **Narzędzia** kliknij polecenie **Opcje**.

     W lewym okienku powinna zostać wyświetlna **moja kategoria**. (Kategorie opcji są wyświetlane w kolejności alfabetycznej, więc powinny pojawić się mniej więcej w połowie listy). Otwórz **pozycję Moja kategoria,** a następnie kliknij pozycję **Moja strona siatki**. Siatka opcji pojawi się w prawym okienku. Kategorią właściwości jest **Moje opcje,** a nazwa właściwości to **Moja opcja całkowita.** Opis właściwości, **Opcja Moja liczba całkowita**, pojawi się w dolnej części okienka. Zmień wartość z wartości początkowej 256 na coś innego. Kliknij **przycisk OK**, a następnie otwórz ponownie stronę Moja **siatka**. Widać, że nowa wartość będzie się powtarzać.

     Strona z opcjami jest również dostępna w polu wyszukiwania programu Visual Studio. W polu wyszukiwania u góry ide wpisz **moja kategoria,** a zobaczysz **pozycję Moja kategoria -> Moja strona siatki** na liście wyników.

## <a name="create-a-tools-options-custom-page"></a>Tworzenie strony niestandardowej Opcje narzędzi

 W tej sekcji utworzysz stronę Opcje narzędzi z niestandardowym interfejsem użytkownika. Ta strona służy do wyświetlania i zmieniania wartości właściwości.

1. Otwórz plik *MyToolsOptionsPackage* w edytorze kodu.

2. Dodaj następującą instrukcję za pomocą.

    ```csharp
    using System.Windows.Forms;
    ```

3. Dodaj `OptionPageCustom` klasę tuż przed `OptionPageGrid` klasą. Wykierowuj nową klasę z `DialogPage`.

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

4. Dodawanie atrybutu GUID. Dodaj właściwość OptionString:

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

5. Zastosuj drugi <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> do VSPackage klasy. Ten atrybut przypisuje klasie kategorię opcji i nazwę strony opcji.

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

6. Dodaj nowy **formant użytkownika** o nazwie MyUserControl do projektu.

7. Dodaj formant **textbox** do formantu użytkownika.

     W oknie **Właściwości** na pasku narzędzi kliknij przycisk **Zdarzenia,** a następnie kliknij dwukrotnie zdarzenie **Pozostaw.** Nowy program obsługi zdarzeń pojawia się w kodzie *MyUserControl.cs.*

8. Dodaj pole `OptionsPage` publiczne, `Initialize` metodę do klasy kontrolnej i zaktualizuj program obsługi zdarzeń, aby ustawić wartość opcji na zawartość pola tekstowego:

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

     To `optionsPage` pole zawiera odwołanie `OptionPageCustom` do wystąpienia nadrzędnego. Metoda `Initialize` jest `OptionString` wyświetlana w **textbox**. Program obsługi zdarzeń zapisuje bieżącą wartość `OptionString` **TextBox** do momentu, gdy fokus opuszcza pole **tekstowe**.

9. W pliku kodu pakietu dodaj zastąpienie `OptionPageCustom.Window` właściwości do `OptionPageCustom` klasy, aby utworzyć, zainicjować i `MyUserControl`zwrócić wystąpienie . Klasa powinna teraz wyglądać następująco:

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

10. Tworzenie i uruchamianie projektu.

11. W wystąpieniu eksperymentalnym kliknij pozycję**Opcje** **narzędzi** > .

12. Znajdź **moją kategorię,** a następnie **pozycję Moja strona niestandardowa**.

13. Zmień wartość **OptionString**. Kliknij **przycisk OK**, a następnie otwórz ponownie stronę **niestandardową**. Widać, że nowa wartość utrwaliła się.

## <a name="access-options"></a>Opcje dostępu

 W tej sekcji można uzyskać wartość opcji z VSPackage, który obsługuje skojarzone opcje narzędzi strony. Ta sama technika może służyć do uzyskania wartości każdej własności publicznej.

1. W pliku kodu pakietu dodaj właściwość publiczną o nazwie **OptionInteger** do klasy **MyToolsOptionsPackage.**

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

     Ten kod <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> wywołuje, aby `OptionPageGrid` utworzyć lub pobrać wystąpienie. `OptionPageGrid`wywołania, <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> aby załadować jego opcje, które są właściwościami publicznymi.

2. Teraz dodaj niestandardowy szablon elementu polecenia o nazwie **MyToolsOptionsCommand,** aby wyświetlić wartość. W oknie dialogowym **Dodawanie nowego elementu** przejdź do pozycji**Rozszerzalność** **programu Visual C#** > i wybierz polecenie **Niestandardowe**. W polu **Nazwa** u dołu okna zmień nazwę pliku polecenia na *MyToolsOptionsCommand.cs*.

3. W pliku *MyToolsOptionsCommand* zastąp treść `ShowMessageBox` metody polecenia następującymi:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. Skompiluj projekt i rozpocznij debugowanie.

5. W przypadku wystąpienia eksperymentalnego w menu **Narzędzia** kliknij polecenie **Wywołaj mytoolsoptionsCommand**.

     W oknie komunikatu wyświetlana jest bieżąca wartość pliku `OptionInteger`.

## <a name="see-also"></a>Zobacz też

- [Strony opcji i opcji](../extensibility/internals/options-and-options-pages.md)
