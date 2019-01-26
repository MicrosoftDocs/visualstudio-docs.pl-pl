---
title: Dodawanie projektu i szablony elementów projektu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8315626f346a96d907686e009af006e2170e072c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929565"
---
# <a name="add-project-and-project-item-templates"></a>Dodaj projekt oraz szablony elementów projektu
Podczas tworzenia własnych typów projektu musi udostępniać pomoc techniczną do dodawania nowych projektów i elementów projektu przy użyciu standardu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrated development środowiska (IDE), okno dialogowe. W poniższych tematach omówiono różne techniki dodawanie projektów i elementów projektu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kontekst projektu](../../extensibility/internals/project-context.md)  
 W tym artykule wyjaśniono, że projekt zawiera większość informacje kontekstu co wynika w środowisku.  
  
 [Priorytet projektu](../../extensibility/internals/project-priority.md)  
 Wyjaśnia, że element projektu jest zazwyczaj członkiem jeden projekt, aby uniknąć niejednoznaczności, o tym, które projektu jest używany, aby otworzyć element.  
  
 [Projekt różne pliki](../../extensibility/internals/miscellaneous-files-project.md)  
 Zawiera informacje o dwa rodzaje edytory, które mogą służyć do otwierania plików w projekcie i rolę, że projekt jest odtwarzany w określeniu, edytor, którego chce używać po otwarciu elementu projektu.  
  
 [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)  
 Wyjaśnia, co występuje, gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projekt zostanie utworzony.  
  
 [Dodawanie elementów do okna dialogowego Dodaj nowy element](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Opisano proces dodawania elementów do **Dodaj nowy element** okno dialogowe.  
  
 [Dodawanie katalogów do okna dialogowego Nowy projekt pola](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Przykład rejestrowania nowy katalog, który zawiera szablony niestandardowe, udostępniane przez pakietu VSPackage.  
  
 [Dodawanie katalogów do okna dialogowego Dodaj nowy element](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Stanowi przykład rejestrowanie nowego zestawu katalogów **Dodaj nowy element** okno dialogowe.  
  
 [Polecenia definiowane w środowisku IDE do rozszerzania systemów projektu](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Wyświetla listę różnych typów elementów polecenia używane do rozszerzania systemów projektu.  
  
 [Identyfikatorów CatID obiektów, które zwykle służą do rozszerzania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Wyświetla listę identyfikatorów CatID obiektów, które służą do rozszerzania [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] systemy projektów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instrukcje: Otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md)  
 Instrukcje krok po kroku do otwierania elementu wewnętrznie powiązany z określonego edytora dla projektu.  
  
 [Instrukcje: Otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)  
 Instrukcje krok po kroku do otwierania Edytora standardowego.  
  
 [Podtypy projektów](../../extensibility/internals/project-subtypes.md)  
 Zawiera łącza do tematów pojęciowych podtypu projektu. Podtypy projektów rozszerzyć istniejące [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektów.  
  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 Zawiera łącza do dodatkowych tematów, które oferują informacji na temat sposobu projektowania nowych typów projektów.