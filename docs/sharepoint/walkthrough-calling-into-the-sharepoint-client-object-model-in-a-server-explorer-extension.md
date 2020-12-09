---
title: 'Eksplorator serwera: rozszerzanie węzła połączeń programu SharePoint'
titleSuffix: ''
description: W tym instruktażu zapoznaj się z tematem jak wywołać model obiektów klienta programu SharePoint z rozszerzenia dla węzła połączenia programu SharePoint w Eksplorator serwera.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: c323f05d341af810eecafae43e8d04d3cba29054
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913948"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>Przewodnik: wywoływanie modelu obiektów klienta programu SharePoint w rozszerzeniu Eksplorator serwera
  W tym instruktażu pokazano, jak wywołać model obiektów klienta programu SharePoint z rozszerzenia dla węzła **połączenia programu SharePoint** w **Eksplorator serwera**. Aby uzyskać więcej informacji o sposobach korzystania z modelu obiektów klienta programu SharePoint, zobacz [Wywoływanie modeli obiektów programu SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

 W tym instruktażu przedstawiono następujące zadania:

- Tworzenie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenia rozszerzającego węzeł **połączeń SharePoint** **Eksplorator serwera** w następujący sposób:

  - Rozszerzenie dodaje węzeł **Galerii składników Web Part** w każdym węźle witryny programu SharePoint w **Eksplorator serwera**. Ten nowy węzeł zawiera węzły podrzędne, które reprezentują każdy składnik Web Part w galerii składników Web Part w witrynie.

  - Rozszerzenie definiuje nowy typ węzła, który reprezentuje wystąpienie składnika Web Part. Ten nowy typ węzła jest podstawą dla węzłów podrzędnych w węźle Galeria nowych **składników Web Part** . Nowy typ węzła składnika Web Part wyświetla informacje w oknie **Właściwości** dotyczące składnika Web Part reprezentowanego przez ten węzeł.

- Kompilowanie pakietu rozszerzenia Visual Studio (VSIX) w celu wdrożenia rozszerzenia.

- Debugowanie i testowanie rozszerzenia.

> [!NOTE]
> Rozszerzenie utworzone w tym instruktażu przypomina rozszerzenie utworzone w [przewodniku: rozszerzanie Eksplorator serwera, aby wyświetlić części sieci Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md). W tym instruktażu jest używany model obiektów programu SharePoint Server, ale ten przewodnik wykonuje te same zadania przy użyciu modelu obiektów klienta.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten przewodnik, potrzebne są następujące składniki na komputerze deweloperskim:

- Obsługiwane wersje systemu Windows, SharePoint i Visual Studio.

- Zestaw SDK programu Visual Studio. W tym instruktażu zostanie użyty szablon **projektu VSIX** w zestawie SDK w celu utworzenia pakietu VSIX do wdrożenia rozszerzenia. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzającą narzędzia programu SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

Znajomość następujących pojęć jest pomocna, ale nie jest wymagana, aby ukończyć Przewodnik:

- Przy użyciu modelu obiektów klienta programu SharePoint. Aby uzyskać więcej informacji, zobacz [model obiektów klienta zarządzanego](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14)).

- Części sieci Web w programie SharePoint. Aby uzyskać więcej informacji, zobacz [składniki Web Part przegląd](/previous-versions/office/ms432401(v=office.14)).

## <a name="create-the-projects"></a>Tworzenie projektów
 Aby ukończyć ten Instruktaż, należy utworzyć dwa projekty:

- Projekt VSIX, aby utworzyć pakiet VSIX do wdrożenia rozszerzenia **Eksplorator serwera** .

- Projekt biblioteki klas implementujący rozszerzenie **Eksplorator serwera** .

  Rozpocznij przewodnik, tworząc projekty.

#### <a name="to-create-the-vsix-project"></a>Aby utworzyć projekt VSIX

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

3. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual C#** lub **Visual Basic** , a następnie wybierz pozycję **rozszerzalność**.

    > [!NOTE]
    > Węzeł **rozszerzalności** jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne we wcześniejszej części tego tematu.

4. W górnej części okna dialogowego wybierz pozycję **.NET Framework 4,5** na liście wersji .NET Framework.

     Rozszerzenia narzędzi programu SharePoint wymagają funkcji w tej wersji .NET Framework.

5. Wybierz szablon **projektu VSIX** .

6. W polu **Nazwa** wpisz **WebPartNode**, a następnie wybierz przycisk **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje projekt **WebPartNode** do **Eksplorator rozwiązań**.

#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia

1. W **Eksplorator rozwiązań** Otwórz menu skrótów dla węzła rozwiązanie, wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

2. W oknie dialogowym  **Nowy projekt** rozwiń węzeł **Visual C#** lub **Visual Basic** , a następnie wybierz pozycję **Windows**.

