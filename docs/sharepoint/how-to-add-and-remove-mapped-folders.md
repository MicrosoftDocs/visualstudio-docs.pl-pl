---
title: 'How to: Add and Remove Mapped Folders | Microsoft Docs'
description: Dodawanie i usuwanie zamapowanych folderów do projektu w programie SharePoint.  Zmień lokalizację wdrożenia zamapowanego folderu. Zmień nazwę lub usuń zamapowane foldery.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a9b74ba786c9d1104fd507442d959e75afb17bf2
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112419"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Jak dodawać i usuwać zamapowane foldery

  Niektóre często używane foldery w programie SharePoint, takie jak Obrazy i Układy, są głęboko osadzone w hierarchii plików. Te foldery można mapować na projekt programu SharePoint, aby łatwiej uzyskać do nich dostęp. Zamapowane foldery to foldery w projekcie programu SharePoint, które odpowiadają fizycznej lokalizacji plików podczas instalacji programu SharePoint Server.

 Podczas wdrażania aplikacji programu SharePoint zawartość zamapowanego folderu i wszystkich jego podfolderów jest kopiowana przez pakiet rozwiązania (wsp) na serwer z uruchomionym programem SharePoint w określonej lokalizacji w drzewie folderów programu SharePoint. Ta lokalizacja jest określana przez właściwość **Lokalizacja** wdrożenia ustawioną dla zamapowanego folderu. Wszystkie podfoldery w zamapowanych folderach są względne względem **lokalizacji** wdrożenia zamapowanego folderu. Należy pamiętać, że właściwość **Lokalizacja** wdrożenia, a nie nazwa zamapowanego folderu, określa miejsce wdrożenia elementów.
Zamapowane foldery można dodać do projektu przy użyciu poleceń na pasku menu lub w menu skrótów dla projektu. Możesz użyć poleceń Dodaj folder **zamapowany "Obrazy"** programu SharePoint i Dodaj **foldery "Układy" programu SharePoint,** aby dodać te zamapowane foldery, które są najczęściej używane. Dowolny z innych dostępnych folderów programu SharePoint można mapować na projekt za pomocą polecenia Dodaj folder zamapowany programu **SharePoint** w menu skrótów, a następnie określając foldery w oknie dialogowym Dodawanie folderu zamapowanego programu **SharePoint.**

## <a name="add-mapped-folders-to-a-project"></a>Dodawanie zamapowanych folderów do projektu

 W poniższej procedurze opisano sposób dodawania dwóch zamapowanych folderów do projektu wizualnego składników Web Part. Aby rozpocząć, należy utworzyć projekt wizualnego składników Web Part.

## <a name="to-add-mapped-folders-to-a-project"></a>Aby dodać zamapowane foldery do projektu

1. Na pasku menu wybierz pozycję **File** New Project  >  **(Plik nowy**  >  **projekt).**
::: moniker range="=vs-2017"
2. W **oknie dialogowym** Nowy projekt rozwiń węzeł **Visual Basic** lub **Visual C#,** rozwiń węzeł **Office/SharePoint,** a następnie wybierz węzeł **Rozwiązania programu SharePoint.**

3. Na liście szablonów projektów wybierz szablon **SharePoint 2013 Visual Web Part.**

4. W polu **Nazwa** wprowadź **test TestProject1,** a następnie wybierz **przycisk OK.**
::: moniker-end
::: moniker range=">=vs-2019"
2. W **oknie dialogowym Create a New Project (Tworzenie** nowego projektu) wybierz pozycję *SharePoint Visual Web Part** dla określonej zainstalowanej wersji programu SharePoint. Jeśli na przykład masz zainstalowany program SharePoint 2019, wybierz szablon Visual Web Part programu **SharePoint 2019.**
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. W polu **Nazwa** wprowadź **TestProject1.**
4. Następnie wybierz **przycisk Utwórz.**
::: moniker-end

5. W **Kreatorze dostosowywania programu SharePoint** wybierz przycisk **Zakończ,** aby zachować ustawienia domyślne.

6. W **Eksplorator rozwiązań** wybierz węzeł projektu, a następnie na pasku menu wybierz pozycję **Projekt** Dodaj  >  **"Obrazy" zamapowanego folderu programu SharePoint.**

     W projekcie zostanie wyświetlony folder o nazwie **Images** zawierający podfolder o nazwie TestProject1. Ten zamapowany folder będzie zawierać obrazy dla projektu wizualnego składników Web Part.

7. W **Eksplorator rozwiązań** projektu wybierz węzeł projektu, a następnie na pasku menu wybierz pozycję **Project** Add SharePoint Mapped Folder (Dodaj folder zamapowany programu  >  **SharePoint),** aby wyświetlić okno dialogowe Dodawanie folderu zamapowanego programu **SharePoint.**

8. W widoku drzewa folderów, które są dostępne do mapowania, wybierz folder **Zasoby,** a następnie wybierz przycisk **OK.**

     W projekcie zostanie wyświetlony folder o nazwie **Resources.** Ten folder może przechowywać elementy, takie jak pliki zasobów ciągów. Podfoldery mogą być przydatne do organizowania zawartości zamapowanego folderu, ale nie są automatycznie tworzone podczas dodawania zamapowanego folderu za pomocą polecenia Dodaj folder zamapowany programu **SharePoint.** Aby dodać podfolder, wybierz folder **Zasoby,** a następnie na pasku menu wybierz pozycję **Projekt**  >  **nowy folder**.

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>Zmienianie lokalizacji wdrożenia zamapowanego folderu

 Domyślnie zamapowane foldery są dodawane do określonych lokalizacji względem ścieżki instalacji głównej programu SharePoint, którą wskazuje \<SharePointRoot> token. Tę lokalizację można jednak zmienić, zmieniając właściwość **Lokalizacja wdrożenia** zamapowanego folderu. Każdy zamapowany folder ma własną właściwość **Lokalizacja wdrożenia.**

### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Aby zmienić lokalizację wdrożenia zamapowanego folderu

1. W projekcie utworzonym wcześniej wybierz zamapowany folder.

2. W **oknie** Właściwości wybierz przycisk wielokropka (![ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ASP.NET wielokropka projektanta aplikacji mobilnych")) we właściwości **Lokalizacja** wdrożenia.

3. W **oknie dialogowym Dodawanie** folderu zamapowanego programu SharePoint przejdź do folderu, do którego ma być wskażony folder zmapowany.

4. Wybierz węzeł, a następnie wybierz przycisk **OK.**

## <a name="rename-or-remove-mapped-folders"></a>Zmienianie nazwy lub usuwanie zamapowanych folderów

### <a name="to-rename-or-remove-a-mapped-folder"></a>Aby zmienić nazwę lub usunąć zamapowany folder

1. W projekcie utworzonym wcześniej wybierz zamapowany folder.

2. Aby zmienić nazwę zamapowanego folderu, otwórz jego menu skrótów, wybierz pozycję **Zmień** nazwę, wprowadź nową nazwę, a następnie naciśnij klawisz Enter.

     Alternatywnie możesz wybrać zamapowany folder, którego nazwę chcesz  zmienić, otworzyć okno Właściwości, a następnie ustawić nową nazwę dla wartości właściwości **Nazwa** folderu.

3. Aby usunąć zamapowany folder z projektu, otwórz jego menu skrótów, wybierz pozycję Usuń **,** a następnie wybierz przycisk **OK** w oknie dialogowym, aby potwierdzić usunięcie.

## <a name="see-also"></a>Zobacz też

- [Opracowywanie rozwiązań programu SharePoint](../sharepoint/developing-sharepoint-solutions.md)
