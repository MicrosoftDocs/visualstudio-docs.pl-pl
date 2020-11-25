---
title: Pakowanie & informacji o wdrożeniu w elementach projektu
description: Dodaj pakowanie i dane wdrożenia w elementach projektu programu SharePoint za pomocą właściwości funkcji, odbiorników funkcji, odwołań do danych wyjściowych projektu i jednostek kontroli bezpiecznego.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f73d8727fb960cf519d368d928aa20cae38ae1a9
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95970475"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>Udostępnianie informacji o pakowaniu i wdrożeniu w elementach projektu
  Wszystkie elementy projektu programu SharePoint w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mają właściwości, których można użyć do dostarczania dodatkowych danych podczas wdrażania projektu w programie SharePoint. Właściwości są następujące:

- Właściwości funkcji

- Odbiorcy funkcji

- Odwołania do danych wyjściowych projektu

- Bezpieczne wpisy kontroli

  Te właściwości są wyświetlane w oknie **Właściwości** .

## <a name="feature-properties"></a>Właściwości funkcji
 Właściwość **właściwości funkcji** służy do określania danych używanych przez funkcję. Dane właściwości funkcji to zbiór wartości (przechowywanych jako pary klucz/wartość), które są dołączone do funkcji podczas wdrażania w programie SharePoint. Po wdrożeniu funkcji można uzyskać dostęp do wartości właściwości w kodzie.

 Po dodaniu wartości właściwości funkcji do elementu projektu, wartość jest dodawana jako element w manifeście funkcji elementu. Na przykład w projekcie modelu łączności danych biznesowych (BDC) Właściwość funkcji ModelFileName jest wyświetlana jako:

```xml
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />
```

 Po ustawieniu wartości właściwości funkcji jest ona dodawana jako element FeatureProperty w pliku *spdata* projektu. Aby uzyskać informacje o uzyskiwaniu dostępu do właściwości w programie SharePoint, zobacz [Klasa SPFeaturePropertyCollection](/previous-versions/office/sharepoint-server/ms461895(v=office.15)).

 Identyczne wartości właściwości funkcji ze wszystkich elementów projektu są scalane razem w manifeście funkcji. Jeśli jednak dwa różne elementy projektu określają ten sam klucz właściwości funkcji z niezgodnymi wartościami, wystąpi błąd walidacji.

 Aby dodać właściwości funkcji bezpośrednio do pliku funkcji (*. feature*), wywołaj [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] metodę modelu obiektów programu SharePoint <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A> . W przypadku użycia tej metody należy pamiętać, że ta sama reguła dotycząca dodawania identycznych wartości właściwości funkcji we właściwościach funkcji ma również zastosowanie do właściwości dodanych bezpośrednio do pliku funkcji.

## <a name="feature-receiver"></a>Odbiorca funkcji
 Odbiorniki funkcji to kod, który jest wykonywany w przypadku wystąpienia określonych zdarzeń do funkcji zawierającej element projektu. Można na przykład zdefiniować odbiorniki funkcji, które są wykonywane, gdy ta funkcja zostanie zainstalowana, aktywowana lub uaktualniona. Jednym ze sposobów dodawania odbiorcy funkcji jest dodanie go bezpośrednio do funkcji, zgodnie z opisem w [przewodniku: Dodawanie odbiorników zdarzeń funkcji](../sharepoint/walkthrough-add-feature-event-receivers.md). Innym sposobem jest odwołanie się do nazwy klasy odbiorcy funkcji i zestawu we właściwości **odbiorcy funkcji** .

### <a name="direct-method"></a>Metoda bezpośrednia
 Po dodaniu odbiorcy funkcji bezpośrednio do funkcji plik kodu jest umieszczany w węźle **funkcji** w Eksplorator rozwiązań. Podczas kompilowania rozwiązania programu SharePoint kod jest kompilowany do zestawu i wdrażany w programie SharePoint. Domyślnie właściwości funkcji **zestawu odbiorcy** i **klasy odbiornika** odwołują się do nazwy klasy i zestawu.

