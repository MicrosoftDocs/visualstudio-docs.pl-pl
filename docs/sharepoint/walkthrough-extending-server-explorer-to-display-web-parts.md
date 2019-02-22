---
title: 'Przewodnik: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników Web Part | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 0d46c5e074da8fefa8dc3d7cf370689ad89ad937
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56606342"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>Przewodnik: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników web Part
  W programie Visual Studio, można użyć **połączeń SharePoint** węźle **Eksploratora serwera** do wyświetlania składników w witrynach programu SharePoint. Jednak **Eksploratora serwera** nie jest wyświetlany domyślnie niektóre składniki. W tym przewodniku możesz rozszerzać **Eksploratora serwera** tak, aby wyświetlał galerii składników Web Part na każdy połączony witryny programu SharePoint.

 W tym instruktażu pokazano następujące zagadnienia:

-   Tworzenie rozszerzenia programu Visual Studio, który rozszerza **Eksploratora serwera** w następujący sposób:

    -   Dodaje rozszerzenie **galerii składników Web Part** węźle każdy węzeł witryny programu SharePoint w **Eksploratora serwera**. Ten nowy węzeł zawiera węzły podrzędne, które reprezentują każdego składnika Web Part w galerii składników Web Part w witrynie.

    -   Rozszerzenie definiuje nowy typ węzła, który reprezentuje wystąpienie składnika Web Part. Ten nowy typ węzła jest podstawą dla węzłów podrzędnych w nowym **galerii składników Web Part** węzła. Nowy typ węzła składnika Web Part wyświetla informacje w **właściwości** okna składnik Web Part, który reprezentuje informacje. Typ węzła zawiera również element menu skrótu niestandardowego, który służy jako punkt wyjścia do wykonywania innych zadań, które odnoszą się do składnika Web Part.

