---
title: Dostarczanie Cofnij pomocy technicznej do projektantów | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9118cbe3f4a8dcee443eca8b3fa5fb9a7664fd41
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60049311"
---
# <a name="supplying-undo-support-to-designers"></a>Dostarczanie obsługi polecenia Cofnij do projektantów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projektanci, takie jak edytory, zazwyczaj należy do obsługi operacji cofania, dzięki czemu użytkownicy można cofnąć ich ostatnich zmian podczas modyfikowania elementu kodu.  
  
 Większość projektantów zaimplementowane w Visual Studio mają Obsługa polecenia Cofnij dostarczana automatycznie przez środowisko.  
  
 Projektanta implementacji, które są potrzebne, aby zapewnić obsługę funkcji cofania:  
  
- Zapewnia zarządzania cofania poprzez implementację abstrakcyjnej klasy bazowej <xref:System.ComponentModel.Design.UndoEngine>  
  
- Trwałość dostarczają i CodeDOM obsługuje implementując <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> i <xref:System.ComponentModel.Design.IComponentChangeService> klasy.  
  
  Aby uzyskać więcej informacji na temat pisania projektantów przy użyciu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], zobacz [rozszerzenie obsługi w czasie projektowania](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
  [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Zapewnia infrastrukturę cofania domyślne przez:  
  
- Zapewnianie Cofnij implementacji zarządzania za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> i <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> klasy.  
  
- Dostarczanie trwałości oraz obsługi modelu CodeDOM za pomocą domyślnego <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> i <xref:System.ComponentModel.Design.IComponentChangeService> implementacji.  
  
## <a name="obtaining-undo-support-automatically"></a>Uzyskiwanie Obsługa polecenia Cofnij automatycznie  
 Projektanta utworzone w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] obsługuje automatyczne i pełne cofania if, Projektant:  
  
- Sprawia, że użycie <xref:System.Windows.Forms.Control> na podstawie klasy interfejs użytkownika.  
  
- Stosuje systemu podczas analizowania i generowanie kodu na podstawie CodeDOM standardowego dla generowania kodu i trwałości.  
  
     Aby uzyskać więcej informacji na temat pracy z obsługą programu Visual Studio CodeDOM, zobacz [dynamiczne generowanie kodu źródłowego i kompilacja](http://msdn.microsoft.com/library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Kiedy należy używać jawnych cofania projektanta pomocy technicznej  
 Projektanci należy podać zarządu cofania, jeśli korzystają z graficznym interfejsem użytkownika, określane jako karty Widok innej niż ta, dostarczone przez <xref:System.Windows.Forms.Control>.  
  
 Na przykład może być tworzenie produktu za pomocą interfejsu opartego na sieci web projektu graficznego zamiast [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] na podstawie interfejsu graficznego.  
  
 W takich przypadkach jeden należy zarejestrować tej karty widoku z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] przy użyciu <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>i zarządzanie jawne cofania.  
  
 Projektanci konieczne jest zapewnienie CodeDOM i trwałość obsługuje, jeśli nie należy używać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] model generowania kodu w <xref:System.CodeDom> przestrzeń nazw.  
  
## <a name="undo-support-features-of-the-designer"></a>Cofnij obsługują funkcje projektanta  
 Zestaw SDK środowiska zawiera implementacje domyślne klasy interfejsy niezbędne do zapewnienia Cofnij pomocy technicznej, które mogą być używane przez projektantów nie używa <xref:System.Windows.Forms.Control> na podstawie klasy dla ich interfejsów użytkownika lub standardowego modelu CodeDOM i trwałości.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Klasa pochodzi od [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.ComponentModel.Design.UndoEngine> przy użyciu implementacji <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> klasy, aby zarządzać cofania operacji.  
  
 Program Visual Studio zawiera następującą funkcję do projektanta cofania:  
  
- Funkcje połączonego cofania w wielu projektantów.  
  
- Jednostki podrzędne w Projektancie mogą wchodzić w interakcje z nadrzędnych implementując <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> na <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.  
  
  Zestaw SDK środowiska umożliwia obsługę CodeDOM i trwałości poprzez dostarczenie:  
  
- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> jako implementacji <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
  A <xref:System.ComponentModel.Design.IComponentChangeService> dostarczone przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]'' projektowania hosta.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Korzystanie z funkcji zestawu SDK środowiska umożliwiają określanie wartości Obsługa polecenia Cofnij  
 Aby uzyskać Obsługa polecenia Cofnij, obiekt Implementowanie projektanta musi:  
  
- Utwórz wystąpienie i zainicjować wystąpienia <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> klasy przy użyciu prawidłowego <xref:System.IServiceProvider> implementacji.  
  
- To <xref:System.IServiceProvider> klasy należy podać następujące usługi:  
  
  - <xref:System.ComponentModel.Design.IDesignerHost>.  
  
  - <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
       Za pomocą projektantów [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] serializacji CodeDOM może wybrać <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> dołączonym [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] jako jego implementacja obiektu <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.  
  
       W tym przypadku <xref:System.IServiceProvider> klasy udostępniane <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> konstruktora powinna zwrócić implementację tego obiektu <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> klasy.  
  
  - <xref:System.ComponentModel.Design.IComponentChangeService>  
  
       Projektanci przy użyciu domyślnego <xref:System.ComponentModel.Design.DesignSurface> dostarczone przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hostów projektu jest gwarantowane mają domyślną implementację elementu <xref:System.ComponentModel.Design.IComponentChangeService> klasy.  
  
  Implementowanie projektantów <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> cofania na podstawie mechanizmu automatycznie śledzi zmiany, jeśli:  
  
- Zmiany właściwości są nawiązywane przy użyciu <xref:System.ComponentModel.TypeDescriptor> obiektu.  
  
- <xref:System.ComponentModel.Design.IComponentChangeService> zdarzenia są generowane ręcznie, gdy można cofnąć zmiana zostaje zatwierdzona.  
  
- Modyfikowanie w Projektancie został utworzony w kontekście <xref:System.ComponentModel.Design.DesignerTransaction>.  
  
- Projektant postanowi jawnie jednostek cofania przy użyciu jednej jednostki standardowe cofania, dostarczone przez implementację <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> lub implementacji programu Visual Studio specyficzne dla <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, które wywodzi się z <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> a także Implementacja obu <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Rozszerzenie obsługi w czasie projektowania](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
