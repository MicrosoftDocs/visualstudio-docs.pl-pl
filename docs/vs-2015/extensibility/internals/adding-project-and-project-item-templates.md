---
title: Dodawanie projektów i szablonów elementów projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b68c9f4bbaed73603c46fc0beab77a308b8933d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203859"
---
# <a name="adding-project-and-project-item-templates"></a>Dodawanie szablonów projektów i elementów projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podczas tworzenia własnych typów projektów należy zapewnić obsługę dodawania nowych projektów i elementów projektu przy użyciu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] okien dialogowych standardowego zintegrowanego środowiska programistycznego (IDE). W poniższych tematach omówiono różne techniki dodawania projektów i elementów projektu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kontekst projektu](../../extensibility/internals/project-context.md)  
 Wyjaśniono, że projekt zawiera większość informacji kontekstowych transpires w środowisku.  
  
 [Priorytet projektu](../../extensibility/internals/project-priority.md)  
 W tym artykule wyjaśniono, że element projektu jest zwykle członkiem jednego projektu, aby uniknąć niejednoznaczności dotyczącej tego, który projekt jest używany do otwierania elementu.  
  
 [Projekt Różne pliki](../../extensibility/internals/miscellaneous-files-project.md)  
 Zawiera informacje o dwóch typach edytorów, których można użyć do otwierania plików w projekcie i roli, w której jest tworzony projekt w celu określenia edytora, który ma być używany podczas otwierania elementu projektu.  
  
 [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)  
 Wyjaśnia, co się dzieje po [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] utworzeniu projektu.  
  
 [Dodawanie elementów do okien dialogowych Dodawanie nowego elementu](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Wyjaśnia proces dodawania elementów do okna dialogowego **Dodaj nowy element** .  
  
 [Dodawanie katalogów do okna dialogowego Nowy projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Zawiera przykład rejestrowania nowego katalogu zawierającego szablony niestandardowe udostępniane przez pakietu VSPackage.  
  
 [Dodawanie katalogów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Zawiera przykład rejestrowania nowego zestawu katalogów w oknie dialogowym **Dodaj nowy element** .  
  
 [Polecenia definiowane w środowisku IDE do rozszerzania systemów projektu](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Wyświetla listę różnych typów elementów poleceń używanych do rozszerzania systemów projektów.  
  
 [Identyfikatory CATID obiektów, które są zwykle używane do rozszerzania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Wyświetla listę CATID dla obiektów, które są używane do rozbudowania [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] , [!INCLUDE[csprcs](../../includes/csprcs-md.md)] i [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] systemu projektu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instrukcje: otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md)  
 Zawiera instrukcje krok po kroku dotyczące otwierania elementu w sposób wewnętrzny do określonego edytora dla projektu.  
  
 [Instrukcje: otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)  
 Zawiera instrukcje krok po kroku dotyczące otwierania edytora standardowego.  
  
 [Podtypy projektów](../../extensibility/internals/project-subtypes.md)  
 Zawiera łącza do tematów pojęciowych podtypów projektu. Podtypy projektu poszerzają istniejące [!INCLUDE[csprcs](../../includes/csprcs-md.md)] i [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projekty.  
  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 Zawiera łącza do dodatkowych tematów, które zawierają informacje o sposobach projektowania nowych typów projektów.