-   Utwórz dwa niestandardowych poleceń programu SharePoint, które wywołuje zestawu rozszerzeń. Polecenia programu SharePoint są metody, które można wywoływać za pomocą zestawów rozszerzenie użycia interfejsów API w modelu obiektów serwera dla programu SharePoint. W tym instruktażu utworzysz polecenia pobierają informacje składnika Web Part w lokalnej witrynie programu SharePoint na komputerze deweloperskim. Aby uzyskać więcej informacji, zobacz [wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

-   Tworzenie pakietu Visual Studio rozszerzenia (VSIX), aby wdrożyć rozszerzenie.

-   Debugowanie i testowanie rozszerzenia.

> [!NOTE]
>  Alternatywne wersja tego przewodnika, która używa modelu obiektów klienta dla programu SharePoint zamiast jego modelu obiektów serwera dla [instruktażu: Wywołania w modelu obiektu klienta SharePoint w rozszerzeniu Eksploratora serwera](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Potrzebne są następujące składniki na komputerze deweloperskim w celu przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Windows, SharePoint i Visual Studio.

- The Visual Studio SDK. W tym instruktażu wykorzystano **projekt VSIX** szablonu w zestawie SDK, aby utworzyć pakiet VSIX do wdrożenia elementu projektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie narzędzi SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Znajomość następujących pojęć jest przydatna, ale nie jest to wymagane, aby ukończyć Instruktaż:

- Za pomocą modelu obiektów serwera dla programu SharePoint. Aby uzyskać więcej informacji, zobacz [za pomocą modelu obiektów programu SharePoint Foundation po stronie serwera](http://go.microsoft.com/fwlink/?LinkId=177796).

- Składniki Web Part w rozwiązaniach programu SharePoint. Aby uzyskać więcej informacji, zobacz [przegląd części sieci Web](http://go.microsoft.com/fwlink/?LinkId=177803).

## <a name="create-the-projects"></a>Tworzenie projektów
 Do przeprowadzenia tego instruktażu, należy utworzyć trzy projekty:

- Projekt VSIX do stworzenia pakietu VSIX, aby wdrożyć rozszerzenie.

- Projekt biblioteki klas, który implementuje rozszerzenie. Ten projekt musi być przeznaczony .NET Framework 4.5.

- Projekt biblioteki klas, który definiuje niestandardowe polecenia programu SharePoint. Ten projekt musi być przeznaczony dla środowiska.NET Framework 3.5.

  Instruktaż należy rozpocząć od utworzenia projektów.

#### <a name="to-create-the-vsix-project"></a>Aby utworzyć projekt VSIX

1.  Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2.  Na pasku menu wybierz **pliku** > **New** > **projektu**.

3.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** węzłów, a następnie wybierz **rozszerzalności** węzła.

    > [!NOTE]
    >  **Rozszerzalności** węzeł jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne niniejszego tematu.

4.  W górnej części okna dialogowego wybierz **.NET Framework 4.5** na liście wersji programu .NET Framework.

5.  Wybierz **projekt VSIX** szablonu, nazwę projektu **WebPartNode**, a następnie wybierz **OK** przycisku.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **WebPartNode** projekt **Eksploratora rozwiązań**.

#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia

1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla węzła rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz **nowy projekt**.

2.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** węzła lub **języka Visual Basic** węzeł, a następnie wybierz opcję **Windows** węzła.

3.  W górnej części okna dialogowego wybierz **.NET Framework 4.5** na liście wersji programu .NET Framework.

4.  Na liście szablonów projektu wybierz **biblioteki klas**, nadaj projektowi nazwę **WebPartNodeExtension**, a następnie wybierz **OK** przycisku.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **WebPartNodeExtension** projektu do rozwiązania i otwiera plik domyślny kodu Class1.

5.  Usuń plik kodu Class1 z projektu.

#### <a name="to-create-the-sharepoint-commands-project"></a>Aby utworzyć projekt poleceń programu SharePoint

1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla węzła rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz **nowy projekt**.

2.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** węzła lub **języka Visual Basic** węzła, a następnie wybierz **Windows** węzła.

3.  W górnej części okna dialogowego wybierz **.NET Framework 3.5** na liście wersji programu .NET Framework.

4.  Na liście szablonów projektu wybierz **biblioteki klas**, nadaj projektowi nazwę **WebPartCommands**, a następnie wybierz **OK** przycisku.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **WebPartCommands** projektu do rozwiązania i otwiera plik domyślny kodu Class1.

5.  Usuń plik kodu Class1 z projektu.

## <a name="configure-the-projects"></a>Konfigurowanie projektów
 Przed przystąpieniem do napisania kod, aby utworzyć rozszerzenie, należy dodać pliki kodu i odwołania do zestawów i skonfiguruj ustawienia projektu.

#### <a name="to-configure-the-webpartnodeextension-project"></a>Aby skonfigurować projekt WebPartNodeExtension

1.  W projekcie WebPartNodeExtension Dodaj cztery pliki kodu, które mają następujące nazwy:

    -   SiteNodeExtension

    -   WebPartNodeTypeProvider

    -   WebPartNodeInfo

    -   WebPartCommandIds

2.  Otwórz menu skrótów dla **WebPartNodeExtension** projektu, a następnie wybierz **Dodaj odwołanie**.

3.  W **Menadżer odwołań - WebPartNodeExtension** okna dialogowego wybierz **Framework** kartę, a następnie zaznacz pole wyboru dla każdego z następujących zestawów:

    -   System.ComponentModel.Composition

    -   System.Windows.Forms

4.  Wybierz **rozszerzenia** kartę, zaznacz pole wyboru dla zestawu Microsoft.VisualStudio.SharePoint, a następnie wybierz **OK** przycisku.

5.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **WebPartNodeExtension** węzła projektu, a następnie wybierz **właściwości**.

     **Projektanta projektu** zostanie otwarty.

6.  Wybierz **aplikacji** kartę.

7.  W **domyślny obszar nazw** pola (C#) lub **głównej przestrzeni nazw** pole ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), wprowadź **ServerExplorer.SharePointConnections.WebPartNode**.

#### <a name="to-configure-the-webpartcommands-project"></a>Aby skonfigurować projekt webpartcommands

1.  W projekcie WebPartCommands należy dodać plik kodu, który nosi nazwę WebPartCommands.

2.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **WebPartCommands** węzła projektu, wybierz polecenie **Dodaj**, a następnie wybierz **istniejący element**.

3.  W **Dodaj istniejący element** okno dialogowe, przejdź do folderu, który zawiera pliki kodu dla projektu WebPartNodeExtension, a następnie wybierz pliki kodu WebPartNodeInfo i WebPartCommandIds.

4.  Wybierz strzałkę obok **Dodaj** przycisk, a następnie wybierz **łącze Dodaj jako** w wyświetlonym menu.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje pliki kodu do projektu WebPartCommands jako linki. W rezultacie w plikach kodu znajdują się w projekcie WebPartNodeExtension, ale kod w plikach również są kompilowane w projekcie WebPartCommands.

5.  Otwórz menu skrótów dla **WebPartCommands** ponownie projekt i wybierz polecenie **Dodaj odwołanie**.

6.  W **Menadżer odwołań - WebPartCommands** okna dialogowego wybierz **rozszerzenia** kartę, zaznacz pole wyboru dla każdego z następujących zestawów, a następnie wybierz **OK** przycisk:

    -   Microsoft.SharePoint

    -   Microsoft.VisualStudio.SharePoint.Commands

7.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **WebPartCommands** ponownie projekt, a następnie wybierz **właściwości**.

     **Projektanta projektu** zostanie otwarty.

8.  Wybierz **aplikacji** kartę.

9. W **domyślny obszar nazw** pola (C#) lub **głównej przestrzeni nazw** pole ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), wprowadź **ServerExplorer.SharePointConnections.WebPartNode**.

## <a name="create-icons-for-the-new-nodes"></a>Tworzenie ikony dla nowych węzłów
 Utwórz dwie ikony **Eksploratora serwera** rozszerzenia: ikonę nowego **galerii składników Web Part** węzeł i inną ikonę dla każdego węzła podrzędnego składnika Web Part, w obszarze **galerii składników Web Part** węzeł. W dalszej części tego przewodnika trzeba napisać kod, który kojarzy tych ikon z węzłów.

#### <a name="to-create-icons-for-the-nodes"></a>Aby utworzyć ikony dla węzłów

1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **WebPartNodeExtension** projektu, a następnie wybierz **właściwości**.

2.  **Projektanta projektu** zostanie otwarty.

3.  Wybierz **zasobów** kartę, a następnie wybierz **ten projekt nie zawiera domyślnego pliku zasobów. Kliknij tutaj, aby utworzyć** łącza.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy plik zasobów i otwiera go w projektancie.

4.  W górnej części projektanta, wybierz strzałkę obok **Dodaj zasób** menu polecenia, a następnie wybierz **dodać nową ikonę** w wyświetlonym menu.

5.  W **Dodaj nowy zasób** okno dialogowe, nazwa nową ikonę **WebPartsNode**, a następnie wybierz **Dodaj** przycisku.

     Nowa ikona otwiera się w **edytora obrazów**.

6.  Edytuj ikonę w wersji 16 x 16 tak, aby miało projekt, który możesz łatwo rozpoznać.

7.  Otwórz menu skrótów dla wersji 32 x 32, ikony, a następnie wybierz **Usuń typ obrazu**.

8.  Powtórz kroki od 5 do 8 w celu dodania drugiej ikony do zasobów projektu i nazwij tę ikonę, **składnika Web Part**.

9. W **Eksploratora rozwiązań**w obszarze **zasobów** folder **WebPartNodeExtension** projektu, otwórz menu skrótów dla **WebPartsNode.ico**.

10. W **właściwości** okna, wybierz strzałkę obok **Akcja kompilacji**, a następnie wybierz **zasób osadzony** w wyświetlonym menu.

11. Powtórz ostatnie dwa kroki dla **WebPart.ico**.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Dodaj węzeł galerii składników Web Part do Eksploratora serwera
 Utwórz klasę, która dodaje nowy **galerii składników Web Part** węzła do każdego węzła w witrynie programu SharePoint. Aby dodać nowy węzeł, klasa implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfejsu. Implementuje ten interfejs, zawsze wtedy, gdy chcesz rozszerzyć istniejący węzeł w zachowanie **Eksploratora serwera**, takie jak dodanie węzła podrzędnego do węzła.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Aby dodać węzeł galerii składników Web Part do Eksploratora serwera

1.  W projekcie WebPartNodeExtension Otwórz plik kodu SiteNodeExtension, a następnie wklej następujący kod do niego.

    > [!NOTE]
    >  Po dodaniu tego kodu, projekt będzie miał pewne błędy kompilacji, ale znikną po dodaniu kodu w dalszych krokach.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>Zdefiniuj typ węzła, który reprezentuje składnik web part
 Utwórz klasę, która definiuje nowy typ węzła, który reprezentuje składnik Web Part. Program Visual Studio używa tego nowego typu węzła do wyświetlania węzłów podrzędnych pod **galerii składników Web Part** węzła. Każdy węzeł podrzędny reprezentuje pojedynczy składnik Web Part w witrynie programu SharePoint.

 Aby zdefiniować nowego typu węzła, klasa implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfejsu. Implementuje ten interfejs, zawsze wtedy, gdy chcesz zdefiniować nowy typ węzła w **Eksploratora serwera**.

#### <a name="to-define-the-web-part-node-type"></a>Aby zdefiniować typ węzła części sieci web

1.  W projekcie WebPartNodeExtension Otwórz plik kodu WebPartNodeTypeProvder, a następnie wklej następujący kod do niego.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]

## <a name="define-the-web-part-data-class"></a>Definiowanie klas danych części sieci web
 Zdefiniuj klasę, która zawiera dane dotyczące pojedynczego składnika Web Part w witrynie programu SharePoint. W dalszej części tego instruktażu utworzysz niestandardowe polecenia programu SharePoint, która pobiera dane o poszczególnych składników Web Part w witrynie, a następnie przypisuje dane do wystąpienia tej klasy.

#### <a name="to-define-the-web-part-data-class"></a>Aby zdefiniować klasę danych części sieci web

1.  W projekcie WebPartNodeExtension Otwórz plik kodu WebPartNodeInfo, a następnie wklej następujący kod do niego.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]

## <a name="define-the-ids-for-the-sharepoint-commands"></a>Określ identyfikatory poleceń programu SharePoint
 Zdefiniuj kilka ciągów, które identyfikują niestandardowych poleceń programu SharePoint. Te polecenia zostaną zaimplementowane w dalszej części tego przewodnika.

#### <a name="to-define-the-command-ids"></a>Aby zdefiniować identyfikatory poleceń

1.  W projekcie WebPartNodeExtension Otwórz plik kodu WebPartCommandIds, a następnie wklej następujący kod do niego.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]

## <a name="create-the-custom-sharepoint-commands"></a>Tworzenie niestandardowych poleceń programu SharePoint
 Tworzenie niestandardowych poleceń do wywołania w modelu obiektów serwera dla programu SharePoint w celu pobrania danych o częściach sieci Web w witrynie programu SharePoint. Każde polecenie jest metodą, która ma <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> stosowane do niego.

#### <a name="to-define-the-sharepoint-commands"></a>Aby zdefiniować poleceń programu SharePoint

1.  W projekcie WebPartCommands Otwórz plik kodu WebPartCommands, a następnie wklej następujący kod do niego.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]

## <a name="checkpoint"></a>Punkt kontrolny
 Na tym etapie w instruktażu, cały kod dla **galerii składników Web Part** węzła i poleceń programu SharePoint są teraz w projektach. Kompiluj rozwiązanie, aby upewnić się, że oba projekty skompilować bez błędów.

#### <a name="to-build-the-solution"></a>Aby skompilować rozwiązanie

1.  Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.

    > [!WARNING]
    >  W tym momencie projektu WebPartNode może być błąd kompilacji, ponieważ plik manifestu VSIX nie ma wartości dla autora. Ten błąd znikną po dodaniu wartości w kolejnych krokach.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Utwórz pakiet VSIX, aby wdrożyć rozszerzenie
 Aby wdrożyć rozszerzenie, należy użyć projektu VSIX w rozwiązaniu Aby utworzyć pakiet VSIX. Najpierw należy skonfigurować pakiet VSIX modyfikując plik source.extension.vsixmanifest w projekcie VSIX. Następnie należy utworzyć pakiet VSIX przez utworzenie rozwiązania.

#### <a name="to-configure-the-vsix-package"></a>Aby skonfigurować pakiet VSIX

1.  W **Eksploratora rozwiązań**, w projekcie WebPartNode Otwórz **source.extension.vsixmanifest** plik w edytorze manifestu.

     Plik source.extension.vsixmanifest jest podstawą dla pliku extension.vsixmanifest, które wymagają wszystkie pakiety VSIX. Aby uzyskać więcej informacji na temat tego pliku, zobacz [odwołania 1.0 schematu rozszerzenia VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2.  W **nazwa produktu** wprowadź **węzła galerię części sieci Web w Eksploratorze serwera**.

3.  W **Autor** wprowadź **Contoso**.

4.  W **opis** wprowadź **dodaje niestandardowy węzeł galerii składników Web Part do węzła połączeń SharePoint w Eksploratorze serwera. To rozszerzenie używa niestandardowych poleceń programu SharePoint do wywołania w modelu obiektów serwera.**

5.  Wybierz **zasoby** karta edytora, a następnie wybierz **New** przycisku.

     **Dodaj nowy zasób** pojawi się okno dialogowe.

6.  W **typu** wybierz **Microsoft.VisualStudio.MefComponent**.

    > [!NOTE]
    >  Ta wartość odpowiada `MefComponent` elementu w pliku extension.vsixmanifest. Ten element Określa nazwę zestawu rozszerzeń w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MEFComponent — Element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.

8.  W **projektu** wybierz **WebPartNodeExtension** , a następnie wybierz **OK** przycisku.

9. W edytorze manifestu wybierz **New** ponownie przycisk.

     **Dodaj nowy zasób** pojawi się okno dialogowe.

10. W **typu** wprowadź **SharePoint.Commands.v4**.

    > [!NOTE]
    >  Ten element określa niestandardowe rozszerzenie, które mają zostać uwzględnione w rozszerzeniu Visual Studio. Aby uzyskać więcej informacji, zobacz [zawartości elementu (schemat VSX)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

11. W **źródła** wybierz **projekt w bieżącym rozwiązaniu** elementu listy.

12. W **projektu** wybierz **WebPartCommands**, a następnie wybierz **OK** przycisku.

13. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**, a następnie upewnij się, że rozwiązanie kompiluje bez błędów.

14. Upewnij się, że folder wyjściowy kompilacji dla projektu WebPartNode zawiera teraz plik WebPartNode.vsix.

     Domyślnie folderem wyjściowym kompilacji jest... folderze \bin\Debug w folderze, który zawiera plik projektu.

## <a name="test-the-extension"></a>Testowanie rozszerzenia
 Teraz można przystąpić do testowania nowego **galerii składników Web Part** w węźle **Eksploratora serwera**. Po pierwsze uruchom debugowanie rozszerzeń w doświadczalnym wystąpieniu programu Visual Studio. Następnie należy użyć nowego **składników Web Part** węzła w doświadczalnym wystąpieniu programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

#### <a name="to-start-debugging-the-extension"></a>Aby rozpocząć debugowanie rozszerzenia

1.  Uruchom ponownie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] przy użyciu poświadczeń administracyjnych, a następnie otwórz rozwiązanie WebPartNode.

2.  W projekcie WebPartNodeExtension, otwórz plik kodu SiteNodeExtension, a następnie Dodaj punkt przerwania do pierwszego wiersza kodu w `NodeChildrenRequested` i `CreateWebPartNodes` metody.

3.  Wybierz **F5** klawisz, aby rozpocząć debugowanie.

     Visual Studio instaluje rozszerzenia do %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web część galerii węzła Rozszerzenia dla serwera Explorer\1.0 i uruchamia doświadczalne wystąpienie programu Visual Studio. Element projektu spowoduje przetestowanie w tym wystąpieniu programu Visual Studio.

#### <a name="to-test-the-extension"></a>Aby przetestować rozszerzenie

1.  W doświadczalnym wystąpieniu programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], na pasku menu wybierz **widoku** > **Eksploratora serwera**.

2.  Wykonaj następujące kroki, jeśli witryna programu SharePoint chcesz używać do testowania nie jest wyświetlana w obszarze **połączeń SharePoint** w węźle **Eksploratora serwera**:

    1.  W **Eksploratora serwera**, otwórz menu skrótów dla **połączeń SharePoint**, a następnie wybierz **Dodaj połączenie**.

    2.  W **Dodawanie połączenia programu SharePoint** okna dialogowego wprowadź adres URL witryny programu SharePoint, do którego chcesz połączyć, a następnie wybierz **OK** przycisku.

         Aby określić witrynę programu SharePoint na komputerze deweloperskim, wprowadź **http://localhost**.

3.  Rozwiń węzeł połączenia lokacji (która zawiera adres URL witryny), a następnie rozwiń węzeł lokacji podrzędnej (na przykład **witryny zespołu**).

4.  Upewnij się, że kod w innym wystąpieniu programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zatrzymaniu w punkcie przerwania, który wcześniej w ustawieniu `NodeChildrenRequested` metody, a następnie wybierz **F5** aby kontynuować debugowanie projektu.

5.  W doświadczalnym wystąpieniu programu Visual Studio, sprawdź, czy nowy węzeł o nazwie **galerii składników Web Part** pojawia się w węźle w lokacji najwyższego poziomu, a następnie rozwiń **galerii składników Web Part** węzła.

6.  Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkcie przerwania, który wcześniej w ustawieniu `CreateWebPartNodes` metody, a następnie wybierz **F5** klawisz, aby kontynuować debugowanie projektu.

7.  W doświadczalnym wystąpieniu programu Visual Studio, sprawdź, czy wszystkie składniki Web Part w podłączonej lokacji są wyświetlane w obszarze **galerii składników Web Part** w węźle **Eksploratora serwera**.

8.  W **Eksploratora serwera**, otwórz menu skrótów dla jednej części sieci Web, a następnie wybierz **właściwości**.

9. To wystąpienie elementu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , debugowanie, upewnij się, że szczegółowe informacje o składniku Web Part są wyświetlane w **właściwości** okna.

## <a name="uninstall-the-extension-from-visual-studio"></a>Odinstaluj rozszerzenie z programu Visual Studio
 Po zakończeniu badania rozszerzenia, należy odinstalować rozszerzenie z programu Visual Studio.

#### <a name="to-uninstall-the-extension"></a>Aby odinstalować rozszerzenie

1.  W doświadczalnym wystąpieniu programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], na pasku menu wybierz **narzędzia** > **rozszerzenia i aktualizacje**.

     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.

2.  Na liście rozszerzeń wybierz **rozszerzenia węzła galerii części sieci Web w Eksploratorze serwera**, a następnie wybierz **Odinstaluj** przycisku.

3.  W oknie dialogowym wybierz **tak** przycisk, aby upewnić się, że chcesz odinstalować rozszerzenie, a następnie wybierz **Uruchom ponownie teraz** przycisk, aby ukończyć dezinstalację.

4.  Zamknij oba wystąpienia programu Visual Studio (wystąpienie doświadczalne i wystąpienie programu Visual Studio, w którym rozwiązanie WebPartNode jest otwarty).

## <a name="see-also"></a>Zobacz także
- [Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Przewodnik: Wywołania w modelu obiektu klienta SharePoint w rozszerzeniu Eksploratora serwera](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)
- [Edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons)
- [Tworzenie ikony lub innego obrazu &#40;edytor obrazów dla ikon&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)
