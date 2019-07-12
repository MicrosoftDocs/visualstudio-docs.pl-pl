---
title: 'Przewodnik: Rozszerzanie typu elementu projektu programu SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 795cc62ca88f7ede87e978d910d397e0ce6e2ad7
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825983"
---
# <a name="walkthrough-extend-a-sharepoint-project-item-type"></a>Przewodnik: Rozszerzanie typu elementu projektu SharePoint
  Możesz użyć **Model usługi łączności danych biznesowych** elementu projektu, aby utworzyć model usługi łączności danych biznesowych (BDC) w programie SharePoint. Domyślnie podczas tworzenia modelu przy użyciu tego elementu projektu danych w modelu jest niewidoczne dla użytkowników. Należy także utworzyć listy zewnętrznej w SharePoint, aby umożliwić użytkownikom wyświetlanie danych.

 W tym instruktażu utworzysz rozszerzeniem dla **Model usługi łączności danych biznesowych** elementu projektu. Deweloperzy mogą używać rozszerzenia do tworzenia list zewnętrznych we własnym projekcie, który wyświetla dane w modelu usługi łączności danych biznesowych. W tym instruktażu pokazano następujące zagadnienia:

- Tworzenie rozszerzenia programu Visual Studio, który wykonuje dwa główne zadania:

  - Generuje listę zewnętrzną, która wyświetla dane w modelu usługi BDC. Rozszerzenie wykorzystuje model obiektów dla systemu projektu programu SharePoint do generowania *Elements.xml* pliku, który definiuje listę. On również dodaje plik do projektu tak, że jest wdrażany wraz z modelu usługi BDC.

  - Dodaje element menu skrótów do **Model usługi łączności danych biznesowych** elementy w projektu **Eksploratora rozwiązań**. Deweloperzy mogą kliknąć element menu w celu wygenerowania listy zewnętrznej dla modelu usługi łączności danych biznesowych.

- Tworzenie pakietu Visual Studio rozszerzenia (VSIX) do wdrażania zestawu rozszerzeń.

- Testowanie rozszerzeń.

## <a name="prerequisites"></a>Wymagania wstępne
 Potrzebne są następujące składniki na komputerze deweloperskim w celu przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Microsoft Windows, SharePoint i Visual Studio.

- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. W tym instruktażu wykorzystano **projekt VSIX** szablonu w zestawie SDK, aby utworzyć pakiet VSIX do wdrożenia elementu projektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie narzędzi SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Znajomość następujących pojęć jest przydatna, ale nie jest to wymagane, aby ukończyć Instruktaż:

