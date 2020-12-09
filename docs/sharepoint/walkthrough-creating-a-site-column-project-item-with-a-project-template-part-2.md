---
title: Utwórz element projektu kolumny witryny z szablonem projektu, część 2
titleSuffix: ''
description: Dodawanie kreatora do szablonu projektu kolumny witryny w celu zbierania danych od użytkowników, gdy używają tego szablonu do tworzenia projektu programu SharePoint zawierającego element projektu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e6e5c9a0bb461f6b81b9cb7e1aa5f0134a7bdcbd
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915144"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 2
  Po zdefiniowaniu niestandardowego typu elementu projektu programu SharePoint i skojarzeniu go z szablonem projektu w programie Visual Studio, można również udostępnić Kreator szablonu. Za pomocą kreatora można zbierać informacje od użytkowników, gdy używają szablonu do tworzenia nowego projektu, który zawiera element projektu. Zbierane informacje mogą służyć do inicjowania elementu projektu.

 W tym instruktażu dodasz kreatora do szablonu projektu kolumny witryny, który jest prezentowany w [przewodniku: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md). Gdy użytkownik tworzy projekt kolumny witryny, Kreator zbiera informacje o kolumnie witryny (takiej jak jej typ podstawowy i Grupa) i dodaje te informacje do pliku *Elements.xml* w nowym projekcie.

 W tym instruktażu przedstawiono następujące zadania:

- Tworzenie Kreatora dla niestandardowego typu elementu projektu programu SharePoint, który jest skojarzony z szablonem projektu.

- Definiowanie niestandardowego interfejsu użytkownika Kreatora podobnego do wbudowanych kreatorów projektów programu SharePoint w programie Visual Studio.

