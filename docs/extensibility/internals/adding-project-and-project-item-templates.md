---
title: Dodawanie projektów i szablonów elementów projektu | Microsoft Docs
description: Dowiedz się więcej na temat dodawania szablonów projektu i elementów projektu do okien dialogowych w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e97b04294f0545c378210d39f343f3b009b6d15
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190177"
---
# <a name="add-project-and-project-item-templates"></a>Dodaj projekty i szablony elementów projektu
Podczas tworzenia własnych typów projektów należy zapewnić obsługę dodawania nowych projektów i elementów projektu przy użyciu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] okien dialogowych standardowego zintegrowanego środowiska programistycznego (IDE). W poniższych tematach omówiono różne techniki dodawania projektów i elementów projektu.

## <a name="in-this-section"></a>W tej sekcji
- [Kontekst projektu](../../extensibility/internals/project-context.md)

 Wyjaśniono, że projekt zawiera większość informacji kontekstowych transpires w środowisku.

- [Priorytet projektu](../../extensibility/internals/project-priority.md)

 W tym artykule wyjaśniono, że element projektu jest zwykle członkiem jednego projektu, aby uniknąć niejednoznaczności dotyczącej tego, który projekt jest używany do otwierania elementu.

- [Projekt różnych plików](../../extensibility/internals/miscellaneous-files-project.md)

 Zawiera informacje o dwóch typach edytorów, których można użyć do otwierania plików w projekcie i roli, w której jest tworzony projekt w celu określenia edytora, który ma być używany podczas otwierania elementu projektu.

- [Rejestruj szablony projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)

 Wyjaśnia, co się dzieje po [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utworzeniu projektu.

- [Dodaj elementy do okna dialogowego Dodaj nowy element](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 Wyjaśnia proces dodawania elementów do okna dialogowego **Dodaj nowy element** .

- [Dodawanie katalogów do okna dialogowego Nowy projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 Zawiera przykład rejestrowania nowego katalogu zawierającego szablony niestandardowe udostępniane przez pakietu VSPackage.

- [Dodawanie katalogów do okna dialogowego Dodaj nowy element](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 Zawiera przykład rejestrowania nowego zestawu katalogów w oknie dialogowym **Dodaj nowy element** .

- [Polecenia zdefiniowane w środowisku IDE służące do rozszerzania systemów projektów](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 Wyświetla listę różnych typów elementów poleceń używanych do rozszerzania systemów projektów.

- [CATID dla obiektów, które są zwykle używane do rozszerania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 Wyświetla listę CATID dla obiektów, które są używane do rozbudowania [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] , [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] systemu projektu.

## <a name="related-sections"></a>Sekcje pokrewne
- [Instrukcje: otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md)

 Zawiera instrukcje krok po kroku dotyczące otwierania elementu w sposób wewnętrzny do określonego edytora dla projektu.

- [Instrukcje: otwieranie edytorów standardowych](../../extensibility/how-to-open-standard-editors.md)

 Zawiera instrukcje krok po kroku dotyczące otwierania edytora standardowego.

- [Podtypy projektu](../../extensibility/internals/project-subtypes.md)

 Zawiera łącza do tematów pojęciowych podtypów projektu. Podtypy projektu poszerzają istniejące [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projekty.

- [Typy projektów](../../extensibility/internals/project-types.md)

 Zawiera łącza do dodatkowych tematów, które zawierają informacje o sposobach projektowania nowych typów projektów.
