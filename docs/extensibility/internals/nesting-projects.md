---
title: Zagnieżdżanie projektów | Microsoft Docs
description: Dowiedz się więcej na temat zagnieżdżania projektów, dzięki którym deweloperzy aplikacji korzystający z pakietu VSPackage mogą grupować podobne typy projektów w programie Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 464538d7f7be68737715cb6fd10fda4017a5556a
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876665"
---
# <a name="nesting-projects"></a>Zagnieżdżanie projektów
Deweloperzy aplikacji korporacyjnych korzystających z pakietu programu VS mogą wygodnie grupować podobne typy projektów w programie przy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] użyciu *zagnieżdżania projektów*. Na przykład projekt szablon przedsiębiorstwa używa zagnieżdżonych projektów do grupowania projektów w kategorii. Projekty fasady biznesowej, projekty interfejsu użytkownika sieci Web i tak dalej są pogrupowane w jednej kategorii.

 W tym scenariuszu nie ma żadnego limitu liczby projektów, które deweloper może zagnieżdżać w każdym projekcie nadrzędnym, Chociaż deweloper może programowo wprowadzić limity. Ten typ grupowania może również spowodować cykliczność, w takim przypadku projekty tego samego typu co projekt podrzędny mogą być zagnieżdżane w elemencie podrzędnym, aby stał się podprojektem elementu podrzędnego, który jest podprojektem elementu nadrzędnego.

 Zagnieżdżanie projektu nie jest częścią wewnętrzną [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Należy napisać kod w celu włączenia zagnieżdżania i zagnieżdżania projektu w ramach projektów podrzędnych. Projekt nadrzędny jest specjalnym pakietu VSPackage lub typem projektu, utworzonym i zarejestrowanym przy użyciu własnego identyfikatora GUID, który zawiera kod, który jest wymagany do wdrożenia zagnieżdżania projektu.

 Przykład sposobu zagnieżdżania projektów można znaleźć w temacie [How to: Implementuj zagnieżdżone projekty](../../extensibility/internals/how-to-implement-nested-projects.md).

## <a name="nested-projects-example"></a>Przykład zagnieżdżonych projektów
 ![Rozwiązanie zagnieżdżonych projektów](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects") Przykład zagnieżdżonych projektów

## <a name="see-also"></a>Zobacz też
- [Zagadnienia dotyczące zwalniania i ponownego ładowania zagnieżdżonych projektów](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Obsługa kreatora dla zagnieżdżonych projektów](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)
- [Implementowanie obsługi poleceń dla zagnieżdżonych projektów](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrowanie okna dialogowego Dodawanie elementu dla projektów zagnieżdżonych](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parametry kontekstu](../../extensibility/internals/context-parameters.md)
- [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
