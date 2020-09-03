---
title: 'Instrukcje: Dodawanie i usuwanie zależności funkcji | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c318a7dc4672a10e993d0149ec77e7f94679d465
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014783"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Instrukcje: Dodawanie i usuwanie zależności funkcji
  Funkcja programu SharePoint może zależeć od innych funkcji dla funkcjonalności lub danych. W takich przypadkach można oznaczyć te inne funkcje jako zależności dla funkcji. W ten sposób serwer programu SharePoint zapewnia Aktywowanie funkcji zależnych przed aktywowaniem funkcji.

## <a name="add-dependencies"></a>Dodaj zależności
 Inne funkcje w rozwiązaniu można dodać jako zależności. W ten sposób można upewnić się, że wymagane funkcje są zainstalowane i aktywowane przed zainstalowaniem funkcji.

#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Aby dodać zależność od funkcji w rozwiązaniu

1. Otwórz projektanta funkcji, rozwiń węzeł **zależności aktywacji funkcji** , a następnie wybierz przycisk **Dodaj** .

2. W oknie dialogowym **Dodawanie zależności aktywacji funkcji** wybierz przycisk opcji **Dodaj zależność od funkcji w rozwiązaniu** , wybierz tytuł funkcji, którą chcesz dodać jako zależność, a następnie wybierz przycisk **Dodaj** .

     Możesz dodać więcej niż jedną funkcję, wybierając wiele tytułów podczas wybierania klawisza **Ctrl** .

## <a name="addi-custom-dependencies"></a>Addi zależności niestandardowe
 Możesz dodać funkcje, które są już wdrożone na serwerze programu SharePoint jako zależność. W ten sposób proces aktywacji programu SharePoint sprawdza, czy wszystkie funkcje zależne są aktywowane przed zainstalowaniem funkcji.

#### <a name="to-add-a-dependency-by-the-feature-id"></a>Aby dodać zależność według identyfikatora funkcji

1. Otwórz projektanta funkcji, rozwiń węzeł **zależności aktywacji funkcji** , a następnie wybierz przycisk **Dodaj** .

2. W oknie dialogowym **Dodawanie zależności aktywacji funkcji** wybierz przycisk opcji **Dodaj niestandardową zależność** .

3. W polu tekstowym **Identyfikator funkcji** wprowadź identyfikator GUID funkcji, którą chcesz oznaczyć jako zależność aktywacji, a następnie wybierz przycisk **Dodaj** .

## <a name="edit-custom-dependencies"></a>Edytuj zależności niestandardowe
 Można edytować niestandardowe zależności, które zostały dodane wcześniej. Jednak funkcje zależne, które znajdują się w rozwiązaniu, mogą zostać usunięte, a nie edytowane.

#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>Aby zmienić zależność od funkcji w rozwiązaniu

1. Otwórz projektanta funkcji, a następnie rozwiń węzeł **zależności aktywacji funkcji** .

2. Wybierz nazwę funkcji, którą chcesz edytować, a następnie wybierz przycisk **Edytuj** .

3. W oknie dialogowym **Edytowanie zależności aktywacji funkcji niestandardowych** Zmień tytuł, identyfikator funkcji lub opis, a następnie wybierz przycisk **Prześlij** .

## <a name="remove-dependencies"></a>Usuń zależności

#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>Aby usunąć zależność od funkcji w rozwiązaniu

1. W Projektancie funkcji rozwiń węzeł **zależności aktywacji funkcji** , wybierz nazwę funkcji, którą chcesz usunąć, a następnie wybierz przycisk **Usuń** .

## <a name="see-also"></a>Zobacz też
- [Tworzenie funkcji programu SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Instrukcje: Dostosowywanie funkcji programu SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Instrukcje: Dodawanie i usuwanie elementów do funkcji programu SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
