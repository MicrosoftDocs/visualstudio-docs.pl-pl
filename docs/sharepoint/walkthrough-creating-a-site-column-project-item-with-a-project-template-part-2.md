---
title: 'Przewodnik: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 2 | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e0445e66b10ca8bfa0ae4f5d2c35246d71745788
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56604870"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>Przewodnik: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 2
  Po zdefiniowaniu niestandardowy typ elementu projektu programu SharePoint i skojarzyć go z szablonem projektu w programie Visual Studio, można również podać Kreatora szablonu. Kreator służy do zbierania informacji od użytkowników, używając szablonu do utworzenia nowego projektu, który zawiera element projektu. Informacje zbierane, może służyć do zainicjowania elementu projektu.

 W tym przewodniku kreatora zostanie dodany do szablonu projektu kolumny witryny, która została przedstawiona w [instruktażu: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md). Gdy użytkownik tworzy projekt kolumny witryny, Kreator zbiera informacje o kolumny witryny (takie jak jego typ podstawowy i grupy) i dodaje te informacje do *Elements.xml* plik w nowym projekcie.

 W tym instruktażu pokazano następujące zagadnienia:

-   Tworzenie kreatora dla programu SharePoint projektu elementu Typ niestandardowy, który jest skojarzony z szablonem projektu.

-   Definiowanie niestandardowego kreatora interfejsu użytkownika, który przypomina wbudowanych kreatorów dla projektów programu SharePoint w programie Visual Studio.