- Usługa łączności danych biznesowych w [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]. Aby uzyskać więcej informacji, zobacz [architektura BDC](http://go.microsoft.com/fwlink/?LinkId=177798).

- Schemat XML dla modeli usługi łączności danych biznesowych. Aby uzyskać więcej informacji, zobacz [infrastruktura modelu usługi BDC](http://go.microsoft.com/fwlink/?LinkId=177799).

## <a name="create-the-projects"></a>Tworzenie projektów
 Aby ukończyć ten Instruktaż, musisz utworzyć dwa projekty:

- Projekt VSIX do stworzenia pakietu VSIX do wdrożenia rozszerzenia elementu projektu.

- Projekt biblioteki klas, który implementuje rozszerzenie elementu projektu.

  Instruktaż należy rozpocząć od utworzenia projektów.

#### <a name="to-create-the-vsix-project"></a>Aby utworzyć projekt VSIX

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Na pasku menu wybierz **pliku** > **New** > **projektu**.

3. W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** węzłów, a następnie wybierz **rozszerzalności** węzła.

    > [!NOTE]
    > **Rozszerzalności** węzeł jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne niniejszego tematu.

4. Na liście u góry **nowy projekt** okna dialogowego wybierz **.NET Framework 4.5**.

     Rozszerzenia narzędzi programu SharePoint wymagają funkcji w tej wersji programu .NET Framework.

5. Wybierz **projekt VSIX** szablonu.

6. W **nazwa** wprowadź **GenerateExternalDataLists**, a następnie wybierz **OK** przycisku.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **GenerateExternalDataLists** projekt **Eksploratora rozwiązań**.

7. Jeśli plik source.extension.vsixmanifest nie jest otwierany automatycznie, otwórz jego menu skrótów w projekcie GenerateExternalDataLists, a następnie wybierz **Otwórz**

8. Sprawdź, czy plik source.extension.vsixmanifest ma wpis nie jest pusty (wprowadź Contoso) dla pola Autor, Zapisz plik, a następnie zamknij go.

#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **GenerateExternalDataLists** węzła rozwiązania wybierz **Dodaj**, a następnie wybierz **nowy projekt**.

2. W **Dodaj nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** węzłów, a następnie wybierz **Windows** węzła.

3. Na liście u góry okna dialogowego wybierz **.NET Framework 4.5**.

4. Na liście szablonów projektu wybierz **biblioteki klas**.

5. W **nazwa** wprowadź **BdcProjectItemExtension**, a następnie wybierz **OK** przycisku.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **BdcProjectItemExtension** projektu do rozwiązania i otwiera plik domyślny kodu Class1.

6. Usuń plik kodu Class1 z projektu.

## <a name="configure-the-extension-project"></a>Konfigurowanie projektu rozszerzenia
 Przed przystąpieniem do napisania kod, aby utworzyć rozszerzenie elementu projektu, Dodaj pliki kodu i odwołania do zestawów do projektu rozszerzenia.

#### <a name="to-configure-the-project"></a>Aby skonfigurować projekt

1. W projekcie BdcProjectItemExtension należy dodać dwa pliki kodu, które mają następujące nazwy:

    - ProjectItemExtension

    - GenerateExternalDataLists

2. Wybierz projekt BdcProjectItemExtension, a następnie na pasku menu wybierz **projektu** > **Dodaj odwołanie**.

3. W obszarze **zestawy** węzła, wybierz **Framework** węzłem, a następnie zaznacz pole wyboru dla każdego z następujących zestawów:

    - System.ComponentModel.Composition

    - WindowsBase

4. W obszarze **zestawy** węzła, wybierz **rozszerzenia** węzeł, a następnie zaznacz pole wyboru dla następującego zestawu:

    - Microsoft.VisualStudio.SharePoint

5. Wybierz **OK** przycisku.

## <a name="define-the-project-item-extension"></a>Definiowanie rozszerzenia elementu projektu
 Utwórz klasę, która określa rozszerzenie dla **Model usługi łączności danych biznesowych** elementu projektu. Aby zdefiniować rozszerzenie, klasa implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfejsu. Zawsze, gdy chcesz rozszerzyć istniejący typ elementu projektu, należy zaimplementować ten interfejs.

#### <a name="to-define-the-project-item-extension"></a>Aby zdefiniować rozszerzenie elementu projektu

1. Wklej następujący kod do pliku kodu ProjectItemExtension.

    > [!NOTE]
    > Po dodaniu tego kodu, projekt będzie miał pewne błędy kompilacji. Te błędy znikną po dodaniu kodu w dalszych krokach.

     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb#1)]

## <a name="create-the-external-data-lists"></a>Tworzenie list danych zewnętrznych
 Dodaj częściową definicję `GenerateExternalDataListsExtension` klasy, która tworzy listę danych zewnętrznych dla każdej jednostki w modelu usługi BDC. Aby utworzyć listę danych zewnętrznych, ten kod najpierw odczytuje dane jednostki w modelu usługi BDC przez analizowanie danych XML w pliku modelu usługi łączności danych biznesowych. Następnie tworzy wystąpienie listy, która jest oparta na modelu usługi BDC i dodaje instancję tej listy do projektu.

#### <a name="to-create-the-external-data-lists"></a>Do tworzenia list danych zewnętrznych

1. Wklej następujący kod do pliku kodu GenerateExternalDataLists.

     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs#2)]

## <a name="checkpoint"></a>Punkt kontrolny
 W tym momencie w instruktażu, cały kod dla rozszerzenia elementu projektu jest teraz w projekcie. Kompiluj rozwiązanie, aby upewnić się, że projekt kompiluje bez błędów.

#### <a name="to-build-the-solution"></a>Aby skompilować rozwiązanie

1. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.

## <a name="create-a-vsix-package-to-deploy-the-project-item-extension"></a>Utwórz pakiet VSIX do wdrożenia rozszerzenia elementu projektu
 Aby wdrożyć rozszerzenie, należy użyć projektu VSIX w rozwiązaniu Aby utworzyć pakiet VSIX. Najpierw należy skonfigurować pakiet VSIX modyfikując plik source.extension.vsixmanifest, który znajduje się w projekcie VSIX. Następnie należy utworzyć pakiet VSIX przez utworzenie rozwiązania.

#### <a name="to-configure-and-create-the-vsix-package"></a>Aby skonfigurować i utworzyć pakiet VSIX

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla pliku source.extension.vsixmanifest w projekcie GenerateExternalDataLists, a następnie wybierz **Otwórz**.

     Program Visual Studio otwiera plik w edytorze manifestu. Plik source.extension.vsixmanifest jest podstawą dla pliku extension.vsixmanifest jest wymagany przez wszystkie pakiety VSIX. Aby uzyskać więcej informacji na temat tego pliku, zobacz [odwołania 1.0 schematu rozszerzenia VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. W **nazwa produktu** wprowadź **Generator listy danych zewnętrznych**.

3. W **Autor** wprowadź **Contoso**.

4. W **opis** wprowadź **rozszerzeniem dla elementów projektu modelu usługi łączności danych biznesowych, które mogą służyć do generowania list danych zewnętrznych**.

5. Na **zasoby** karta w edytorze wybierz **nowy** przycisku.

     **Dodaj nowy zasób** pojawi się okno dialogowe.

6. W **typu** wybierz **Microsoft.VisualStudio.MefComponent**.

    > [!NOTE]
    > Ta wartość odpowiada `MefComponent` elementu w pliku extension.vsixmanifest. Ten element Określa nazwę zestawu rozszerzeń w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MEFComponent — Element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.

8. W **projektu** wybierz **BdcProjectItemExtension**, a następnie wybierz **OK** przycisku.

9. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.

10. Upewnij się, że projekt kompiluje i buduje bez błędów.

11. Upewnij się, że folder wyjściowy kompilacji dla projektu GenerateExternalDataLists zawiera teraz plik GenerateExternalDataLists.vsix.

     Domyślnie folderem wyjściowym kompilacji jest... folderze \bin\Debug w folderze, który zawiera plik projektu.

## <a name="test-the-project-item-extension"></a>Testowanie rozszerzenia element projektu
 Teraz można przystąpić do testowania rozszerzenie elementu projektu. Po pierwsze uruchom debugowanie projektu rozszerzenia w doświadczalnym wystąpieniu programu Visual Studio. Następnie należy użyć rozszerzenia w doświadczalnym wystąpieniu programu Visual Studio do generowania listy zewnętrznej dla modelu usługi BDC. Wreszcie Otwórz listę zewnętrzną w witrynie programu SharePoint, aby sprawdzić, czy działa zgodnie z oczekiwaniami.

#### <a name="to-start-debugging-the-extension"></a>Aby rozpocząć debugowanie rozszerzenia

1. Jeśli to konieczne, uruchom program Visual Studio przy użyciu poświadczeń administracyjnych, a następnie otwórz rozwiązanie GenerateExternalDataLists.

2. W projekcie BdcProjectItemExtension, otwórz plik kodu ProjectItemExtension, a następnie Dodaj punkt przerwania do wierszy kodu z `Initialize` metody.

3. Otwórz plik kodu GenerateExternalDataLists, a następnie Dodaj punkt przerwania do pierwszego wiersza kodu w `GenerateExternalDataLists_Execute` metody.

4. Rozpocznij debugowanie wybierając **F5** klucza lub na pasku menu, wybierając **debugowania** > **Rozpocznij debugowanie**.

     Visual Studio instaluje rozszerzenia do %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External danych listy generator\1. 0 i uruchamia doświadczalne wystąpienie programu Visual Studio. Element projektu spowoduje przetestowanie w tym wystąpieniu programu Visual Studio.

#### <a name="to-test-the-extension"></a>Aby przetestować rozszerzenie

1. W doświadczalnym wystąpieniu programu Visual Studio, na pasku menu wybierz **pliku** > **New** > **projektu**.

2. W **nowy projekt** okna dialogowego rozwiń **szablony** węzła, rozwiń węzeł **Visual C#** węzła, rozwiń węzeł **SharePoint** węzła, a następnie Wybierz **2010**.

3. Upewnij się, że na liście u góry okna dialogowego **.NET Framework 3.5** jest zaznaczone. Projekty dla [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] wymagają tej wersji systemu .NET Framework.

4. Na liście szablonów projektu wybierz **projekt programu SharePoint 2010**.

5. W **nazwa** wprowadź **SharePointProjectTestBDC**, a następnie wybierz **OK** przycisku.

6. W Kreatorze dostosowywania programu SharePoint, wprowadź adres URL witryny, której chcesz używać do debugowania, wybierz **Wdróż jako rozwiązanie farmy**, a następnie wybierz **Zakończ** przycisku.

7. Otwórz menu skrótów dla projektu SharePointProjectTestBDC, wybierz polecenie **Dodaj**, a następnie wybierz **nowy element**.

8. W **Dodaj NewItem - SharePointProjectTestBDC** okna dialogowego rozwiń węzeł zainstalowanego języka, rozwiń węzeł **SharePoint** węzła.

9. Wybierz **2010** węzła, a następnie wybierz **Model usługi łączności danych biznesowych (tylko rozwiązanie farmy)** szablonu.

10. W **nazwa** wprowadź **TestBDCModel**, a następnie wybierz **Dodaj** przycisku.

11. Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkcie przerwania, który zostało ustawiony w `Initialize` metodzie pliku kodu ProjectItemExtension.

12. W przypadku zatrzymania programu Visual Studio, wybierz **F5** klucza lub na pasku menu wybierz **debugowania** > **Kontynuuj** aby kontynuować debugowanie projektu.

13. W doświadczalnym wystąpieniu programu Visual Studio, wybierz **F5** klucza lub na pasku menu wybierz **debugowania** > **Rozpocznij debugowanie** do kompilowania, wdrażania i uruchomienia **TestBDCModel** projektu.

     Przeglądarka sieci web otworzy stronę domyślnej witryny programu SharePoint, która jest określona dla debugowania.

14. Upewnij się, że **Wyświetla** sekcji w obszarze szybkiego uruchamiania jeszcze nie zawiera listy, który jest oparty na domyślnym modelu usługi BDC w projekcie. Należy najpierw utworzyć listę danych zewnętrznych, za pomocą interfejsu użytkownika programu SharePoint lub za pomocą rozszerzenie elementu projektu.

15. Zamknij przeglądarkę sieci web.

16. W wystąpieniu programu Visual Studio, które ma projekt testbdcmodel, otwórz menu skrótów dla **TestBDCModel** w węźle **Eksploratora rozwiązań**, a następnie wybierz **Generowanie danych zewnętrznych Lista**.

17. Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkcie przerwania, który zostało ustawiony w `GenerateExternalDataLists_Execute` metody. Wybierz **F5** klucza lub na pasku menu wybierz **debugowania** > **Kontynuuj** aby kontynuować debugowanie projektu.

18. Doświadczalnym wystąpieniu programu Visual Studio dodaje wystąpienie listy, który nosi nazwę **Entity1DataList** do TestBDCModel, projektu i instancja generuje również funkcję, która nosi nazwę **funkcja2** dla listy wystąpienie.

19. Wybierz **F5** klucza lub na pasku menu wybierz **debugowania** > **Rozpocznij debugowanie** do kompilowania, wdrażania i uruchomienia projektu TestBDCModel.

     Przeglądarka sieci web otworzy stronę domyślnej witryny programu SharePoint, która jest używana do debugowania.

20. W **Wyświetla** sekcji obszaru szybkiego uruchamiania wybierz **Entity1DataList** listy.

21. Sprawdź, czy lista zawiera kolumny o nazwie Identifier1 i wiadomość, oprócz jednego elementu, który ma wartość Identifier1 0 i wartość wiadomości Hello World.

     **Model usługi łączności danych biznesowych** szablonu projektu generuje domyślnym modelu usługi BDC, który udostępnia wszystkie te dane.

22. Zamknij przeglądarkę sieci web.

## <a name="clean-up-the-development-computer"></a>Czyszczenie na komputerze deweloperskim
 Po zakończeniu badania rozszerzenia elementu projektu, Usuń listy zewnętrzne i model usługi BDC z witryny programu SharePoint i usuń rozszerzenie elementu projektu z programu Visual Studio.

#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>Aby usunąć listę danych zewnętrznych z witryny programu SharePoint

1. W obszarze Szybkie uruchamianie witryny programu SharePoint, wybierz **Entity1DataList** listy.

2. Na Wstążce w witrynie programu SharePoint wybierz **listy** kartę.

3. Na **listy** na karcie **ustawienia** grupy, wybierz **ustawienia listy**.

4. W obszarze **uprawnienia i zarządzanie**, wybierz **Usuń tę listę**, a następnie wybierz **OK** aby upewnić się, że chcesz wysłać listę do Kosza.

5. Zamknij przeglądarkę sieci web.

#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>Aby usunąć BDC model z witryny programu SharePoint

1. W doświadczalnym wystąpieniu programu Visual Studio, na pasku menu wybierz **kompilacji** > **Wycofaj**.

     Program Visual Studio usuwa BDC model z witryny programu SharePoint.

#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>Aby usunąć rozszerzenie elementu projektu z programu Visual Studio

1. W doświadczalnym wystąpieniu programu Visual Studio, na pasku menu wybierz **narzędzia** > **rozszerzenia i aktualizacje**.

     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.

2. Na liście rozszerzeń wybierz **Generator listy danych zewnętrznych**, a następnie wybierz **Odinstaluj** przycisku.

3. W oknie dialogowym wybierz **tak** aby upewnić się, że chcesz odinstalować rozszerzenie.

4. Wybierz **Uruchom ponownie teraz** aby ukończyć dezinstalację.

5. Zamknij oba wystąpienia programu Visual Studio (wystąpienie doświadczalne i wystąpienie, w którym rozwiązanie GenerateExternalDataLists jest otwarte).

## <a name="see-also"></a>Zobacz także
- [Rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)