### <a name="reference-method"></a>reference — Metoda
 Innym sposobem dodania odbiornika funkcji jest użycie właściwości **odbiorcy funkcji** elementu projektu, aby odwołać się do zestawu odbiorcy funkcji. Wartość właściwości odbiorcy funkcji ma dwie podwłaściwości: **zestaw** i **Nazwa klasy**. Zestaw musi używać w pełni kwalifikowanej nazwy "Strong", a nazwa klasy musi być pełną nazwą typu. Aby uzyskać więcej informacji, zobacz [zestawy o silnych nazwach](/previous-versions/dotnet/netframework-4.0/wd40t7ad(v=vs.100)). Po wdrożeniu rozwiązania do programu SharePoint Funkcja używa przywoływanego odbiornika funkcji do obsługi zdarzeń funkcji.

 W czasie kompilacji rozwiązania wartości właściwości odbiorcy funkcji w funkcji i jej projektach są scalane w celu ustawienia atrybutów ReceiverAssembly i ReceiverClass elementu Feature w manifeście funkcji pliku rozwiązania programu SharePoint (*wsp*). W związku z tym, jeśli określono wartości właściwości Assembly i Class elementu projektu i funkcji, element projektu i wartości właściwości funkcji muszą być zgodne. Jeśli wartości nie są zgodne, zostanie wyświetlony komunikat o błędzie walidacji. Jeśli chcesz, aby element projektu odwołuje się do zestawu odbiorcy funkcji innego niż używany przez jego funkcja, przenieś go do innej funkcji.

 Jeśli odwołujesz się do zestawu odbiorcy funkcji, który nie znajduje się jeszcze na serwerze, należy również dołączyć sam plik zestawu do pakietu. nie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje go do użytkownika. Podczas wdrażania tej funkcji plik zestawu jest kopiowany do folderu systemowego [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] lub bin w katalogu fizycznym programu SharePoint. Aby uzyskać więcej informacji, zobacz jak to zrobić: [Dodawanie i usuwanie dodatkowych zestawów](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Aby uzyskać więcej informacji na temat odbiorników funkcji, zobacz [odbiornik zdarzeń funkcji](/previous-versions/office/developer/sharepoint-2007/bb862634(v=office.12)) i [zdarzenia funkcji](/previous-versions/office/developer/sharepoint-2010/ms469501(v=office.14)).

## <a name="project-output-references"></a>Odwołania do danych wyjściowych projektu
 Właściwość odwołania danych wyjściowych projektu określa zależność, taką jak zestaw, że element projektu musi zostać uruchomiony. Załóżmy na przykład, że Twoje rozwiązanie ma projekt usługi BDC i projekt klasy. Jeśli projekt BDC ma zależność od zestawu, który jest wyprowadzany przez projekt klasy, można odwołać się do zestawu we właściwości odwołania danych wyjściowych projektu usługi BDC. Gdy projekt BDC jest spakowany, zestaw zależny jest dołączony do pakietu.

 Odwołania do danych wyjściowych projektu są zwykle zestawami, ale w niektórych przypadkach (takich jak projekty Silverlight) mogą być innymi typami plików.

 Aby uzyskać więcej informacji, zobacz [jak: Dodawanie odwołania do danych wyjściowych projektu](../sharepoint/how-to-add-a-project-output-reference.md).

## <a name="safe-control-entries"></a>Bezpieczne wpisy kontroli
 Program SharePoint zapewnia mechanizm zabezpieczeń nazywany wpisami bezpiecznego sterowania, aby ograniczyć dostęp użytkowników niezaufanych do określonych kontrolek. Po zaprojektowaniu program SharePoint umożliwia niezaufanym użytkownikom przekazywanie i tworzenie stron ASPX na serwerze programu SharePoint. Aby uniemożliwić tym użytkownikom dodawanie niebezpiecznego kodu do stron ASPX, program SharePoint ogranicza dostęp do *bezpiecznych kontrolek*. Bezpieczne formanty to kontrolki ASPX i części sieci Web, które są oznaczone jako bezpieczne i mogą być używane przez dowolnego użytkownika w witrynie. Aby uzyskać więcej informacji, zobacz [krok 4. Dodawanie składnika Web Part do listy bezpiecznych kontrolek](/previous-versions/office/developer/sharepoint-2007/ms581321(v=office.12)).

 Każdy element projektu programu SharePoint w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ma właściwość o nazwie **wpisy kontroli bezpiecznego** , która ma dwie właściwości logiczne: **bezpieczny** i **bezpieczny względem skryptu**. Bezpieczna Właściwość określa, czy niezaufani użytkownicy mogą uzyskiwać dostęp do kontrolki. Właściwość bezpieczne dla skryptu określa, czy niezaufani użytkownicy mogą wyświetlać i zmieniać właściwości kontrolki.

 Na podstawie zestawu są przywoływane bezpieczne wpisy kontroli. Aby dodać bezpieczne wpisy kontroli do zestawu projektu, wprowadź je w właściwości **wpisy kontroli bezpiecznego** elementu projektu. Można jednak dodać do zestawu projektu bezpieczne wpisy kontroli przy użyciu karty **Zaawansowane** w **projektancie pakietów** po dodaniu dodatkowego zestawu do pakietu. Aby uzyskać więcej informacji, zobacz [How to: Mark Controls as Safe Controls](../sharepoint/how-to-mark-controls-as-safe-controls.md) lub Register [a Assembly Web Part jako bezpieczną kontrolę](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11)).

### <a name="xml-entries-for-safe-controls"></a>Wpisy XML dla bezpiecznych formantów
 Po dodaniu wpisu kontroli bezpiecznego do elementu projektu lub zestawu projektu odwołanie jest zapisywane do manifestu pakietu w następującym formacie:

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

## <a name="see-also"></a>Zobacz też
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Używanie modułów do dołączania plików w rozwiązaniu](../sharepoint/using-modules-to-include-files-in-the-solution.md)
- [Rozszerzona pakowanie i wdrażanie programu SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