-   Utworzenie dwóch *poleceń programu SharePoint* zostaną one użyte do wywołania w lokalnej witrynie SharePoint, po uruchomieniu kreatora. Polecenia programu SharePoint są metodami, używane przez rozszerzenia programu Visual Studio w celu wywoływania interfejsów API w modelu obiektów serwera SharePoint. Aby uzyskać więcej informacji, zobacz [wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

-   Używanie wymiennych parametrów można zainicjować plików projektu programu SharePoint z danymi, które można zbierać w kreatorze.

-   Tworzenie nowego pliku .snk, w każdym nowe wystąpienie projektu kolumny witryny. Ten plik jest używany do podpisywania projektu, dane wyjściowe, tak aby zestawu rozwiązania programu SharePoint można wdrażać w globalnej pamięci podręcznej.

-   Debugowanie i testowanie kreatora.

> [!NOTE]
> Aby szereg przykładowych przepływów pracy, zobacz [przepływu pracy SharePoint — przykłady](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples).

## <a name="prerequisites"></a>Wymagania wstępne
 Aby wykonać ten Instruktaż, należy najpierw utworzyć rozwiązanie SiteColumnProjectItem, wykonując [instruktażu: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 Wymagane są również następujące składniki na komputerze deweloperskim w celu przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Windows, SharePoint i Visual Studio.

- The Visual Studio SDK. W tym instruktażu wykorzystano **projekt VSIX** szablonu w zestawie SDK, aby utworzyć pakiet VSIX do wdrożenia elementu projektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie narzędzi SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Znajomość następujących pojęć jest przydatna, ale nie jest to wymagane, aby ukończyć Instruktaż:

- Kreatorzy szablonów projektów i elementów w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [jak: Korzystanie z kreatorów z szablonami projektu](../extensibility/how-to-use-wizards-with-project-templates.md) i <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsu.

- Kolumny witryny w programie SharePoint. Aby uzyskać więcej informacji, zobacz [kolumn](http://go.microsoft.com/fwlink/?LinkId=183547).

## <a name="understand-the-wizard-components"></a>Opis składników Kreatora
 Kreator przedstawionej w tym przewodniku zawiera kilka składników. W poniższej tabeli opisano te składniki.

|Składnik|Opis|
|---------------|-----------------|
|Kreator implementacji|Jest to klasa o nazwie `SiteColumnProjectWizard`, który implementuje <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsu. Ten interfejs definiuje metody, które wywołuje program Visual Studio, gdy Kreator rozpoczyna się zakończy i w określonym czasie podczas Kreator uruchamia.|
|Kreator interfejsu użytkownika|Jest to okno opartego na podsystemie WPF, o nazwie `WizardWindow`. To okno zawiera dwie kontrolki użytkownika, o nazwie `Page1` i `Page2`. Te kontrolki użytkownika reprezentować dwie strony kreatora.<br /><br /> W tym przewodniku <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> metod wdrażania Kreator wyświetli Kreatora interfejsu użytkownika.|
|Kreator modelu danych|Jest to pośrednie klasę o nazwie `SiteColumnWizardModel`, który stanowi warstwę między Kreator interfejsu użytkownika i implementację kreatora. W tym przykładzie korzysta z tej klasy ułatwiające abstrakcji implementację kreatora i Kreatora interfejsu użytkownika od siebie; Ta klasa nie jest wymaganym składnikiem wszystkich kreatorów.<br /><br /> W tym przewodniku przekazuje implementację kreatora `SiteColumnWizardModel` obiekt okna kreatora, jeśli Wyświetla Kreator interfejsu użytkownika. Kreator interfejsu użytkownika używa metody tego obiektu, aby zapisać wartości formantów w interfejsie użytkownika i wykonywać zadania takie jak weryfikowanie, czy adres URL witryny wejściowy jest nieprawidłowy. Po zakończeniu pracy kreatora użytkownik korzysta z Kreatora wdrażania `SiteColumnWizardModel` obiekt, aby określić ostateczny stan interfejsu użytkownika.|
|Menedżer podpisywania projektu|Jest to klasa pomocy, o nazwie `ProjectSigningManager`, umożliwiający przez implementację kreator Utwórz nowy plik key.snk w każdym wystąpieniu projektu.|
|SharePoint — Polecenia|Są to metody, które są używane przez Kreator modelu danych do wywołania w lokalnej witrynie SharePoint, po uruchomieniu kreatora. Ponieważ polecenia programu SharePoint musi być przeznaczony dla .NET Framework 3.5, te polecenia są implementowane w innym zestawie niż pozostałe kodem kreatora.|

## <a name="create-the-projects"></a>Tworzenie projektów
 Do przeprowadzenia tego instruktażu, należy dodać kilka projektów w rozwiązaniu SiteColumnProjectItem, który został utworzony w [instruktażu: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):

- Projekt WPF. Zostaną zaimplementowane <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejs i zdefiniuj Kreatora interfejsu użytkownika w tym projekcie.

- Projekt biblioteki klas, który definiuje poleceń programu SharePoint. Ten projekt musi być przeznaczony dla środowiska.NET Framework 3.5.

  Instruktaż należy rozpocząć od utworzenia projektów.

#### <a name="to-create-the-wpf-project"></a>Aby utworzyć projekt WPF

1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], otwórz rozwiązanie SiteColumnProjectItem.

2.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **SiteColumnProjectItem** węzła rozwiązania wybierz **Dodaj**, a następnie wybierz **nowy projekt**.

3.  W górnej części **Dodaj nowy projekt** okna dialogowego pole, upewnij się, że **.NET Framework 4.5** jest wybierany w listę wersji programu .NET Framework.

4.  Rozwiń **Visual C#** węzła lub **języka Visual Basic** węzeł i wybierz polecenie **Windows** węzła.

5.  Na liście szablonów projektu wybierz **Biblioteka kontrolek użytkownika WPF**, nadaj projektowi nazwę **ProjectTemplateWizard**, a następnie wybierz **OK** przycisku.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **ProjectTemplateWizard** projektu do rozwiązania i otwiera plik UserControl1.xaml domyślne.

6.  Usuń plik UserControl1.xaml z projektu.

#### <a name="to-create-the-sharepoint-commands-project"></a>Aby utworzyć projekt poleceń programu SharePoint

1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla węzła rozwiązania SiteColumnProjectItem, wybierz pozycję **Dodaj**, a następnie wybierz **nowy projekt**.

2.  W górnej części **Dodaj nowy projekt** okna dialogowego wybierz **.NET Framework 3.5** na liście wersji programu .NET Framework.

3.  Rozwiń **Visual C#** węzła lub **języka Visual Basic** węzła, a następnie wybierz **Windows** węzła.

4.  Wybierz **biblioteki klas** projektu szablonu, nadaj projektowi nazwę **SharePointCommands**, a następnie wybierz **OK** przycisku.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **SharePointCommands** projektu do rozwiązania i otwiera plik domyślny kodu Class1.

5.  Usuń plik kodu Class1 z projektu.

## <a name="configure-the-projects"></a>Konfigurowanie projektów
 Przed utworzeniem kreatora, należy dodać niektórych plików kodu i odwołania do zestawów, do projektów.

#### <a name="to-configure-the-wizard-project"></a>Aby skonfigurować projekt Kreatora

1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **ProjectTemplateWizard** węzła projektu, a następnie wybierz **właściwości**.

2.  W **projektanta projektu**, wybierz **aplikacji** karty Projekt Visual C# lub **skompilować** karty Projekt języka Visual Basic.

3.  Upewnij się, że platforma docelowa jest ustawiona na .NET Framework 4.5, nie .NET Framework 4.5 Client Profile.

     Aby uzyskać więcej informacji, zobacz [jak: Docelowa wersja systemu .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

4.  Otwórz menu skrótów dla **ProjectTemplateWizard** projektu, wybierz **Dodaj**, a następnie wybierz **nowy element**.

5.  Wybierz **okno (WPF)** elementu, określ nazwę elementu **WizardWindow**, a następnie wybierz **Dodaj** przycisku.

6.  Dodaj dwie **kontrolki użytkownika (WPF)** elementy do projektu i nazwij je **strona 1** i **Strona2**.

7.  Dodaj cztery pliki kodu do projektu i nadaj im następujące nazwy:

    -   SiteColumnProjectWizard

    -   SiteColumnWizardModel

    -   ProjectSigningManager

    -   CommandIds

8.  Otwórz menu skrótów dla **ProjectTemplateWizard** węzła projektu, a następnie wybierz **Dodaj odwołanie**.

9. Rozwiń **zestawy** węzła, wybierz **rozszerzenia** węzeł, a następnie zaznacz pole wyboru obok następujących zestawów:

    -   EnvDTE

    -   Microsoft.VisualStudio.OLE.Interop

    -   Microsoft.VisualStudio.SharePoint

    -   Microsoft.VisualStudio.Shell.11.0

    -   Microsoft.VisualStudio.Shell.Interop.10.0

    -   Microsoft.VisualStudio.Shell.Interop.11.0

    -   Microsoft.VisualStudio.TemplateWizardInterface

10. Wybierz **OK** przycisk, aby dodać zestawy do projektu.

11. W **Eksploratora rozwiązań**w obszarze **odwołania** folder **ProjectTemplateWizard** projektu, wybierz **EnvDTE**.

12. W **właściwości** okna, zmień wartość właściwości **Osadź typy współdziałania** właściwości **False**.

13. Jeśli tworzysz projekt języka Visual Basic importowania przestrzeni nazw ProjectTemplateWizard do projektu przy użyciu **projektanta projektu**.

     Aby uzyskać więcej informacji, zobacz [jak: Dodawanie lub usuwanie importowanych przestrzeni nazw &#40;języka Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).

#### <a name="to-configure-the-sharepointcommands-project"></a>Aby skonfigurować projekt SharePointcommands

1.  W **Eksploratora rozwiązań**, wybierz **SharePointCommands** węzeł projektu.

2.  Na pasku menu wybierz **projektu**, **Dodaj istniejący element**.

3.  W **Dodaj istniejący element** okno dialogowe, przejdź do folderu, który zawiera pliki kodu dla projektu ProjectTemplateWizard, a następnie wybierz **CommandIds** pliku kodu.

4.  Wybierz strzałkę obok **Dodaj** przycisk, a następnie wybierz **łącze Dodaj jako** opcję z menu.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje plik kodu, aby **SharePointCommands** projektu jako link. Plik kodu znajduje się w **ProjectTemplateWizard** również skompilowany projekt, ale kod w pliku **SharePointCommands** projektu.

5.  W **SharePointCommands** projektu, należy dodać inny plik kodu, który nosi nazwę polecenia.

6.  Wybierz projekt SharePointCommands, a następnie na pasku menu wybierz **projektu** > **Dodaj odwołanie**.

7.  Rozwiń **zestawy** węzła, wybierz **rozszerzenia** węzeł, a następnie zaznacz pole wyboru obok następujących zestawów:

    -   Microsoft.SharePoint

    -   Microsoft.VisualStudio.SharePoint.Commands

8.  Wybierz **OK** przycisk, aby dodać zestawy do projektu.

## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Tworzenie modelu kreatora, Menedżer podpisywania i identyfikatory poleceń programu SharePoint
 Dodaj kod do projektu ProjectTemplateWizard, aby zaimplementować następujące składniki w przykładzie:

- Identyfikatory poleceń programu SharePoint. Te ciągi zidentyfikować poleceń programu SharePoint, które korzysta z kreatora. W dalszej części tego przewodnika dodasz kod do projektu SharePointCommands do wykonania polecenia.

- Kreator modelu danych.

- Menedżer podpisywania projektu.

  Aby uzyskać więcej informacji dotyczących tych składników, zobacz [opis składników kreatora](#wizardcomponents).

#### <a name="to-define-the-sharepoint-command-ids"></a>Aby zdefiniować identyfikatory poleceń programu SharePoint

1.  W projekcie ProjectTemplateWizard Otwórz plik kodu CommandIds, a następnie zastąp całą zawartość tego pliku następującym kodem.

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]

#### <a name="to-create-the-wizard-model"></a>Aby utworzyć model Kreatora

1.  Otwórz plik kodu SiteColumnWizardModel i Zastąp całą zawartość tego pliku następującym kodem.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]

#### <a name="to-create-the-project-signing-manager"></a>Aby utworzyć Menedżera podpisywania projektu

1.  Otwórz plik kodu ProjectSigningManager, a następnie zastąp całą zawartość tego pliku następującym kodem.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]

## <a name="create-the-wizard-ui"></a>Kreator interfejsu użytkownika
 Dodaj XAML zdefiniować interfejsu użytkownika w oknie kreatora i kontrolki użytkownika dwóch, które udostępniają interfejs użytkownika dla stron kreatora, a następnie dodać kod do określania zachowania kontrolki okna i użytkownika. Kreator, którą tworzysz przypomina wbudowanego kreatora dla projektów programu SharePoint w programie Visual Studio.

> [!NOTE]
>  W poniższych krokach projekt będzie miał pewne błędy kompilacji, po dodaniu XAML lub kodu do projektu. Te błędy znikną po dodaniu kodu w dalszych krokach.

#### <a name="to-create-the-wizard-window-ui"></a>Aby utworzyć okno Kreatora interfejsu użytkownika

1.  W projekcie ProjectTemplateWizard, otwórz menu skrótów dla pliku WizardWindow.xaml, a następnie wybierz **Otwórz** aby otworzyć okno w projektancie.

2.  W widoku XAML w Projektancie XAML bieżącego należy zastąpić następujące XAML. XAML definiuje interfejs użytkownika, który zawiera nagłówek, <xref:System.Windows.Controls.Grid> , która zawiera strony kreatora, przyciski nawigacji w dolnej części okna.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]

    > [!NOTE]
    >  Okno, który jest tworzony w tym XAML jest tworzony na podstawie <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> klasy bazowej. Po dodaniu niestandardowe okno dialogowe WPF w programie Visual Studio, firma Microsoft zaleca, pochodzi z okna dialogowego z tej klasy mają spójnego stylów z innych oknach dialogowych programu Visual Studio i uniknąć problemów modalne okno dialogowe, które mogłyby wystąpić. Aby uzyskać więcej informacji, zobacz [tworzenie i zarządzanie modalne okna dialogowe](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).

3.  Jeśli tworzysz projekt języka Visual Basic, Usuń `ProjectTemplateWizard` przestrzeni nazw z `WizardWindow` nazwy klasy w `x:Class` atrybutu `Window` elementu. Ten element jest w pierwszym wierszu XAML. Gdy wszystko będzie gotowe, pierwszy wiersz powinien wyglądać podobnie jak w poniższym przykładzie.

    ```xml
    <Window x:Class="WizardWindow"
    ```

4.  Otwórz plik CodeBehind dla pliku WizardWindow.xaml.

5.  Zastąp zawartość tego pliku, z wyjątkiem `using` deklaracje na górze pliku następującym kodem.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]

