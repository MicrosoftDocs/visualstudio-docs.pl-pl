---
title: Rozszerzanie przybornika | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- tools [Visual Studio], Toolbox
- Toolbox [Visual Studio SDK]
ms.assetid: bb84a79e-cd4c-4a58-8871-2513e7119b6e
caps.latest.revision: 38
manager: jillfra
ms.openlocfilehash: ddf67fba3ae603dbd31d4628c61a6f14cc2441c4
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686934"
---
# <a name="extending-the-toolbox"></a>Rozszerzanie przybornika
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Przybornika** zawiera kolekcję obiektów, które zapewniać funkcje w edytorach i projektantach za pośrednictwem mechanizmu przeciągania i upuszczania środowiska IDE.  
  
 Istnieją dwa podstawowe sposoby, w których pakietu VSPackage współpracuje z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **przybornika**:  
  
- Pakietu VSPackage można dodać nowe elementy danych i kontrole w celu **przybornika**.  
  
- Pakietu VSPackage może być docelowego lub konsumenta istniejących **przybornika** funkcji obsługi operacji przeciągania i upuszczania oraz konfigurowanie **przybornika**firmy wygląd.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Tworzenie kontrolki przybornika korzystającej z Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md)  
 W tym artykule opisano się do tworzenia kontrolki przybornika za pomocą szablonu kontrolki formularzy Windows Forms przybornika.  
  
 [Tworzenie kontrolki przybornika WPF](../extensibility/creating-a-wpf-toolbox-control.md)  
 W tym artykule opisano się do tworzenia kontrolki przybornika za pomocą szablonu kontrolki przybornika WPF.  
  
 [Zarządzanie przybornika](../misc/managing-the-toolbox.md)  
 W tym artykule opisano, jak zarządzać pakietu VSPackage zawartość i wygląd **przybornika**.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instrukcje: Zarządzanie oknem przybornika](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
 W tym artykule opisano sposób pracy z **przybornika** w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE).  
  
 [Instrukcje: Kontrolowanie przybornika](https://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599)  
 W tym artykule opisano sposób zarządzania **przybornika** za pomocą modelu programowania usługi automation.  
  
 [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Opis sposobu użycia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usługi, aby tworzyć elementy interfejsu użytkownika, które pasują reszty [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].