- Tworzenie dwóch *poleceń programu SharePoint* , które są używane do wywoływania w lokalnej witrynie programu SharePoint podczas działania kreatora. Polecenia programu SharePoint to metody, które mogą być używane przez rozszerzenia programu Visual Studio do wywoływania interfejsów API w modelu obiektów programu SharePoint Server. Aby uzyskać więcej informacji, zobacz [Wywoływanie modeli obiektów programu SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Użycie parametrów wymiennych w celu zainicjowania plików projektu programu SharePoint za pomocą danych zebranych w kreatorze.

- Tworzenie nowego pliku. snk w każdym nowym wystąpieniu projektu kolumny witryny. Ten plik jest używany do podpisywania danych wyjściowych projektu, dzięki czemu można wdrożyć zestaw rozwiązań programu SharePoint w globalnej pamięci podręcznej zestawów.

- Debugowanie i testowanie Kreatora.

> [!NOTE]
> Aby uzyskać szereg przykładowych przepływów pracy, zobacz [przykłady przepływu pracy programu SharePoint](/sharepoint/dev/general-development/sharepoint-workflow-samples).

## <a name="prerequisites"></a>Wymagania wstępne
 Aby wykonać ten Instruktaż, należy najpierw utworzyć rozwiązanie SiteColumnProjectItem, wykonując wskazówki [: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 Aby ukończyć ten przewodnik, potrzebne są również następujące składniki na komputerze deweloperskim:

- Obsługiwane wersje systemu Windows, SharePoint i Visual Studio.

- Zestaw SDK programu Visual Studio. W tym instruktażu zostanie użyty szablon **projektu VSIX** w zestawie SDK, aby utworzyć pakiet VSIX do wdrożenia elementu projektu. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzającą narzędzia programu SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Znajomość następujących pojęć jest pomocna, ale nie jest wymagana, aby ukończyć Przewodnik:

- Kreatorzy szablonów projektów i elementów w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [jak: korzystanie z kreatorów z szablonami projektów](../extensibility/how-to-use-wizards-with-project-templates.md) i <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsem.

- Kolumny witryny w programie SharePoint. Aby uzyskać więcej informacji, zobacz [kolumny](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

## <a name="understand-the-wizard-components"></a>Omówienie składników Kreatora
 Kreator, który jest prezentowany w tym instruktażu, zawiera kilka składników. W poniższej tabeli opisano te składniki.

|Składnik|Opis|
|---------------|-----------------|
|Implementacja Kreatora|Jest to Klasa o nazwie `SiteColumnProjectWizard` , która implementuje <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejs. Ten interfejs definiuje metody, które program Visual Studio wywołuje po uruchomieniu i zakończeniu pracy kreatora, a w pewnym czasie w trakcie działania kreatora.|
|Interfejs użytkownika Kreatora|To jest okno oparte na platformie WPF o nazwie `WizardWindow` . To okno zawiera dwie kontrolki użytkownika o nazwie `Page1` i `Page2` . Te kontrolki użytkownika reprezentują dwie strony kreatora.<br /><br /> W tym instruktażu <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> Metoda implementacji kreatora wyświetla interfejs użytkownika kreatora.|
|Model danych kreatora|Jest to Klasa pośrednicząca o nazwie `SiteColumnWizardModel` , która udostępnia warstwę między interfejsem użytkownika Kreatora a implementacją kreatora. Ten przykład używa tej klasy w celu ułatwienia abstrakcyjnej implementacji kreatora i interfejsu użytkownika kreatora. Ta klasa nie jest składnikiem wymaganym przez wszystkich kreatorów.<br /><br /> W tym instruktażu implementacja kreatora przekazuje `SiteColumnWizardModel` obiekt do okna kreatora, gdy zostanie wyświetlony interfejs użytkownika kreatora. Interfejs użytkownika Kreatora używa metod tego obiektu do zapisania wartości formantów w interfejsie użytkownika i wykonywania zadań, takich jak sprawdzenie, czy adres URL witryny wejściowej jest prawidłowy. Po zakończeniu pracy kreatora przez użytkownika, implementacja kreatora używa `SiteColumnWizardModel` obiektu do określenia końcowego stanu interfejsu użytkownika.|
|Menedżer podpisywania projektu|Jest to Klasa pomocnika o nazwie `ProjectSigningManager` , która jest używana przez implementację kreatora do utworzenia nowego pliku Key. snk w każdym nowym wystąpieniu projektu.|
|SharePoint — Polecenia|Są to metody, które są używane przez model danych kreatora do wywoływania lokalnej witryny programu SharePoint podczas działania kreatora. Ponieważ polecenia programu SharePoint muszą wskazywać .NET Framework 3,5, te polecenia są implementowane w innym zestawie niż pozostała część kodu kreatora.|

## <a name="create-the-projects"></a>Tworzenie projektów
 Aby ukończyć ten przewodnik, musisz dodać kilka projektów do rozwiązania SiteColumnProjectItem, które zostało utworzone w [przewodniku: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):

- Projekt WPF. Interfejs zostanie wdrożony <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> i zdefiniujesz interfejs użytkownika kreatora w tym projekcie.

- Projekt biblioteki klas, który definiuje polecenia programu SharePoint. Ten projekt musi być przeznaczony dla the.NET Framework 3,5.

  Rozpocznij przewodnik, tworząc projekty.

#### <a name="to-create-the-wpf-project"></a>Aby utworzyć projekt WPF

1. W programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwórz rozwiązanie SiteColumnProjectItem.

2. W **Eksplorator rozwiązań** Otwórz menu skrótów dla węzła rozwiązanie **SiteColumnProjectItem** , wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

3. Na początku okna dialogowego **Dodawanie nowego projektu** upewnij się, że na liście wersji .NET Framework wybrano **.NET Framework 4,5** .

4. Rozwiń węzeł **Visual C#** lub węzeł **Visual Basic** i wybierz węzeł **systemu Windows** .

5. Na liście szablonów projektu wybierz pozycję **Biblioteka formantów użytkownika WPF**, nazwij projekt **ProjectTemplateWizard**, a następnie wybierz przycisk **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje projekt **ProjectTemplateWizard** do rozwiązania i otwiera domyślny plik UserControl1. XAML.

6. Usuń plik UserControl1. XAML z projektu.

#### <a name="to-create-the-sharepoint-commands-project"></a>Aby utworzyć projekt poleceń programu SharePoint

1. W **Eksplorator rozwiązań** Otwórz menu skrótów dla węzła rozwiązanie SiteColumnProjectItem, wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

2. W górnej części okna dialogowego **Dodaj nowy projekt** wybierz pozycję **.NET Framework 3,5** na liście wersji .NET Framework.

3. Rozwiń węzeł **Visual C#** lub węzeł  **Visual Basic** , a następnie wybierz węzeł **systemu Windows** .

4. Wybierz szablon projektu **Biblioteka klas** , nazwij projekt **SharePointCommands**, a następnie wybierz przycisk **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje projekt **SharePointCommands** do rozwiązania i otwiera domyślny plik kodu Class1.

5. Usuń plik kodu Class1 z projektu.

## <a name="configure-the-projects"></a>Konfigurowanie projektów
 Przed utworzeniem kreatora należy dodać do projektu pewne pliki kodu i odwołania do zestawów.

#### <a name="to-configure-the-wizard-project"></a>Aby skonfigurować projekt Kreatora

1. W **Eksplorator rozwiązań** Otwórz menu skrótów dla węzła projektu **ProjectTemplateWizard** , a następnie wybierz polecenie **Właściwości**.

2. W **projektancie projektu** wybierz kartę **aplikacja** dla projektu Visual C# lub kartę **kompilacja** dla projektu Visual Basic.

3. Upewnij się, że dla platformy docelowej ustawiono .NET Framework 4,5, a nie profil klienta .NET Framework 4,5.

     Aby uzyskać więcej informacji, zobacz [How to: Target of a wersja .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

4. Otwórz menu skrótów dla projektu **ProjectTemplateWizard** , wybierz **Dodaj**, a następnie wybierz **nowy element**.

5. Wybierz element **window (WPF)** , nazwij element **WizardWindow**, a następnie wybierz przycisk **Dodaj** .

6. Dodaj dwa elementy **kontrolki użytkownika (WPF)** do projektu i nadaj im nazwę **Strona1** i **PAGE2**.

7. Dodaj cztery pliki kodu do projektu i nadaj im następujące nazwy:

    - SiteColumnProjectWizard

    - SiteColumnWizardModel

    - ProjectSigningManager

    - CommandIds

8. Otwórz menu skrótów dla węzła projektu **ProjectTemplateWizard** , a następnie wybierz **Dodaj odwołanie**.

9. Rozwiń węzeł **zestawy** , wybierz węzeł **rozszerzenia** , a następnie zaznacz pola wyboru obok następujących zestawów:

    - EnvDTE

    - Microsoft. VisualStudio. OLE. Interop

    - Microsoft. VisualStudio. SharePoint

    - Microsoft. VisualStudio. Shell. 11.0

    - Microsoft. VisualStudio. Shell. Interop. 10.0

    - Microsoft. VisualStudio. Shell. Interop. 11.0

    - Microsoft. VisualStudio. TemplateWizardInterface

10. Wybierz przycisk **OK** , aby dodać zestawy do projektu.

11. W **Eksplorator rozwiązań**, w folderze **References** dla projektu **ProjectTemplateWizard** , wybierz **EnvDTE**.

12. W oknie **Właściwości** Zmień wartość właściwości **Osadź typy** współdziałania na **wartość false**.

13. Jeśli tworzysz projekt Visual Basic, zaimportuj przestrzeń nazw ProjectTemplateWizard do projektu za pomocą **projektanta projektu**.

     Aby uzyskać więcej informacji, zobacz [jak: Dodawanie lub usuwanie importowanych przestrzeni nazw &#40;Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).

#### <a name="to-configure-the-sharepointcommands-project"></a>Aby skonfigurować projekt SharePointcommands

1. W **Eksplorator rozwiązań** wybierz węzeł projektu **SharePointCommands** .

2. Na pasku menu wybierz **projekt**,  **Dodaj istniejący element**.

3. W oknie dialogowym **Dodaj istniejący element** przejdź do folderu, który zawiera pliki kodu dla projektu ProjectTemplateWizard, a następnie wybierz plik kodu **CommandIds** .

4. Wybierz strzałkę obok przycisku **Dodaj** , a następnie wybierz opcję **Dodaj jako łącze** w wyświetlonym menu.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje plik kodu do projektu **SharePointCommands** jako link. Plik kodu znajduje się w projekcie **ProjectTemplateWizard** , ale kod w pliku jest również kompilowany w projekcie **SharePointCommands** .

5. W projekcie **SharePointCommands** Dodaj inny plik kodu o nazwie Commands.

6. Wybierz projekt SharePointCommands, a następnie na pasku menu wybierz **projekt**  >  **Dodaj odwołanie**.

7. Rozwiń węzeł **zestawy** , wybierz węzeł **rozszerzenia** , a następnie zaznacz pola wyboru obok następujących zestawów:

    - Microsoft. SharePoint

    - Microsoft. VisualStudio. SharePoint. Commands

8. Wybierz przycisk **OK** , aby dodać zestawy do projektu.

## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Tworzenie modelu kreatora, Menedżera podpisywania i identyfikatorów poleceń programu SharePoint
 Dodaj kod do projektu ProjectTemplateWizard, aby zaimplementować następujące składniki w przykładzie:

- Identyfikatory poleceń programu SharePoint. Te ciągi identyfikują polecenia programu SharePoint, które są używane przez kreatora. W dalszej części tego instruktażu dodasz kod do projektu SharePointCommands w celu zaimplementowania poleceń.

- Model danych kreatora.

- Menedżer podpisywania projektu.

  Aby uzyskać więcej informacji o tych składnikach, zobacz [Omówienie składników kreatora](#understand-the-wizard-components).

#### <a name="to-define-the-sharepoint-command-ids"></a>Aby zdefiniować identyfikatory poleceń programu SharePoint

1. W projekcie ProjectTemplateWizard Otwórz plik kodu CommandIds, a następnie zastąp całą zawartość tego pliku następującym kodem.

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]

#### <a name="to-create-the-wizard-model"></a>Aby utworzyć model Kreatora

1. Otwórz plik kodu SiteColumnWizardModel i Zastąp całą zawartość tego pliku następującym kodem.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]

#### <a name="to-create-the-project-signing-manager"></a>Aby utworzyć Menedżera podpisywania projektu

1. Otwórz plik kodu ProjectSigningManager, a następnie zastąp całą zawartość tego pliku następującym kodem.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]

## <a name="create-the-wizard-ui"></a>Tworzenie interfejsu użytkownika Kreatora
 Dodaj XAML, aby zdefiniować interfejs użytkownika okna kreatora oraz dwie kontrolki użytkownika, które udostępniają interfejs użytkownika dla stron kreatora, a następnie Dodaj kod, aby zdefiniować zachowanie formantów okna i użytkownika. Kreator, który utworzysz, przypomina kreatora wbudowanego dla projektów programu SharePoint w programie Visual Studio.

> [!NOTE]
> W poniższych krokach projekt będzie zawierał pewne błędy kompilacji po dodaniu kodu XAML lub Code do projektu. Te błędy zostaną odrzucone po dodaniu kodu w dalszych krokach.

#### <a name="to-create-the-wizard-window-ui"></a>Aby utworzyć interfejs użytkownika okna Kreatora

1. W projekcie ProjectTemplateWizard Otwórz menu skrótów dla pliku WizardWindow. XAML, a następnie wybierz **Otwórz** , aby otworzyć okno w projektancie.

2. W widoku XAML projektanta zastąp bieżący kod XAML następującym XAML. KOD XAML definiuje interfejs użytkownika, który zawiera nagłówek, zawierający <xref:System.Windows.Controls.Grid> strony kreatora i przyciski nawigacji w dolnej części okna.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]

    > [!NOTE]
    > Okno, które zostało utworzone w tym języku XAML, pochodzi od <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> klasy bazowej. Po dodaniu niestandardowego okna dialogowego WPF do programu Visual Studio zalecamy, aby można było utworzyć okno dialogowe z tej klasy, aby mieć spójne style z innymi oknach dialogowych programu Visual Studio i uniknąć problemów z modalnym oknem dialogowym, które mogłyby wystąpić w przeciwnym razie. Aby uzyskać więcej informacji, zobacz [Tworzenie modalnych okien dialogowych i zarządzanie nimi](../extensibility/creating-and-managing-modal-dialog-boxes.md).

3. Jeśli tworzysz projekt Visual Basic, Usuń `ProjectTemplateWizard` przestrzeń nazw z `WizardWindow` nazwy klasy w `x:Class` atrybucie `Window` elementu. Ten element znajduje się w pierwszym wierszu XAML. Gdy skończysz, pierwszy wiersz powinien wyglądać podobnie do poniższego przykładu.

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. Otwórz plik związany z kodem dla pliku WizardWindow. XAML.

5. Zastąp zawartość tego pliku, z wyjątkiem `using` deklaracji w górnej części pliku, przy użyciu następującego kodu.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]

#### <a name="to-create-the-first-wizard-page-ui"></a>Aby utworzyć pierwszy interfejs użytkownika strony kreatora

1. W projekcie ProjectTemplateWizard, otwórz menu skrótów dla pliku Strona1. XAML, a następnie wybierz **Otwórz** , aby otworzyć kontrolkę użytkownika w projektancie.

2. W widoku XAML projektanta zastąp bieżący kod XAML następującym XAML. KOD XAML definiuje interfejs użytkownika, który zawiera pole tekstowe, w którym użytkownicy mogą wprowadzić adres URL lokalnych witryn, których chcą używać do debugowania. Interfejs użytkownika zawiera również przyciski opcji, za pomocą których użytkownicy mogą określić, czy projekt jest w trybie piaskownicy.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]