3. W górnej części okna dialogowego wybierz pozycję **.NET Framework 4,5** na liście wersji .NET Framework.

4. Na liście szablonów projektu wybierz pozycję **Biblioteka klas**.

5. W polu **Nazwa** wprowadź **WebPartNodeExtension**, a następnie wybierz przycisk **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje projekt **WebPartNodeExtension** do rozwiązania i otwiera domyślny plik kodu Class1.

6. Usuń plik kodu Class1 z projektu.

## <a name="configure-the-extension-project"></a>Skonfiguruj projekt rozszerzenia
 Przed napisaniem kodu w celu utworzenia rozszerzenia należy dodać pliki kodu i odwołania do zestawu do projektu i należy zaktualizować domyślną przestrzeń nazw.

#### <a name="to-configure-the-project"></a>Aby skonfigurować projekt

1. W projekcie **WebPartNodeExtension** Dodaj dwa pliki kodu o nazwach SiteNodeExtension i WebPartNodeTypeProvider.

2. Otwórz menu skrótów dla projektu WebPartNodeExtension, a następnie wybierz **Dodaj odwołanie**.

3. W oknie dialogowym **Menedżer odwołań — WebPartNodeExtension** wybierz węzeł **Framework** , a następnie zaznacz pola wyboru dla zestawów System. ComponentModel. kompozycji i system. Windows. Forms.

4. Wybierz węzeł **rozszerzenia** , zaznacz pole wyboru dla każdego z następujących zestawów, a następnie wybierz przycisk **OK** :

    - Microsoft. SharePoint. Client

    - Microsoft. SharePoint. Client. Runtime

    - Microsoft. VisualStudio. SharePoint

5. Otwórz menu skrótów dla projektu **WebPartNodeExtension** , a następnie wybierz polecenie **Właściwości**.

     Zostanie otwarty **Projektant projektu** .

6. Wybierz kartę **aplikacja** .

7. W polu **domyślny obszar nazw** (C#) lub **głównej przestrzeni nazw** (Visual Basic) wprowadź **ServerExplorer. SharePointConnections. WebPartNode**.

## <a name="create-icons-for-the-new-nodes"></a>Utwórz ikony dla nowych węzłów
 Utwórz dwie ikony rozszerzenia **Eksplorator serwera** : ikona nowego węzła **Galerii składników Web Part** oraz inna ikona dla każdego podrzędnego węzła składnika Web Part w węźle **Galeria składników Web Part** . W dalszej części tego przewodnika napiszesz kod, który kojarzy te ikony z węzłami.

#### <a name="to-create-icons-for-the-nodes"></a>Aby utworzyć ikony dla węzłów

1. W **projektancie projektu** dla projektu WebPartNodeExtension, wybierz kartę **zasoby** .

2. Wybierz łącze **ten projekt nie zawiera domyślnego pliku zasobów. Kliknij tutaj, aby go utworzyć.**

     Program Visual Studio tworzy plik zasobów i otwiera go w projektancie.

3. W górnej części okna projektanta wybierz strzałkę w menu **Dodaj zasób** , a następnie wybierz polecenie **Dodaj nową ikonę**.

4. Wprowadź **WebPartsNode** dla nowej nazwy ikony, a następnie wybierz przycisk **Dodaj** .

     Nowa ikona zostanie otwarta w **Edytorze obrazu**.

5. Edytuj wersję 16x16 ikon, aby mieć projekt, który można łatwo rozpoznać.

6. Otwórz menu skrótów dla wersji 32x32 ikony, a następnie wybierz polecenie **Usuń typ obrazu**.

7. Powtórz kroki od 3 do 7, aby dodać drugą ikonę do zasobów projektu i nazwać ten **składnik**.

8. W **Eksplorator rozwiązań** w folderze **resources** projektu **WebPartNodeExtension** wybierz *WebPartsNode. ico*.

9. W oknie **Właściwości** Otwórz listę **Akcja kompilacji** , a następnie wybierz pozycję **zasób osadzony**.

10. Powtórz ostatnie dwa kroki dla elementu *WebPart. ico*.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Dodaj węzeł Galerii składników Web Part do Eksplorator serwera
 Utwórz klasę, która dodaje nowy węzeł **Galerii składników Web Part** do każdego węzła witryny programu SharePoint. Aby dodać nowy węzeł, Klasa implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfejs. Zaimplementuj ten interfejs w każdym przypadku, gdy chcesz zwiększyć zachowanie istniejącego węzła w **Eksplorator serwera**, na przykład dodając nowy węzeł podrzędny do węzła.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Aby dodać węzeł Galerii składników Web Part do Eksplorator serwera

1. Wklej następujący kod do pliku kodu **SiteNodeExtension** dla projektu **WebPartNodeExtension** .

    > [!NOTE]
    > Po dodaniu tego kodu projekt będzie zawierał błędy kompilacji. Te błędy zostaną odrzucone po dodaniu kodu w dalszych krokach.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>Zdefiniuj typ węzła, który reprezentuje część sieci Web
 Utwórz klasę, która definiuje nowy typ węzła, który reprezentuje składnik Web Part. Program Visual Studio używa tego nowego typu węzła do wyświetlania węzłów podrzędnych w węźle **Galeria składników Web Part** . Każdy z tych węzłów podrzędnych reprezentuje pojedynczy składnik Web Part w witrynie programu SharePoint.

 Aby zdefiniować nowy typ węzła, Klasa implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfejs. Zaimplementuj ten interfejs w każdym przypadku, gdy chcesz zdefiniować nowy typ węzła w **Eksplorator serwera**.

#### <a name="to-define-the-web-part-node-type"></a>Aby zdefiniować typ węzła składnika Web Part

1. Wklej następujący kod do pliku kodu **WebPartNodeTypeProvider** dla projektu **WebPartNodeExtension** .

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]

