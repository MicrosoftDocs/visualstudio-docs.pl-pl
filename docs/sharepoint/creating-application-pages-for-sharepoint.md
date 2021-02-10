---
title: Tworzenie stron aplikacji dla programu SharePoint | Microsoft Docs
description: Tworzenie stron aplikacji dla programu SharePoint. Strona aplikacji to strona sieci Web ASP.NET przeznaczona do użycia w witrynie programu SharePoint.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9ecd6573573d76c3e47a2c87a4f455cb9890fb31
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949184"
---
# <a name="create-application-pages-for-sharepoint"></a>Tworzenie stron aplikacji dla programu SharePoint
  *Strona aplikacji* to strona sieci Web ASP.NET przeznaczona do użycia w witrynie sieci Web programu SharePoint. Strony aplikacji są wyspecjalizowanym typem strony ASP.NET. Główną różnicą między stroną aplikacji a standardową stroną ASP.NET jest to, że Strona aplikacji zawiera zawartość scaloną ze stroną wzorcową programu SharePoint. Strona wzorcowa umożliwia stronom aplikacji udostępnianie tego samego wyglądu i zachowań co inne strony w witrynie.

 Program Visual Studio umożliwia projektowanie stron aplikacji przy użyciu projektanta. Projektant wyświetla obszar zawartości dla każdego symbolu zastępczego zawartości zdefiniowanego na stronie wzorcowej. Stronę aplikacji można zaprojektować, przeciągając kontrolki do tych obszarów zawartości.

## <a name="application-pages"></a>Strony aplikacji
 Strony aplikacji są współużytkowane przez wszystkie lokacje na serwerze, natomiast strona witryny jest specyficzna dla jednej lokacji. Aby uzyskać więcej informacji, należy zapoznać się z [typami stron programu SharePoint](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14)).

 Domyślnie większość stron, które pojawiają się podczas tworzenia witryny programu SharePoint, to strony witryny. Stronę witryny można dodać do biblioteki stron programu SharePoint. Użytkownicy mogą dostosować stronę witryny przy użyciu narzędzi, takich jak SharePoint Designer. Strona witryny może również hostować funkcje, takie jak dynamiczne składniki Web Part i strefy składników Web Part.

 Strony aplikacji nie mogą wykonać tych czynności. Jednak Strona aplikacji jest najlepszym typem strony, która ma zostać utworzona, jeśli chcesz, aby strona zawierała kod niestandardowy. Mimo że można dodać niestandardowy kod do strony witryny, kod przestaje działać, gdy użytkownik dostosowuje stronę przy użyciu narzędzi, takich jak SharePoint Designer.

> [!NOTE]
> Program Visual Studio nie udostępnia szablonów, które ułatwiają tworzenie stron witryny programu SharePoint. Aby uzyskać więcej informacji, zobacz [typy stron programu SharePoint](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14)).

## <a name="create-an-application-page"></a>Tworzenie strony aplikacji
 Aby utworzyć stronę aplikacji, Dodaj element **strony aplikacji** do projektu programu SharePoint. Podczas tworzenia strony aplikacji program Visual Studio dodaje do projektu następujące foldery:

|Folder|Opis|
|------------|-----------------|
|Układy|Mapuje do katalogu wirtualnego _layouts systemu plików programu SharePoint.|
|Podfolder Layouts|Zawiera pliki wchodzące w skład strony aplikacji. Domyślnie ten folder ma taką samą nazwę jak projekt. W każdej chwili można zmienić nazwę tego folderu. Po uruchomieniu projektu program Visual Studio wdraża ten folder w katalogu wirtualnym _layouts systemu plików programu SharePoint.|

 Program Visual Studio dodaje do projektu następujące pliki:

|Plik|Opis|
|----------|-----------------|
|Plik stronicowania ASP.NET (*. aspx*)|Zawiera znacznik XML definiujący stronę.|
|Plik kodu strony aplikacji|Zawiera kod związany ze stroną aplikacji. Dodaj kod, który obsługuje zdarzenia do tego pliku.|
|Plik kodu projektanta stron aplikacji|Zawiera kod, który jest generowany przez projektanta. Nie Edytuj bezpośrednio tego pliku.|

## <a name="design-and-debug-an-application-page"></a>Projektowanie i debugowanie strony aplikacji
 Zaprojektuj zawartość strony aplikacji przy użyciu widoku projektanta w programie Visual Studio. Ten projektant pojawia się po otwarciu strony aplikacji w projekcie (klikając ją dwukrotnie lub otwierając menu skrótów, a następnie wybierając polecenie **Otwórz**), a następnie klikając przycisk **projekt** u dołu edytora.

> [!NOTE]
> Stronę można zaprojektować tylko w widoku **źródła** projektanta. Widok **projekt** projektanta jest wyłączony dla stron aplikacji.

 Można debugować stronę aplikacji tak samo jak w przypadku debugowania innych elementów projektu programu SharePoint w programie Visual Studio. Po uruchomieniu debugera programu Visual Studio program Visual Studio otwiera witrynę programu SharePoint.

 Aby wyświetlić stronę aplikacji, musisz ręcznie przejść do lokalizacji strony aplikacji (na przykład: http://<em>server_name</em>/_layouts/*Project_Name*/ApplicationPage1.aspx).

 Aby uzyskać więcej informacji na temat debugowania projektów programu SharePoint, zobacz [Rozwiązywanie problemów z rozwiązaniami programu SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="choose-a-master-page"></a>Wybierz stronę wzorcową
 Domyślnie element **strony aplikacji** odwołuje się do strony wzorcowej witryny, która jest używana do debugowania projektu. Ta strona ma nazwę v4. Master i można ją znaleźć w **galerii stron wzorcowych** witryny programu SharePoint.

 Możesz jawnie zmienić stronę wzorcową używaną przez ustawienie `MasterPageFile` atrybutu `Page` elementu aplikacji. (Na przykład: `MasterPageFile="~/_layouts/applicationv4.master"` ). W rzeczywistości należy ustawić ten atrybut, jeśli dynamiczne strony główne nie są włączone na serwerze programu SharePoint. Aby uzyskać więcej informacji na temat stron wzorcowych w programie SharePoint, zobacz [stronę wzorcową](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14)).

## <a name="see-also"></a>Zobacz też
- [Projektowanie programu SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee539092(v=office.14))
- [Omówienie platformy ASP.NET](/aspnet/overview)
- [ASP.NET Web Pages](/aspnet/web-pages/index)