3. Jeśli tworzysz projekt Visual Basic, Usuń `ProjectTemplateWizard` przestrzeń nazw z `Page1` nazwy klasy w `x:Class` atrybucie `UserControl` elementu. Jest to pierwsza linia XAML. Gdy skończysz, pierwszy wiersz powinien wyglądać podobnie do poniższego.

    ```xml
    <UserControl x:Class="Page1"
    ```

4. Zastąp zawartość pliku Strona1. XAML, z wyjątkiem `using` deklaracji w górnej części pliku, przy użyciu następującego kodu.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]

#### <a name="to-create-the-second-wizard-page-ui"></a>Aby utworzyć drugi interfejs użytkownika strony kreatora

1. W projekcie ProjectTemplateWizard Otwórz menu skrótów dla pliku PAGE2. XAML, a następnie wybierz polecenie **Otwórz**.

     Formant użytkownika zostanie otwarty w projektancie.

2. W widoku XAML zastąp bieżący kod XAML następującym XAML. KOD XAML definiuje interfejs użytkownika, który zawiera listę rozwijaną służącą do wybierania typu podstawowego kolumny lokacja, pola kombi do określania wbudowanej lub niestandardowej grupy, w której ma zostać wyświetlona kolumna lokacja w galerii, oraz pole tekstowe służące do określania nazwy kolumny witryny.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]