#### <a name="to-create-the-first-wizard-page-ui"></a>Aby utworzyć pierwszą stronę kreatora interfejsu użytkownika

1.  W projekcie ProjectTemplateWizard, otwórz menu skrótów dla pliku Page1.xaml, a następnie wybierz **Otwórz** do otwierania kontrolki użytkownika w projektancie.

2.  W widoku XAML w Projektancie XAML bieżącego należy zastąpić następujące XAML. XAML definiuje interfejs użytkownika, który zawiera pole tekstowe, w którym użytkownik może wprowadzić adres URL witryny lokalne, które mają być używane do debugowania. Interfejs użytkownika umożliwia także przycisków opcji za pomocą którego użytkownicy mogą określić, czy projekt jest w trybie piaskownicy.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]

3.  Jeśli tworzysz projekt języka Visual Basic, Usuń `ProjectTemplateWizard` przestrzeni nazw z `Page1` nazwy klasy w `x:Class` atrybutu `UserControl` elementu. Jest to w pierwszym wierszu XAML. Gdy wszystko będzie gotowe, pierwszy wiersz powinien wyglądać następująco.

    ```xml
    <UserControl x:Class="Page1"
    ```

4.  Zastąp zawartość pliku Page1.xaml, z wyjątkiem `using` deklaracje na górze pliku następującym kodem.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]

