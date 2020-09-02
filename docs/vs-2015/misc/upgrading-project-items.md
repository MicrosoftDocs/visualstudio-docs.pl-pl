---
title: Uaktualnianie elementów projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project items
- projects [Visual Studio SDK], upgrading items
- project items [Visual Studio], upgrading
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: eb3619e187c7856cf03ee60c8a04cbe527bf0a69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698682"
---
# <a name="upgrading-project-items"></a>Uaktualnianie elementów projektu
W przypadku dodawania elementów i zarządzania nimi w systemach projektów, które nie zostały wdrożone, może być konieczne uczestnictwo w procesie uaktualniania projektu. Crystal Reports to przykład elementu, który można dodać do systemu projektu.  
  
 Zazwyczaj implementujący elementy projektu chcą korzystać z już w pełni skonkretyzowanych i uaktualnionych projektów, ponieważ chcą wiedzieć, jakie są odwołania do projektu i jakie inne właściwości projektu mają być podejmowane w celu podjęcia decyzji o uaktualnieniu.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Aby uzyskać powiadomienie o uaktualnieniu projektu  
  
1. Ustaw <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> flagę (zdefiniowaną w vsshell80. idl) w implementacji elementu projektu. Powoduje to automatyczne ładowanie elementu projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , gdy powłoka ustali, że system projektu jest w trakcie uaktualniania.  
  
2. Doradzanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfejsem za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> metody.  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>Interfejs jest uruchamiany po zakończeniu wykonywania operacji uaktualniania przez implementację systemu projektu i zostanie utworzony nowy uaktualniony projekt. W zależności od scenariusza <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfejs jest uruchamiany po <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> metodzie, lub.  
  
### <a name="to-upgrade-the-project-item-files"></a>Aby uaktualnić pliki elementów projektu  
  
1. Należy dokładnie zarządzać procesem tworzenia kopii zapasowej plików w implementacji elementu projektu. Ma to zastosowanie w szczególności w przypadku kopii zapasowej równoległej, gdzie `fUpgradeFlag` parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metody jest ustawiony na <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> , gdzie pliki, których kopia zapasowa została utworzona, są umieszczane na plikach, które są oznaczone jako ". old". Kopie zapasowe plików starszej niż czas systemowy, po uaktualnieniu projektu, można wyznaczyć jako nieodświeżone. Ponadto mogą zostać nadpisywane, chyba że podejmujesz konkretne czynności, aby tego uniknąć.  
  
2. Po otrzymaniu przez element projektu powiadomienia o uaktualnieniu projektu zostanie wyświetlony **Kreator konwersji programu Visual Studio** . W związku z tym należy używać metod <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interfejsu do udostępniania komunikatów uaktualniania do interfejsu użytkownika kreatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator konwersji programu Visual Studio](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Uaktualnianie projektów niestandardowych](../misc/upgrading-custom-projects.md)