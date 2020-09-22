---
title: 'Przewodnik: rozszerzanie typu elementu projektu SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e8186b1a1388745527fbb9f4dd37478942c36e62
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90740009"
---
# <a name="walkthrough-extend-a-sharepoint-project-item-type"></a>Przewodnik: zwiększanie typu elementu projektu SharePoint
  Za pomocą elementu projektu **model usługi łączności danych biznesowych** można utworzyć model usługi łączności danych biznesowych (BDC) w programie SharePoint. Domyślnie, gdy tworzysz model przy użyciu tego elementu projektu, dane w modelu nie są wyświetlane użytkownikom. Należy również utworzyć listę zewnętrzną w programie SharePoint, aby umożliwić użytkownikom wyświetlanie danych.

 W tym instruktażu utworzysz rozszerzenie dla elementu projektu **model usługi łączności danych firmowych** . Deweloperzy mogą użyć rozszerzenia, aby utworzyć listę zewnętrzną w projekcie, który wyświetla dane w modelu usługi BDC. W tym instruktażu przedstawiono następujące zadania:

- Tworzenie rozszerzenia programu Visual Studio, które wykonuje dwa podstawowe zadania:

  - Generuje listę zewnętrzną, która wyświetla dane w modelu usługi BDC. Rozszerzenie używa modelu obiektów dla systemu projektu SharePoint do wygenerowania pliku *Elements.xml* , który definiuje listę. Dodaje również plik do projektu, tak aby został wdrożony razem z modelem usługi BDC.

  - Dodaje element menu skrótów do elementów projektu **modelu usługi łączności danych firmowych** w **Eksplorator rozwiązań**. Deweloperzy mogą kliknąć ten element menu, aby wygenerować listę zewnętrzną dla modelu usługi BDC.

- Kompilowanie pakietu rozszerzenia Visual Studio (VSIX) w celu wdrożenia zestawu rozszerzeń.

- Testowanie rozszerzenia.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten przewodnik, potrzebne są następujące składniki na komputerze deweloperskim:

- Obsługiwane wersje systemu Microsoft Windows, SharePoint i Visual Studio.