#### <a name="to-create-the-second-wizard-page-ui"></a>Aby utworzyć drugiej stronie Kreatora interfejsu użytkownika

1.  W projekcie ProjectTemplateWizard, otwórz menu skrótów dla pliku Page2.xaml, a następnie wybierz **Otwórz**.

     Formant użytkownika zostanie otwarty w projektancie.

2.  W widoku XAML Zastąp bieżący XAML następujące XAML. XAML definiuje interfejs użytkownika, który zawiera listy rozwijanej wyboru podstawowy typ kolumny witryny, pola kombi do określania wbudowanych lub niestandardowych grupę, do którego mają być wyświetlone kolumny witryny w galerii i pole tekstowe do określania nazwy kolumny witryny.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]

3.  Jeśli tworzysz projekt języka Visual Basic, Usuń `ProjectTemplateWizard` przestrzeni nazw z `Page2` nazwy klasy w `x:Class` atrybutu `UserControl` elementu. Jest to w pierwszym wierszu XAML. Gdy wszystko będzie gotowe, pierwszy wiersz powinien wyglądać następująco.

    ```xml
    <UserControl x:Class="Page2"
    ```

4.  Zastąp zawartość pliku związanego z kodem dla pliku Page2.xaml, z wyjątkiem `using` deklaracje na górze pliku następującym kodem.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]