3. Jeśli tworzysz projekt Visual Basic, Usuń `ProjectTemplateWizard` przestrzeń nazw z `Page2` nazwy klasy w `x:Class` atrybucie `UserControl` elementu. Jest to pierwsza linia XAML. Gdy skończysz, pierwszy wiersz powinien wyglądać podobnie do poniższego.

    ```xml
    <UserControl x:Class="Page2"
    ```

4. Zastąp zawartość pliku związanego z kodem dla pliku PAGE2. XAML, z wyjątkiem `using` deklaracji w górnej części pliku, przy użyciu następującego kodu.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]

## <a name="implement-the-wizard"></a>Zaimplementuj Kreatora
 Definiowanie głównych funkcji Kreatora przez implementację <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsu. Ten interfejs definiuje metody, które program Visual Studio wywołuje po uruchomieniu i zakończeniu pracy kreatora, a w pewnym czasie w trakcie działania kreatora.

#### <a name="to-implement-the-wizard"></a>Aby zaimplementować Kreatora

1. W projekcie ProjectTemplateWizard Otwórz plik kodu SiteColumnProjectWizard.

2. Zastąp całą zawartość tego pliku następującym kodem.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]

## <a name="create-the-sharepoint-commands"></a>Tworzenie poleceń programu SharePoint
 Utwórz dwa niestandardowe polecenia, które odwołują się do modelu obiektów programu SharePoint Server. Jedno polecenie określa, czy adres URL witryny, który jest w kreatorze, jest prawidłowy. Inne polecenie pobiera wszystkie typy pól z określonej witryny programu SharePoint, dzięki czemu użytkownicy mogą wybrać, który z nich ma być używany jako podstawa dla nowej kolumny witryny.

