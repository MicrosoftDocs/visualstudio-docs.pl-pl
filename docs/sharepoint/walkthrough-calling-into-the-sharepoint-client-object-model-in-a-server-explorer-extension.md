---
title: 'Przewodnik: Wywoływanie modelu obiektów klienta SharePoint w rozszerzeniu Eksploratora serwera | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b140a1dcadd86ed8d4c3634669ecf753ad84e25e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873603"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>Przewodnik: Wywoływanie modelu obiektu klienta SharePoint w rozszerzeniu Eksploratora serwera
  W tym instruktażu pokazano, jak wywołać modelu obiektu klienta SharePoint z rozszerzeniem dla **połączeń SharePoint** w węźle **Eksploratora serwera**. Aby uzyskać więcej informacji o sposobie używania modelu obiektu klienta SharePoint, zobacz [wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
 W tym instruktażu pokazano następujące zagadnienia:  
  
-   Tworzenie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenia, która rozszerza **połączeń SharePoint** węźle **Eksploratora serwera** w następujący sposób:  
  
    -   Dodaje rozszerzenie **galerii składników Web Part** węźle każdy węzeł witryny programu SharePoint w **Eksploratora serwera**. Ten nowy węzeł zawiera węzły podrzędne, które reprezentują każdego składnika Web Part w galerii składników Web Part w witrynie.  
  
    -   Rozszerzenie definiuje nowy typ węzła, który reprezentuje wystąpienie składnika Web Part. Ten nowy typ węzła jest podstawą dla węzłów podrzędnych w nowym **galerii składników Web Part** węzła. Nowy typ węzła składnika Web Part wyświetla informacje w **właściwości** okna o składnika Web Part, który reprezentuje węzeł.  
  
-   Tworzenie pakietu Visual Studio rozszerzenia (VSIX), aby wdrożyć rozszerzenie.  
  
-   Debugowanie i testowanie rozszerzenia.  
  
> [!NOTE]  
>  Rozszerzenie, które tworzysz w tym przewodniku przypomina rozszerzenia, który zostanie utworzony w [instruktażu: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md). Ten przewodnik korzysta z modelu obiektów serwera SharePoint, ale w tym przewodniku wykonuje te same zadania przy użyciu client object model.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Potrzebne są następujące składniki na komputerze deweloperskim w celu przeprowadzenia tego instruktażu:  
  
-   Obsługiwane wersje systemu Windows, SharePoint i Visual Studio.
  
-   The Visual Studio SDK. W tym instruktażu wykorzystano **projekt VSIX** szablonu w zestawie SDK, aby utworzyć pakiet VSIX do wdrożenia rozszerzenia. Aby uzyskać więcej informacji, zobacz [Rozszerzanie narzędzi SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
Znajomość następujących pojęć jest przydatna, ale nie jest to wymagane, aby ukończyć Instruktaż:  
  
-   Przy użyciu modelu obiektu klienta SharePoint. Aby uzyskać więcej informacji, zobacz [zarządzane Client Object Model](http://go.microsoft.com/fwlink/?LinkId=177797).  
  
-   Składniki Web Part w programie SharePoint. Aby uzyskać więcej informacji, zobacz [przegląd części sieci Web](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## <a name="create-the-projects"></a>Tworzenie projektów
 Do przeprowadzenia tego instruktażu, należy utworzyć dwa projekty:  
  
- Projekt VSIX do stworzenia pakietu VSIX do wdrożenia **Eksploratora serwera** rozszerzenia.  
  
- Projekt biblioteki klas, który implementuje **Eksploratora serwera** rozszerzenia.  
  
  Instruktaż należy rozpocząć od utworzenia projektów.  
  
#### <a name="to-create-the-vsix-project"></a>Aby utworzyć projekt VSIX  
  
1.  Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na pasku menu wybierz **pliku** > **New** > **projektu**.  
  
3.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** węzłów, a następnie wybierz **rozszerzalności**.  
  
    > [!NOTE]  
    >  **Rozszerzalności** węzeł jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne niniejszego tematu.  
  
4.  W górnej części okna dialogowego wybierz **.NET Framework 4.5** na liście wersji programu .NET Framework.  
  
     Rozszerzenia narzędzi programu SharePoint wymagają funkcji w tej wersji programu .NET Framework.  
  
5.  Wybierz **projekt VSIX** szablonu.  
  
6.  W **nazwa** wpisz **WebPartNode**, a następnie wybierz **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **WebPartNode** projekt **Eksploratora rozwiązań**.  
  
#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla węzła rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz **nowy projekt**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** węzłów, a następnie wybierz **Windows**.  
  
3.  W górnej części okna dialogowego wybierz **.NET Framework 4.5** na liście wersji programu .NET Framework.  
  
4.  Na liście szablonów projektu wybierz **biblioteki klas**.  
  
5.  W **nazwa** wprowadź **WebPartNodeExtension**, a następnie wybierz **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **WebPartNodeExtension** projektu do rozwiązania i otwiera plik domyślny kodu Class1.  
  
6.  Usuń plik kodu Class1 z projektu.  
  
## <a name="configure-the-extension-project"></a>Konfigurowanie projektu rozszerzenia
 Przed przystąpieniem do napisania kod, aby utworzyć rozszerzenie, należy dodać pliki kodu i odwołania do zestawów do projektu, a następnie należy zaktualizować domyślny obszar nazw.  
  
#### <a name="to-configure-the-project"></a>Aby skonfigurować projekt  
  
1.  W **WebPartNodeExtension** projektu, należy dodać dwa pliki kodu, które są nazywane SiteNodeExtension i WebPartNodeTypeProvider.  
  
2.  Otwórz menu skrótów dla projektu WebPartNodeExtension, a następnie wybierz **Dodaj odwołanie**.  
  
3.  W **Menadżer odwołań - WebPartNodeExtension** okna dialogowego wybierz **Framework** węzeł, a następnie zaznacz pola wyboru dla elementy System.ComponentModel.Composition i przestrzeń nazw System.Windows.Forms zestawy.  
  
4.  Wybierz **rozszerzenia** węzeł, zaznacz pole wyboru dla każdego z następujących zestawów, a następnie wybierz **OK** przycisku:  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Otwórz menu skrótów dla **WebPartNodeExtension** projektu, a następnie wybierz **właściwości**.  
  
     **Projektanta projektu** zostanie otwarty.  
  
6.  Wybierz **aplikacji** kartę.  
  
7.  W **domyślny obszar nazw** pola (C#) lub **głównej przestrzeni nazw** polu (Visual Basic), wprowadź **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## <a name="create-icons-for-the-new-nodes"></a>Tworzenie ikony dla nowych węzłów
 Utwórz dwie ikony **Eksploratora serwera** rozszerzenia: ikonę nowego **galerii składników Web Part** węzła i inną ikonę dla każdego węzła podrzędnego składnika Web Part, w obszarze **galerii składników Web Part** węzeł. W dalszej części tego przewodnika napiszesz kod, który kojarzy tych ikon z węzłów.  
  
#### <a name="to-create-icons-for-the-nodes"></a>Aby utworzyć ikony dla węzłów  
  
1.  W **projektanta projektu** WebPartNodeExtension projektu, wybierz **zasobów** kartę.  
  
2.  Wybierz łącze **ten projekt nie zawiera domyślnego pliku zasobów. Kliknij tutaj, aby go utworzyć.**  
  
     Program Visual Studio tworzy plik zasobów i otwiera go w projektancie.  
  
3.  W górnej części projektanta, wybierz strzałkę znajdującą się na **Dodaj zasób** menu polecenia, a następnie wybierz **dodać nową ikonę**.  
  
4.  Wprowadź **WebPartsNode** nowe ikony nazwę, a następnie wybierz **Dodaj** przycisku.  
  
     Nowa ikona otwiera się w **edytora obrazów**.  
  
5.  Edytuj ikonę w wersji 16 x 16 tak, aby miało projekt, który możesz łatwo rozpoznać.  
  
6.  Otwórz menu skrótów dla wersji 32 x 32, ikony, a następnie wybierz **Usuń typ obrazu**.  
  
7.  Powtórz kroki od 3 do 7, aby dodać drugiej ikony do zasobów projektu i nazwij tę ikonę, **składnika Web Part**.  
  
8.  W **Eksploratora rozwiązań**w **zasobów** folder **WebPartNodeExtension** projektu, wybierz *WebPartsNode.ico*.  
  
9. W **właściwości** otwarte okno **Build Action** , a następnie wybierz **zasób osadzony**.  
  
10. Powtórz ostatnie dwa kroki dla *WebPart.ico*.  
  
## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Dodawanie węzła galerię części sieci web do Eksploratora serwera
 Utwórz klasę, która dodaje nowy **galerii składników Web Part** węzła do każdego węzła w witrynie programu SharePoint. Aby dodać nowy węzeł, klasa implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfejsu. Implementuje ten interfejs, zawsze wtedy, gdy chcesz rozszerzyć istniejący węzeł w zachowanie **Eksploratora serwera**, takie jak dodanie nowego węzła podrzędnego do węzła.  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Aby dodać węzeł galerię części sieci web do Eksploratora serwera
  
1.  Wklej następujący kod do **SiteNodeExtension** plik kodu dla **WebPartNodeExtension** projektu.  
  
    > [!NOTE]  
    >  Po dodaniu tego kodu, projekt będzie miał pewne błędy kompilacji. Te błędy znikną po dodaniu kodu w dalszych krokach.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="define-a-node-type-that-represents-a-web-part"></a>Zdefiniuj typ węzła, który reprezentuje składnik web part
 Utwórz klasę, która definiuje nowy typ węzła, który reprezentuje składnik Web Part. Program Visual Studio używa tego nowego typu węzła do wyświetlania węzłów podrzędnych pod **galerii składników Web Part** węzła. Każdy z tych węzłów podrzędnych reprezentuje pojedynczy składnik Web Part w witrynie programu SharePoint.  
  
 Aby zdefiniować nowego typu węzła, klasa implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfejsu. Implementuje ten interfejs, zawsze wtedy, gdy chcesz zdefiniować nowy typ węzła w **Eksploratora serwera**.  
  
#### <a name="to-define-the-web-part-node-type"></a>Aby zdefiniować typ węzła części sieci web
  
1.  Wklej następujący kod do **WebPartNodeTypeProvider** plik kodu dla **WebPartNodeExtension** projektu.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 Na tym etapie w instruktażu, cały kod dla **galerii składników Web Part** węzeł znajduje się teraz w projekcie. Tworzenie **WebPartNodeExtension** projektu, aby upewnić się, że kompiluje bez błędów.  
  
#### <a name="to-build-the-project"></a>Aby skompilować projekt  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **WebPartNodeExtension** projektu, a następnie wybierz **kompilacji**.  
  
## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Utwórz pakiet VSIX, aby wdrożyć rozszerzenie
 Aby wdrożyć rozszerzenie, należy użyć projektu VSIX w rozwiązaniu Aby utworzyć pakiet VSIX. Najpierw należy skonfigurować pakiet VSIX modyfikując plik source.extension.vsixmanifest, który znajduje się w projekcie. Następnie należy utworzyć pakiet VSIX przez utworzenie rozwiązania.  
  
#### <a name="to-configure-the-vsix-package"></a>Aby skonfigurować pakiet VSIX  
  
1.  W **Eksploratora rozwiązań**w **WebPartNode** otwarty projekt **source.extension.vsixmanifest** plik w edytorze manifestu.  
  
     Plik source.extension.vsixmanifest jest podstawą dla pliku extension.vsixmanifest, które wymagają wszystkie pakiety VSIX. Aby uzyskać więcej informacji na temat tego pliku, zobacz [odwołania 1.0 schematu rozszerzenia VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  W **nazwa produktu** wprowadź **węzła galerię części sieci Web w Eksploratorze serwera**.  
  
3.  W **Autor** wprowadź **Contoso**.  
  
4.  W **opis** wprowadź **dodaje niestandardowy węzeł galerii składników Web Part do węzła połączeń SharePoint w Eksploratorze serwera**.  
  
5.  Na **zasoby** karta w edytorze wybierz **nowy** przycisku.  
  
6.  W **Dodaj nowy zasób** dialogowym **typu** wybierz **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Ta wartość odpowiada `MefComponent` elementu w pliku extension.vsixmanifest. Ten element Określa nazwę zestawu rozszerzeń w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MEFComponent — Element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
7.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
8.  W **projektu** wybierz **WebPartNodeExtension**, a następnie wybierz **OK** przycisku.  
  
9. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**, a następnie upewnij się, że rozwiązanie kompiluje bez błędów.  
  
10. Upewnij się, że folder wyjściowy kompilacji dla projektu WebPartNode zawiera teraz plik WebPartNode.vsix.  
  
     Domyślnie folderem wyjściowym kompilacji jest... folderze \bin\Debug w folderze, który zawiera plik projektu.  
  
## <a name="test-the-extension"></a>Testowanie rozszerzenia
 Teraz można przystąpić do testowania nowego **galerii składników Web Part** w węźle **Eksploratora serwera**. Po pierwsze uruchom debugowanie projektu rozszerzenia w eksperymentalnym wystąpieniu programu Visual Studio. Następnie użyj nowego **składników Web Part** węzła w doświadczalnym wystąpieniu programu Visual Studio.  
  
#### <a name="to-start-debugging-the-extension"></a>Aby rozpocząć debugowanie rozszerzenia  
  
1.  Uruchom program Visual Studio przy użyciu poświadczeń administracyjnych, a następnie otwórz **WebPartNode** rozwiązania.  
  
2.  W projekcie WebPartNodeExtension Otwórz **SiteNodeExtension** plik kodu, a następnie Dodaj punkt przerwania do pierwszej linii kodu w `NodeChildrenRequested` i `CreateWebPartNodes` metody.  
  
3.  Wybierz **F5** klawisz, aby rozpocząć debugowanie.  
  
     Visual Studio instaluje rozszerzenia do %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web część galerii węzła Rozszerzenia dla serwera Explorer\1.0 i uruchamia doświadczalne wystąpienie programu Visual Studio. Element projektu będzie testu, w tym wystąpieniu programu Visual Studio.  
  
#### <a name="to-test-the-extension"></a>Aby przetestować rozszerzenie  
  
1.  W doświadczalnym wystąpieniu programu Visual Studio, na pasku menu wybierz **widoku** > **Eksploratora serwera**.  
  
2.  Sprawdź, czy witryna programu SharePoint chcesz używać do testowania jest wyświetlana w obszarze **połączeń SharePoint** w węźle **Eksploratora serwera**. Jeśli nie ma na liście, wykonaj następujące czynności:  
  
    1.  Otwórz menu skrótów dla **połączeń SharePoint**, a następnie wybierz **Dodaj połączenie**.  
  
    2.  W **Dodawanie połączenia programu SharePoint** okna dialogowego wprowadź adres URL witryny programu SharePoint, do którego chcesz połączyć, a następnie wybierz **OK** przycisku.  
  
         Aby określić witrynę programu SharePoint na komputerze deweloperskim, wpisz **http://localhost**.  
  
3.  Rozwiń węzeł połączenia lokacji (która zawiera adres URL witryny), a następnie rozwiń węzeł lokacji podrzędnej (na przykład **witryny zespołu**).  
  
4.  Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkcie przerwania, który wcześniej w ustawieniu `NodeChildrenRequested` metody, a następnie wybierz **F5** klawisz, aby kontynuować debugowanie projektu.  
  
5.  W doświadczalnym wystąpieniu programu Visual Studio, rozwiń **galerii składników Web Part** węzła, który pojawia się w węźle w lokacji najwyższego poziomu.  
  
6.  Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkcie przerwania, który wcześniej w ustawieniu `CreateWebPartNodes` metody, a następnie wybierz **F5** klawisz, aby kontynuować debugowanie projektu.  
  
7.  W doświadczalnym wystąpieniu programu Visual Studio, sprawdź, czy wszystkie składniki Web Part w podłączonej lokacji są wyświetlane w obszarze **galerii składników Web Part** w węźle **Eksploratora serwera**.  
  
8.  Otwórz menu skrótów dla składnika Web Part, a następnie wybierz **właściwości**.  
  
9. W **właściwości** okna, sprawdź, czy są wyświetlane szczegółowe informacje o składniku Web Part.  
  
10. W **Eksploratora serwera**, otwórz menu skrótów dla tego samego składnika Web Part, a następnie wybierz **Wyświetl komunikat**.  
  
     W wyświetlonym oknie komunikatu wybierz **OK** przycisku.  
  
## <a name="uninstall-the-extension-from-visual-studio"></a>Odinstaluj rozszerzenie z programu Visual Studio
 Po zakończeniu badania rozszerzenia, należy go odinstalować za pomocą programu Visual Studio.  
  
#### <a name="to-uninstall-the-extension"></a>Aby odinstalować rozszerzenie  
  
1.  W doświadczalnym wystąpieniu programu Visual Studio, na pasku menu wybierz **narzędzia** > **rozszerzenia i aktualizacje**.  
  
     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.  
  
2.  Na liście rozszerzeń wybierz **węzła galerię części sieci Web w Eksploratorze serwera**, a następnie wybierz **Odinstaluj** przycisku.  
  
3.  W oknie dialogowym wybierz **tak** przycisku.  
  
4.  Wybierz **Uruchom ponownie teraz** przycisk, aby ukończyć dezinstalację.  
  
     Element projektu również zostanie odinstalowana.  
  
5.  Zamknij oba wystąpienia programu Visual Studio (wystąpienie doświadczalne i wystąpienie programu Visual Studio, w którym rozwiązanie WebPartNode jest otwarty).  
  
## <a name="see-also"></a>Zobacz także
 [Wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Przewodnik: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons)   
 [Tworzenie ikony lub innego obrazu &#40;edytor obrazów dla ikon&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)