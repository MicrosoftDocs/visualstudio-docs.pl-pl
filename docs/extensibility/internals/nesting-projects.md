---
title: Zagnieżdżanie projektów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2e05b47563c62f34e4a01c945a45d5c7ec069ee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909486"
---
# <a name="nesting-projects"></a>Zagnieżdżanie projektów
Deweloperom aplikacji dla przedsiębiorstw, którzy korzystają z pakietu programu VS wygodnie można grupować podobne typy projektów w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przy użyciu *projektu zagnieżdżanie*. Na przykład projekt szablonu organizacji używa zagnieżdżonych projektów i projektów grupy na kategorie. Projekty fasady biznesowe, projekty interfejsu użytkownika sieci Web i tak dalej są zgrupowane razem w jednej kategorii.

 W tym scenariuszu nie ma żadnego limitu liczby projekty, do których Deweloper można zagnieździć w każdym projekcie nadrzędnego, mimo że deweloper może programowo limitami. Tego rodzaju grupowania można również wprowadzić rekursywny, w którym to przypadku projekty tego samego typu co projekt podrzędny może być zagnieżdżona w taki sposób, w obszarze podrzędny stają się podprojekt elementu podrzędnego, który jest podprojektem elementu nadrzędnego.

 Zagnieżdżanie projektów nie jest wewnętrzna część [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Trzeba napisać kod, aby włączyć zagnieżdżanie i subproject zagnieżdżenia w obrębie projektów podrzędnych. Projekt nadrzędny jest VSPackage specjalne lub typ projektu, utworzona i zarejestrowana przy użyciu swój własny identyfikator GUID, który zawiera kod, który jest wymagany do zaimplementowania zagnieżdżanie projektów.

 Przykładem zagnieżdżonych projektów można znaleźć w przykładowym projekcie Example.Nested C#.

## <a name="nested-projects-example"></a>Przykład zagnieżdżonych projektów
 ![Zagnieżdżone projektów rozwiązania](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects") przykładowe projekty zagnieżdżone

## <a name="see-also"></a>Zobacz też
- [Instrukcje: implementowanie zagnieżdżonych projektów](../../extensibility/internals/how-to-implement-nested-projects.md)
- [Zagadnienia dotyczące zwalniania i ponownego ładowania zagnieżdżonych projektów](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Obsługa kreatora dla zagnieżdżonych projektów](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)
- [Implementowanie obsługi poleceń dla zagnieżdżonych projektów](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrowanie okna dialogowego Dodawanie elementu dla projektów zagnieżdżonych](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parametry kontekstu](../../extensibility/internals/context-parameters.md)
- [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)