#### <a name="to-define-the-sharepoint-commands"></a>Aby zdefiniować polecenia programu SharePoint

1. W projekcie **SharePointCommands** Otwórz plik kodu poleceń.

2. Zastąp całą zawartość tego pliku następującym kodem.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]

## <a name="checkpoint"></a>Punkt kontrolny
 W tym momencie w przewodniku cały kod kreatora jest teraz w projekcie. Skompiluj projekt, aby upewnić się, że kompiluje się bez błędów.

#### <a name="to-build-your-project"></a>Aby skompilować projekt

1. Na pasku menu wybierz polecenie **Kompiluj**  >  **kompilację rozwiązania**.

## <a name="removing-the-keysnk-file-from-the-project-template"></a>Usuwanie pliku Key. snk z szablonu projektu
 W [przewodniku: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), utworzony szablon projektu zawiera plik Key. snk, który jest używany do podpisywania każdego wystąpienia projektu kolumny witryny. Ten plik Key. snk nie jest już potrzebny, ponieważ Kreator generuje teraz nowy plik Key. snk dla każdego projektu. Usuń plik Key. snk z szablonu projektu i Usuń odwołania do tego pliku.

#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>Aby usunąć plik Key. snk z szablonu projektu

1. W **Eksplorator rozwiązań** w węźle **SiteColumnProjectTemplate** Otwórz menu skrótów dla pliku **Key. snk** , a następnie wybierz polecenie **Usuń**.