## <a name="implement-the-wizard"></a>Implementowanie Kreatora
 Zdefiniuj główne funkcje kreatora implementując <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsu. Ten interfejs definiuje metody, które wywołuje program Visual Studio, gdy Kreator rozpoczyna się zakończy i w określonym czasie podczas Kreator uruchamia.

#### <a name="to-implement-the-wizard"></a>Aby zaimplementować Kreatora

1.  W projekcie ProjectTemplateWizard Otwórz plik kodu SiteColumnProjectWizard.

2.  Zamień całą zawartość tego pliku następującym kodem.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]

## <a name="create-the-sharepoint-commands"></a>Tworzenie polecenia SharePoint
 Utwórz dwa polecenia niestandardowe odwołujące się do modelu obiektów serwera SharePoint. Jedno polecenie Określa, czy adres URL witryny użytkownik wpisze w kreatorze jest prawidłowa. Inne polecenie pobiera wszystkie typy pól z określonej witryny programu SharePoint, tak, aby użytkownicy mogą wybrać, który z nich będzie użyć jako podstawy dla ich nowej kolumny witryny.

#### <a name="to-define-the-sharepoint-commands"></a>Aby zdefiniować poleceń programu SharePoint

1.  W **SharePointCommands** projektu, otwórz plik kodu poleceń.

2.  Zamień całą zawartość tego pliku następującym kodem.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]

## <a name="checkpoint"></a>Punkt kontrolny
 W tym momencie w instruktażu, cały kod dla kreatora znajduje się teraz w projekcie. Skompiluj projekt, aby upewnić się, że kompiluje bez błędów.

#### <a name="to-build-your-project"></a>Do kompilowania projektu

1.  Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.

## <a name="removing-the-keysnk-file-from-the-project-template"></a>Usuwanie pliku key.snk za pomocą szablonu projektu
 W [instruktażu: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), szablon projektu, który został utworzony zawiera plik key.snk, który jest używany do podpisywania każde wystąpienie projektu kolumny witryny. Ten plik key.snk nie jest już konieczne ponieważ Kreator generuje nowy plik key.snk dla każdego projektu. Usuń plik key.snk z szablonu projektu i usuń odwołania do tego pliku.

#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>Aby usunąć plik key.snk z szablonu projektu

