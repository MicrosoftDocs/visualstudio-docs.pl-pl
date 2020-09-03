---
title: 'Instrukcje: Dodawanie i usuwanie zamapowanych folderów | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 80fbd3e18b8d440eae2873c73013ad7468073640
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014652"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Instrukcje: Dodawanie i usuwanie mapowanych folderów
  Niektóre często używane foldery w programie SharePoint, takie jak obrazy i układy, są głęboko osadzone w hierarchii plików. Te foldery można mapować do projektu programu SharePoint, aby łatwiej uzyskać do nich dostęp. Mapowane foldery to foldery w projekcie programu SharePoint, które odpowiadają lokalizacji fizycznej plików w instalacji programu SharePoint Server.

 Podczas wdrażania aplikacji SharePoint zawartość zamapowanego folderu i wszystkie jego podfoldery są kopiowane przez pakiet rozwiązania (wsp) na serwer, na którym działa program SharePoint w określonej lokalizacji w drzewie folderów programu SharePoint. Ta lokalizacja jest określana przez właściwość **Lokalizacja wdrożenia** ustawioną dla zamapowanego folderu. Wszystkie podfoldery w mapowanym folderze są względne do **lokalizacji wdrożenia** zamapowanego folderu. Należy pamiętać, że właściwość **Lokalizacja wdrożenia** , a nie nazwa zamapowanego folderu, określa, gdzie są wdrażane elementy.
Do projektu można dodać mapowane foldery przy użyciu poleceń na pasku menu lub menu skrótów dla projektu. Możesz użyć **zamapowanego folderu "obrazy" programu SharePoint** i **dodać polecenia folderu "Layouts" programu SharePoint** , aby dodać te mapowane foldery, które są najczęściej używane. Wszystkie inne dostępne foldery programu SharePoint można mapować do projektu za pomocą polecenia **Dodaj zamapowany folder programu SharePoint** w menu skrótów, a następnie określając foldery w oknie dialogowym **Dodaj zamapowany folder programu SharePoint** .

## <a name="add-mapped-folders-to-a-project"></a>Dodawanie zamapowanych folderów do projektu
 Poniższa procedura opisuje sposób dodawania dwóch mapowanych folderów do projektu wizualnego składnika Web Part. Aby rozpocząć, należy utworzyć projekt wizualnego składnika Web Part.

#### <a name="to-add-mapped-folders-to-a-project"></a>Aby dodać mapowane foldery do projektu

1. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual Basic** lub **Visual C#** , rozwiń węzeł **Office/SharePoint** , a następnie wybierz węzeł **rozwiązania programu SharePoint** .

3. Na liście szablonów projektu wybierz szablon **Visual Web Part programu SharePoint 2013** .

4. W polu **Nazwa** wprowadź **TestProject1**, a następnie wybierz przycisk **OK** .

5. W **Kreatorze dostosowania programu SharePoint**wybierz przycisk **Zakończ** , aby zachować ustawienia domyślne.

6. W **Eksplorator rozwiązań**wybierz węzeł projektu, a następnie na pasku menu wybierz pozycję **projekt**  >  **Dodaj SharePoint "obrazy" folder zamapowany**.

     Folder o nazwie **obrazy** pojawia się w projekcie i zawiera podfolder o nazwie TestProject1. Ten zamapowany folder będzie zawierać obrazy dla projektu wizualnego składnika Web Part.

7. W **Eksplorator rozwiązań**wybierz węzeł projektu, a następnie na pasku menu wybierz **projekt**  >  **Dodaj zamapowany folder programu SharePoint** , aby wyświetlić okno dialogowe **Dodaj zamapowany folder programu SharePoint** .

8. W widoku drzewa folderów, które są dostępne do mapowania, wybierz folder **resources** , a następnie wybierz przycisk **OK** .

     W projekcie pojawi się folder o nazwie **zasoby** . Ten folder może przechowywać elementy, takie jak pliki zasobów typu String. Podfoldery mogą być przydatne do organizowania zawartości zamapowanego folderu, ale nie są automatycznie tworzone podczas dodawania zamapowanego folderu przy użyciu polecenia **Dodaj zamapowany folder programu SharePoint** . Aby dodać podfolder, wybierz folder **resources** , a następnie na pasku menu wybierz **projekt**  >  **Nowy folder**.

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>Zmień lokalizację wdrożenia zamapowanego folderu
 Domyślnie mapowane foldery są dodawane do określonych lokalizacji względem ścieżki instalacji głównej programu SharePoint, która jest oznaczona jako token \<SharePointRoot> . Można jednak zmienić tę lokalizację, zmieniając właściwość **Lokalizacja wdrożenia** zamapowanego folderu. Każdy zamapowany folder ma własną właściwość **lokalizacji wdrożenia** .

#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Aby zmienić lokalizację wdrożenia zamapowanego folderu

1. W projekcie, który został utworzony wcześniej, wybierz zamapowany folder.

2. W oknie **Właściwości** wybierz przycisk wielokropka (![ASP.net Mobile Designer](../sharepoint/media/mwellipsis.gif "Wielokropek projektanta ASP.NET Mobile")) we właściwości **Lokalizacja wdrożenia** .

3. W oknie dialogowym **Dodaj zamapowany folder programu SharePoint** przejdź do folderu, do którego ma zostać wskazywany mapowany folder.

4. Wybierz węzeł, a następnie wybierz przycisk **OK** .

## <a name="rename-or-remove-mapped-folders"></a>Zmień nazwę lub Usuń zamapowane foldery

#### <a name="to-rename-or-remove-a-mapped-folder"></a>Aby zmienić nazwę lub usunąć zamapowany folder

1. W projekcie, który został utworzony wcześniej, wybierz zamapowany folder.

2. Aby zmienić nazwę zamapowanego folderu, otwórz jego menu skrótów, wybierz polecenie **Zmień**nazwę, wprowadź nową wartość, a następnie wybierz klawisz ENTER.

     Alternatywnie możesz wybrać mapowany folder, którego nazwę chcesz zmienić, Otwórz okno **Właściwości** , a następnie ustaw wartość właściwości **Nazwa folderu** na nową nazwę.

3. Aby usunąć zamapowany folder z projektu, otwórz jego menu skrótów, wybierz polecenie **Usuń**, a następnie wybierz przycisk **OK** w oknie dialogowym, aby potwierdzić usunięcie.

## <a name="see-also"></a>Zobacz też
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
