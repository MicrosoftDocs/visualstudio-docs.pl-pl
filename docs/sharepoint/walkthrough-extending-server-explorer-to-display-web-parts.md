---
title: 'Przewodnik: rozszerzanie Eksplorator serwera w celu wyświetlenia składniki Web Part | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5e5221d1cce065a352051ca700cf0fc5ef4ae843
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015632"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>Przewodnik: rozszerzona Eksplorator serwera do wyświetlania składników Web Part
  W programie Visual Studio można użyć węzła **połączenia SharePoint** **Eksplorator serwera** , aby wyświetlić składniki w witrynach programu SharePoint. Jednak **Eksplorator serwera** domyślnie nie wyświetla niektórych składników. W tym instruktażu zostanie rozbudowana **Eksplorator serwera** tak, aby była wyświetlana Galeria składników Web Part w każdej połączonej witrynie programu SharePoint.

 W tym instruktażu przedstawiono następujące zadania:

- Tworzenie rozszerzenia programu Visual Studio, które rozszerza **Eksplorator serwera** w następujący sposób:

  - Rozszerzenie dodaje węzeł **Galerii składników Web Part** w każdym węźle witryny programu SharePoint w **Eksplorator serwera**. Ten nowy węzeł zawiera węzły podrzędne, które reprezentują każdy składnik Web Part w galerii składników Web Part w witrynie.

  - Rozszerzenie definiuje nowy typ węzła, który reprezentuje wystąpienie składnika Web Part. Ten nowy typ węzła jest podstawą dla węzłów podrzędnych w węźle Galeria nowych **składników Web Part** . Nowy typ węzła składnika Web Part wyświetla informacje w oknie **Właściwości** dotyczące części sieci Web, którą reprezentuje. Typ węzła zawiera również niestandardowy element menu skrótów, którego można użyć jako punktu wyjścia do wykonywania innych zadań odnoszących się do składnika Web Part.