2. W wyświetlonym oknie dialogowym potwierdzenia wybierz przycisk **OK** .

3. W węźle **SiteColumnProjectTemplate** Otwórz plik SiteColumnProjectTemplate. vstemplate, a następnie usuń z niego następujący element.

    ```xml
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
    ```

4. Zapisz i zamknij plik.

5. W węźle **SiteColumnProjectTemplate** Otwórz plik ProjectTemplate. csproj lub ProjectTemplate. vbproj, a następnie usuń `PropertyGroup` z niego następujący element.

    ```xml
    <PropertyGroup>
      <SignAssembly>true</SignAssembly>
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
    </PropertyGroup>
    ```

6. Usuń następujący `None` element.

    ```xml
    <None Include="key.snk" />
    ```

7. Zapisz i zamknij plik.

## <a name="associating-the-wizard-with-the-project-template"></a>Kojarzenie kreatora z szablonem projektu
 Po zaimplementowaniu kreatora należy skojarzyć kreatora z szablonem projektu **kolumny witryny** . Istnieją trzy procedury, które należy wykonać, aby to zrobić:

1. Podpisz zestaw kreatora silną nazwą.

2. Pobierz token klucza publicznego dla zestawu Kreatora.

3. Dodaj odwołanie do zestawu Kreatora w pliku. vstemplate dla szablonu projektu **kolumny witryny** .

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Aby podpisać zestaw kreatora silną nazwą

1. W **Eksplorator rozwiązań** Otwórz menu skrótów dla projektu **ProjectTemplateWizard** , a następnie wybierz polecenie **Właściwości**.

2. Na karcie **podpisywanie** wybierz pole wyboru **podpisz zestaw** .

3. Z listy **Wybierz plik klucza o silnej nazwie** wybierz opcję **\<New...>** .

4. W oknie dialogowym **Tworzenie klucza silnej nazwy** wprowadź nazwę nowego pliku klucza, wyczyść pole wyboru **Chroń mój klucz przy użyciu hasła** , a następnie wybierz przycisk **OK** .

5. Otwórz menu skrótów dla projektu **ProjectTemplateWizard** , a następnie wybierz polecenie **Kompiluj** , aby utworzyć plik ProjectTemplateWizard.dll.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Aby uzyskać token klucza publicznego dla zestawu Kreatora

1. W **menu Start** wybierz polecenie **Wszystkie programy**, wybierz **Microsoft Visual Studio**, wybierz **Visual Studio Tools**, a następnie wybierz **wiersz polecenia dla deweloperów**.

     Zostanie otwarte okno wiersza polecenia programu Visual Studio.

2. Uruchom następujące polecenie, zastępując *PathToWizardAssembly* z pełną ścieżką do skompilowanego zestawu ProjectTemplateWizard.dll dla projektu ProjectTemplateWizard na komputerze deweloperskim:

    ```cmd
    sn.exe -T PathToWizardAssembly
    ```

     Token klucza publicznego dla zestawu ProjectTemplateWizard.dll jest zapisywana w oknie wiersza polecenia programu Visual Studio.

3. Pozostaw otwarte okno wiersza polecenia programu Visual Studio. Podczas kolejnej procedury będzie potrzebny token klucza publicznego.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Aby dodać odwołanie do zestawu Kreatora w pliku. vstemplate

1. W **Eksplorator rozwiązań** rozwiń węzeł projektu **SiteColumnProjectTemplate** i Otwórz plik SiteColumnProjectTemplate. vstemplate.

