---
title: Projekty zagnieżdżania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 814780fa8e7e57a022a75b2e09115cfa55a1b8be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707029"
---
# <a name="nesting-projects"></a>Zagnieżdżanie projektów
Deweloperzy aplikacji korporacyjnych, którzy korzystają z pakietu VS [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] można wygodnie grupować podobne typy projektów razem za pomocą *zagnieżdżania projektu*. Na przykład projekt Szablon przedsięwzięcia używa projektów zagnieżdżonych do grupowania projektów w kategorie. Projekty fasady biznesowej, projekty interfejsu użytkownika sieci Web i tak dalej są zgrupowane w jednej kategorii.

 W tym scenariuszu nie ma limitu liczby projektów dewelopera można zagnieżdżać w ramach każdego projektu nadrzędnego, chociaż deweloper może programowo podać limity. Ten typ grupowania można również rekursywne, w którym to przypadku projekty tego samego typu jako projekt podrzędny mogą być zagnieżdżone pod elementem podrzędnym, aby stać się podprojektem podrzędnym, który jest podprojektem nadrzędnego.

 Zagnieżdżanie projektu nie jest [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]nieodłączną częścią programu . Musisz napisać kod, aby włączyć zagnieżdżanie i zagnieżdżanie podprojektu w projektach podrzędnych. Projekt nadrzędny jest specjalny VSPackage lub typ projektu, utworzony i zarejestrowany z własnym identyfikatorem GUID, który zawiera kod, który jest wymagany do zaimplementowania projektu.

 Przykład dotyczący sposobu zagnieżdżania projektów można znaleźć w programie [Jak: Implementowanie projektów zagnieżdżonych](../../extensibility/internals/how-to-implement-nested-projects.md).

## <a name="nested-projects-example"></a>Przykład projektów zagnieżdżonych
 ![Rozwiązanie dla projektów zagnieżdżonych](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects") Przykład projektów zagnieżdżonych

## <a name="see-also"></a>Zobacz też
- [Zagadnienia dotyczące zwalniania i ponownego ładowania zagnieżdżonych projektów](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Obsługa kreatora dla zagnieżdżonych projektów](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)
- [Implementowanie obsługi poleceń dla zagnieżdżonych projektów](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrowanie okna dialogowego Dodawanie elementu dla projektów zagnieżdżonych](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parametry kontekstu](../../extensibility/internals/context-parameters.md)
- [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