1.  W **Eksploratora rozwiązań**w obszarze **SiteColumnProjectTemplate** węzła, otwórz menu skrótów dla **key.snk** , a następnie wybierz **Usuń**.

2.  W oknie dialogowym potwierdzenia wybierz **OK** przycisku.

3.  W obszarze **SiteColumnProjectTemplate** węzła, otwórz plik SiteColumnProjectTemplate.vstemplate, a następnie usuń następujący element z niego.

    ```xml
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
    ```

4.  Zapisz i zamknij plik.

5.  W obszarze **SiteColumnProjectTemplate** węzła, otwórz plik ProjectTemplate.csproj lub ProjectTemplate.vbproj, a następnie usuń następujące `PropertyGroup` elementu z niego.

    ```xml
    <PropertyGroup>
      <SignAssembly>true</SignAssembly>
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
    </PropertyGroup>
    ```

6.  Usuń następujący `None` elementu.

    ```xml
    <None Include="key.snk" />
    ```

7.  Zapisz i zamknij plik.

## <a name="associating-the-wizard-with-the-project-template"></a>Kojarzenie kreatora z szablonu projektu
 Teraz, że udało Ci się wdrożyć kreatora, należy skojarzyć kreatora **kolumny witryny** szablonu projektu. Istnieją trzy procedury, które należy wykonać, aby to zrobić:

1.  Podpisz zestaw kreatora, za pomocą silnej nazwy.

2.  Pobierz token klucza publicznego dla zestawu kreatora.

3.  Dodaj odwołanie do zestawu kreatora w pliku .vstemplate **kolumny witryny** szablonu projektu.

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Aby zarejestrować Kreatora zestawu o silnej nazwie

1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **ProjectTemplateWizard** projektu, a następnie wybierz **właściwości**.

2.  Na **podpisywanie** zaznacz **Podpisz zestaw** pole wyboru.

3.  W **wybierz plik klucza o silnej nazwie** wybierz  **\<nowy... >**.

4.  W **Utwórz klucz silnej nazwy** okna dialogowego wprowadź nazwę dla nowego pliku klucza, usuń zaznaczenie **Chroń mój plik klucza przy użyciu hasła** pole wyboru, a następnie wybierz **OK** przycisku.

5.  Otwórz menu skrótów dla **ProjectTemplateWizard** projektu, a następnie wybierz **kompilacji** można utworzyć pliku ProjectTemplateWizard.dll.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Aby uzyskać klucz publiczny token dla zestawu Kreatora

1.  Na **Start Menu**, wybierz **wszystkie programy**, wybierz **programu Microsoft Visual Studio**, wybierz **Visual Studio Tools**, a następnie wybierz polecenie  **Wiersz polecenia dla deweloperów**.

     Zostanie otwarte okno wiersza polecenia programu Visual Studio.

2.  Uruchom następujące polecenie, zastępując *PathToWizardAssembly* mającym pełną ścieżkę do zestawu ProjectTemplateWizard.dll utworzone dla projektu ProjectTemplateWizard na komputerze deweloperskim:

    ```cmd
    sn.exe -T PathToWizardAssembly
    ```

     Token klucza publicznego dla zestawu ProjectTemplateWizard.dll są zapisywane do okna wiersza polecenia programu Visual Studio.

3.  Nie zamykaj okna wiersza polecenia programu Visual Studio. Token klucza publicznego, należy podczas następnej procedury.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Aby dodać odwołanie do zestawu kreatora w pliku .vstemplate

1.  W **Eksploratora rozwiązań**, rozwiń węzeł **SiteColumnProjectTemplate** węzeł projektu i Otwórz plik SiteColumnProjectTemplate.vstemplate.

