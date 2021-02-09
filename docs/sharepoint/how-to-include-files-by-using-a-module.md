---
title: 'Instrukcje: Dołączanie plików przy użyciu modułu | Microsoft Docs'
description: Dowiedz się, jak dołączać pliki przy użyciu modułu, który jest kontenerem, który umożliwia wdrażanie plików, takich jak strony wzorcowe ASPX, pliki tekstowe lub obrazy, do programu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e83a1474c7dfe6385c36cc13646bfe40fc897640
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913619"
---
# <a name="how-to-include-files-by-using-a-module"></a>Instrukcje: Dołączanie plików przy użyciu modułu
  *Moduły* (nie należy mylić z [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] modułami) to kontenery, które umożliwiają wdrażanie plików, takich jak strony wzorcowe aspx, pliki tekstowe lub obrazy, do programu SharePoint.

 Możesz wybrać wdrożenie pliku w bibliotece dokumentów lub jako normalny plik (na przykład Default. aspx) poza biblioteką dokumentów. Aby dodać plik do biblioteki dokumentów, określ `Type="GhostableInLibrary"` jako atrybut w elemencie **pliku** . To ustawienie powoduje, że program SharePoint utworzy element listy, który będzie przełączać się do pliku, gdy zostanie on dodany do biblioteki. Aby wdrożyć plik poza biblioteką dokumentów, należy określić `Type="Ghostable"` lub po prostu pominąć atrybut **typu** .

## <a name="add-a-module-to-a-sharepoint-solution"></a>Dodawanie modułu do rozwiązania programu SharePoint

#### <a name="to-add-a-module"></a>Aby dodać moduł

1. W programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwórz lub Utwórz projekt programu SharePoint.

     Aby uzyskać więcej informacji, zobacz [Szablony projektów i elementów projektu programu SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. W **Eksplorator rozwiązań** wybierz węzeł projektu, a następnie na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

     Zostanie otwarte okno dialogowe **Dodaj nowy element** .

3. Na liście szablonów programu SharePoint wybierz szablon **modułu** , a następnie wybierz przycisk **Dodaj** .

     Ten krok powoduje utworzenie węzła w projekcie o nazwie Module1.

4. W obszarze Module1 Usuń plik *Sample.txt* .

     Sample.txt jest uwzględniona we wszystkich nowych modułach na przykład i nie jest wymagana. (Należy zauważyć, że usunięcie pliku spowoduje również usunięcie jego wpisu z *Elements.xml* pliku modułu).

5. Jeśli chcesz, aby pliki zostały wdrożone w określonej strukturze folderów w programie SharePoint, Utwórz te foldery w obszarze Module1 w programie, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wybierając węzeł Module1, a następnie na pasku menu wybierz **projekt**, **Nowy folder**.

6. Wybierz folder, do którego chcesz dodać plik, a następnie na pasku menu wybierz **projekt**, **Dodaj istniejący element**.

7. Wybierz co najmniej jeden plik, który chcesz wdrożyć w programie SharePoint, a następnie wybierz przycisk **Dodaj** .

     Po dodaniu pliku do projektu, jego wpis jest automatycznie dodawany do pliku Elements.xml modułu. Po wdrożeniu projektu pliki są kopiowane do programu SharePoint Server względem katalogu głównego projektu, który jest określony przez atrybut **adresu URL** elementu **pliku** , na przykład `Url="Module1/New Folder/SomeFile.doc` . Jeśli chcesz zmienić lokalizację wdrożenia pliku, przenieś go do innego folderu w **Eksplorator rozwiązań** lub zmień jego ustawienie **adresu URL** .

8. Dla wszystkich plików, które mają być wyświetlane w bibliotece dokumentów, Dołącz `Type="GhostableInLibrary"` atrybut do ich wpisu w *Elements.xml*. Na przykład

    ```xml
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />
    ```

9. Wdróż projekt.

     Pliki są kopiowane do określonych lokalizacji w programie SharePoint.

## <a name="see-also"></a>Zobacz też
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
