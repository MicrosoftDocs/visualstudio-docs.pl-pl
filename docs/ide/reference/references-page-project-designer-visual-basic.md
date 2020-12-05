---
title: Strona odwołań, Projektant projektu (Visual Basic)
description: Dowiedz się, jak za pomocą strony odwołań projektanta projektu zarządzać odwołaniami do projektu, odwołaniami sieci Web i importowanymi przestrzeniami nazw.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesReference
- vb.ProjectPropertiesUnusedReference
- vb.ProjectPropertiesReferencePaths
helpviewer_keywords:
- References page in Project Designer
- Project Designer, References page
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6cc06bd51d66b49991e12db8bb03a63a5a742fe1
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616671"
---
# <a name="references-page-project-designer-visual-basic"></a>Strona odwołań, Projektant projektu (Visual Basic)

Za pomocą strony **odwołania** **projektanta projektu** można zarządzać odwołaniami, odwołaniami sieci Web i importowanymi przestrzeniami nazw w projekcie. Projekty mogą zawierać odwołania do składników COM, usług sieci Web XML, bibliotek lub zestawów platformy .NET lub innych bibliotek klas. Aby uzyskać więcej informacji na temat korzystania z odwołań, zobacz [Zarządzanie odwołaniami w projekcie](../../ide/managing-references-in-a-project.md).

Aby uzyskać dostęp do strony **odwołań** , wybierz węzeł projektu (nie węzeł **rozwiązania** ) w **Eksplorator rozwiązań**. Następnie wybierz **projekt**, **Właściwości** na pasku menu. Gdy pojawi się Projektant projektu, kliknij kartę **odwołania** .

## <a name="uielement-list"></a>Lista elementów UI

Poniższe opcje umożliwiają Zaznaczanie lub usuwanie odwołań i zaimportowanych przestrzeni nazw w projekcie.

**Ścieżki odwołań**

Kliknij ten przycisk, aby uzyskać dostęp do okna dialogowego **ścieżki odwołań** .

> [!NOTE]
> Gdy system projektu znajdzie odwołanie do zestawu, system rozpoznaje odwołanie, przeglądając następujące lokalizacje w następującej kolejności:
>
> 1. Folder projektu. Pliki folderu projektu pojawiają się w **Eksplorator rozwiązań** , gdy **pokazywane są wszystkie pliki** .
> 2. Foldery, które są określone w oknie dialogowym **ścieżki odwołań** .
> 3. Foldery, które wyświetlają pliki w oknie dialogowym **Dodaj odwołanie** .
> 4. Folder obj projektu. (Po dodaniu odwołania COM do projektu można dodać jeden lub więcej zestawów do folderu obj projektu).

 **Odwołania**

Ta lista zawiera wszystkie odwołania w projekcie, używane lub nieużywane.

 **Dodaj**

Kliknij ten przycisk, aby dodać odwołanie lub odwołanie sieci Web do listy **odwołań** .

Wybierz **odwołanie** , aby dodać odwołanie do projektu za pomocą okna dialogowego Dodaj odwołanie.

Wybierz pozycję **odwołanie sieci Web** , aby dodać odwołanie sieci Web do projektu za pomocą okna dialogowego **Dodaj odwołanie sieci Web** .

 **Usuń**

Wybierz co najmniej jedno odwołanie na liście **odwołań** , a następnie kliknij ten przycisk, aby go usunąć.

 **Aktualizuj odwołanie sieci Web**

Wybierz odwołanie sieci Web na liście **odwołań** i kliknij ten przycisk, aby go zaktualizować.

 **Zaimportowane przestrzenie nazw**

W tym polu można wpisać własną przestrzeń nazw, a następnie kliknąć pozycję **Dodaj Import użytkowników** , aby dodać go do listy przestrzeni nazw.

Można tworzyć aliasy dla przestrzeni nazw zaimportowanych przez użytkownika. W tym celu wprowadź alias i przestrzeń nazw w formacie *alias* = *przestrzeni nazw* aliasu. Jest to przydatne, jeśli używasz długich przestrzeni nazw, na przykład: `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http` .

 **Dodaj Import użytkownika**

Kliknij ten przycisk, aby dodać obszar nazw określony w polu **zaimportowane przestrzenie** nazw do listy importowanych przestrzeni nazw. Przycisk jest aktywny tylko wtedy, gdy określona przestrzeń nazw nie znajduje się już na liście.

 **Lista przestrzeni nazw**

Ta lista zawiera wszystkie dostępne przestrzenie nazw. Wybrane są pola wyboru dla przestrzeni nazw zawartych w projekcie.

 **Aktualizowanie importowania użytkowników**

Wybierz określoną przez użytkownika przestrzeń nazw na liście przestrzenie nazw, wpisz nazwę, która ma zostać zastąpiona w polu **zaimportowane przestrzenie nazw** , a następnie kliknij ten przycisk, aby przejść do nowej przestrzeni nazw. Przycisk jest aktywny tylko wtedy, gdy wybrany obszar nazw jest taki, który został dodany do listy za pomocą przycisku **Dodaj użytkownika importowania** . Możesz dodać:

- Klasy lub przestrzenie nazw, takie jak <xref:System.Math?displayProperty=fullName> .

- Importy aliasów, takie jak `VB=Microsoft.VisualBasic` .

- Przestrzenie nazw XML, takie jak `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">` .

## <a name="see-also"></a>Zobacz także

- [Zarządzanie odwołaniami w projekcie](../../ide/managing-references-in-a-project.md)
- [Instrukcje: Dodawanie lub usuwanie importowanych przestrzeni nazw (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)
- [Imports — Instrukcja (przestrzeń nazw XML)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)