- Tworzenie dwóch niestandardowych poleceń programu SharePoint, do których odwołuje się zestaw rozszerzenia. Polecenia programu SharePoint to metody, które mogą być wywoływane przez zestawy rozszerzeń do używania interfejsów API w modelu obiektów serwera dla programu SharePoint. W tym instruktażu utworzysz polecenia, które pobierają informacje o składniku Web Part z lokalnej witryny programu SharePoint na komputerze deweloperskim. Aby uzyskać więcej informacji, zobacz [Wywoływanie modeli obiektów programu SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Kompilowanie pakietu rozszerzenia Visual Studio (VSIX) w celu wdrożenia rozszerzenia.

- Debugowanie i testowanie rozszerzenia.

> [!NOTE]
> Aby zapoznać się z alternatywną wersją tego instruktażu, która używa modelu obiektów klienta programu SharePoint, a nie modelu obiektów serwera, zobacz [Przewodnik: wywoływanie modelu obiektów klienta programu SharePoint w rozszerzeniu Eksplorator serwera](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten przewodnik, potrzebne są następujące składniki na komputerze deweloperskim:

- Obsługiwane wersje systemów Windows, SharePoint i Visual Studio.

- Zestaw SDK programu Visual Studio. W tym instruktażu zostanie użyty szablon **projektu VSIX** w zestawie SDK, aby utworzyć pakiet VSIX do wdrożenia elementu projektu. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzającą narzędzia programu SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Znajomość następujących pojęć jest pomocna, ale nie jest wymagana, aby ukończyć Przewodnik:

- Korzystanie z modelu obiektów serwera dla programu SharePoint. Aby uzyskać więcej informacji, zobacz [Korzystanie z modelu obiektów po stronie serwera programu SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).

- Składniki Web Part w rozwiązaniach programu SharePoint. Aby uzyskać więcej informacji, zobacz [składniki Web Part przegląd](/previous-versions/office/ms432401(v=office.14)).

## <a name="create-the-projects"></a>Tworzenie projektów
 Aby ukończyć ten Instruktaż, należy utworzyć trzy projekty:

- Projekt VSIX, aby utworzyć pakiet VSIX do wdrożenia rozszerzenia.

- Projekt biblioteki klas, który implementuje rozszerzenie. Ten projekt musi być przeznaczony dla .NET Framework 4,5.

- Projekt biblioteki klas, który definiuje niestandardowe polecenia programu SharePoint. Ten projekt musi być przeznaczony dla the.NET Framework 3,5.

  Rozpocznij przewodnik, tworząc projekty.

#### <a name="to-create-the-vsix-project"></a>Aby utworzyć projekt VSIX

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

3. W oknie dialogowym **Nowy projekt** rozwiń węzły **Visual C#** lub **Visual Basic** , a następnie wybierz węzeł **rozszerzalności** .

    > [!NOTE]
    > Węzeł **rozszerzalności** jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne we wcześniejszej części tego tematu.

4. W górnej części okna dialogowego wybierz pozycję **.NET Framework 4,5** na liście wersji .NET Framework.

5. Wybierz szablon **projektu VSIX** , nazwij projekt **WebPartNode**, a następnie wybierz przycisk **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dodaje projekt **WebPartNode** do **Eksplorator rozwiązań**.

#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła rozwiązanie, wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual C#** Node lub **Visual Basic** , a następnie wybierz węzeł **systemu Windows** .

3. W górnej części okna dialogowego wybierz pozycję **.NET Framework 4,5** na liście wersji .NET Framework.

4. Na liście szablonów projektu wybierz pozycję **Biblioteka klas**, nazwij projekt **WebPartNodeExtension**, a następnie wybierz przycisk **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dodaje projekt **WebPartNodeExtension** do rozwiązania i otwiera domyślny plik kodu Class1.

5. Usuń plik kodu Class1 z projektu.

#### <a name="to-create-the-sharepoint-commands-project"></a>Aby utworzyć projekt poleceń programu SharePoint

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła rozwiązanie, wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual C#** Node lub **Visual Basic** , a następnie wybierz węzeł **systemu Windows** .

3. W górnej części okna dialogowego wybierz pozycję **.NET Framework 3,5** na liście wersji .NET Framework.

4. Na liście szablonów projektu wybierz pozycję **Biblioteka klas**, nazwij projekt **WebPartCommands**, a następnie wybierz przycisk **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dodaje projekt **WebPartCommands** do rozwiązania i otwiera domyślny plik kodu Class1.

5. Usuń plik kodu Class1 z projektu.

## <a name="configure-the-projects"></a>Konfigurowanie projektów
 Przed napisaniem kodu w celu utworzenia rozszerzenia należy dodać pliki kodu i odwołania do zestawów i skonfigurować ustawienia projektu.

#### <a name="to-configure-the-webpartnodeextension-project"></a>Aby skonfigurować projekt WebPartNodeExtension

1. W projekcie WebPartNodeExtension Dodaj cztery pliki kodu, które mają następujące nazwy:

    - SiteNodeExtension

    - WebPartNodeTypeProvider

    - WebPartNodeInfo

    - WebPartCommandIds

2. Otwórz menu skrótów dla projektu **WebPartNodeExtension** , a następnie wybierz **Dodaj odwołanie**.

3. W oknie dialogowym **Menedżer odwołań — WebPartNodeExtension** wybierz kartę **Struktura** , a następnie zaznacz pole wyboru dla każdego z następujących zestawów:

    - System. ComponentModel. kompozycji

    - System. Windows. Forms

4. Wybierz kartę **rozszerzenia** , zaznacz pole wyboru dla zestawu Microsoft. VisualStudio. SharePoint, a następnie wybierz przycisk **OK** .

5. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła projektu **WebPartNodeExtension** , a następnie wybierz polecenie **Właściwości**.

     Zostanie otwarty **Projektant projektu** .

6. Wybierz kartę **aplikacja** .

7. W polu **domyślny obszar nazw** (C#) lub **główna przestrzeń nazw** ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) wprowadź **ServerExplorer. SharePointConnections. WebPartNode**.

#### <a name="to-configure-the-webpartcommands-project"></a>Aby skonfigurować projekt WebPartCommands

1. W projekcie WebPartCommands Dodaj plik kodu o nazwie WebPartCommands.

2. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła projektu **WebPartCommands** , wybierz **Dodaj**, a następnie wybierz **istniejący element**.

3. W oknie dialogowym **Dodaj istniejący element** przejdź do folderu, który zawiera pliki kodu dla projektu WebPartNodeExtension, a następnie wybierz pliki kodu WebPartNodeInfo i WebPartCommandIds.

4. Wybierz strzałkę obok przycisku **Dodaj** , a następnie wybierz polecenie **Dodaj jako link** w wyświetlonym menu.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dodaje pliki kodu do projektu WebPartCommands jako linki. W związku z tym pliki kodu znajdują się w projekcie WebPartNodeExtension, ale kod w plikach są również kompilowane w projekcie WebPartCommands.

5. Otwórz menu skrótów dla projektu **WebPartCommands** i wybierz polecenie **Dodaj odwołanie**.

6. W oknie dialogowym **Menedżer odwołań — WebPartCommands** wybierz kartę **rozszerzenia** , zaznacz pole wyboru dla każdego z następujących zestawów, a następnie wybierz przycisk **OK** :

    - Microsoft. SharePoint

    - Microsoft. VisualStudio. SharePoint. Commands

7. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **WebPartCommands** , a następnie wybierz polecenie **Właściwości**.

     Zostanie otwarty **Projektant projektu** .

8. Wybierz kartę **aplikacja** .

9. W polu **domyślny obszar nazw** (C#) lub **główna przestrzeń nazw** ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) wprowadź **ServerExplorer. SharePointConnections. WebPartNode**.

## <a name="create-icons-for-the-new-nodes"></a>Utwórz ikony dla nowych węzłów
 Utwórz dwie ikony rozszerzenia **Eksplorator serwera** : ikona nowego węzła **Galerii składników Web Part** oraz inna ikona dla każdego podrzędnego węzła składnika Web Part w węźle **Galeria składników Web Part** . W dalszej części tego przewodnika napiszesz kod, który kojarzy te ikony z węzłami.

#### <a name="to-create-icons-for-the-nodes"></a>Aby utworzyć ikony dla węzłów

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **WebPartNodeExtension** , a następnie wybierz polecenie **Właściwości**.

2. Zostanie otwarty **Projektant projektu** .

3. Wybierz kartę **zasoby** , a następnie wybierz **ten projekt nie zawiera domyślnego pliku zasobów. Kliknij tutaj, aby utworzyć jedno** łącze.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]tworzy plik zasobów i otwiera go w projektancie.

4. W górnej części okna projektanta wybierz strzałkę obok pozycji menu **Dodaj zasób** , a następnie wybierz polecenie **Dodaj nową ikonę** w wyświetlonym menu.

5. W oknie dialogowym **Dodaj nowy zasób** nadaj nowej ikonie ikonę **WebPartsNode**, a następnie wybierz przycisk **Dodaj** .

     Nowa ikona zostanie otwarta w **Edytorze obrazu**.

6. Edytuj wersję 16x16 ikon, aby mieć projekt, który można łatwo rozpoznać.

7. Otwórz menu skrótów dla wersji 32x32 ikony, a następnie wybierz polecenie **Usuń typ obrazu**.

8. Powtórz kroki od 5 do 8, aby dodać drugą ikonę do zasobów projektu i nazwać ten **składnik**.

9. W **Eksplorator rozwiązań**, w folderze **resources** dla projektu **WebPartNodeExtension** , otwórz menu skrótów dla **WebPartsNode. ico**.

10. W oknie **Właściwości** wybierz strzałkę obok pozycji **Akcja kompilacji**, a następnie wybierz pozycję **zasób osadzony** w wyświetlonym menu.

11. Powtórz ostatnie dwa kroki dla elementu **WebPart. ico**.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Dodaj węzeł Galerii składników Web Part do Eksplorator serwera
 Utwórz klasę, która dodaje nowy węzeł **Galerii składników Web Part** do każdego węzła witryny programu SharePoint. Aby dodać nowy węzeł, Klasa implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfejs. Zaimplementuj ten interfejs w każdym przypadku, gdy chcesz zwiększyć zachowanie istniejącego węzła w **Eksplorator serwera**, na przykład dodając węzeł podrzędny do węzła.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Aby dodać węzeł Galerii składników Web Part do Eksplorator serwera

1. W projekcie WebPartNodeExtension Otwórz plik kodu SiteNodeExtension, a następnie wklej do niego następujący kod.

    > [!NOTE]
    > Po dodaniu tego kodu projekt będzie miał pewne błędy kompilacji, ale w późniejszych krokach zostanie dodany kod.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>Zdefiniuj typ węzła, który reprezentuje część sieci Web
 Utwórz klasę, która definiuje nowy typ węzła, który reprezentuje składnik Web Part. Program Visual Studio używa tego nowego typu węzła do wyświetlania węzłów podrzędnych w węźle **Galeria składników Web Part** . Każdy węzeł podrzędny reprezentuje pojedynczy składnik Web Part w witrynie programu SharePoint.

 Aby zdefiniować nowy typ węzła, Klasa implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfejs. Zaimplementuj ten interfejs w każdym przypadku, gdy chcesz zdefiniować nowy typ węzła w **Eksplorator serwera**.

#### <a name="to-define-the-web-part-node-type"></a>Aby zdefiniować typ węzła składnika Web Part

1. W projekcie WebPartNodeExtension Otwórz plik kodu WebPartNodeTypeProvder, a następnie wklej do niego następujący kod.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]

## <a name="define-the-web-part-data-class"></a>Definiowanie klasy danych składnika Web Part
 Zdefiniuj klasę zawierającą dane o pojedynczym składniku Web Part w witrynie programu SharePoint. W dalszej części tego przewodnika utworzysz niestandardowe polecenie programu SharePoint, które pobiera dane dotyczące poszczególnych składników sieci Web w lokacji, a następnie przypisze dane do wystąpień tej klasy.

#### <a name="to-define-the-web-part-data-class"></a>Aby zdefiniować klasę danych składnika Web Part

1. W projekcie WebPartNodeExtension Otwórz plik kodu WebPartNodeInfo, a następnie wklej do niego następujący kod.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]

## <a name="define-the-ids-for-the-sharepoint-commands"></a>Zdefiniuj identyfikatory dla poleceń programu SharePoint
 Zdefiniuj kilka ciągów, które identyfikują niestandardowe polecenia programu SharePoint. Te polecenia zostaną zaimplementowane w dalszej części tego przewodnika.

#### <a name="to-define-the-command-ids"></a>Aby zdefiniować identyfikatory poleceń

1. W projekcie WebPartNodeExtension Otwórz plik kodu WebPartCommandIds, a następnie wklej do niego następujący kod.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]

