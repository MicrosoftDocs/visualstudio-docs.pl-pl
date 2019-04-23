---
title: Strona odwołań, Projektant (Visual Basic) projektu | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dd579e6bf434903ecc1e2fe60b1e62d54c165034
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60114369"
---
# <a name="references-page-project-designer-visual-basic"></a>Strona odwołań, Projektant projektu (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Użyj **odwołania** strony **projektanta projektu** Zarządzanie odwołania, odwołania sieci Web i importowanych przestrzeni nazw w projekcie. Projekty mogą zawierać odwołania do składników modelu COM, usług sieci Web XML, zestawów i biblioteki klas .NET Framework lub inne biblioteki klas. Aby uzyskać więcej informacji na temat korzystania z odwołań, zobacz [Zarządzanie odwołaniami w projekcie](../../ide/managing-references-in-a-project.md).  
  
 Aby uzyskać dostęp do **odwołania** wybierz węzeł projektu (nie **rozwiązania** węzła) w **Eksploratora rozwiązań**. Następnie wybierz **projektu**, **właściwości** na pasku menu. Gdy pojawi się w Projektancie projektu, kliknij przycisk **odwołania** kartę.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 Poniższe opcje umożliwiają zaznacz lub usuń odwołania i importowanych przestrzeni nazw w projekcie.  
  
 **Nieużywane odwołania**  
 Kliknij ten przycisk, aby uzyskać dostęp do **odwołań nieużywanych** okno dialogowe.  
  
 **Odwołań nieużywanych** okno dialogowe umożliwia usunięcie odwołań, które są zawarte w projekcie, ale bez faktycznego używane przez kod. Zawiera on siatki, zawierającego **Nazwa odwołania**, **ścieżki**oraz inne informacje o odwołaniach do nieużywanych przestrzeni nazw w projekcie. W siatce, wybierz odwołania do przestrzeni nazw, które chcesz usunąć z projektu, a następnie kliknij przycisk **Usuń**.  
  
 **Ścieżki odwołania**  
 Kliknij ten przycisk, aby uzyskać dostęp do **ścieżki odwołania** okno dialogowe.  
  
> [!NOTE]
>  Jeśli system projektu znajdzie odwołania do zestawu, system rozwiązuje odwołania przez wyszukiwanie w następujących lokalizacjach, w następującej kolejności:  
> 
> 1. Folder projektu. Pliki folderu projektu pojawiają się w **Eksploratora rozwiązań** podczas **Pokaż wszystkie pliki** nie ma zastosowania.  
>    2. Foldery, które są określone w **ścieżki odwołania** okno dialogowe.  
>    3. Foldery zawierające pliki w **Dodaj odwołanie** okno dialogowe.  
>    4. Folder obj tego projektu. (Po dodaniu do projektu odwołanie COM, jeden lub więcej zestawów można dodać do folderu obj projektu.)  
  
 **Odwołania**  
 Ta lista zawiera wszystkie odwołania w projekcie, używane lub nieużywane.  
  
 **Add**  
 Kliknij ten przycisk, aby dodać odwołania lub odwołania sieci Web do **odwołania** listy.  
  
 Wybierz **odwołania** można dodać odwołania do projektu przy użyciu okna dialogowego Dodaj odwołanie.  
  
 Wybierz **odwołania sieci Web** można dodać odwołania sieci Web do projektu przy użyciu okna dialogowego Dodaj odwołanie sieci Web.  
  
 **Usuń**  
 Wybierz jedno lub więcej odwołań w **odwołania** listy, a następnie kliknij ten przycisk, aby go usunąć.  
  
 **Aktualizuj odwołanie sieci Web**  
 Wybierz odwołanie sieci Web w **odwołania** listy i kliknij ten przycisk, aby go zaktualizować.  
  
 **Importowane przestrzenie nazw**  
 Można wpisać własny obszar nazw, w tym polu i kliknij przycisk **dodać Import użytkownika** ją dodać do listy obszarów nazw.  
  
 Możesz tworzyć aliasy dla importowanych przestrzeni nazw. Aby to zrobić, wprowadź alias i przestrzeni nazw w formacie *alias*=*przestrzeni nazw*. Jest to przydatne, jeśli używasz długich nazw, na przykład: `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`.  
  
 **Dodaj Import użytkownika**  
 Kliknij ten przycisk, aby dodać przestrzeń nazw określona w **zaimportowane przestrzenie nazw** pole do listy importowanych przestrzeni nazw. Ten przycisk jest aktywny tylko wtedy, gdy w określonej przestrzeni nazw nie jest już na liście.  
  
 **Lista przestrzeni nazw**  
 Ta lista zawiera wszystkich dostępnych przestrzeni nazw. Zaznaczone są pola wyboru dla przestrzeni nazw zawartym w projekcie.  
  
 **Importowanie użytkowników aktualizacji**  
 Wybierz przestrzeń nazw określonych przez użytkownika na liście przestrzeni nazw, wpisz nazwę, którą chcesz zamienić go w **zaimportowane przestrzenie nazw** , a następnie kliknij ten przycisk, aby przejść do nowej przestrzeni nazw. Przycisk jest aktywny tylko wtedy, gdy w wybranej przestrzeni nazw to taki, który zostanie dodany do listy przy użyciu **dodać Import użytkownika** przycisku. Możesz dodać:  
  
- Klas lub przestrzeni nazw, takich jak <xref:System.Math?displayProperty=fullName>.  
  
- Importuje aliasem, takich jak `VB=Microsoft.VisualBasic`.  
  
- Obszary nazw XML, takie jak `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`.  
  
## <a name="see-also"></a>Zobacz też  
 [NIB jak: Dodawanie lub usuwanie odwołań za pomocą okno dialogowe Dodawanie odwołania](http://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Instrukcje: Dodawanie lub usuwanie importowanych przestrzeni nazw (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)   
 [NIB: Dodaj odwołanie sieci Web, okno dialogowe](http://msdn.microsoft.com/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)   
 [Imports, instrukcja (przestrzeń nazw XML)](http://msdn.microsoft.com/library/1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4)