- Element [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. W tym instruktażu zostanie użyty szablon **projektu VSIX** w zestawie SDK, aby utworzyć pakiet VSIX do wdrożenia elementu projektu. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzającą narzędzia programu SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Znajomość następujących pojęć jest pomocna, ale nie jest wymagana, aby ukończyć Przewodnik:

- Usługa BDC w [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] . Aby uzyskać więcej informacji, zobacz [Architektura usługi BDC](/previous-versions/office/developer/sharepoint-2010/ee558876(v=office.14)).

- Schemat XML dla modeli usługi BDC. Aby uzyskać więcej informacji, zobacz [infrastruktura modelu usługi BDC](/previous-versions/office/developer/sharepoint-2010/ee556378(v=office.14)).

## <a name="create-the-projects"></a>Tworzenie projektów
 Aby ukończyć ten przewodnik, musisz utworzyć dwa projekty:

- Projekt VSIX, aby utworzyć pakiet VSIX do wdrożenia rozszerzenia elementu projektu.

- Projekt biblioteki klas implementujący rozszerzenie elementu projektu.

  Rozpocznij przewodnik, tworząc projekty.

#### <a name="to-create-the-vsix-project"></a>Aby utworzyć projekt VSIX

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

3. W oknie dialogowym **Nowy projekt** rozwiń węzły **Visual C#** lub **Visual Basic** , a następnie wybierz węzeł **rozszerzalności** .

    > [!NOTE]
    > Węzeł **rozszerzalności** jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne we wcześniejszej części tego tematu.

4. Na liście u góry okna dialogowego **Nowy projekt** wybierz **.NET Framework 4,5**.

     Rozszerzenia narzędzi programu SharePoint wymagają funkcji w tej wersji .NET Framework.

5. Wybierz szablon **projektu VSIX** .

6. W polu **Nazwa** wprowadź **GenerateExternalDataLists**, a następnie wybierz przycisk **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje projekt **GenerateExternalDataLists** do **Eksplorator rozwiązań**.

7. Jeśli plik source. Extension. vsixmanifest nie zostanie otwarty automatycznie, otwórz jego menu skrótów w projekcie GenerateExternalDataLists, a następnie wybierz polecenie **Otwórz** .

8. Sprawdź, czy plik source. Extension. vsixmanifest ma niepusty wpis (wprowadź Contoso) dla pola Author, Zapisz plik i zamknij go.

#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła rozwiązanie **GenerateExternalDataLists** , wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

2. W oknie dialogowym **Dodaj nowy projekt** rozwiń węzły **Visual C#** lub **Visual Basic** , a następnie wybierz węzeł **systemu Windows** .

3. Na liście u góry okna dialogowego wybierz **.NET Framework 4,5**.

4. Na liście szablonów projektu wybierz pozycję **Biblioteka klas**.

5. W polu **Nazwa** wprowadź **BdcProjectItemExtension**, a następnie wybierz przycisk **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje projekt **BdcProjectItemExtension** do rozwiązania i otwiera domyślny plik kodu Class1.

6. Usuń plik kodu Class1 z projektu.

## <a name="configure-the-extension-project"></a>Skonfiguruj projekt rozszerzenia
 Przed napisaniem kodu w celu utworzenia rozszerzenia elementu projektu, Dodaj pliki kodu i odwołania do zestawu do projektu rozszerzenia.

#### <a name="to-configure-the-project"></a>Aby skonfigurować projekt

1. W projekcie BdcProjectItemExtension Dodaj dwa pliki kodu, które mają następujące nazwy:

    - ProjectItemExtension

    - GenerateExternalDataLists

2. Wybierz projekt BdcProjectItemExtension, a następnie na pasku menu wybierz **projekt**  >  **Dodaj odwołanie**.

3. W węźle **zestawy** wybierz węzeł **Framework** , a następnie zaznacz pole wyboru dla każdego z następujących zestawów:

    - System. ComponentModel. kompozycji

    - 'Windowsbase

4. W węźle **zestawy** wybierz węzeł **rozszerzenia** , a następnie zaznacz pole wyboru dla następującego zestawu:

    - Microsoft. VisualStudio. SharePoint

5. Wybierz przycisk **OK** .

## <a name="define-the-project-item-extension"></a>Zdefiniuj rozszerzenie elementu projektu
 Utwórz klasę, która definiuje rozszerzenie dla elementu projektu **modelu usługi łączności danych firmowych** . Aby zdefiniować rozszerzenie, Klasa implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfejs. Zaimplementuj ten interfejs w każdym przypadku, gdy chcesz rozłożyć istniejący typ elementu projektu.

#### <a name="to-define-the-project-item-extension"></a>Aby zdefiniować rozszerzenie elementu projektu

1. Wklej następujący kod do pliku kodu ProjectItemExtension.

    > [!NOTE]
    > Po dodaniu tego kodu projekt będzie zawierał błędy kompilacji. Te błędy zostaną odrzucone po dodaniu kodu w dalszych krokach.

     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb#1)]

## <a name="create-the-external-data-lists"></a>Tworzenie list danych zewnętrznych
 Dodaj definicję częściową `GenerateExternalDataListsExtension` klasy, która tworzy listę danych zewnętrznych dla każdej jednostki w modelu usługi BDC. Aby utworzyć listę danych zewnętrznych, ten kod najpierw odczytuje dane jednostki w modelu usługi BDC przez analizowanie danych XML w pliku modelu usługi BDC. Następnie tworzy wystąpienie listy, które jest oparte na modelu BDC i dodaje to wystąpienie listy do projektu.

#### <a name="to-create-the-external-data-lists"></a>Aby utworzyć listę danych zewnętrznych

1. Wklej następujący kod do pliku kodu GenerateExternalDataLists.

     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs#2)]

## <a name="checkpoint"></a>Punkt kontrolny
 W tym momencie w przewodniku cały kod rozszerzenia elementu projektu znajduje się teraz w projekcie. Skompiluj rozwiązanie, aby upewnić się, że projekt kompiluje się bez błędów.

#### <a name="to-build-the-solution"></a>Aby skompilować rozwiązanie

1. Na pasku menu wybierz polecenie **Kompiluj**  >  **kompilację rozwiązania**.

## <a name="create-a-vsix-package-to-deploy-the-project-item-extension"></a>Utwórz pakiet VSIX, aby wdrożyć rozszerzenie elementu projektu
 Aby wdrożyć rozszerzenie, użyj projektu VSIX w rozwiązaniu, aby utworzyć pakiet VSIX. Najpierw skonfiguruj pakiet VSIX, modyfikując plik source. Extension. vsixmanifest, który jest zawarty w projekcie VSIX. Następnie Utwórz pakiet VSIX, tworząc rozwiązanie.

#### <a name="to-configure-and-create-the-vsix-package"></a>Aby skonfigurować i utworzyć pakiet VSIX

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla pliku source. Extension. vsixmanifest w projekcie GenerateExternalDataLists, a następnie wybierz polecenie **Otwórz**.

     Program Visual Studio otwiera plik w edytorze manifestu. Plik source. Extension. vsixmanifest jest podstawą dla rozszerzenia. plik vsixmanifest jest wymagany przez wszystkie pakiety VSIX. Aby uzyskać więcej informacji na temat tego pliku, zobacz [Dokumentacja schematu rozszerzenia VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. W polu **Nazwa produktu** wprowadź **Generator listy danych zewnętrznych**.

3. W polu **autor** wprowadź wartość **contoso**.

4. W polu **Opis** wprowadź **rozszerzenie dla elementów projektu modelu usługi łączności danych firmowych, których można użyć do generowania list danych zewnętrznych**.

5. Na karcie **zasoby** edytora wybierz przycisk **Nowy** .

     Pojawi się okno dialogowe **Dodaj nowy element zawartości** .

6. Na liście **Typ** wybierz **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Ta wartość odnosi się do `MefComponent` elementu w pliku Extension. vsixmanifest. Ten element określa nazwę zestawu rozszerzenia w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MefComponent element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Z listy **Źródło** wybierz **projekt w bieżącym rozwiązaniu**.

8. Na liście **projekt** wybierz pozycję **BdcProjectItemExtension**, a następnie wybierz przycisk **OK** .

9. Na pasku menu wybierz polecenie **Kompiluj**  >  **kompilację rozwiązania**.

10. Upewnij się, że projekt kompiluje i kompiluje bez błędów.

11. Upewnij się, że folder danych wyjściowych kompilacji dla projektu GenerateExternalDataLists zawiera teraz plik GenerateExternalDataLists. VSIX.

     Domyślnie folder wyjściowy kompilacji to... folder \bin\Debug w folderze, który zawiera plik projektu.

## <a name="test-the-project-item-extension"></a>Testowanie rozszerzenia elementu projektu
 Teraz można przystąpić do testowania rozszerzenia elementu projektu. Najpierw Rozpocznij debugowanie projektu rozszerzenia w eksperymentalnym wystąpieniu programu Visual Studio. Następnie użyj rozszerzenia w eksperymentalnym wystąpieniu programu Visual Studio w celu wygenerowania listy zewnętrznej dla modelu usługi BDC. Na koniec Otwórz listę zewnętrzną w witrynie programu SharePoint, aby sprawdzić, czy działa zgodnie z oczekiwaniami.

#### <a name="to-start-debugging-the-extension"></a>Aby rozpocząć debugowanie rozszerzenia

1. W razie potrzeby uruchom ponownie program Visual Studio z poświadczeniami administracyjnymi, a następnie otwórz rozwiązanie GenerateExternalDataLists.

2. W projekcie BdcProjectItemExtension Otwórz plik kodu ProjectItemExtension, a następnie Dodaj punkt przerwania do wiersza kodu w `Initialize` metodzie.

3. Otwórz plik kodu GenerateExternalDataLists, a następnie Dodaj punkt przerwania do pierwszego wiersza kodu w `GenerateExternalDataLists_Execute` metodzie.

4. Rozpocznij debugowanie, wybierając klawisz **F5** lub na pasku menu, wybierając **Debuguj**  >  **Rozpocznij debugowanie**.

     Program Visual Studio instaluje rozszerzenie%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External Data list Generator\1.0 i uruchamia eksperymentalne wystąpienie programu Visual Studio. Testujesz element projektu w tym wystąpieniu programu Visual Studio.

#### <a name="to-test-the-extension"></a>Aby przetestować rozszerzenie

1. W eksperymentalnym wystąpieniu programu Visual Studio na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Szablony** , rozwiń węzeł **Visual C#** , rozwiń węzeł **SharePoint** , a następnie wybierz pozycję **2010**.

3. Upewnij się, że na liście u góry okna dialogowego jest zaznaczone pole wyboru **.NET Framework 3,5** . Projekty dla programu [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] wymagają tej wersji .NET Framework.

4. Na liście szablonów projektu wybierz **projekt SharePoint 2010**.

5. W polu **Nazwa** wprowadź **SharePointProjectTestBDC**, a następnie wybierz przycisk **OK** .

6. W Kreatorze dostosowania programu SharePoint wprowadź adres URL witryny, która ma być używana do debugowania, wybierz pozycję **Wdróż jako rozwiązanie farmy**, a następnie wybierz przycisk **Zakończ** .

7. Otwórz menu skrótów dla projektu SharePointProjectTestBDC, wybierz **Dodaj**, a następnie wybierz **nowy element**.

8. W oknie dialogowym **Dodawanie newItem-SharePointProjectTestBDC** rozwiń węzeł zainstalowanego języka, rozwiń węzeł **SharePoint** .

9. Wybierz węzeł **2010** , a następnie wybierz szablon **model łączności danych firmowych (tylko rozwiązanie farmy)** .

10. W polu **Nazwa** wprowadź **TestBDCModel**, a następnie wybierz przycisk **Dodaj** .

11. Sprawdź, czy kod w innym wystąpieniu programu Visual Studio jest zatrzymany w punkcie przerwania, który został ustawiony w `Initialize` metodzie pliku kodu ProjectItemExtension.

12. W zatrzymanym wystąpieniu programu Visual Studio, wybierz klawisz **F5** lub na pasku menu wybierz **Debuguj**  >  **Kontynuuj** , aby kontynuować debugowanie projektu.

13. W eksperymentalnym wystąpieniu programu Visual Studio, wybierz klawisz **F5** lub na pasku menu wybierz **Debuguj**  >  **Rozpocznij debugowanie** w celu skompilowania, wdrożenia i uruchomienia projektu **TestBDCModel** .

     Przeglądarka sieci Web otworzy się na stronie domyślnej witryny programu SharePoint, która jest określona na potrzeby debugowania.

14. Sprawdź, czy sekcja **listy** w obszarze szybkiego uruchamiania nie zawiera jeszcze listy, która jest oparta na domyślnym modelu usługi BDC w projekcie. Najpierw należy utworzyć listę danych zewnętrznych przy użyciu interfejsu użytkownika programu SharePoint lub rozszerzenia elementu projektu.

15. Zamknij przeglądarkę internetową.

16. W wystąpieniu programu Visual Studio, w którym jest otwarty projekt TestBDCModel, otwórz menu skrótów dla węzła **TestBDCModel** w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Generuj listę danych zewnętrznych**.

17. Sprawdź, czy kod w innym wystąpieniu programu Visual Studio jest zatrzymany w punkcie przerwania, który został ustawiony w `GenerateExternalDataLists_Execute` metodzie. Wybierz klawisz **F5** lub na pasku menu wybierz **Debuguj**  >  **Kontynuuj** , aby kontynuować debugowanie projektu.

18. Eksperymentalne wystąpienie programu Visual Studio dodaje wystąpienie listy o nazwie **Entity1DataList** do projektu TestBDCModel, a wystąpienie generuje również funkcję o nazwie **Feature2** dla wystąpienia listy.

19. Wybierz klawisz **F5** lub na pasku menu wybierz **Debuguj**  >  **Rozpocznij debugowanie** w celu skompilowania, wdrożenia i uruchomienia projektu TestBDCModel.

     Przeglądarka sieci Web otworzy się na stronie domyślnej witryny programu SharePoint, która jest używana do debugowania.

20. W sekcji **listy** obszaru szybkie uruchamianie wybierz listę **Entity1DataList** .

21. Upewnij się, że lista zawiera kolumny o nazwach Identifier1 i Message, oprócz jednego elementu, który ma Identifier1 wartość 0 i wartość komunikatu Hello world.

     Szablon projektu **modelu usługi łączności danych biznesowych** generuje domyślny model usługi BDC, który zapewnia wszystkie te dane.

22. Zamknij przeglądarkę internetową.

## <a name="clean-up-the-development-computer"></a>Czyszczenie komputera deweloperskiego
 Po zakończeniu testowania rozszerzenia elementu projektu, Usuń listę zewnętrzną i model usługi BDC z witryny programu SharePoint i Usuń rozszerzenie elementu projektu z programu Visual Studio.

#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>Aby usunąć listę danych zewnętrznych z witryny programu SharePoint

1. W obszarze Szybkie uruchamianie witryny programu SharePoint wybierz listę **Entity1DataList** .

2. Na Wstążce w witrynie programu SharePoint wybierz kartę **Lista** .

3. Na karcie **Lista** w grupie **Ustawienia** wybierz pozycję **Ustawienia listy**.

4. W obszarze **uprawnienia i zarządzanie**wybierz pozycję **Usuń tę listę**, a następnie wybierz przycisk **OK** , aby potwierdzić, że chcesz wysłać listę do kosza.

5. Zamknij przeglądarkę internetową.

#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>Aby usunąć model usługi BDC z witryny programu SharePoint

1. W eksperymentalnym wystąpieniu programu Visual Studio na pasku menu wybierz kolejno pozycje **kompilacja**  >  **wycofywanie**.

     Program Visual Studio usuwa model usługi BDC z witryny programu SharePoint.

#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>Aby usunąć rozszerzenie elementu projektu z programu Visual Studio

1. W eksperymentalnym wystąpieniu programu Visual Studio na pasku menu wybierz kolejno opcje **Narzędzia**  >  **rozszerzenia i aktualizacje**.

     Zostanie otwarte okno dialogowe **rozszerzenia i aktualizacje** .

2. Na liście rozszerzeń wybierz **Generator listy danych zewnętrznych**, a następnie wybierz przycisk **Odinstaluj** .

3. W wyświetlonym oknie dialogowym wybierz pozycję **tak** , aby potwierdzić, że chcesz odinstalować rozszerzenie.

4. Wybierz pozycję **Uruchom ponownie teraz** , aby ukończyć dezinstalację.

5. Zamknij oba wystąpienia programu Visual Studio (wystąpienie eksperymentalne i wystąpienie, w którym jest otwarte rozwiązanie GenerateExternalDataLists).

## <a name="see-also"></a>Zobacz też
- [Poszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Tworzenie modelu łączności danych firmy](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Projektowanie modelu łączności danych firmy](../sharepoint/designing-a-business-data-connectivity-model.md)