## <a name="create-the-custom-sharepoint-commands"></a>Tworzenie niestandardowych poleceń programu SharePoint
 Utwórz niestandardowe polecenia, które wywołują model obiektów serwera dla programu SharePoint, aby pobierać dane dotyczące składniki Web Part w witrynie programu SharePoint. Każde polecenie jest metodą, która ma <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> zastosowanie.

#### <a name="to-define-the-sharepoint-commands"></a>Aby zdefiniować polecenia programu SharePoint

1. W projekcie WebPartCommands Otwórz plik kodu WebPartCommands, a następnie wklej do niego następujący kod.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]

## <a name="checkpoint"></a>Punkt kontrolny
 Na tym etapie przewodnika wszystkie kod węzła **Galerii składników Web Part** i poleceń programu SharePoint znajdują się teraz w projektach. Skompiluj rozwiązanie, aby upewnić się, że oba projekty kompilują się bez błędów.

#### <a name="to-build-the-solution"></a>Aby skompilować rozwiązanie

1. Na pasku menu wybierz polecenie **Kompiluj**  >  **kompilację rozwiązania**.

    > [!WARNING]
    > W tym momencie projekt WebPartNode może mieć błąd kompilacji, ponieważ plik manifestu VSIX nie ma wartości dla autora. Ten błąd zostanie odsunięty po dodaniu wartości w dalszych krokach.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Tworzenie pakietu VSIX w celu wdrożenia rozszerzenia
 Aby wdrożyć rozszerzenie, użyj projektu VSIX w rozwiązaniu, aby utworzyć pakiet VSIX. Najpierw skonfiguruj pakiet VSIX, modyfikując plik source. Extension. vsixmanifest w projekcie VSIX. Następnie Utwórz pakiet VSIX, tworząc rozwiązanie.

