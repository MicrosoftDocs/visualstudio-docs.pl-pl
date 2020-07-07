---
title: 'Przewodnik: Tworzenie rozszerzenia projektu SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5df10e2da9e6b4c31894dce0669e9aa0e580b92f
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015071"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>Przewodnik: Tworzenie rozszerzenia projektu SharePoint
  W tym instruktażu pokazano, jak utworzyć rozszerzenie dla projektów programu SharePoint. Możesz użyć rozszerzenia projektu, aby odpowiedzieć na zdarzenia na poziomie projektu, takie jak w przypadku dodania, usunięcia lub zmiany nazwy projektu. Możesz również dodać właściwości niestandardowe lub odpowiedzieć, gdy zmieni się wartość właściwości. W przeciwieństwie do rozszerzeń elementu projektu, rozszerzenia projektu nie mogą być skojarzone z konkretnym typem projektu programu SharePoint. Podczas tworzenia rozszerzenia projektu rozszerzenie jest ładowane, gdy dowolny rodzaj projektu programu SharePoint jest otwarty w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 W tym instruktażu utworzysz niestandardową Właściwość logiczną, która jest dodawana do dowolnego projektu programu SharePoint utworzonego w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Po ustawieniu na **wartość true**Nowa właściwość dodaje lub mapuje folder zasobów obrazów do projektu. Po ustawieniu na **wartość false**folder images jest usuwany, jeśli istnieje. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie mapowanych folderów](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 W tym instruktażu przedstawiono następujące zadania:

- Tworzenie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenia dla projektów programu SharePoint, które wykonuje następujące czynności:

  - Dodaje niestandardową właściwość projektu do okno Właściwości. Właściwość ma zastosowanie do dowolnego projektu programu SharePoint.

  - Używa modelu obiektów projektu programu SharePoint w celu dodania zamapowanego folderu do projektu.

  - Używa [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modelu obiektów automatyzacji (DTE) do usuwania zamapowanego folderu z projektu.

- Kompilowanie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) w celu wdrożenia zestawu rozszerzeń właściwości projektu.

- Debugowanie i testowanie właściwości projektu.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten przewodnik, potrzebne są następujące składniki na komputerze deweloperskim:

- Obsługiwane wersje programów [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] , SharePoint i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- Element [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. W tym instruktażu zostanie użyty szablon **projektu VSIX** w programie, [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] Aby utworzyć pakiet VSIX do wdrożenia rozszerzenia właściwości projektu. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzającą narzędzia programu SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

## <a name="create-the-projects"></a>Tworzenie projektów
 Aby ukończyć ten Instruktaż, należy utworzyć dwa projekty:

- Projekt VSIX, aby utworzyć pakiet VSIX do wdrożenia rozszerzenia projektu.

- Projekt biblioteki klas implementujący rozszerzenie projektu.

  Rozpocznij przewodnik, tworząc projekty.

#### <a name="to-create-the-vsix-project"></a>Aby utworzyć projekt VSIX

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

3. W oknie dialogowym **Nowy projekt** rozwiń węzły **Visual C#** lub **Visual Basic** , a następnie wybierz węzeł **rozszerzalności** .

    > [!NOTE]
    > Ten węzeł jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne we wcześniejszej części tego tematu.

4. W górnej części okna dialogowego wybierz pozycję **.NET Framework 4,5** na liście wersji .NET Framework, a następnie wybierz szablon **projektu VSIX** .

5. W polu **Nazwa** wprowadź **ProjectExtensionPackage**, a następnie wybierz przycisk **OK** .

     Projekt **ProjectExtensionPackage** pojawia się w **Eksplorator rozwiązań**.

#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła rozwiązanie, wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual C#** lub **Visual Basic** , a następnie wybierz pozycję **Windows**.

3. W górnej części okna dialogowego wybierz pozycję **.NET Framework 4,5** na liście wersji .NET Framework, a następnie wybierz szablon projektu **Biblioteka klas** .

4. W polu **Nazwa** wprowadź **elementu ProjectExtension**, a następnie wybierz przycisk **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dodaje projekt **elementu ProjectExtension** do rozwiązania i otwiera domyślny plik kodu Class1.

5. Usuń plik kodu Class1 z projektu.

## <a name="configure-the-project"></a>Konfigurowanie projektu
 Przed napisaniem kodu w celu utworzenia rozszerzenia projektu, Dodaj pliki kodu i odwołania do zestawu do projektu rozszerzenia.

#### <a name="to-configure-the-project"></a>Aby skonfigurować projekt

1. Dodaj plik kodu o nazwie **CustomProperty** do projektu elementu ProjectExtension.

2. Otwórz menu skrótów dla projektu **elementu ProjectExtension** , a następnie wybierz **Dodaj odwołanie**.

3. W oknie dialogowym **Menedżer odwołań — CustomProperty** wybierz węzeł **Framework** , a następnie zaznacz pole wyboru obok zestawów System. ComponentModel. kompozycji i system. Windows. Forms.

4. Wybierz węzeł **rozszerzenia** , zaznacz pole wyboru obok zestawów Microsoft. VisualStudio. SharePoint i EnvDTE, a następnie wybierz przycisk **OK** .

5. W **Eksplorator rozwiązań**, w folderze **References** dla projektu **elementu ProjectExtension** , wybierz **EnvDTE**.

6. W oknie **Właściwości** Zmień właściwość **Osadź typy** współdziałania na **wartość false**.

## <a name="define-the-new-sharepoint-project-property"></a>Zdefiniuj nową właściwość projektu programu SharePoint
 Utwórz klasę, która definiuje rozszerzenie projektu i zachowanie nowej właściwości projektu. Aby zdefiniować nowe rozszerzenie projektu, Klasa implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfejs. Zaimplementuj ten interfejs, gdy chcesz zdefiniować rozszerzenie dla projektu programu SharePoint. Należy również dodać <xref:System.ComponentModel.Composition.ExportAttribute> do klasy. Ten atrybut umożliwia [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] odnajdywanie i ładowanie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementacji. Przekaż <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Typ do konstruktora atrybutu.

#### <a name="to-define-the-new-sharepoint-project-property"></a>Aby zdefiniować nową właściwość projektu programu SharePoint

1. Wklej następujący kod do pliku kodu CustomProperty.

     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]

## <a name="build-the-solution"></a>Kompilowanie rozwiązania
 Następnie Skompiluj rozwiązanie, aby upewnić się, że kompiluje się bez błędów.

#### <a name="to-build-the-solution"></a>Aby skompilować rozwiązanie

1. Na pasku menu wybierz polecenie **Kompiluj**  >  **kompilację rozwiązania**.

## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>Tworzenie pakietu VSIX w celu wdrożenia rozszerzenia właściwości projektu
 Aby wdrożyć rozszerzenie projektu, należy użyć projektu VSIX w rozwiązaniu, aby utworzyć pakiet VSIX. Najpierw skonfiguruj pakiet VSIX, modyfikując plik source. Extension. vsixmanifest, który jest zawarty w projekcie VSIX. Następnie Utwórz pakiet VSIX, tworząc rozwiązanie.

#### <a name="to-configure-and-create-the-vsix-package"></a>Aby skonfigurować i utworzyć pakiet VSIX

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla pliku source. Extension. vsixmanifest, a następnie wybierz przycisk **Otwórz** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]otwiera plik w Projektancie manifestów. Informacje wyświetlane na karcie **metadane** są również wyświetlane w obszarze **rozszerzenia i aktualizacje**. Wszystkie pakiety VSIX wymagają pliku Extension. vsixmanifest. Aby uzyskać więcej informacji na temat tego pliku, zobacz [Dokumentacja schematu rozszerzenia VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. W polu **Nazwa produktu** wprowadź **niestandardową właściwość projektu**.

3. W polu **autor** wprowadź wartość **contoso**.

4. W polu **Opis** wprowadź **niestandardową właściwość projektu programu SharePoint, która przełącza mapowanie folderu zasobów obrazów do projektu**.

5. Wybierz kartę **zasoby** , a następnie wybierz przycisk **Nowy** .

     Pojawi się okno dialogowe **Dodaj nowy element zawartości** .

6. Na liście **Typ** wybierz **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Ta wartość odnosi się do `MEFComponent` elementu w pliku Extension. vsixmanifest. Ten element określa nazwę zestawu rozszerzenia w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MefComponent element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Na liście **Źródło** wybierz przycisk opcji **projekt w bieżącym rozwiązaniu** .

8. Na liście **projekt** wybierz pozycję **elementu ProjectExtension**.

     Ta wartość określa nazwę zestawu, który jest kompilowany w projekcie.

9. Wybierz **przycisk OK** , aby zamknąć okno dialogowe **Dodaj nowy element zawartości** .

10. Na pasku menu wybierz kolejno opcje **plik**  >  **Zapisz wszystko** po zakończeniu, a następnie zamknij projektanta manifestu.

11. Na pasku menu wybierz kompilacja Kompiluj **Build**  >  **rozwiązanie**, a następnie upewnij się, że projekt kompiluje się bez błędów.

12. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **ProjectExtensionPackage** i wybierz polecenie **Otwórz folder w Eksploratorze plików** .

13. W **Eksploratorze plików**Otwórz folder danych wyjściowych kompilacji dla projektu ProjectExtensionPackage, a następnie sprawdź, czy folder zawiera plik o nazwie ProjectExtensionPackage. VSIX.

     Domyślnie folder wyjściowy kompilacji to... folder \bin\Debug w folderze, który zawiera plik projektu.

## <a name="test-the-project-property"></a>Testowanie właściwości projektu
 Teraz można przystąpić do testowania niestandardowej właściwości projektu. Najłatwiej jest debugować i testować nowe rozszerzenie właściwości projektu w eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . To wystąpienie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] jest tworzone podczas uruchamiania programu VSIX lub innego projektu rozszerzalności. Po debugowaniu projektu można zainstalować rozszerzenie w systemie, a następnie kontynuować debugowanie i testowanie go w regularnych wystąpieniach [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Aby debugować i testować rozszerzenie w eksperymentalnym wystąpieniu programu Visual Studio

1. Uruchom ponownie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] z poświadczeniami administracyjnymi, a następnie otwórz rozwiązanie ProjectExtensionPackage.

