---
title: Dodawanie szablonów elementów projektu i projektu | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 14eb1a9e2e63fa6e63d3ba2efa4426421e6b5593
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710208"
---
# <a name="add-project-and-project-item-templates"></a>Dodawanie szablonów elementów projektu i projektu
Podczas tworzenia własnych typów projektów, należy zapewnić obsługę dodawania nowych projektów [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i elementów projektu przy użyciu standardowych okien dialogowych zintegrowanego środowiska programistycznego (IDE). W poniższych tematach omówiono różne techniki dodawania projektów i elementów projektu.

## <a name="in-this-section"></a>W tej sekcji
- [Kontekst projektu](../../extensibility/internals/project-context.md)

 Wyjaśnia, że projekt zawiera większość informacji kontekstowych dla tego, co dzieje się w środowisku.

- [Priorytet projektu](../../extensibility/internals/project-priority.md)

 Wyjaśnia, że element projektu jest zwykle członkiem jednego projektu, aby uniknąć niejednoznaczności, który projekt jest używany do otwierania elementu.

- [Projekt Różne pliki](../../extensibility/internals/miscellaneous-files-project.md)

 Zawiera informacje o dwóch typach edytorów, które mogą być używane do otwierania plików w projekcie i roli, jaką odgrywa projekt w określaniu edytora, który ma być używany podczas otwierania elementu projektu.

- [Rejestrowanie szablonów projektów i towarów](../../extensibility/internals/registering-project-and-item-templates.md)

 Wyjaśnia, co [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] występuje podczas tworzenia projektu.

- [Dodawanie elementów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 W tym artykule wyjaśniono proces dodawania elementów do okna dialogowego **Dodawanie nowego elementu.**

- [Dodawanie katalogów do okna dialogowego Nowy projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 Zawiera przykład rejestrowania nowego katalogu, który zawiera szablony niestandardowe udostępnione przez VSPackage.

- [Dodawanie katalogów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 Zawiera przykład rejestrowania nowego zestawu katalogów dla okna dialogowego **Dodawanie nowego elementu.**

- [Polecenia zdefiniowane przez IDE do rozszerzania systemów projektowych](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 Wyświetla listę różnych typów elementów poleceń używanych do rozszerzania systemów projektu.

- [Catidy dla obiektów, które są zwykle używane do rozszerzania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 Wyświetla listę identyfikatorów CATID dla [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]obiektów, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] które są używane do rozszerzania , i systemów projektu.

## <a name="related-sections"></a>Powiązane sekcje
- [Jak: Otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md)

 Zawiera instrukcje krok po kroku dotyczące otwierania elementu wewnętrznie powiązanego z określonym edytorem dla projektu.

- [Jak: Otwórz edytory standardowe](../../extensibility/how-to-open-standard-editors.md)

 Zawiera instrukcje krok po kroku dotyczące otwierania standardowego edytora.

- [Podtypy projektu](../../extensibility/internals/project-subtypes.md)

 Zawiera łącza do tematów koncepcyjnych podtypu projektu. Podtypy projektu [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] rozszerzają istniejące i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projekty.

- [Typy projektów](../../extensibility/internals/project-types.md)

 Zawiera łącza do dodatkowych tematów, które oferują informacje dotyczące sposobu projektowania nowych typów projektów.