#### <a name="to-configure-the-vsix-package"></a>Aby skonfigurować pakiet VSIX

1. W **Eksplorator rozwiązań**w projekcie WebPartNode Otwórz plik **source. Extension. vsixmanifest** w edytorze manifestu.

     Plik source. Extension. vsixmanifest jest podstawą dla pliku Extension. vsixmanifest, który wymaga wszystkich pakietów VSIX. Aby uzyskać więcej informacji na temat tego pliku, zobacz [Dokumentacja schematu rozszerzenia VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. W polu **Nazwa produktu** wprowadź **węzeł Galerii składników Web Part dla Eksplorator serwera**.

3. W polu **autor** wprowadź wartość **contoso**.

4. W polu **Opis** wprowadź polecenie **dodaje niestandardowy węzeł Galerii składników Web Part do węzła połączenia programu SharePoint w Eksplorator serwera. To rozszerzenie używa niestandardowego polecenia programu SharePoint do wywołania modelu obiektów serwera.**

5. Wybierz kartę **składniki** w edytorze, a następnie wybierz przycisk **Nowy** .

     Pojawi się okno dialogowe **Dodaj nowy element zawartości** .

6. Na liście **Typ** wybierz **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Ta wartość odnosi się do `MefComponent` elementu w pliku Extension. vsixmanifest. Ten element określa nazwę zestawu rozszerzenia w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MefComponent element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Z listy **Źródło** wybierz **projekt w bieżącym rozwiązaniu**.

8. Na liście **projekt** wybierz pozycję **WebPartNodeExtension** , a następnie wybierz przycisk **OK** .

9. W edytorze manifestu ponownie wybierz przycisk **Nowy** .

     Pojawi się okno dialogowe **Dodaj nowy element zawartości** .

10. W polu **Typ** wprowadź wartość **SharePoint. Commands. v4**.

    > [!NOTE]
    > Ten element określa niestandardowe rozszerzenie, które ma zostać dołączone do rozszerzenia programu Visual Studio. Aby uzyskać więcej informacji, zobacz [element zawartości (schemat VSX)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

11. Z listy **Źródło** wybierz **projekt w bieżącym** elemencie listy rozwiązania.

12. Na liście **projekt** wybierz pozycję **WebPartCommands**, a następnie wybierz przycisk **OK** .

13. Na pasku menu wybierz kompilacja Kompiluj **Build**  >  **rozwiązanie**, a następnie upewnij się, że rozwiązanie kompiluje się bez błędów.

14. Upewnij się, że folder danych wyjściowych kompilacji dla projektu WebPartNode zawiera teraz plik WebPartNode. VSIX.

     Domyślnie folder wyjściowy kompilacji to... folder \bin\Debug w folderze, który zawiera plik projektu.

## <a name="test-the-extension"></a>Testowanie rozszerzenia
 Teraz można przystąpić do testowania nowego węzła **Galerii składników Web Part** w **Eksplorator serwera**. Najpierw Rozpocznij debugowanie rozszerzenia w eksperymentalnym wystąpieniu programu Visual Studio. Następnie użyj nowego węzła **składniki Web Part** w eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-start-debugging-the-extension"></a>Aby rozpocząć debugowanie rozszerzenia

1. Uruchom ponownie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] z poświadczeniami administracyjnymi, a następnie otwórz rozwiązanie WebPartNode.

2. W projekcie WebPartNodeExtension Otwórz plik kodu SiteNodeExtension, a następnie Dodaj punkt przerwania do pierwszego wiersza kodu w `NodeChildrenRequested` `CreateWebPartNodes` metodach i.

3. Wybierz klawisz **F5** , aby rozpocząć debugowanie.

     Program Visual Studio instaluje rozszerzenie rozszerzenia węzła galerii części%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web dla serwera Explorer\1.0 i uruchamia eksperymentalne wystąpienie programu Visual Studio. Testujesz element projektu w tym wystąpieniu programu Visual Studio.

#### <a name="to-test-the-extension"></a>Aby przetestować rozszerzenie

1. W eksperymentalnym wystąpieniu programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] na pasku menu wybierz polecenie **Wyświetl**  >  **Eksplorator serwera**.

