---
title: Tworzenie stron aplikacji dla programu SharePoint | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8ac9340ea853a1852d039f05a3ecbb100845ab84
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443543"
---
# <a name="create-application-pages-for-sharepoint"></a>Tworzenie stron aplikacji dla programu SharePoint
  *Strony aplikacji* jest to strona sieci Web platformy ASP.NET, który jest przeznaczony do użytku w witrynie sieci Web programu SharePoint. Strony aplikacji są specjalistyczną odmianą strony ASP.NET. Główną różnicą między strony aplikacji i standardowej strony ASP.NET jest to, że na stronie aplikacji zawiera zawartość, która jest połączone ze stroną wzorcową programu SharePoint. Strona wzorcowa umożliwia stron aplikacji do udostępniania tego samego wygląd i zachowanie jak innych stron w witrynie.

 Program Visual Studio umożliwia projektowanie stron aplikacji za pomocą projektanta. Projektant wyświetla obszar zawartości każdego symbolu zastępczego zawartości, która jest zdefiniowana w strony wzorcowej. Na stronie aplikacji można zaprojektować, przeciągając formanty do tych obszarów zawartości.

## <a name="application-pages"></a>Strony aplikacji
 Strony aplikacji są współdzielone przez wszystkich witryn na serwerze, strony witryny jest specyficzne dla jednej lokacji. Aby uzyskać więcej informacji [typy stron SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).

 Domyślnie większość stron, które pojawiają się podczas tworzenia witryny programu SharePoint są strony witryny. Strony witryny można dodać do biblioteki strony programu SharePoint. Użytkownicy mogą dostosować stronę witryny za pomocą narzędzi, takich jak SharePoint Designer. Witryna może również obsługiwać funkcje, takie jak dynamiczna składników Web Part i strefy składników Web Part.

 Strony aplikacji nie może korzystać z tych możliwości. Jednak na stronie aplikacji jest najlepszy typ strony, aby utworzyć stronę, aby zawierać kod niestandardowy. Chociaż możesz dodać niestandardowy kod do strony witryny, kod zatrzymane, kiedy użytkownik dostosowuje strony za pomocą narzędzi, takich jak SharePoint Designer.

> [!NOTE]
> Program Visual Studio nie zapewnia szablony, które ułatwiają tworzenie stron witryny dla witryny programu SharePoint. Aby uzyskać więcej informacji, zobacz [typy stron SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).

## <a name="create-an-application-page"></a>Tworzenie strony aplikacji
 Aby utworzyć stronę aplikacji, należy dodać **strony aplikacji** elementu do projektu programu SharePoint. Po utworzeniu strony aplikacji programu Visual Studio dodaje następujące foldery do projektu:

|Folder|Opis|
|------------|-----------------|
|Układy|Mapy do układu katalogu wirtualnego systemu plików programu SharePoint.|
|Podfolder układów|Zawiera pliki, które składają się na stronie aplikacji. Domyślnie ten folder ma taką samą nazwę jak projektu. W dowolnym momencie można zmienić nazwę tego folderu. Kiedy uruchamiasz projekt, program Visual Studio wdroży ten folder do układu katalogu wirtualnego systemu plików programu SharePoint.|

 Visual Studio dodaje następujące pliki do projektu:

|Plik|Opis|
|----------|-----------------|
|Plik strony ASP.NET (*.aspx*)|Zawiera znacznik XML, który definiuje stronę.|
|Plik kodu strony aplikacji|Zawiera kod związany z strony aplikacji. Dodaj kod, który obsługuje zdarzenia do tego pliku.|
|Plik projektanta kodu strony aplikacji|Zawiera kod, który jest generowany przez projektanta. Nie bezpośrednio edytować ten plik.|

## <a name="design-and-debug-an-application-page"></a>Projektowanie i debugowanie strony aplikacji
 Projektowanie zawartość strony aplikacji przy użyciu projektanta widoku w programie Visual Studio. Projektant pojawia się po otwarciu strony aplikacji w projekcie (klikając je dwukrotnie lub otwierając jego menu skrótów, a następnie wybierając **Otwórz**), a następnie wybierz **projektowania** znajdujący się u dołu Edytor.

> [!NOTE]
> Można zaprojektować strony tylko w **źródła** Widok projektanta. **Projektowania** Widok projektanta jest wyłączona w przypadku stron aplikacji.

 Można debugować strony aplikacji, tak samo, jak debuguje się inne elementy projektu programu SharePoint w programie Visual Studio. Po uruchomieniu debugera programu Visual Studio, Visual Studio otwiera witrynę programu SharePoint.

 Aby wyświetlić stronę aplikacji, musisz ręcznie przejść do lokalizacji strony aplikacji (na przykład: http://<em>nazwa_serwera</em>folderze /_layouts/*Project_Name*/ApplicationPage1.aspx).

 Aby uzyskać więcej informacji na temat debugowania projektów programu SharePoint, zobacz [rozwiązań SharePoint Rozwiązywanie problemów z](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="choose-a-master-page"></a>Wybierz stronę wzorcową
 Domyślnie **strony aplikacji** stronę wzorcową witryny, którego używasz, aby debugować projekt odwołuje się do elementu. Czy strona o nazwie v4.master i można znaleźć na liście **galerii stron wzorcowych** witryny programu SharePoint.

 Można jawnie zmiany, które strony wzorcowej jest używany przez strony aplikacji, ustawiając `MasterPageFile` atrybut aplikacji `Page` elementu. (Na przykład: `MasterPageFile="~/_layouts/applicationv4.master"`). W rzeczywistości należy ustawić ten atrybut, jeśli strony wzorcowej dynamiczne nie są włączone na serwerze programu SharePoint. Aby uzyskać więcej informacji na temat stron wzorcowych w programie SharePoint, zobacz [stronami wzorcowymi](http://go.microsoft.com/fwlink/?LinkID=169281).

## <a name="see-also"></a>Zobacz także
- [Rozwój SharePoint Foundation w głębi](http://go.microsoft.com/fwlink/?LinkID=182103)
- [Omówienie platformy ASP.NET](/aspnet/overview)
- [ASP.NET Web Pages](/aspnet/web-pages/index)
