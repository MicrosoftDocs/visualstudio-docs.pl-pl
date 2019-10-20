---
title: Strona odwołań, Projektant projektu (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesReference
- vb.ProjectPropertiesUnusedReference
- vb.ProjectPropertiesReferencePaths
helpviewer_keywords:
- References page in Project Designer
- Project Designer, References page
- Unused References dialog box
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8bb18ec8dd12431d650d844e3698c1986c8d8bd8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665642"
---
# <a name="references-page-project-designer-visual-basic"></a>Strona odwołań, Projektant projektu (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Za pomocą strony **odwołania** **projektanta projektu** można zarządzać odwołaniami, odwołaniami sieci Web i importowanymi przestrzeniami nazw w projekcie. Projekty mogą zawierać odwołania do składników COM, usług sieci Web XML, .NET Framework bibliotek klas lub zestawów lub innych bibliotek klas. Aby uzyskać więcej informacji na temat korzystania z odwołań, zobacz [Zarządzanie odwołaniami w projekcie](../../ide/managing-references-in-a-project.md).

 Aby uzyskać dostęp do strony **odwołań** , wybierz węzeł projektu (nie węzeł **rozwiązania** ) w **Eksplorator rozwiązań**. Następnie wybierz **projekt**, **Właściwości** na pasku menu. Gdy pojawi się Projektant projektu, kliknij kartę **odwołania** .

## <a name="uielement-list"></a>Lista elementów UI
 Poniższe opcje umożliwiają Zaznaczanie lub usuwanie odwołań i zaimportowanych przestrzeni nazw w projekcie.

 **Nieużywane odwołania** Kliknij ten przycisk, aby uzyskać dostęp do okna dialogowego **nieużywane odwołania** .

 Okno dialogowe **nieużywane odwołania** umożliwia usunięcie odwołań, które są zawarte w projekcie, ale nie są faktycznie używane przez kod. Zawiera siatkę, która wyświetla **nazwę odwołania**, **ścieżkę**i inne informacje o nieużywanych odwołaniach do przestrzeni nazw w projekcie. W siatce wybierz odwołania do przestrzeni nazw, które chcesz usunąć z projektu, a następnie kliknij przycisk **Usuń**.

 **Ścieżki odwołań** Kliknij ten przycisk, aby uzyskać dostęp do okna dialogowego **ścieżki odwołań** .

> [!NOTE]
> Gdy system projektu znajdzie odwołanie do zestawu, system rozpoznaje odwołanie, przeglądając następujące lokalizacje w następującej kolejności:
>
> 1. Folder projektu. Pliki folderu projektu pojawiają się w **Eksplorator rozwiązań** , gdy **pokazywane są wszystkie pliki** .
>    2. Foldery, które są określone w oknie dialogowym **ścieżki odwołań** .
>    3. Foldery, które wyświetlają pliki w oknie dialogowym **Dodaj odwołanie** .
>    4. Folder obj projektu. (Po dodaniu odwołania COM do projektu można dodać jeden lub więcej zestawów do folderu obj projektu).

 **Odwołania** Ta lista zawiera wszystkie odwołania w projekcie, używane lub nieużywane.

 **Dodaj** Kliknij ten przycisk, aby dodać odwołanie lub odwołanie sieci Web do listy **odwołań** .

 Wybierz **odwołanie** , aby dodać odwołanie do projektu za pomocą okna dialogowego Dodaj odwołanie.

 Wybierz pozycję **odwołanie sieci Web** , aby dodać odwołanie sieci Web do projektu za pomocą okna dialogowego Dodaj odwołanie sieci Web.

 **Usuń** Wybierz co najmniej jedno odwołanie na liście **odwołań** , a następnie kliknij ten przycisk, aby go usunąć.

 **Aktualizuj odwołanie sieci Web** Wybierz odwołanie sieci Web na liście **odwołań** i kliknij ten przycisk, aby go zaktualizować.

 **Zaimportowane przestrzenie nazw** W tym polu można wpisać własną przestrzeń nazw, a następnie kliknąć pozycję **Dodaj Import użytkowników** , aby dodać go do listy przestrzeni nazw.

 Można tworzyć aliasy dla przestrzeni nazw zaimportowanych przez użytkownika. W tym celu wprowadź alias i przestrzeń nazw w formacie *alias* =*przestrzeni nazw*. Jest to przydatne, jeśli używasz długich przestrzeni nazw, na przykład: `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`.

 **Dodaj Import użytkownika** Kliknij ten przycisk, aby dodać obszar nazw określony w polu **zaimportowane przestrzenie** nazw do listy importowanych przestrzeni nazw. Przycisk jest aktywny tylko wtedy, gdy określona przestrzeń nazw nie znajduje się już na liście.

 **Lista przestrzeni nazw** Ta lista zawiera wszystkie dostępne przestrzenie nazw. Wybrane są pola wyboru dla przestrzeni nazw zawartych w projekcie.

 **Aktualizowanie importowania użytkowników** Wybierz określoną przez użytkownika przestrzeń nazw na liście przestrzenie nazw, wpisz nazwę, która ma zostać zastąpiona w polu **zaimportowane przestrzenie nazw** , a następnie kliknij ten przycisk, aby przejść do nowej przestrzeni nazw. Przycisk jest aktywny tylko wtedy, gdy wybrany obszar nazw jest taki, który został dodany do listy za pomocą przycisku **Dodaj użytkownika importowania** . Możesz dodać:

- Klasy lub przestrzenie nazw, takie jak <xref:System.Math?displayProperty=fullName>.

- Importy aliasów, takie jak `VB=Microsoft.VisualBasic`.

- Przestrzenie nazw XML, takie jak `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`.

## <a name="see-also"></a>Zobacz też
 [NIB: Dodawanie lub usuwanie odwołań za pomocą okna dialogowego Dodaj odwołanie](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) [instrukcje: Dodawanie lub usuwanie importowanych przestrzeni nazw (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md) [NIB: Dodaj odwołanie sieci Web](https://msdn.microsoft.com/bdf05776-c591-40af-bfd7-e1e2aa1e87b5) , [instrukcja Imports (przestrzeń nazw XML)](https://msdn.microsoft.com/library/1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4)