2. Rozpocznij kompilację debugowania projektu, wybierając klawisz **F5** lub na pasku menu, wybierając **Debuguj**  >  **Rozpocznij debugowanie**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]instaluje rozszerzenie%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Project Property\1.0 i uruchamia eksperymentalne wystąpienie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

3. W eksperymentalnym wystąpieniu programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Utwórz projekt SharePoint dla rozwiązania farmy i użyj wartości domyślnych dla innych wartości w kreatorze.

    1. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

    2. W górnej części okna dialogowego **Nowy projekt** wybierz pozycję **.NET Framework 3,5** na liście wersji .NET Framework.

         Rozszerzenia narzędzi programu SharePoint wymagają funkcji w tej wersji programu [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .

    3. W węźle **Szablony** rozwiń węzeł **Visual C#** lub **Visual Basic** , wybierz węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

    4. Wybierz szablon **projektu programu SharePoint 2010** , a następnie wprowadź **ModuleTest** jako nazwę projektu.

4. W **Eksplorator rozwiązań**wybierz węzeł projektu **ModuleTest** .

     Nowy **folder obrazów mapy** właściwości niestandardowych pojawi się w oknie **Właściwości** z wartością domyślną **false**.

5. Zmień wartość tej właściwości na **true**.

     Folder zasobów obrazów jest dodawany do projektu programu SharePoint.

6. Zmień wartość tej właściwości z powrotem na **false**.

     Jeśli wybierzesz przycisk **tak** w oknie dialogowym **usuwanie obrazów?** folder zasobów obrazy zostanie usunięty z projektu programu SharePoint.

7. Zamknij wystąpienie eksperymentalne [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

## <a name="see-also"></a>Zobacz także
- [Zwiększ projekty programu SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Instrukcje: Dodawanie właściwości do projektów programu SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Konwersja między typami systemu projektu SharePoint a innymi typami projektów programu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Zapisywanie danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi programu SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
