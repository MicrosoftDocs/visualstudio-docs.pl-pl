---
title: 'Przewodnik: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu — część 2 | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4305fd980252515f126df2c1b3848c0676cd2079
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913939"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>Przewodnik: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu — część 2
  Po zdefiniowaniu niestandardowy typ elementu projektu programu SharePoint i skojarzyć go z szablonem elementu w programie Visual Studio, można również podać Kreatora szablonu. Kreator służy do zbierania informacji od użytkowników, używając szablonu można dodać nowe wystąpienie elementu projektu do projektu. Informacje zbierane, może służyć do zainicjowania elementu projektu.  
  
 W tym przewodniku kreatora zostanie dodany do elementu projektu Akcja niestandardowa, która została przedstawiona w [instruktażu: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Gdy użytkownik doda niestandardowej akcji elementu projektu do projektu programu SharePoint, Kreator zbiera informacje o akcji niestandardowej (na przykład lokalizacji i adres URL do nawigacji po użytkownik końcowy ją wybierze) i dodaje te informacje do *Elements.xml* plików do nowego elementu projektu.  
  
 W tym instruktażu pokazano następujące zagadnienia:  
  
-   Tworzenie kreatora dla programu SharePoint projektu elementu Typ niestandardowy, który jest skojarzony z szablonem elementu.  
  
-   Definiowanie niestandardowego kreatora interfejsu użytkownika, który przypomina wbudowanych kreatorów dla elementów projektu programu SharePoint w programie Visual Studio.  
  
-   Używanie wymiennych parametrów można zainicjować plików projektu programu SharePoint z danymi, które można zbierać w kreatorze.  
  
-   Debugowanie i testowanie kreatora.  
  
> [!NOTE]  
>  Możesz pobrać próbkę z [Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) pokazujący sposób tworzenia działań niestandardowych do przepływu pracy.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby wykonać ten Instruktaż, należy najpierw utworzyć rozwiązanie CustomActionProjectItem, wykonując [instruktażu: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 Wymagane są również następujące składniki na komputerze deweloperskim w celu przeprowadzenia tego instruktażu:  
  
- Obsługiwane wersje systemu Windows, SharePoint i Visual Studio.
  
- Program Visual Studio SDK. W tym instruktażu wykorzystano **projekt VSIX** szablonu w zestawie SDK, aby utworzyć pakiet VSIX do wdrożenia elementu projektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie narzędzi SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Znajomość następujących pojęć jest przydatna, ale nie jest to wymagane, aby ukończyć Instruktaż:  
  
- Kreatorzy szablonów projektów i elementów w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [jak: Korzystanie z kreatorów z szablonami projektu](../extensibility/how-to-use-wizards-with-project-templates.md) i <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsu.  
  
- Akcje niestandardowe w programie SharePoint. Aby uzyskać więcej informacji, zobacz [Akcja niestandardowa](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
## <a name="create-the-wizard-project"></a>Utwórz projekt Kreatora
 Do przeprowadzenia tego instruktażu, należy dodać projekt do rozwiązania CustomActionProjectItem, który został utworzony w [instruktażu: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Zostaną zaimplementowane <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejs i zdefiniuj Kreatora interfejsu użytkownika w tym projekcie.  
  
#### <a name="to-create-the-wizard-project"></a>Aby utworzyć projekt Kreatora  
  
1.  W programie Visual Studio Otwórz rozwiązanie CustomActionProjectItem  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla węzła rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz **nowy projekt**.  
  
3.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** węzłów, a następnie wybierz **Windows** węzła.  
  
4.  W górnej części **nowy projekt** okna dialogowego pole, upewnij się, że **.NET Framework 4.5** jest wybierany w listę wersji programu .NET Framework.  
  
5.  Wybierz **Biblioteka kontrolek użytkownika WPF** projektu szablonu, nadaj projektowi nazwę **ItemTemplateWizard**, a następnie wybierz **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **ItemTemplateWizard** projektu do rozwiązania.  
  
6.  Usuń element UserControl1 z projektu.  
  
## <a name="configure-the-wizard-project"></a>Konfigurowanie projektu Kreatora
 Przed utworzeniem kreatora, należy dodać okno programu Windows Presentation Foundation (WPF), plik kodu i odwołania do zestawów do projektu.  
  
#### <a name="to-configure-the-wizard-project"></a>Aby skonfigurować projekt Kreatora  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów z **ItemTemplateWizard** węzła projektu, a następnie wybierz **właściwości**.  
  
2.  W **projektanta projektu**, upewnij się, że platforma docelowa jest ustawiona na .NET Framework 4.5.  
  
     Projekty Visual C#, tę wartość można ustawić na **aplikacji** kartę. Projekty języka Visual Basic tę wartość można ustawić na **skompilować** kartę. Aby uzyskać więcej informacji, zobacz [jak: Docelowa wersja systemu .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
3.  W **ItemTemplateWizard** projektu, Dodaj **okno (WPF)** elementu do projektu, a następnie nadaj nazwę elementu **WizardWindow**.  
  
4.  Dodaj dwa pliki kodu, które są nazwane CustomActionWizard i ciągów.  
  
5.  Otwórz menu skrótów dla **ItemTemplateWizard** projektu, a następnie wybierz **Dodaj odwołanie**.  
  
6.  W **Menadżer odwołań - ItemTemplateWizard** dialogowego **zestawy** węzła, wybierz **rozszerzenia** węzła.  
  
7.  Zaznacz pole wyboru obok następujących zestawów, a następnie wybierz **OK** przycisku:  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  W **Eksploratora rozwiązań**w **odwołania** wybierz folder dla projektu ItemTemplateWizard **EnvDTE** odwołania.  
  
9. W **właściwości** okna, zmień wartość właściwości **Osadź typy współdziałania** właściwości **False**.  
  
## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>Zdefiniuj lokalizację domyślną i ciągi identyfikatorów akcji niestandardowych
 Co akcja niestandardowa ma położenie i identyfikator, który jest określony w `GroupID` i `Location` atrybuty `CustomAction` element *Elements.xml* pliku. W tym kroku zdefiniujesz niektóre prawidłowe ciągi tych atrybutów w projekcie ItemTemplateWizard. Po ukończeniu tego przewodnika, te ciągi są zapisywane w *Elements.xml* pliku w elemencie projektu Akcja niestandardowa, gdy użytkownicy określić lokalizację i identyfikator w kreatorze.  
  
 Dla uproszczenia w tym przykładzie obsługuje tylko domyślne dostępne lokalizacje i identyfikatorów. Aby uzyskać pełną listę, zobacz [domyślnej lokalizacji akcji niestandardowych i identyfikatory](http://go.microsoft.com/fwlink/?LinkId=181964).  
  
#### <a name="to-define-the-default-location-and-id-strings"></a>Aby określić domyślną lokalizację i ciągi identyfikatorów
  
1.  Otwórz.  
  
2.  W **ItemTemplateWizard** projektu, Zastąp kod w pliku kodu ciągi z następującym kodem.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]  
  
## <a name="create-the-wizard-ui"></a>Kreator interfejsu użytkownika
 Dodaj XAML zdefiniować interfejsu użytkownika kreatora, a następnie dodać kod niektóre formanty w kreatorze można powiązać ciągi identyfikatorów. Kreator, którą tworzysz przypomina wbudowanego kreatora dla projektów programu SharePoint w programie Visual Studio.  
  
#### <a name="to-create-the-wizard-ui"></a>Aby utworzyć Kreator interfejsu użytkownika
  
1.  W **ItemTemplateWizard** projektu, otwórz menu skrótów dla **WizardWindow.xaml** , a następnie wybierz **Otwórz** aby otworzyć okno w projektancie.  
  
2.  W widoku XAML Zastąp bieżący XAML następujące XAML. XAML definiuje interfejs użytkownika, który zawiera nagłówek, kontrolki do określania zachowania akcję niestandardową i przycisków nawigacji w dolnej części okna.  
  
    > [!NOTE]  
    >  Projekt będzie miał pewne błędy kompilacji, po dodaniu tego kodu. Te błędy znikną po dodaniu kodu w dalszych krokach.  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  Okno, który jest tworzony w tym XAML jest tworzony na podstawie <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> klasy bazowej. Po dodaniu niestandardowe okno dialogowe WPF w programie Visual Studio, firma Microsoft zaleca, pochodzi z okna dialogowego z tej klasy mają spójnego stylów z innych oknach dialogowych w programie Visual Studio i uniknąć problemów, które mogłyby wystąpić z modalnych okien dialogowych. Aby uzyskać więcej informacji, zobacz [tworzenie i zarządzanie modalne okna dialogowe](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).  
  
3.  Jeśli tworzysz projekt języka Visual Basic, Usuń `ItemTemplateWizard` przestrzeni nazw z `WizardWindow` nazwy klasy w `x:Class` atrybutu `Window` elementu. Ten element jest w pierwszym wierszu XAML. Gdy wszystko będzie gotowe, pierwszy wiersz powinien przypominać następujący kod:  
  
    ```xml  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  W pliku związanym z kodem dla pliku WizardWindow.xaml Zastąp bieżący kod następującym kodem.  
  
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]  
  
## <a name="implement-the-wizard"></a>Implementowanie Kreatora
 Zdefiniuj funkcji w Kreatorze poprzez implementację <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsu.  
  
#### <a name="to-implement-the-wizard"></a>Aby zaimplementować Kreatora  
  
1.  W **ItemTemplateWizard** otwarty projekt **CustomActionWizard** plik kodu, a następnie zastąp bieżący kod w tym pliku następującym kodem:  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie w instruktażu, cały kod dla kreatora znajduje się teraz w projekcie. Skompiluj projekt, aby upewnić się, że kompiluje bez błędów.  
  
#### <a name="to-build-your-project"></a>Do kompilowania projektu  
  
1.  Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.  
  
## <a name="associate-the-wizard-with-the-item-template"></a>Kojarzenie kreatora z szablonu elementu
 Teraz, że udało Ci się wdrożyć kreatora, musisz skojarzyć go z **Akcja niestandardowa** szablon elementu, wykonując trzy podstawowe kroki:  
  
1.  Podpisz zestaw kreatora, za pomocą silnej nazwy.  
  
2.  Pobierz token klucza publicznego dla zestawu kreatora.  
  
3.  Dodaj odwołanie do zestawu kreatora w pliku .vstemplate **Akcja niestandardowa** szablon elementu.  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Aby zarejestrować Kreatora zestawu o silnej nazwie  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów z **ItemTemplateWizard** węzła projektu, a następnie wybierz **właściwości**.  
  
2.  Na **podpisywanie** zaznacz **Podpisz zestaw** pole wyboru.  
  
3.  W **wybierz plik klucza o silnej nazwie** wybierz  **\<nowy... >**.  
  
4.  W **Utwórz klucz silnej nazwy** okna dialogowego wprowadź nazwę, usuń zaznaczenie **Chroń mój plik klucza przy użyciu hasła** pole wyboru, a następnie wybierz **OK** przycisku.  
  
5.  Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Aby uzyskać klucz publiczny token dla zestawu Kreatora  
  
1.  W oknie wiersza polecenia programu Visual Studio, uruchom następujące polecenie, zastępując *PathToWizardAssembly* mającym pełną ścieżkę do zestawu ItemTemplateWizard.dll utworzone dla projektu ItemTemplateWizard na programowanie komputer.  
  
    ```xml  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Token klucza publicznego dla *ItemTemplateWizard.dll* zestawu są zapisywane do okna wiersza polecenia programu Visual Studio.  
  
2.  Nie zamykaj okna wiersza polecenia programu Visual Studio. Należy token klucza publicznego do wykonania w następnej procedurze.  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Aby dodać odwołanie do zestawu kreatora w pliku .vstemplate  
  
1.  W **Eksploratora rozwiązań**, rozwiń węzeł **właściwości ItemTemplate** węzła projektu, a następnie otwórz *ItemTemplate.vstemplate* pliku.  
  
2.  Pod koniec pliku, Dodaj następujący kod `WizardExtension` element między `</TemplateContent>` i `</VSTemplate>` tagów. Zastąp *YourToken* wartość `PublicKeyToken` atrybut o token klucza publicznego, uzyskaną w poprzedniej procedurze.  
  
    ```xml  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Aby uzyskać więcej informacji na temat `WizardExtension` elementu, zobacz [wizardextension — Element &#40;szablony programu Visual Studio&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  Zapisz i zamknij plik.  
  
## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Parametry wymienne, aby dodać *Elements.xml* pliku w szablonie elementu
 Dodaj kilku wymiennych parametrów w celu *Elements.xml* pliku w projekcie właściwości ItemTemplate. Te parametry są inicjowane w `PopulateReplacementDictionary` method in Class metoda `CustomActionWizard` klasy określonej wcześniej. Gdy użytkownik doda Akcja niestandardowa elementu projektu do projektu, Visual Studio automatycznie zastępuje tych parametrów w *Elements.xml* plików do nowego elementu projektu z wartościami, które są określone w kreatorze.  
  
 Parametr wymienny jest token, który zaczyna się i kończy się znakiem dolara ($). Oprócz definiowania wymienne parametry, można użyć wbudowanych parametry, które definiuje systemu projektu programu SharePoint i inicjuje. Aby uzyskać więcej informacji, zobacz [parametrów zastępowalnych](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Aby dodać parametry wymienne *Elements.xml* pliku
  
1.  W projekcie właściwości ItemTemplate Zastąp zawartość *Elements.xml* pliku następujący kod XML.  
  
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
  
     Nowy plik XML powoduje zmianę wartości `Id`, `GroupId`, `Location`, `Description`, i `Url` atrybuty zastępowalnych parametrów.  
  
2.  Zapisz i zamknij plik.  
  
## <a name="add-the-wizard-to-the-vsix-package"></a>Kreator dodawania do pakietu VSIX
 W pliku source.extension.vsixmanifest w projekcie VSIX Dodaj odwołanie do Kreatora projektu, dzięki czemu jest wdrażana przy użyciu pakietu VSIX, który zawiera element projektu.  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Aby dodać kreatora do pakietu VSIX  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów z **source.extension.vsixmanifest** plik w projekcie CustomActionProjectItem, a następnie wybierz **Otwórz** do otwarcia plik w edytorze manifestu.  
  
2.  W edytorze manifestu wybierz **zasoby** kartę, a następnie wybierz **New** przycisku.  
  
     **Dodaj nowy zasób** pojawi się okno dialogowe.  
  
3.  W **typu** wybierz **Microsoft.VisualStudio.Assembly**.  
  
4.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
5.  W **projektu** wybierz **ItemTemplateWizard**, a następnie wybierz **OK** przycisku.  
  
6.  Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**, a następnie upewnij się, że rozwiązanie kompiluje bez błędów.  
  
## <a name="test-the-wizard"></a>Kreator testu
 Teraz można przystąpić do testowania kreatora. Po pierwsze uruchom debugowanie rozwiązania CustomActionProjectItem w doświadczalnym wystąpieniu programu Visual Studio. Następnie przetestuj kreatora dla niestandardowych akcji elementu projektu w projekcie programu SharePoint w doświadczalnym wystąpieniu programu Visual Studio. Na koniec Skompiluj i uruchom projekt programu SharePoint, aby sprawdzić, czy akcja niestandardowa działa zgodnie z oczekiwaniami.  
  
#### <a name="to-start-to-debug-the-solution"></a>Aby zacząć debugować rozwiązania  
  
1.  Uruchom program Visual Studio przy użyciu poświadczeń administracyjnych, a następnie otwórz rozwiązanie CustomActionProjectItem.  
  
2.  W projekcie ItemTemplateWizard, otwórz plik kodu CustomActionWizard, a następnie Dodaj punkt przerwania do pierwszego wiersza kodu w `RunStarted` metody.  
  
3.  Na pasku menu wybierz **debugowania** > **wyjątki**.  
  
4.  W **wyjątki** okna dialogowego pole, upewnij się, że **zgłoszenia** i **User-unhandled** pola wyboru dla **wyjątki środowiska uruchomieniowego języka wspólnego**zostaną wyczyszczone, a następnie wybierz **OK** przycisku.  
  
5.  Rozpocznij debugowanie wybierając **F5** klucza, lub na pasku menu, wybierając **debugowania** > **Rozpocznij debugowanie**.  
  
     Visual Studio instaluje rozszerzenia do %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Item\1.0 projektu działanie i uruchamia doświadczalne wystąpienie programu Visual Studio. Element projektu będzie testu, w tym wystąpieniu programu Visual Studio.  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>Aby przetestować kreatora w programie Visual Studio  
  
1.  W doświadczalnym wystąpieniu programu Visual Studio, na pasku menu wybierz **pliku** > **New** > **projektu**.  
  
2.  Rozwiń **Visual C#** lub **języka Visual Basic** węzeł (w zależności od języka obsługującego szablonu elementu), rozwiń węzeł **SharePoint** węzła, a następnie wybierz polecenie **2010** węzła.  
  
3.  Na liście szablonów projektu wybierz **projekt programu SharePoint 2010**, nadaj projektowi nazwę **CustomActionWizardTest**, a następnie wybierz **OK** przycisku.  
  
4.  W **Kreator ustawień niestandardowych SharePoint**, wprowadź adres URL witryny, której chcesz używać do debugowania, a następnie wybierz **Zakończ** przycisku.  
  
5.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla węzła projektu, wybierz pozycję **Dodaj**, a następnie wybierz **nowy element**.  
  
6.  W **Dodaj nowy element - CustomItemWizardTest** okna dialogowego rozwiń **SharePoint** węzła, a następnie rozwiń węzeł **2010** węzła.  
  
7.  Na liście elementów projektu, wybierz opcję **Akcja niestandardowa** elementu, a następnie wybierz **Dodaj** przycisku.  
  
8.  Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkcie przerwania, który wcześniej w ustawieniu `RunStarted` metody.  
  
9. Kontynuuj debugowanie projektu, wybierając **F5** klucza lub na pasku menu, wybierając **debugowania** > **Kontynuuj**.  
  
     Zostanie wyświetlony Kreator dostosowania programu SharePoint.  
  
10. W obszarze **lokalizacji**, wybierz **listy edytować** przycisku opcji.  
  
11. W **identyfikator grupy** wybierz **komunikacji**.  
  
12. W **tytuł** wprowadź **Centrum deweloperów programu SharePoint**.  
  
13. W **opis** wprowadź **otwiera witrynę sieci Web programu SharePoint Developer Center**.  
  
14. W **adresu URL** wprowadź **https://docs.microsoft.com/sharepoint/dev/**, a następnie wybierz **Zakończ** przycisku.  
  
     Program Visual Studio dodaje element o nazwie **CustomAction1** do projektu i otwiera *Elements.xml* plik w edytorze. Upewnij się, że *Elements.xml* zawiera wartości, które są określone w kreatorze.  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>Aby przetestować akcji niestandardowej w programie SharePoint  
  
1.  W doświadczalnym wystąpieniu programu Visual Studio, wybierz **F5** klucza, lub na pasku menu wybierz **debugowania** > **Rozpocznij debugowanie**.  
  
     Akcja niestandardowa zostaje spakowany i wdrożyć w witrynie programu SharePoint, określony przez **adres URL witryny** właściwości projektu i przeglądarki sieci web otworzy stronę domyślnej witryny.  
  
    > [!NOTE]  
    >  Jeśli **wyłączenia debugowania skryptu** pojawi się okno dialogowe, wybierz **tak** przycisku.  
  
2.  W obszarze listy w witrynie programu SharePoint wybierz **zadania** łącza.  
  
     **Zadania — wszystkie zadania** zostanie wyświetlona strona.  
  
3.  Na **narzędzia do obsługi List** karty na Wstążce wybierz **listy** kartę, a następnie w **ustawienia** grupy, wybierz **ustawienia listy**.  
  
     **Ustawienia listy** zostanie wyświetlona strona.  
  
4.  W obszarze **komunikacji** nagłówkiem w górnej części strony wybierz **Centrum deweloperów programu SharePoint** połączyć, sprawdź, czy witryny sieci Web zostanie otwarta przeglądarka https://docs.microsoft.com/sharepoint/dev/, a następnie zamknij przeglądarkę.  
  
## <a name="cleaning-up-the-development-computer"></a>Czyszczenie na komputerze deweloperskim
 Po zakończeniu badania elementu projektu, należy usunąć szablonu elementu projektu w doświadczalnym wystąpieniu programu Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Aby wyczyścić komputerze deweloperskim  
  
1.  W doświadczalnym wystąpieniu programu Visual Studio, na pasku menu wybierz **narzędzia** > **rozszerzenia i aktualizacje**.  
  
     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.  
  
2.  Na liście rozszerzeń wybierz **niestandardowych akcji elementu projektu** rozszerzenie, a następnie wybierz **Odinstaluj** przycisku.  
  
3.  W oknie dialogowym wybierz **tak** przycisk, aby upewnić się, że chcesz odinstalować rozszerzenie, a następnie wybierz **Uruchom ponownie teraz** przycisk, aby ukończyć dezinstalację.  
  
4.  Zamknij oba wystąpienia programu Visual Studio (wystąpienie doświadczalne i wystąpienie programu Visual Studio, w którym rozwiązanie CustomActionProjectItem jest otwarty).  
  
## <a name="see-also"></a>Zobacz także
 [Przewodnik: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Odwołanie do schematu szablonu Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Instrukcje: Korzystanie z kreatorów z szablonami projektu](../extensibility/how-to-use-wizards-with-project-templates.md)   
 [Identyfikatory i domyślne lokalizacje niestandardową akcję](http://go.microsoft.com/fwlink/?LinkId=181964)  