## <a name="checkpoint"></a>Punkt kontrolny
 W tym momencie w przewodniku cały kod węzła **Galerii składników Web Part** znajduje się teraz w projekcie. Utwórz projekt **WebPartNodeExtension** , aby upewnić się, że kompiluje się bez błędów.

#### <a name="to-build-the-project"></a>Aby skompilować projekt

1. W **Eksplorator rozwiązań** Otwórz menu skrótów dla projektu **WebPartNodeExtension** , a następnie wybierz polecenie **Kompiluj**.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Tworzenie pakietu VSIX w celu wdrożenia rozszerzenia
 Aby wdrożyć rozszerzenie, użyj projektu VSIX w rozwiązaniu, aby utworzyć pakiet VSIX. Najpierw skonfiguruj pakiet VSIX, modyfikując plik source. Extension. vsixmanifest, który znajduje się w projekcie. Następnie Utwórz pakiet VSIX, tworząc rozwiązanie.

#### <a name="to-configure-the-vsix-package"></a>Aby skonfigurować pakiet VSIX

1. W **Eksplorator rozwiązań**, w projekcie **WebPartNode** , Otwórz plik **source. Extension. vsixmanifest** w edytorze manifestu.

     Plik source. Extension. vsixmanifest jest podstawą dla pliku Extension. vsixmanifest, który wymaga wszystkich pakietów VSIX. Aby uzyskać więcej informacji na temat tego pliku, zobacz [Dokumentacja schematu rozszerzenia VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. W polu **Nazwa produktu** wprowadź **węzeł Galerii składników Web Part dla Eksplorator serwera**.

3. W polu **autor** wprowadź wartość **contoso**.

4. W polu **Opis** wprowadź polecenie **dodaje niestandardowy węzeł Galerii składników Web Part do węzła połączenia programu SharePoint w Eksplorator serwera**.

5. Na karcie **zasoby** edytora wybierz przycisk **Nowy** .

6. W oknie dialogowym **Dodaj nowy zasób** , na liście **typ** wybierz **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Ta wartość odnosi się do `MefComponent` elementu w pliku Extension. vsixmanifest. Ten element określa nazwę zestawu rozszerzenia w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MefComponent element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Z listy **Źródło** wybierz **projekt w bieżącym rozwiązaniu**.

8. Na liście **projekt** wybierz pozycję **WebPartNodeExtension**, a następnie wybierz przycisk **OK** .

9. Na pasku menu wybierz kompilacja Kompiluj **Build**  >  **rozwiązanie**, a następnie upewnij się, że rozwiązanie kompiluje się bez błędów.

10. Upewnij się, że folder danych wyjściowych kompilacji dla projektu WebPartNode zawiera teraz plik WebPartNode. VSIX.

     Domyślnie folder wyjściowy kompilacji to... folder \bin\Debug w folderze, który zawiera plik projektu.

## <a name="test-the-extension"></a>Testowanie rozszerzenia
 Teraz można przystąpić do testowania nowego węzła **Galerii składników Web Part** w **Eksplorator serwera**. Najpierw Rozpocznij debugowanie projektu rozszerzenia w eksperymentalnym wystąpieniu programu Visual Studio. Następnie użyj nowego węzła **składniki Web Part** w eksperymentalnym wystąpieniu programu Visual Studio.

#### <a name="to-start-debugging-the-extension"></a>Aby rozpocząć debugowanie rozszerzenia

1. Uruchom ponownie program Visual Studio z poświadczeniami administracyjnymi, a następnie otwórz rozwiązanie **WebPartNode** .

2. W projekcie WebPartNodeExtension Otwórz plik kodu **SiteNodeExtension** , a następnie Dodaj punkt przerwania do pierwszego wiersza kodu w `NodeChildrenRequested` `CreateWebPartNodes` metodach i.

3. Wybierz klawisz **F5** , aby rozpocząć debugowanie.

     Program Visual Studio instaluje rozszerzenie rozszerzenia węzła galerii części%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web dla serwera Explorer\1.0 i uruchamia eksperymentalne wystąpienie programu Visual Studio. Testujesz element projektu w tym wystąpieniu programu Visual Studio.

#### <a name="to-test-the-extension"></a>Aby przetestować rozszerzenie

1. W eksperymentalnym wystąpieniu programu Visual Studio na pasku menu wybierz pozycję **Wyświetl**  >  **Eksplorator serwera**.

2. Sprawdź, czy witryna programu SharePoint, która ma być używana do testowania, jest wyświetlana w węźle **połączenia programu SharePoint** w **Eksplorator serwera**. Jeśli nie ma go na liście, wykonaj następujące kroki:

    1. Otwórz menu skrótów dla **połączeń programu SharePoint**, a następnie wybierz polecenie **Dodaj połączenie**.

    2. W oknie dialogowym **Dodawanie połączenia programu SharePoint** wprowadź adres URL witryny programu SharePoint, z którą chcesz nawiązać połączenie, a następnie wybierz przycisk **OK** .

         Aby określić witrynę programu SharePoint na komputerze deweloperskim, wpisz polecenie **http://localhost** .

3. Rozwiń węzeł połączenie lokacji (w którym jest wyświetlany adres URL witryny), a następnie rozwiń węzeł lokacji podrzędnej (na przykład **Witryna zespołu**).

4. Sprawdź, czy kod w innym wystąpieniu programu Visual Studio jest zatrzymany w punkcie przerwania, który został ustawiony we wcześniejszej części `NodeChildrenRequested` metody, a następnie wybierz klawisz **F5** , aby kontynuować debugowanie projektu.

5. W eksperymentalnym wystąpieniu programu Visual Studio rozwiń węzeł **Galeria składników Web Part** , który jest wyświetlany w węźle lokacja najwyższego poziomu.

6. Sprawdź, czy kod w innym wystąpieniu programu Visual Studio jest zatrzymany w punkcie przerwania, który został ustawiony we wcześniejszej części `CreateWebPartNodes` metody, a następnie wybierz klawisz **F5** , aby kontynuować debugowanie projektu.

7. W eksperymentalnym wystąpieniu programu Visual Studio Sprawdź, czy wszystkie składniki Web Part w połączonej lokacji są wyświetlane w węźle **Galeria składników Web Part** w **Eksplorator serwera**.

8. Otwórz menu skrótów dla składnika Web Part, a następnie wybierz polecenie **Właściwości**.

9. W oknie **Właściwości** Sprawdź, czy są wyświetlane szczegółowe informacje o części sieci Web.

10. W **Eksplorator serwera** Otwórz menu skrótów dla tego samego składnika Web Part, a następnie wybierz polecenie **Wyświetl komunikat**.

     W wyświetlonym oknie komunikatu wybierz przycisk **OK** .

## <a name="uninstall-the-extension-from-visual-studio"></a>Odinstaluj rozszerzenie z programu Visual Studio
 Po zakończeniu testowania rozszerzenia Odinstaluj je z programu Visual Studio.

#### <a name="to-uninstall-the-extension"></a>Aby odinstalować rozszerzenie

1. W eksperymentalnym wystąpieniu programu Visual Studio na pasku menu wybierz kolejno opcje **Narzędzia**  >  **rozszerzenia i aktualizacje**.

     Zostanie otwarte okno dialogowe **rozszerzenia i aktualizacje** .

2. Na liście rozszerzeń wybierz **węzeł Galeria składników Web Part dla Eksplorator serwera**, a następnie wybierz przycisk **Odinstaluj** .

3. W oknie dialogowym, które się pojawi, wybierz przycisk **tak** .

4. Wybierz przycisk **Uruchom ponownie teraz** , aby ukończyć dezinstalację.

     Element projektu również zostanie odinstalowany.

5. Zamknij oba wystąpienia programu Visual Studio (wystąpienie eksperymentalne i wystąpienie programu Visual Studio, w którym jest otwarte rozwiązanie WebPartNode).

## <a name="see-also"></a>Zobacz też
- [Wywoływanie modeli obiektów programu SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Rozwiń węzeł połączenia programu SharePoint w Eksplorator serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Przewodnik: rozszerzona Eksplorator serwera do wyświetlania składników Web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons)
- [Tworzenie ikony lub innego obrazu &#40;Edytor obrazów dla ikon&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)