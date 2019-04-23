---
title: 'Instrukcje: Dodawanie i usuwanie folderów mapowanych | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: d5d1acc40b23c979a5746c50be50a584d11112b5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60046984"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Porady: Dodawanie i usuwanie folderów mapowanych
  Niektóre często używane foldery w programie SharePoint, takich jak obrazy i układy, głęboko są osadzone w hierarchii plików. Te foldery można mapować do projektu programu SharePoint do nich łatwiejszy dostęp. Mapowane foldery są foldery w projekcie programu SharePoint, które odnoszą się do fizycznej lokalizacji plików w instalacji programu SharePoint Server.

 Podczas wdrażania aplikacji programu SharePoint, zawartość zamapowany folder i wszystkie jego podfolderów, są kopiowane rozwiązania pakietu (wsp) do serwera, programem SharePoint w określonej lokalizacji w drzewie folderów programu SharePoint. Ta lokalizacja jest określana przez **lokalizacji wdrożenia** właściwość, która jest ustawiona dla zamapowany folder. Wszystkie podfoldery w zamapowany folder są względem **lokalizacji wdrożenia** z zamapowany folder. Należy pamiętać, że **lokalizacji wdrożenia** właściwość nie nazwę zamapowany folder określa, których elementy są wdrażane.
Za pomocą poleceń w pasku menu lub menu skrótów dla projektu, można dodawać foldery zamapowany do projektu. Możesz użyć **Dodaj program SharePoint "Obrazy" zamapowany Folder** i **Dodaj program SharePoint "Układów" folder** polecenia, aby dodać te mapowane foldery, które są używane najczęściej. Można mapować dowolnej innych dostępnych folderów programu SharePoint do projektu przy użyciu **Dodaj program SharePoint zamapowany Folder** polecenia w menu skrótów, a następnie określając folderów w **Dodaj program SharePoint zamapowany Folder** okno dialogowe.

## <a name="add-mapped-folders-to-a-project"></a>Dodawanie folderów mapowanych do projektu
 Poniższa procedura opisuje sposób dodawania dwóch folderów mapowanych do projektu wizualnego składnika web part. Aby rozpocząć, należy utworzyć projekt wizualnego składnika web part.

#### <a name="to-add-mapped-folders-to-a-project"></a>Aby dodać mapowane foldery do projektu

1. Na pasku menu wybierz **pliku** > **New** > **projektu**.

2. W **nowy projekt** okna dialogowego rozwiń **języka Visual Basic** lub **Visual C#**  węzła, rozwiń węzeł **Office/SharePoint** węzeł, a następnie wybierz **rozwiązań programu SharePoint** węzła.

3. Na liście szablonów projektu wybierz **składnik Web Part programu SharePoint 2013 Visual** szablonu.

4. W **nazwa** wprowadź **TestProject1**, a następnie wybierz **OK** przycisku.

5. W **Kreator ustawień niestandardowych SharePoint**, wybierz **Zakończ** przycisk, aby zachować ustawienia domyślne.

6. W **Eksploratora rozwiązań**, wybierz węzeł projektu, a następnie na pasku menu wybierz **projektu** > **Dodaj program SharePoint "Obrazy" zamapowany Folder**.

     Folder o nazwie **obrazów** pojawia się w projekcie i zawiera osobny podfolder o nazwie TestProject1. Ta zamapowany folder będzie zawierać obrazów dla projektu wizualnego składnika web part.

7. W **Eksploratora rozwiązań**, wybierz węzeł projektu, a następnie na pasku menu wybierz **projektu** > **Dodaj program SharePoint zamapowany Folder** do wyświetlenia  **Dodaj program SharePoint zamapowany Folder** okno dialogowe.

8. W widoku drzewa folderów, które są dostępne dla mapowania, wybierz **zasobów** folder, a następnie wybierz **OK** przycisku.

     Folder o nazwie **zasobów** pojawia się w projekcie. Ten folder może przechowywać elementy, takie jak pliki zasobów ciągu. Podfoldery mogą być przydatne do organizowania zawartości zamapowany folder, ale są automatycznie tworzone podczas dodawania zamapowany folder przy użyciu **Dodaj program SharePoint zamapowany Folder** polecenia. Aby dodać folder podrzędny, wybierz **zasobów** folder, a następnie na pasku menu wybierz **projektu** > **nowy Folder**.

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>Zmiana lokalizacji wdrożenia zamapowany folder
 Domyślnie mapowane foldery są dodawane do określonych lokalizacji względem ścieżki instalacji głównym programu SharePoint, której token \<SharePointRoot > oznacza. Można jednak zmienić tę lokalizację, zmieniając **lokalizacji wdrożenia** właściwość zamapowany folder. Każdy zamapowany folder ma swój własny **lokalizacji wdrożenia** właściwości.

#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Aby zmienić lokalizację wdrażania zamapowany folder

1. W projekcie, który został utworzony wcześniej wybierz zamapowany folder.

2. W **właściwości** okna, wybierz przycisk wielokropka (![elipsy projektanta Mobile ASP.NET](../sharepoint/media/mwellipsis.gif "elipsy projektanta Mobile ASP.NET")) znajdujący się na **wdrożenia Lokalizacja** właściwości.

3. W **Dodaj program SharePoint zamapowany Folder** okno dialogowe, przejdź do folderu, do którego ma zostać zamapowany folder, aby wskazać.

4. Wybierz węzeł, a następnie wybierz **OK** przycisku.

## <a name="rename-or-remove-mapped-folders"></a>Zmiana nazwy lub usuwanie folderów mapowanych

#### <a name="to-rename-or-remove-a-mapped-folder"></a>Aby zmienić nazwę lub usunąć zmapowany folder

1. W projekcie, który został utworzony wcześniej wybierz zamapowany folder.

2. Aby zmienić nazwę zamapowany folder, otwórz jego menu skrótów wybierz pozycję **Zmień nazwę**, wprowadź nową nazwę, a następnie naciśnij klawisz Enter.

     Alternatywnie, można wybrać zamapowany folder, który chcesz zmienić, otwórz **właściwości** okna, a następnie ustaw wartość **nazwa folderu** właściwości na nową nazwę.

3. Aby usunąć zmapowany folder projektu, otwórz jego menu skrótów wybierz pozycję **Usuń**, a następnie wybierz **OK** przycisku w oknie dialogowym, aby potwierdzić usunięcie.

## <a name="see-also"></a>Zobacz także
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