2. W prawie na końcu pliku Dodaj następujący `WizardExtension` element między `</TemplateContent>` `</VSTemplate>` tagami i. Zastąp wartość *tokenu* `PublicKeyToken` klucza publicznego, który został uzyskany w poprzedniej procedurze.

    ```xml
    <WizardExtension>
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>
    </WizardExtension>
    ```

     Aby uzyskać więcej informacji na temat `WizardExtension` elementu, zobacz [wizardextension — elementu &#40;szablonów programu Visual Studio&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).

3. Zapisz i zamknij plik.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Dodawanie parametrów wymiennych do pliku Elements.xml w szablonie projektu
 Dodaj kilka wymiennych parametrów do pliku *Elements.xml* w projekcie SiteColumnProjectTemplate. Te parametry są inicjowane w `RunStarted` metodzie `SiteColumnProjectWizard` zdefiniowanej wcześniej w klasie. Gdy użytkownik tworzy projekt kolumny witryny, program Visual Studio automatycznie zastępuje te parametry w pliku *Elements.xml* w nowym projekcie wartościami określonymi w kreatorze.

 Parametr wymienny jest tokenem rozpoczynającym się i kończącym znakiem dolara ($). Oprócz definiowania własnych parametrów do przemieszczenia można używać wbudowanych parametrów, które są zdefiniowane i inicjowane przez system projektu programu SharePoint. Aby uzyskać więcej informacji, zobacz [Parametry wymienne](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Aby dodać do pliku Elements.xml parametry wymienne

1. W projekcie SiteColumnProjectTemplate Zastąp zawartość pliku *Elements.xml* następującym kodem XML.

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

     Nowy kod XML zmienia wartości `Name` atrybutów,, `DisplayName` `Type` i `Group` na parametry niestandardowe wymienne.

2. Zapisz i zamknij plik.

## <a name="add-the-wizard-to-the-vsix-package"></a>Dodawanie kreatora do pakietu VSIX
 Aby wdrożyć kreatora z pakietem VSIX zawierającym szablon projektu kolumny witryny, Dodaj odwołania do projektu kreatora i projektu poleceń programu SharePoint do pliku source. Extension. vsixmanifest w projekcie VSIX.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Aby dodać kreatora do pakietu VSIX

1. W **Eksplorator rozwiązań**, w projekcie **SiteColumnProjectItem** , otwórz menu skrótów dla pliku **source. Extension. vsixmanifest** , a następnie wybierz **Otwórz**.

     Program Visual Studio otwiera plik w edytorze manifestu.

2. Na karcie **zasoby** edytora wybierz przycisk **Nowy** .

     Zostanie otwarte okno dialogowe **Dodaj nowy element zawartości** .

3. Z listy **Typ** wybierz **Microsoft. VisualStudio. Assembly**.

4. Z listy **Źródło** wybierz **projekt w bieżącym rozwiązaniu**.

5. Na liście **projekt** wybierz pozycję **ProjectTemplateWizard**, a następnie wybierz przycisk **OK** .

6. Na karcie **zasoby** edytora wybierz przycisk **Nowy** ponownie.

     Zostanie otwarte okno dialogowe **Dodaj nowy element zawartości** .

7. Na liście **Typ** wprowadź wartość **SharePoint. Commands. v4**.

8. Z listy **Źródło** wybierz **projekt w bieżącym rozwiązaniu**.

9. Na liście **projekt** wybierz projekt **SharePointCommands** , a następnie wybierz przycisk **OK** .

10. Na pasku menu wybierz kompilacja Kompiluj **Build**  >  **rozwiązanie**, a następnie upewnij się, że rozwiązanie nie ma błędów.

## <a name="test-the-wizard"></a>Testowanie Kreatora
 Teraz można przystąpić do testowania kreatora. Najpierw Rozpocznij debugowanie rozwiązania SiteColumnProjectItem w eksperymentalnym wystąpieniu programu Visual Studio. Następnie przetestuj kreatora dla projektu kolumny witryny w eksperymentalnym wystąpieniu programu Visual Studio. Na koniec Skompiluj i Uruchom projekt, aby sprawdzić, czy kolumna lokacja działa zgodnie z oczekiwaniami.

#### <a name="to-start-debugging-the-solution"></a>Aby rozpocząć debugowanie rozwiązania

1. Uruchom ponownie program Visual Studio z poświadczeniami administracyjnymi, a następnie otwórz rozwiązanie SiteColumnProjectItem.

2. W projekcie ProjectTemplateWizard Otwórz plik kodu SiteColumnProjectWizard, a następnie Dodaj punkt przerwania do pierwszego wiersza kodu w `RunStarted` metodzie.

3. Na pasku menu wybierz polecenie **Debuguj**  >  **wyjątki**.

4. Upewnij się, że w oknie dialogowym **wyjątki** zostały wyczyszczone pola wyboru **zgłoszone** i **nieobsługiwane przez użytkownika** dla **wyjątków środowiska uruchomieniowego języka wspólnego** , a następnie wybierz przycisk **OK** .

5. Rozpocznij debugowanie, wybierając klawisz **F5** lub na pasku menu, wybierając **Debuguj**  >  **Rozpocznij debugowanie**.

     Program Visual Studio instaluje rozszerzenie%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 i uruchamia eksperymentalne wystąpienie programu Visual Studio. Testujesz element projektu w tym wystąpieniu programu Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Aby przetestować kreatora w programie Visual Studio

1. W eksperymentalnym wystąpieniu programu Visual Studio na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

2. Rozwiń węzeł **Visual C#** lub węzeł **Visual Basic** (w zależności od języka obsługiwanego przez szablon projektu) rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

3. Na liście szablonów projektu wybierz **kolumnę lokacja**, nazwij projekt **SiteColumnWizardTest**, a następnie wybierz przycisk **OK** .

4. Sprawdź, czy kod w innym wystąpieniu programu Visual Studio jest zatrzymany w punkcie przerwania, który został ustawiony wcześniej w `RunStarted` metodzie.

5. Kontynuuj debugowanie projektu, wybierając klawisz **F5** lub na pasku menu wybierz **Debuguj**  >  **Kontynuuj**.

6. W **Kreatorze dostosowania programu SharePoint** wprowadź adres URL witryny, która ma być używana do debugowania, a następnie wybierz przycisk **dalej** .

7. Na drugiej stronie **Kreatora dostosowania programu SharePoint** wykonaj następujące czynności:

   - Z listy **Typ** wybierz **wartość Boolean**.

   - Na liście **Grupa** wybierz opcję **niestandardowa tak/nie kolumn**.

   - W polu **Nazwa** wprowadź **wartość my/No Column**, a następnie wybierz przycisk **Zakończ** .

     W **Eksplorator rozwiązań** pojawia się nowy projekt zawierający element projektu o nazwie **pole1**, a program Visual Studio otwiera plik *Elements.xml* projektu w edytorze.

8. Sprawdź, czy *Elements.xml* zawiera wartości, które zostały określone w kreatorze.

#### <a name="to-test-the-site-column-in-sharepoint"></a>Aby przetestować kolumnę witryny w programie SharePoint

1. W eksperymentalnym wystąpieniu programu Visual Studio, wybierz klawisz **F5** .

     Kolumna lokacja jest spakowana i wdrożona w witrynie programu SharePoint, która określa właściwość **adres URL witryny** projektu. Przeglądarka sieci Web otworzy się na stronie domyślnej tej witryny.

    > [!NOTE]
    > Jeśli zostanie wyświetlone okno dialogowe **debugowanie skryptu wyłączone** , wybierz przycisk **tak** , aby kontynuować debugowanie projektu.

2. W menu **Akcje witryny** wybierz pozycję **Ustawienia lokacji**.

3. Na stronie Ustawienia lokacji w obszarze **Galerie** wybierz łącze **kolumny witryny** .

4. Na liście kolumn lokacji Sprawdź, czy grupa **niestandardowa tak/nie** zawiera kolumny o nazwie **My No/No Column**, a następnie zamknij przeglądarkę sieci Web.

## <a name="clean-up-the-development-computer"></a>Czyszczenie komputera deweloperskiego
 Po zakończeniu testowania elementu projektu, Usuń szablon projektu z eksperymentalnego wystąpienia programu Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Aby wyczyścić komputer deweloperski

1. W eksperymentalnym wystąpieniu programu Visual Studio na pasku menu wybierz kolejno opcje **Narzędzia**  >  **rozszerzenia i aktualizacje**.

     Zostanie otwarte okno dialogowe **rozszerzenia i aktualizacje** .

2. Na liście rozszerzeń wybierz **kolumnę lokacja**, a następnie wybierz przycisk **Odinstaluj** .

3. W wyświetlonym oknie dialogowym wybierz przycisk **tak** , aby potwierdzić, że chcesz odinstalować rozszerzenie, a następnie wybierz przycisk **Uruchom ponownie teraz** , aby ukończyć dezinstalację.

4. Zamknij zarówno eksperymentalne wystąpienie programu Visual Studio, jak i wystąpienie, w którym jest otwarte rozwiązanie CustomActionProjectItem.

     Aby uzyskać informacje o sposobach wdrażania [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzeń, zobacz [wysyłanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

## <a name="see-also"></a>Zobacz też
- [Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Porady: korzystanie z kreatora z szablonami projektu](../extensibility/how-to-use-wizards-with-project-templates.md)
