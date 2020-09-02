---
title: Rozszerzanie przybornika | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686934"
---
# <a name="extending-the-toolbox"></a>Rozszerzanie przybornika
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Przybornik** zawiera kolekcję obiektów, które zapewniają funkcjonalność dla edytorów i projektantów za pomocą mechanizmu przeciągania i upuszczania w środowisku IDE.  
  
 Istnieją dwa podstawowe sposoby, w których pakietu VSPackage współpracuje z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **przybornikiem**:  
  
- Pakietu VSPackage może dodawać nowe elementy danych i kontrolki do **przybornika**.  
  
- Pakietu VSPackage może być obiektem docelowym lub konsumentem istniejącej funkcji **przybornika** , obsługę operacji przeciągania i upuszczania oraz konfigurowania wyglądu **przybornika**.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Tworzenie kontrolki przybornika korzystającej z Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md)  
 Zawiera opis tworzenia kontrolki przybornika przy użyciu szablonu kontrolki przybornika Windows Forms.  
  
 [Tworzenie kontrolki przybornika WPF](../extensibility/creating-a-wpf-toolbox-control.md)  
 Zawiera opis tworzenia kontrolki przybornika przy użyciu szablonu kontrolki przybornika WPF.  
  
 [Zarządzanie przybornikiem](../misc/managing-the-toolbox.md)  
 Opisuje, w jaki sposób pakietu VSPackage może zarządzać zawartością i wyglądem **przybornika**.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instrukcje: Zarządzanie oknem przybornika](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
 Opisuje, jak korzystać z **przybornika** w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanym środowisku programistycznym (IDE).  
  
 [Instrukcje: kontrolowanie przybornika](https://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599)  
 Opisuje sposób zarządzania **przybornikiem** przy użyciu modelu programowania automatyzacji.  
  
 [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Wyjaśnia, jak używać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usług do tworzenia elementów interfejsu użytkownika, które pasują do pozostałej części [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .