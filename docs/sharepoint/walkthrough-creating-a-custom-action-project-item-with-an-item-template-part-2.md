---
title: Utwórz niestandardowy element projektu akcji z szablonem elementu, część 2
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
ms.openlocfilehash: a873d00e1befc9126f4fe89b05a66a8331853ac2
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984977"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>Przewodnik: Tworzenie niestandardowego elementu projektu akcji z szablonem elementu część 2
  Po zdefiniowaniu niestandardowego typu elementu projektu programu SharePoint i skojarzeniu go z szablonem elementu w programie Visual Studio, można również udostępnić Kreator szablonu. Za pomocą kreatora można zbierać informacje od użytkowników, gdy używają one szablonu, aby dodać nowe wystąpienie elementu projektu do projektu. Zbierane informacje mogą służyć do inicjowania elementu projektu.

 W tym instruktażu dodasz kreatora do elementu projektu akcji niestandardowej, który jest prezentowany w [przewodniku: Tworzenie niestandardowego elementu projektu akcji z szablonem elementu część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Gdy użytkownik dodaje niestandardowy element projektu akcji do projektu programu SharePoint, Kreator zbiera informacje o akcji niestandardowej (na przykład o lokalizacji i adresie URL, do którego należy przejść po wybraniu przez użytkownika końcowego) i dodaje te informacje do pliku Items *. XML* w nowy element projektu.

 W tym instruktażu przedstawiono następujące zadania:

- Tworzenie Kreatora dla niestandardowego typu elementu projektu programu SharePoint, który jest skojarzony z szablonem elementu.

- Definiowanie niestandardowego interfejsu użytkownika Kreatora podobnego do wbudowanych kreatorów elementów projektu programu SharePoint w programie Visual Studio.

- Użycie parametrów wymiennych w celu zainicjowania plików projektu programu SharePoint za pomocą danych zebranych w kreatorze.

- Debugowanie i testowanie Kreatora.

> [!NOTE]
> Możesz pobrać przykład z witryny [GitHub](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) , który pokazuje, jak utworzyć niestandardowe działania dla przepływu pracy.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby wykonać ten Instruktaż, należy najpierw utworzyć rozwiązanie CustomActionProjectItem, wykonując wskazówki [: Tworzenie niestandardowego elementu projektu akcji z szablonem elementu część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 Aby ukończyć ten przewodnik, potrzebne są również następujące składniki na komputerze deweloperskim:

- Obsługiwane wersje systemu Windows, SharePoint i Visual Studio.

- Zestaw SDK programu Visual Studio. W tym instruktażu zostanie użyty szablon **projektu VSIX** w zestawie SDK, aby utworzyć pakiet VSIX do wdrożenia elementu projektu. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzającą narzędzia programu SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Znajomość następujących pojęć jest pomocna, ale nie jest wymagana, aby ukończyć Przewodnik:

- Kreatorzy szablonów projektów i elementów w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [jak: korzystanie z kreatorów z szablonami projektów](../extensibility/how-to-use-wizards-with-project-templates.md) i interfejsem <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.

- Akcje niestandardowe w programie SharePoint. Aby uzyskać więcej informacji, zobacz [Akcja niestandardowa](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

## <a name="create-the-wizard-project"></a>Utwórz projekt Kreatora
 Aby ukończyć ten Instruktaż, należy dodać projekt do rozwiązania CustomActionProjectItem, które zostało utworzone w [przewodniku: Tworzenie niestandardowego elementu projektu akcji z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Zostanie wdrożony interfejs <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> i zdefiniujesz interfejs użytkownika kreatora w tym projekcie.

#### <a name="to-create-the-wizard-project"></a>Aby utworzyć projekt Kreatora

1. W programie Visual Studio Otwórz rozwiązanie CustomActionProjectItem

2. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła rozwiązanie, wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

3. W oknie dialogowym **Nowy projekt** rozwiń węzły **wizualizacji C#**  lub **Visual Basic** , a następnie wybierz węzeł **systemu Windows** .

4. W górnej części okna dialogowego **Nowy projekt** upewnij się, że na liście wersji .NET Framework wybrano **.NET Framework 4,5** .

5. Wybierz szablon projektu **Biblioteka formantów użytkownika WPF** , nazwij projekt **ItemTemplateWizard**, a następnie wybierz przycisk **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje projekt **ItemTemplateWizard** do rozwiązania.

6. Usuń element UserControl1 z projektu.

## <a name="configure-the-wizard-project"></a>Konfigurowanie projektu kreatora
 Przed utworzeniem kreatora należy dodać do projektu okno Windows Presentation Foundation (WPF), plik kodu i odwołania do zestawu.

#### <a name="to-configure-the-wizard-project"></a>Aby skonfigurować projekt Kreatora

1. W **Eksplorator rozwiązań**Otwórz menu skrótów z węzła projektu **ItemTemplateWizard** , a następnie wybierz polecenie **Właściwości**.

2. W **projektancie projektu**upewnij się, że struktura docelowa jest ustawiona na .NET Framework 4,5.

     W przypadku C# projektów wizualnych można ustawić tę wartość na karcie **aplikacja** . W przypadku projektów Visual Basic można ustawić tę wartość na karcie **Kompilowanie** . Aby uzyskać więcej informacji, zobacz [How to: Target of a wersja .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

3. W projekcie **ItemTemplateWizard** Dodaj element **window (WPF)** do projektu, a następnie nadaj mu nazwę Item **WizardWindow**.

4. Dodaj dwa pliki kodu o nazwach CustomActionWizard i ciągi.

5. Otwórz menu skrótów dla projektu **ItemTemplateWizard** , a następnie wybierz **Dodaj odwołanie**.

6. W oknie dialogowym **Menedżer odwołań — ItemTemplateWizard** w węźle **zestawy** wybierz węzeł **rozszerzenia** .

7. Zaznacz pola wyboru obok następujących zestawów, a następnie wybierz przycisk **OK** :

    - EnvDTE

    - Microsoft. VisualStudio. Shell. 11.0

    - Microsoft. VisualStudio. TemplateWizardInterface

8. W **Eksplorator rozwiązań**, w folderze **References** dla projektu ItemTemplateWizard, wybierz odwołanie **EnvDTE** .

9. W oknie **Właściwości** Zmień wartość właściwości **Osadź typy** współdziałania na **wartość false**.

## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>Zdefiniuj domyślne parametry lokalizacji i identyfikatora dla akcji niestandardowych
 Każda akcja niestandardowa ma lokalizację i identyfikator, który jest określony w `GroupID` i `Location` atrybutów elementu `CustomAction` w pliku. *XML* . W tym kroku zdefiniujesz kilka prawidłowych ciągów dla tych atrybutów w projekcie ItemTemplateWizard. Po zakończeniu tego instruktażu te ciągi są zapisywane w pliku Items *. XML* w niestandardowym elemencie projektu akcji, gdy użytkownicy określą lokalizację i identyfikator w kreatorze.

 Dla uproszczenia ten przykład obsługuje tylko podzestaw dostępnych domyślnych lokalizacji i identyfikatorów. Aby uzyskać pełną listę, zobacz [domyślne lokalizacje i identyfikatory akcji niestandardowych](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14)).

#### <a name="to-define-the-default-location-and-id-strings"></a>Aby zdefiniować domyślne parametry lokalizacji i identyfikatora

1. Otwórz.

2. W projekcie **ItemTemplateWizard** Zastąp kod w pliku z kodem ciągów poniższym kodem.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]

## <a name="create-the-wizard-ui"></a>Tworzenie interfejsu użytkownika Kreatora
 Dodaj XAML, aby zdefiniować interfejs użytkownika kreatora, a następnie Dodaj kod, aby powiązać niektóre kontrolki w Kreatorze z ciągami identyfikatorów. Kreator, który utworzysz, przypomina kreatora wbudowanego dla projektów programu SharePoint w programie Visual Studio.

#### <a name="to-create-the-wizard-ui"></a>Aby utworzyć interfejs użytkownika Kreatora

1. W projekcie **ItemTemplateWizard** Otwórz menu skrótów dla pliku **WizardWindow. XAML** , a następnie wybierz **Otwórz** , aby otworzyć okno w projektancie.

2. W widoku XAML zastąp bieżący kod XAML następującym XAML. KOD XAML definiuje interfejs użytkownika, który zawiera nagłówek, kontrolki służące do określania zachowania akcji niestandardowej i przycisków nawigacji u dołu okna.

    > [!NOTE]
    > Po dodaniu tego kodu projekt będzie zawierał błędy kompilacji. Te błędy zostaną odrzucone po dodaniu kodu w dalszych krokach.

     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]

    > [!NOTE]
    > Okno, które jest tworzone w tym języku XAML, pochodzi od klasy bazowej <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>. Po dodaniu niestandardowego okna dialogowego WPF do programu Visual Studio zalecamy, aby można było utworzyć okno dialogowe z tej klasy, aby mieć spójne style z innymi oknach dialogowych w programie Visual Studio i uniknąć problemów, które mogłyby wystąpić w innych oknach dialogowych modalnych. Aby uzyskać więcej informacji, zobacz [Tworzenie modalnych okien dialogowych i zarządzanie nimi](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).

3. Jeśli tworzysz projekt Visual Basic, Usuń przestrzeń nazw `ItemTemplateWizard` z nazwy klasy `WizardWindow` w atrybucie `x:Class` elementu `Window`. Ten element znajduje się w pierwszym wierszu XAML. Gdy skończysz, pierwszy wiersz powinien wyglądać podobnie do następującego kodu:

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. W pliku związanym z kodem dla pliku WizardWindow. XAML zastąp bieżący kod następującym kodem.

     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]

## <a name="implement-the-wizard"></a>Zaimplementuj Kreatora
 Zdefiniuj funkcje Kreatora, implementując interfejs <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.

#### <a name="to-implement-the-wizard"></a>Aby zaimplementować Kreatora

1. W projekcie **ItemTemplateWizard** Otwórz plik kodu **CustomActionWizard** , a następnie zastąp bieżący kod w tym pliku następującym kodem:

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]

## <a name="checkpoint"></a>Elementu
 W tym momencie w przewodniku cały kod kreatora jest teraz w projekcie. Skompiluj projekt, aby upewnić się, że kompiluje się bez błędów.

#### <a name="to-build-your-project"></a>Aby skompilować projekt

1. Na pasku menu wybierz **kompiluj**  > **Kompiluj rozwiązanie**.

## <a name="associate-the-wizard-with-the-item-template"></a>Skojarz kreatora z szablonem elementu
 Po zaimplementowaniu kreatora należy skojarzyć go z szablonem **niestandardowego elementu akcji** , wykonując trzy podstawowe kroki:

1. Podpisz zestaw kreatora silną nazwą.

2. Pobierz token klucza publicznego dla zestawu Kreatora.

3. Dodaj odwołanie do zestawu Kreatora w pliku. vstemplate dla szablonu **niestandardowego elementu akcji** .

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Aby podpisać zestaw kreatora silną nazwą

1. W **Eksplorator rozwiązań**Otwórz menu skrótów z węzła projektu **ItemTemplateWizard** , a następnie wybierz polecenie **Właściwości**.

2. Na karcie **podpisywanie** wybierz pole wyboru **podpisz zestaw** .

3. Z listy **Wybierz plik klucza o silnej nazwie** wybierz pozycję **\<nowy... >** .

4. W oknie dialogowym **Tworzenie klucza silnej nazwy** wprowadź nazwę, wyczyść pole wyboru **Chroń mój klucz z hasłem** , a następnie wybierz przycisk **OK** .

5. Na pasku menu wybierz **kompiluj**  > **Kompiluj rozwiązanie**.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Aby uzyskać token klucza publicznego dla zestawu Kreatora

1. W oknie wiersza polecenia programu Visual Studio Uruchom następujące polecenie, zastępując *PathToWizardAssembly* z pełną ścieżką do skompilowanego zestawu ItemTemplateWizard. dll dla projektu ItemTemplateWizard na komputerze deweloperskim.

    ```xml
    sn.exe -T PathToWizardAssembly
    ```

     Token klucza publicznego dla zestawu *ItemTemplateWizard. dll* jest zapisywana w oknie wiersza polecenia programu Visual Studio.

2. Pozostaw otwarte okno wiersza polecenia programu Visual Studio. Aby ukończyć następną procedurę, potrzebny będzie token klucza publicznego.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Aby dodać odwołanie do zestawu Kreatora w pliku. vstemplate

1. W **Eksplorator rozwiązań**rozwiń węzeł projektu **ItemTemplate** , a następnie otwórz plik *ItemTemplate. vstemplate* .

2. Obok końca pliku Dodaj następujący element `WizardExtension` między tagami `</TemplateContent>` i `</VSTemplate>`. Zastąp wartość *YourToken* atrybutu `PublicKeyToken` kluczem publicznym, który został uzyskany w poprzedniej procedurze.

    ```xml
    <WizardExtension>
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>
    </WizardExtension>
    ```

     Aby uzyskać więcej informacji na temat `WizardExtension` elementu, zobacz [Szablony &#40;&#41;programu Visual Studio WizardExtension —](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).

3. Zapisz i zamknij plik.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Dodawanie parametrów wymiennych do pliku Items *. XML* w szablonie elementu
 Dodaj kilka wymiennych parametrów do pliku repliks *. XML* w projekcie ItemTemplate. Te parametry są inicjowane w metodzie `PopulateReplacementDictionary` w zdefiniowanej wcześniej klasie `CustomActionWizard`. Gdy użytkownik dodaje niestandardowy element projektu akcji do projektu, program Visual Studio automatycznie zastępuje te parametry w pliku Items *. XML* w nowym elemencie projektu wartościami określonymi w kreatorze.

 Parametr wymienny jest tokenem rozpoczynającym się i kończącym znakiem dolara ($). Oprócz definiowania własnych parametrów do przemieszczenia można używać wbudowanych parametrów, które system projektu SharePoint definiuje i inicjuje. Aby uzyskać więcej informacji, zobacz [Parametry wymienne](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Aby dodać parametry wymienne do pliku *. XML*

1. W projekcie ItemTemplate Zastąp zawartość pliku repliks *. XML* następującym kodem XML.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">
      <CustomAction Id="$IdValue$"
                    GroupId="$GroupIdValue$"
                    Location="$LocationValue$"
                    Sequence="1000"
                    Title="$TitleValue$"
                    Description="$DescriptionValue$" >
        <UrlAction Url="$UrlValue$"/>
      </CustomAction>
    </Elements>
    ```

     Nowy kod XML zmienia wartości atrybutów `Id`, `GroupId`, `Location`, `Description`i `Url` do wymiennych parametrów.

2. Zapisz i zamknij plik.

## <a name="add-the-wizard-to-the-vsix-package"></a>Dodawanie kreatora do pakietu VSIX
 W pliku source. Extension. vsixmanifest w projekcie VSIX Dodaj odwołanie do projektu kreatora, tak aby został on wdrożony z pakietem VSIX zawierającym element projektu.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Aby dodać kreatora do pakietu VSIX

1. W **Eksplorator rozwiązań**Otwórz menu skrótów z pliku **source. Extension. vsixmanifest** w projekcie CustomActionProjectItem, a następnie wybierz **Otwórz** , aby otworzyć plik w edytorze manifestu.

2. W edytorze manifestu wybierz kartę **zasoby** , a następnie wybierz przycisk **Nowy** .

     Pojawi się okno dialogowe **Dodaj nowy element zawartości** .

3. Z listy **Typ** wybierz **Microsoft. VisualStudio. Assembly**.

4. Z listy **Źródło** wybierz **projekt w bieżącym rozwiązaniu**.

5. Na liście **projekt** wybierz pozycję **ItemTemplateWizard**, a następnie wybierz przycisk **OK** .

6. Na pasku menu wybierz **kompiluj** > **Kompiluj rozwiązanie**, a następnie upewnij się, że rozwiązanie kompiluje się bez błędów.

## <a name="test-the-wizard"></a>Testowanie Kreatora
 Teraz można przystąpić do testowania kreatora. Najpierw Rozpocznij debugowanie rozwiązania CustomActionProjectItem w eksperymentalnym wystąpieniu programu Visual Studio. Następnie przetestuj kreatora dla elementu projektu akcji niestandardowej w projekcie programu SharePoint w eksperymentalnym wystąpieniu programu Visual Studio. Na koniec Skompiluj i Uruchom projekt programu SharePoint, aby sprawdzić, czy działanie niestandardowe działa zgodnie z oczekiwaniami.

#### <a name="to-start-to-debug-the-solution"></a>Aby rozpocząć debugowanie rozwiązania

1. Uruchom ponownie program Visual Studio z poświadczeniami administracyjnymi, a następnie otwórz rozwiązanie CustomActionProjectItem.

2. W projekcie ItemTemplateWizard Otwórz plik kodu CustomActionWizard, a następnie Dodaj punkt przerwania do pierwszego wiersza kodu w metodzie `RunStarted`.

3. Na pasku menu wybierz kolejno opcje **debuguj** > **wyjątki**.

4. Upewnij się, że w oknie dialogowym **wyjątki** zostały wyczyszczone pola wyboru **zgłoszone** i **nieobsługiwane przez użytkownika** dla **wyjątków środowiska uruchomieniowego języka wspólnego** , a następnie wybierz przycisk **OK** .

5. Rozpocznij debugowanie, wybierając klawisz **F5** lub na pasku menu wybierz polecenie **Debuguj** > **Rozpocznij debugowanie**.

     Program Visual Studio instaluje rozszerzenie do%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom akcji projektu Item\1.0 i uruchamia eksperymentalne wystąpienie programu Visual Studio. Testujesz element projektu w tym wystąpieniu programu Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Aby przetestować kreatora w programie Visual Studio

1. W eksperymentalnym wystąpieniu programu Visual Studio na pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

2. Rozwiń węzeł **wizualizacji C#**  lub **Visual Basic** (w zależności od języka obsługiwanego przez szablon elementu), rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

3. Na liście szablonów projektu wybierz **projekt SharePoint 2010**, nazwij projekt **CustomActionWizardTest**, a następnie wybierz przycisk **OK** .

4. W **Kreatorze dostosowania programu SharePoint**wprowadź adres URL witryny, która ma być używana do debugowania, a następnie wybierz przycisk **Zakończ** .

5. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła projektu, wybierz **Dodaj**, a następnie wybierz **nowy element**.

6. W oknie dialogowym **Dodaj nowy element — CustomItemWizardTest** rozwiń węzeł **SharePoint** , a następnie rozwiń węzeł **2010** .

7. Na liście elementów projektu wybierz element **Akcja niestandardowa** , a następnie wybierz przycisk **Dodaj** .

8. Sprawdź, czy kod w innym wystąpieniu programu Visual Studio jest zatrzymany w punkcie przerwania, który został ustawiony wcześniej w metodzie `RunStarted`.

9. Kontynuuj debugowanie projektu, wybierając klawisz **F5** lub na pasku menu wybierz polecenie **Debuguj** > **Kontynuuj**.

     Zostanie wyświetlony Kreator dostosowania programu SharePoint.

10. W obszarze **Lokalizacja**wybierz przycisk opcji **Edytuj listę** .

11. Na liście **Identyfikator grupy** wybierz pozycję **komunikacja**.

12. W polu **tytuł** wprowadź **Centrum deweloperów programu SharePoint**.

13. W polu **Opis** wprowadź polecenie **otwiera witrynę sieci Web Centrum deweloperów programu SharePoint**.

14. W polu **adres URL** wprowadź **https://docs.microsoft.com/sharepoint/dev/** , a następnie wybierz przycisk **Zakończ** .

     Program Visual Studio dodaje element o nazwie **CustomAction1** do projektu i otwiera plik Items *. XML* w edytorze. Sprawdź, czy *element. XML* zawiera wartości, które zostały określone w kreatorze.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Aby przetestować akcję niestandardową w programie SharePoint

1. W eksperymentalnym wystąpieniu programu Visual Studio, wybierz klawisz **F5** lub na pasku menu wybierz **Debuguj** > **Rozpocznij debugowanie**.

     Akcja niestandardowa zostanie spakowana i wdrożona w witrynie programu SharePoint określonej przez właściwość **adres URL witryny** projektu, a w przeglądarce sieci Web zostanie otwarta strona domyślna tej witryny.

    > [!NOTE]
    > Jeśli zostanie wyświetlone okno dialogowe **debugowanie skryptu wyłączone** , wybierz przycisk **tak** .

2. W obszarze listy witryny programu SharePoint wybierz łącze **zadania** .

     Zostanie wyświetlona strona **zadania — wszystkie zadania** .

3. Na karcie **Narzędzia listy** wstążki wybierz kartę **Lista** , a następnie w grupie **Ustawienia** wybierz pozycję **Ustawienia listy**.

     Zostanie wyświetlona strona **Ustawienia listy** .

4. W obszarze nagłówka **komunikacja** w górnej części strony wybierz łącze **Centrum deweloperów programu SharePoint** , sprawdź, czy przeglądarka otwiera witrynę sieci Web https://docs.microsoft.com/sharepoint/dev/, a następnie zamknij przeglądarkę.

## <a name="cleaning-up-the-development-computer"></a>Czyszczenie komputera deweloperskiego
 Po zakończeniu testowania elementu projektu, Usuń szablon elementu projektu z eksperymentalnego wystąpienia programu Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Aby wyczyścić komputer deweloperski

1. W eksperymentalnym wystąpieniu programu Visual Studio na pasku menu wybierz kolejno opcje **narzędzia** > **rozszerzenia i aktualizacje**.

     Zostanie otwarte okno dialogowe **rozszerzenia i aktualizacje** .

2. Na liście rozszerzeń wybierz rozszerzenie **elementu projektu akcji niestandardowej** , a następnie wybierz przycisk **Odinstaluj** .

3. W wyświetlonym oknie dialogowym wybierz przycisk **tak** , aby potwierdzić, że chcesz odinstalować rozszerzenie, a następnie wybierz przycisk **Uruchom ponownie teraz** , aby ukończyć dezinstalację.

4. Zamknij oba wystąpienia programu Visual Studio (wystąpienie eksperymentalne i wystąpienie programu Visual Studio, w którym jest otwarte rozwiązanie CustomActionProjectItem).

## <a name="see-also"></a>Zobacz także
- [Przewodnik: Tworzenie niestandardowego elementu projektu akcji z szablonem elementu część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Odwołanie do schematu szablonu Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [Instrukcje: korzystanie z kreatorów z szablonami projektu](../extensibility/how-to-use-wizards-with-project-templates.md)
- [Domyślne lokalizacje i identyfikatory akcji niestandardowych](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14))
