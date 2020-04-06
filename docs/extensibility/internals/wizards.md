---
title: Kreatorzy | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d65cf2dcc10380b0ac750c8e1b0e7fd56eab95b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703211"
---
# <a name="wizards"></a>Kreatory
Po utworzeniu kreatora zazwyczaj chcesz dodać go [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] do zintegrowanego środowiska programistycznego (IDE), aby inni mogli go używać. Dodany kreator pojawi się następnie w oknach dialogowych **Dodawanie nowego projektu** lub Dodawanie nowego **elementu.** Aby wyświetlić okna dialogowe **Dodawanie nowego projektu** lub Dodawanie nowego **elementu,** kliknij prawym przyciskiem myszy otwarte rozwiązanie w **Eksploratorze rozwiązań**, wskaż polecenie **Dodaj**, a następnie kliknij polecenie **Nowy projekt** lub Nowy **element**.

 Kreatory można [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zaimplementować, aby umożliwić użytkownikom wybranie z widoku drzewa dostępnych wartości po otwarciu okna dialogowego Dodawanie nowego **projektu** lub okna dialogowego Dodawanie nowego **elementu** lub po kliknięciu prawym przyciskiem myszy elementu w **Eksploratorze rozwiązań**.

 W kreatorze można podać opcję lokalizowania nazwy nowego projektu lub ites, a także określić ikonę, którą użytkownicy zobaczą po wybraniu kreatora. Można również kontrolować kolejność, w jakiej nowe elementy pojawiają się względem innych dostępnych elementów; elementy nie muszą być uporządkowane alfabetycznie.

 Można również podać kreatora, który uruchamia się inaczej, na podstawie parametrów niestandardowych, które są przekazywane do kreatora po jego otwarciu.

 Tematy w tej sekcji omówiono pliki, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] które można zaimplementować, aby spowodować **Dodawanie nowego projektu** i Dodaj nowy **element** okna dialogowe do listy kreatora wśród dostępnych kreatorów i szablonów i wymagania, które kreator musi spełniać, aby działać poprawnie w ŚRODOWISKU IDE.

## <a name="in-this-section"></a>W tej sekcji
- [Opis katalogu szablonu (pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 Zawiera omówienie plików opisu katalogu szablonów i wyjaśniono, jak działają one w IDE do wyświetlania folderów, kreatora plików vsz i plików szablonów, które są skojarzone z projektem w oknach dialogowych.

- [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

 W tym artykule wyjaśniono, jak ide uruchamia kreatorów i wyświetla listę trzech części pliku .vsz.

- [Interfejs kreatora (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 Opisuje `IDTWizard` interfejs, który kreatorzy muszą zaimplementować do pracy w IDE.

- [Parametry kontekstu](../../extensibility/internals/context-parameters.md)

 Wyjaśniono, jak kreatory są implementowane i co występuje, gdy IDE przekazuje parametry kontekstu do implementacji.

- [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md)

 W tym artykule wyjaśniono, jak używać parametrów niestandardowych do kontrolowania działania kreatora po uruchomieniu kreatora.

## <a name="related-sections"></a>Sekcje pokrewne
- [Project Types (Typy projektów)](../../extensibility/internals/project-types.md)

 Zawiera łącza do dodatkowych tematów, które oferują informacje dotyczące sposobu projektowania nowych typów projektów.

- [Rozszerzanie projektów](../../extensibility/extending-projects.md)

 W tym [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] artykule opisano, jak używać projektów i rozwiązań do organizowania plików kodu i plików zasobów oraz jak zaimplementować kontrolę źródła.