2.  Pod koniec pliku, Dodaj następujący kod `WizardExtension` element między `</TemplateContent>` i `</VSTemplate>` tagów. Zastąp *token* wartość `PublicKeyToken` atrybut o token klucza publicznego, uzyskaną w poprzedniej procedurze.

    ```xml
    <WizardExtension>
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>
    </WizardExtension>
    ```

     Aby uzyskać więcej informacji na temat `WizardExtension` elementu, zobacz [wizardextension — Element &#40;szablony programu Visual Studio&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).

3.  Zapisz i zamknij plik.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Dodaj parametry wymienne do pliku Elements.xml w szablonie projektu
 Dodaj kilku wymiennych parametrów w celu *Elements.xml* pliku w projekcie SiteColumnProjectTemplate. Te parametry są inicjowane w `RunStarted` method in Class metoda `SiteColumnProjectWizard` klasy określonej wcześniej. Gdy użytkownik tworzy projekt kolumny witryny, Visual Studio automatycznie zastępuje tych parametrów w *Elements.xml* plik w nowym projekcie z wartościami, które są określone w kreatorze.

 Parametr wymienny jest token, który rozpoczyna się i kończy znak dolara ($). Oprócz definiowania wymienne parametry, można użyć wbudowanych parametry, które są zdefiniowane i zainicjowane przez system projektu programu SharePoint. Aby uzyskać więcej informacji, zobacz [parametrów zastępowalnych](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Aby dodać parametry wymienne do pliku Elements.xml

1.  W projekcie SiteColumnProjectTemplate, Zastąp zawartość *Elements.xml* pliku następujący kod XML.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <Field ID="{$guid5$}"
             Name="$fieldname$"
             DisplayName="$fieldname$"
             Type="$selectedfieldtype$"
             Group="$selectedgrouptype$">
      </Field>
    </Elements>
    ```

     Nowy plik XML powoduje zmianę wartości `Name`, `DisplayName`, `Type`, i `Group` atrybuty niestandardowe zastępowalnych parametrów.

2.  Zapisz i zamknij plik.

## <a name="add-the-wizard-to-the-vsix-package"></a>Kreator dodawania do pakietu VSIX
 Aby wdrożyć kreatora pakiet VSIX, który zawiera szablon projektu kolumny witryny, należy dodać odwołania do Kreatora projektu i projektu poleceń programu SharePoint do pliku source.extension.vsixmanifest w projekcie VSIX.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Aby dodać kreatora do pakietu VSIX

1.  W **Eksploratora rozwiązań**w **SiteColumnProjectItem** projektu, otwórz menu skrótów dla **source.extension.vsixmanifest** , a następnie wybierz **Otwórz**.

     Program Visual Studio otwiera plik w edytorze manifestu.

2.  Na **zasoby** karta w edytorze wybierz **nowy** przycisku.

     **Dodaj nowy zasób** zostanie otwarte okno dialogowe.

3.  W **typu** wybierz **Microsoft.VisualStudio.Assembly**.

4.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.

5.  W **projektu** wybierz **ProjectTemplateWizard**, a następnie wybierz **OK** przycisku.

6.  Na **zasoby** karta w edytorze wybierz **New** ponownie przycisk.

     **Dodaj nowy zasób** zostanie otwarte okno dialogowe.

7.  W **typu** listy, wprowadź **SharePoint.Commands.v4**.

8.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.

9. W **projektu** wybierz **SharePointCommands** projektu, a następnie wybierz **OK** przycisku.

10. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**, a następnie upewnij się, że rozwiązanie zostanie skompilowane bez błędów.

## <a name="test-the-wizard"></a>Kreator testu
 Teraz można przystąpić do testowania kreatora. Po pierwsze uruchom debugowanie rozwiązania SiteColumnProjectItem w doświadczalnym wystąpieniu programu Visual Studio. Następnie przetestuj Kreator projektu kolumn witryny w doświadczalnym wystąpieniu programu Visual Studio. Na koniec Skompiluj i uruchom projekt, aby sprawdzić, czy kolumny witryny działa zgodnie z oczekiwaniami.

#### <a name="to-start-debugging-the-solution"></a>Aby rozpocząć debugowanie rozwiązania

1.  Uruchom program Visual Studio przy użyciu poświadczeń administracyjnych, a następnie otwórz rozwiązanie SiteColumnProjectItem.

2.  W projekcie ProjectTemplateWizard, otwórz plik kodu SiteColumnProjectWizard, a następnie Dodaj punkt przerwania do pierwszego wiersza kodu w `RunStarted` metody.

3.  Na pasku menu wybierz **debugowania** > **wyjątki**.

4.  W **wyjątki** okna dialogowego pole, upewnij się, że **zgłoszenia** i **User-unhandled** pola wyboru dla **wyjątki środowiska uruchomieniowego języka wspólnego**zostaną wyczyszczone, a następnie wybierz **OK** przycisku.

5.  Rozpocznij debugowanie wybierając **F5** klucza lub na pasku menu, wybierając **debugowania** > **Rozpocznij debugowanie**.

     Visual Studio instaluje rozszerzenia do %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 i uruchamia doświadczalne wystąpienie programu Visual Studio. Element projektu będzie testu, w tym wystąpieniu programu Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Aby przetestować kreatora w programie Visual Studio

1. W doświadczalnym wystąpieniu programu Visual Studio, na pasku menu wybierz **pliku** > **New** > **projektu**.

2. Rozwiń **Visual C#** węzła lub **języka Visual Basic** węzeł (w zależności od języka obsługującego przez szablon projektu), rozwiń węzeł **programu SharePoint** węzła, a następnie wybierz pozycję **2010** węzła.

3. Na liście szablonów projektu wybierz **kolumny witryny**, nadaj projektowi nazwę **SiteColumnWizardTest**, a następnie wybierz **OK** przycisku.

4. Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkcie przerwania, który wcześniej w ustawieniu `RunStarted` metody.

5. Kontynuuj debugowanie projektu, wybierając **F5** klucza lub na pasku menu, wybierając **debugowania** > **Kontynuuj**.

6. W **Kreator ustawień niestandardowych SharePoint**, wprowadź adres URL witryny, której chcesz używać do debugowania, a następnie wybierz **dalej** przycisku.

7. W drugiej stronie **Kreator ustawień niestandardowych SharePoint**, wybierz następujące opcje:

   - W **typu** wybierz **logiczna**.

   - W **grupy** wybierz **kolumn Yes/No niestandardowe**.

   - W **nazwa** wprowadź **Moje kolumny Yes/No**, a następnie wybierz **Zakończ** przycisku.

     W **Eksploratora rozwiązań**, pojawia się nowy projekt i zawiera element projektu o nazwie **pole1**, i Visual Studio otwiera projektu *Elements.xml* plik w edytorze.

8. Upewnij się, że *Elements.xml* zawiera wartości, które są określone w kreatorze.

#### <a name="to-test-the-site-column-in-sharepoint"></a>Aby przetestować kolumny witryny w programie SharePoint

1.  W doświadczalnym wystąpieniu programu Visual Studio, wybierz **F5** klucza.

     Kolumny witryny zostaną spakowane i wdrożone dla programu SharePoint witryny **adres URL witryny** Określa właściwość projektu. Przeglądarka sieci web zostanie otwarta domyślna strona tej lokacji.

    > [!NOTE]
    >  Jeśli **wyłączenia debugowania skryptu** pojawi się okno dialogowe, wybierz **tak** przycisk, aby kontynuować debugowanie projektu.

2.  Na **Akcje witryny** menu, wybierz **ustawienia lokacji**.

3.  Na stronie Ustawienia lokacji w ramach **galerie**, wybierz **kolumny witryny** łącza.

4.  Na liście kolumn witryn, upewnij się, że **kolumn Yes/No niestandardowe** grupa zawiera kolumnę o nazwie **Moje kolumny Yes/No**, a następnie zamknij przeglądarkę sieci web.

## <a name="clean-up-the-development-computer"></a>Czyszczenie na komputerze deweloperskim
 Po zakończeniu badania elementu projektu, należy usunąć szablon projektu w doświadczalnym wystąpieniu programu Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Aby wyczyścić komputerze deweloperskim

1.  W doświadczalnym wystąpieniu programu Visual Studio, na pasku menu wybierz **narzędzia** > **rozszerzenia i aktualizacje**.

     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.

2.  Na liście rozszerzeń wybierz **kolumny witryny**, a następnie wybierz **Odinstaluj** przycisku.

3.  W oknie dialogowym wybierz **tak** przycisk, aby upewnić się, że chcesz odinstalować rozszerzenie, a następnie wybierz **Uruchom ponownie teraz** przycisk, aby ukończyć dezinstalację.

4.  Zamknij zarówno w doświadczalnym wystąpieniu programu Visual Studio, jak i wystąpienia, w którym rozwiązanie CustomActionProjectItem jest otwarty.

     Aby uzyskać informacje o sposobie wdrażania [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenia, zobacz [wysyłania rozszerzenia programu Visual Studio](/visualstudio/extensibility/shipping-visual-studio-extensions).

## <a name="see-also"></a>Zobacz także
- [Przewodnik: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Odwołanie do schematu szablonu Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [Instrukcje: Korzystanie z kreatorów z szablonami projektu](../extensibility/how-to-use-wizards-with-project-templates.md)