2. Wykonaj następujące kroki, jeśli witryna programu SharePoint, która ma być używana do testowania, nie jest wyświetlana w węźle **połączenia programu SharePoint** w **Eksplorator serwera**:

    1. W **Eksplorator serwera**Otwórz menu skrótów dla **połączeń programu SharePoint**, a następnie wybierz polecenie **Dodaj połączenie**.

    2. W oknie dialogowym **Dodawanie połączenia programu SharePoint** wprowadź adres URL witryny programu SharePoint, z którą chcesz nawiązać połączenie, a następnie wybierz przycisk **OK** .

         Aby określić witrynę programu SharePoint na komputerze deweloperskim, wprowadź **http://localhost** .

3. Rozwiń węzeł połączenie lokacji (w którym jest wyświetlany adres URL witryny), a następnie rozwiń węzeł lokacji podrzędnej (na przykład **Witryna zespołu**).

4. Sprawdź, czy kod w drugim wystąpieniu jest [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zatrzymany w punkcie przerwania, który został ustawiony we wcześniejszej części `NodeChildrenRequested` metody, a następnie naciśnij klawisz **F5** , aby kontynuować debugowanie projektu.

5. W eksperymentalnym wystąpieniu programu Visual Studio Sprawdź, czy nowy węzeł o nazwie **Galeria składników Web Part** pojawia się pod węzłem lokacja najwyższego poziomu, a następnie rozwiń węzeł **Galeria składników Web Part** .

6. Sprawdź, czy kod w innym wystąpieniu programu Visual Studio jest zatrzymany w punkcie przerwania, który został ustawiony we wcześniejszej części `CreateWebPartNodes` metody, a następnie wybierz klawisz **F5** , aby kontynuować debugowanie projektu.

7. W eksperymentalnym wystąpieniu programu Visual Studio Sprawdź, czy wszystkie składniki Web Part w połączonej lokacji są wyświetlane w węźle **Galeria składników Web Part** w **Eksplorator serwera**.

8. W **Eksplorator serwera**Otwórz menu skrótów dla jednego z składniki Web Part, a następnie wybierz polecenie **Właściwości**.

9. W wystąpieniu debugowania należy [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sprawdzić, czy szczegółowe informacje o składniku Web Part pojawiają się w oknie **Właściwości** .

## <a name="uninstall-the-extension-from-visual-studio"></a>Odinstaluj rozszerzenie z programu Visual Studio
 Po zakończeniu testowania rozszerzenia Odinstaluj rozszerzenie z programu Visual Studio.

#### <a name="to-uninstall-the-extension"></a>Aby odinstalować rozszerzenie

1. W eksperymentalnym wystąpieniu programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] na pasku menu wybierz kolejno opcje **Narzędzia**  >  **rozszerzenia i aktualizacje**.

     Zostanie otwarte okno dialogowe **rozszerzenia i aktualizacje** .

2. Na liście rozszerzeń wybierz opcję **rozszerzenie węzła Galeria składników Web Part dla Eksplorator serwera**, a następnie wybierz przycisk **Odinstaluj** .

3. W wyświetlonym oknie dialogowym wybierz przycisk **tak** , aby potwierdzić, że chcesz odinstalować rozszerzenie, a następnie wybierz przycisk **Uruchom ponownie teraz** , aby ukończyć dezinstalację.

4. Zamknij oba wystąpienia programu Visual Studio (wystąpienie eksperymentalne i wystąpienie programu Visual Studio, w którym jest otwarte rozwiązanie WebPartNode).

## <a name="see-also"></a>Zobacz także
- [Rozwiń węzeł połączenia programu SharePoint w Eksplorator serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Przewodnik: wywoływanie modelu obiektów klienta programu SharePoint w rozszerzeniu Eksplorator serwera](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)
- [Edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons)
- [Tworzenie ikony lub innego obrazu &#40;Edytor obrazów dla ikon&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)
