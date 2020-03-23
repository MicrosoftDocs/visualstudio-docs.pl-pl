---
title: Strona odwołań, Projektant projektu (Visual Basic)
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
ms.openlocfilehash: b80427999ad841c493e61cd704b64435f81c3914
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565607"
---
# <a name="references-page-project-designer-visual-basic"></a>Strona odwołań, Projektant projektu (Visual Basic)

Strona **Odwołania projektanta** **projektu** służy do zarządzania odwołaniami, odwołaniami do sieci Web i zaimportowanymi obszarami nazw w projekcie. Projekty mogą zawierać odwołania do składników COM, usług internetowych XML, bibliotek lub zestawów .NET lub innych bibliotek klas. Aby uzyskać więcej informacji na temat używania odwołań, zobacz [Zarządzanie odwołaniami w projekcie](../../ide/managing-references-in-a-project.md).

Aby uzyskać dostęp do strony **Odwołania,** wybierz węzeł projektu (a nie węzeł **Rozwiązanie)** w **Eksploratorze rozwiązań**. Następnie wybierz polecenie **Projekt**, **Właściwości** na pasku menu. Po wyświetleniu projektanta projektu kliknij kartę **Odwołania.**

## <a name="uielement-list"></a>Lista elementów UI

Poniższe opcje umożliwiają zaznaczanie lub usuwanie odwołań i importowanych obszarów nazw w projekcie.

**Ścieżki referencyjne**

Kliknij ten przycisk, aby uzyskać dostęp do okna dialogowego **Ścieżki odwołań.**

> [!NOTE]
> Gdy system projektu znajdzie odwołanie do zestawu, system rozpoznaje odwołanie, patrząc w następujących lokalizacjach, w następującej kolejności:
>
> 1. Folder projektu. Pliki folderów projektu są wyświetlane w **Eksploratorze rozwiązań,** gdy nie obowiązuje program **Pokaż wszystkie pliki.**
> 2. Foldery określone w oknie dialogowym **Ścieżki odwołań.**
> 3. Foldery, które wyświetlają pliki w oknie dialogowym **Dodawanie odwołania.**
> 4. W folderze obj projektu. (Po dodaniu odwołania COM do projektu, co najmniej jedno zestawy mogą zostać dodane do folderu obj projektu.)

 **Odwołania**

Ta lista zawiera wszystkie odwołania w projekcie, używane lub nieużywane.

 **Dodaj**

Kliknij ten przycisk, aby dodać odwołanie lub odwołanie do listy **Odwołania.**

Wybierz **pozycję Odwołanie,** aby dodać odwołanie do projektu za pomocą okna dialogowego Dodawanie odwołania.

Wybierz pozycję Odwołanie do **sieci Web,** aby dodać odwołanie do projektu za pomocą okna dialogowego **Dodawanie odwołania do sieci Web.**

 **Usuń**

Wybierz jedno lub więcej odwołań na liście **Odwołania,** a następnie kliknij ten przycisk, aby je usunąć.

 **Aktualizowanie odwołania do sieci Web**

Wybierz odwołanie do sieci Web na liście **Odwołania** i kliknij ten przycisk, aby go zaktualizować.

 **Importowane przestrzenie nazw**

W tym polu możesz wpisać własną przestrzeń nazw i kliknąć przycisk **Dodaj import użytkowników,** aby dodać go do listy obszarów nazw.

Można tworzyć aliasy dla obszarów nazw importowanych przez użytkowników. Aby to zrobić, wprowadź alias i obszar nazw w obszarze *nazw aliasu*=*formatu*. Jest to przydatne, jeśli używasz długich `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`przestrzeni nazw, na przykład: .

 **Dodaj import użytkownika**

Kliknij ten przycisk, aby dodać obszar nazw określony w polu **Importowane przestrzenie nazw** do listy importowanych obszarów nazw. Przycisk jest aktywny tylko wtedy, gdy określony obszar nazw nie jest jeszcze na liście.

 **Lista obszarów nazw**

Ta lista zawiera wszystkie dostępne przestrzenie nazw. Zostaną zaznaczone pola wyboru dla obszarów nazw uwzględnionych w projekcie.

 **Aktualizuj import użytkownika**

Wybierz obszar nazw określony przez użytkownika na liście obszarów nazw, wpisz nazwę, którą chcesz zastąpić w polu **Importowane przestrzenie nazw,** a następnie kliknij ten przycisk, aby zmienić ją na nowy obszar nazw. Przycisk jest aktywny tylko wtedy, gdy wybrany obszar nazw jest obszarem dodanym do listy za pomocą przycisku **Dodaj importowanie użytkowników.** Można dodać:

- Klasy lub przestrzenie nazw, takie jak <xref:System.Math?displayProperty=fullName>.

- Import aliasów, na `VB=Microsoft.VisualBasic`przykład .

- Przestrzenie nazw XML, `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`takie jak .

## <a name="see-also"></a>Zobacz też

- [Zarządzanie odwołaniami w projekcie](../../ide/managing-references-in-a-project.md)
- [Instrukcje: Dodawanie lub usuwanie importowanych przestrzeni nazw (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)
- [Imports, instrukcja (przestrzeń nazw XML)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)
