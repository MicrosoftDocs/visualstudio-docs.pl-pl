---
title: Zapewnianie pakowaniu i informacje o wdrożeniu w elementach projektu | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature properties
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
- feature properties [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature receiver
- feature receiver [SharePoint development in Visual Studio]
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 248bf442924ab427b41875272771d2d55708f233
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870078"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>Podaj informacji opakowań i wdrażania w elementach projektu
  Wszystkie elementy projektu programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mają właściwości, które służy do zapewnienia dodatkowych danych, gdy projekt jest wdrażany w programie SharePoint. Właściwości są następujące:  
  
- Właściwości funkcji  
  
- Odbiorcy funkcji  
  
- Odwołania danych wyjściowych projektu  
  
- Wpisy bezpiecznych kontrolek  
  
  Te właściwości są wyświetlane w **właściwości** okna.  
  
## <a name="feature-properties"></a>Właściwości funkcji
 Użyj **właściwości funkcji** właściwości w celu określenia danych, która korzysta z tej funkcji. Dane właściwości funkcji jest zestaw wartości (przechowywanych jako pary klucz/wartość) jest uwzględniany w funkcji podczas wdrażania w programie SharePoint. Po wdrożeniu funkcji wartości właściwości są dostępne w kodzie.  
  
 Po dodaniu funkcji wartości właściwości do elementu projektu, wartość jest dodawana jako element w manifeście funkcji elementu. W projekcie modelu łączności danych biznesowych (BDC) na przykład właściwość funkcji ModelFileName wygląda następująco:  
  
```xml  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 Po ustawieniu wartości właściwości funkcji zostanie dodany jako FeatureProperty — element w projekcie *spdata* pliku. Aby uzyskać informacje na temat uzyskiwania dostępu do właściwości w programie SharePoint, zobacz [klasy SPFeaturePropertyCollection](http://go.microsoft.com/fwlink/?LinkId=177391).  
  
 Funkcja identyczne wartości właściwości z wszystkich elementów projektu są scalane w manifeście funkcji. Jednakże jeśli dwa elementy inny projekt określić ten sam klucz właściwości funkcji z wartościami niezgodny, wystąpienia błędu sprawdzania poprawności.  
  
 Aby dodać właściwości funkcji bezpośrednio do pliku funkcji (*.feature*), wywołanie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] metoda modelu obiektu SharePoint <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>. Możesz użyć tej metody, należy pamiętać, że tę samą regułę o dodawaniu funkcji identyczne wartości właściwości w oknie właściwości funkcji dotyczy także dodać bezpośrednio do pliku funkcji właściwości.  
  
## <a name="feature-receiver"></a>Odbiorca funkcji
 Funkcji odbiorcy są kod wykonywany po wystąpieniu określonego zdarzenia z elementem projektu zawierającym funkcję. Na przykład można zdefiniować funkcji odbiorcy, które są wykonywane po zainstalowaniu, aktywacji lub uaktualnić tę funkcję. Jednym sposobem dodania odbiorcę funkcji jest dodanie go bezpośrednio do funkcji, zgodnie z opisem w [instruktażu: Dodawanie odbiorców zdarzeń funkcji](../sharepoint/walkthrough-add-feature-event-receivers.md). Innym sposobem jest odwołanie Nazwa klasy odbiorcy funkcji i zestawu w **odbiorcy funkcji** właściwości.  
  
### <a name="direct-method"></a>Metoda bezpośrednia
 Po dodaniu odbiorcę funkcji z funkcją bezpośrednio, plik kodu jest umieszczony pod **funkcji** węzła w Eksploratorze rozwiązań. W przypadku tworzenia rozwiązania programu SharePoint, kod kompiluje się do zestawu i wdrażania do programu SharePoint. Domyślnie właściwości funkcji **zestaw odbiorcy** i **Klasa odbiorcy** odwoływać się do nazwy klasy i zestawu.  
  
### <a name="reference-method"></a>reference — Metoda
 Innym sposobem dodania odbiorcę funkcji polega na użyciu **odbiorcy funkcji** właściwości elementu projektu, aby odwołać zestaw odbiorcy funkcji. Wartość właściwości odbiorcy funkcji ma dwie właściwości: **Zestaw** i **Nazwa klasy**. Zestaw, należy użyć jej w pełni kwalifikowaną, nazwę "strong" i nazwa klasy musi być pełna nazwa typu. Aby uzyskać więcej informacji, zobacz [zestawy Strong-Named](http://go.microsoft.com/fwlink/?LinkID=169573). Po wdrożeniu rozwiązania programu SharePoint, funkcja używa odbiorcy funkcji odwołania do obsługi zdarzeń funkcji.  
  
 Rozwiązania kompilowania, funkcji odbiorcy wartości właściwości w funkcji oraz jego projekty scalone razem można ustawić atrybuty ReceiverAssembly i ReceiverClass element funkcji w manifeście funkcji rozwiązania programu SharePoint (*.wsp* ) pliku. W związku z tym jeśli zestawu i nazwa klasy wartości właściwości elementu projektu i funkcji są określone oba wartości właściwości elementu i funkcji projektu muszą być zgodne. Jeśli wartości nie są zgodne, otrzymasz błąd sprawdzania poprawności. Jeśli chcesz, aby element projektu odwołanie zestaw odbiorcy funkcji, innej niż ta, do jego funkcja używa, przenieś go do innej funkcji.  
  
 Jeśli odwołujesz się zestaw odbiorcy funkcji, która nie znajduje się już na serwerze, należy również uwzględnić w samym pliku zestawu w pakiecie; [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nie powoduje dodania dla Ciebie. Podczas wdrażania funkcji plik zestawu jest kopiowany do tego systemu [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] lub folder Bin w katalogu fizycznym programu SharePoint. Aby uzyskać więcej informacji, zobacz jak: [Instrukcje: Dodawanie i usuwanie zestawów dodatkowych](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Aby uzyskać więcej informacji na temat funkcji odbiorcy, zobacz [odbiorcę zdarzeń funkcji](http://go.microsoft.com/fwlink/?LinkID=169574) i [zdarzeń funkcji](http://go.microsoft.com/fwlink/?LinkID=169575).  
  
## <a name="project-output-references"></a>Odwołania danych wyjściowych projektu
 Właściwości odwołania danych wyjściowych projektu określa zależność, takich jak zestaw, który element projektu musi zostać uruchomiony. Na przykład załóżmy, że rozwiązanie ma projektu usługi łączności danych biznesowych i klasy projektu. Jeśli projekt BDC ma zależność od zestawu, które znajdują się dane wyjściowe w projekcie klasy, można się odwołać zestawu we właściwości odwołania do projektu danych wyjściowych projektu usługi łączności danych biznesowych. Gdy projekt BDC jest spakowany, zależnego zestawu znajduje się w pakiecie.  
  
 Odwołania danych wyjściowych projektu są zazwyczaj zestawy, ale w niektórych przypadkach (na przykład projekty Silverlight) mogą być inne typy plików.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Dodawanie odwołania wyjścia projektu](../sharepoint/how-to-add-a-project-output-reference.md).  
  
## <a name="safe-control-entries"></a>Wpisy bezpiecznych kontrolek
 Program SharePoint udostępnia mechanizm zabezpieczeń o nazwie wpisy kontroli bezpiecznego, aby ograniczyć dostęp niezaufanym użytkownikom na niektórych kontrolek. Zgodnie z projektem programu SharePoint pozwala niezaufanym użytkownikom na przekazywanie i tworzenie stron ASPX na serwerze programu SharePoint. Aby uniemożliwić dodawanie niebezpieczny kod do stron ASPX tych użytkowników, SharePoint ogranicza ich dostęp do *bezpiecznych kontrolek*. Bezpieczne kontrolki są formantów ASPX i składniki Web Part oznaczone jako bezpieczne i który może służyć przez dowolnego użytkownika w witrynie. Aby uzyskać więcej informacji, zobacz [krok 4: Dodaj składnik Web Part do listy bezpiecznych kontrolek](http://go.microsoft.com/fwlink/?LinkID=171014).  
  
 Każdy element projektu programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ma właściwość o nazwie **wpisy bezpiecznych kontrolek** ma dwie właściwości logiczne: **Bezpieczne** i **zabezpieczony przed skryptami**. Bezpieczne właściwość określa, czy niezaufanym użytkownikom może uzyskiwać dostęp do formantu. Właściwość bezpieczne względem skryptu określa, czy niezaufanym użytkownikom można wyświetlać i zmieniać właściwości formantu.  
  
 Wpisy bezpiecznych kontrolek odwołują się na podstawie zestawu. Dodać wpisy bezpiecznych kontrolek do projektu zespołu, wprowadzając je w elemencie projektu **wpisy bezpiecznych kontrolek** właściwości. Jednak możesz można również dodać wpisy bezpiecznych kontrolek do projektu zestawu za pomocą **zaawansowane** karcie **projektancie pakietu** po dodaniu dodatkowego zestawu do pakietu. Aby uzyskać więcej informacji, zobacz [jak: Oznaczanie kontrolek pojęciem bezpiecznych kontrolek](../sharepoint/how-to-mark-controls-as-safe-controls.md) lub [rejestrowanie zestaw części sieci Web jako bezpiecznej kontrolki](http://go.microsoft.com/fwlink/?LinkID=171013).  
  
### <a name="xml-entries-for-safe-controls"></a>Wpisy XML dla bezpiecznych kontrolek
 Po dodaniu wpisu bezpiecznej kontrolki do elementu projektu lub zestawu projektu, odwołania są zapisywane do manifestu pakietu w następującym formacie:  
  
```xml  
<Assemblies>  
    <Assembly Location="<assembly name>.dll"     
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>  
        <SafeControls>  
            <SafeControl Assembly="<assembly name>.dll" Namespace=  
              "<SharePoint project name>" Safe="<true/false>"     
                TypeName="<control name>"   
                SafeAgainstScript="<true/false>" />  
        </SafeControls>  
    </Assembly>  
</Assemblies>  
```  
  
## <a name="see-also"></a>Zobacz także
 [Pakiet rozwiązania i wdrażania SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Użyj modułów, aby uwzględnić pliki w rozwiązaniu](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [Rozszerzanie pakowania i wdrażania SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
