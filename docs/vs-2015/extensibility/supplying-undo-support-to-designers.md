---
title: Dostarczanie obsługi Cofnij do projektantów | Microsoft Docs
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
ms.openlocfilehash: 6136caaec0cb8f0d79e3fb7b96245fc3fd070710
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675337"
---
# <a name="supplying-undo-support-to-designers"></a>Dostarczanie obsługi polecenia Cofnij do projektantów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projektanci, podobnie jak edytory, zazwyczaj muszą obsługiwać operacje cofania, dzięki czemu użytkownicy mogą odwracać ostatnie zmiany podczas modyfikacji elementu kodu.  
  
 Większość projektantów wdrożonych w programie Visual Studio ma obsługę cofania automatycznie dostarczaną przez środowisko.  
  
 Implementacje projektanta, które muszą zapewnić obsługę funkcji cofania:  
  
- Zapewnij zarządzanie Cofnij przez implementację abstrakcyjnej klasy podstawowej <xref:System.ComponentModel.Design.UndoEngine>  
  
- Zapewnij obsługę trwałości i CodeDOM, implementując <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> klasy i <xref:System.ComponentModel.Design.IComponentChangeService> .  
  
  Aby uzyskać więcej informacji na temat pisania projektantów przy użyciu programu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , zobacz [rozszerzanie obsługi czasu projektowania](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
  Program [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] udostępnia domyślną infrastrukturę cofania według:  
  
- Udostępnianie implementacji cofania zarządzania za <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> pomocą <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> klas i.  
  
- Zapewnianie obsługi trwałości i CodeDOM przy użyciu domyślnych <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> i <xref:System.ComponentModel.Design.IComponentChangeService> implementacji.  
  
## <a name="obtaining-undo-support-automatically"></a>Automatyczne uzyskiwanie pomocy technicznej do cofania  
 Każdy projektant utworzony w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ma automatyczną i pełną obsługę cofania, jeśli projektant:  
  
- Używa <xref:System.Windows.Forms.Control> klasy bazującej na interfejsie użytkownika.  
  
- Wykorzystuje standardowy system generowania kodu oparty na CodeDOM i umożliwiający generowanie kodu i trwałość.  
  
     Aby uzyskać więcej informacji na temat pracy z obsługą języka CodeDOM programu Visual Studio, zobacz [dynamiczne generowanie kodu źródłowego i kompilacja](https://msdn.microsoft.com/library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Kiedy używać jawnego projektanta Cofnij obsługę  
 Projektanci muszą podać własne zarządzanie cofaniem, jeśli korzystają z graficznego interfejsu użytkownika, nazywanego adapterem widoku, innym niż dostarczony przez <xref:System.Windows.Forms.Control> .  
  
 Przykładem może być tworzenie produktu z graficznym interfejsem projektowym opartym na sieci Web, a nie [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] opartym na interfejsie graficznym.  
  
 W takich przypadkach należy zarejestrować ten adapter widoku przy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] użyciu <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> i zapewnić jawne zarządzanie Cofnij.  
  
 Projektanci muszą zapewnić obsługę CodeDOM i trwałości, jeśli nie korzystają z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modelu generowania kodu podanego w <xref:System.CodeDom> przestrzeni nazw.  
  
## <a name="undo-support-features-of-the-designer"></a>Cofnij funkcje obsługi projektanta  
 Zestaw SDK środowiska udostępnia domyślne implementacje interfejsów, które są konieczne w celu zapewnienia obsługi Cofnij, które mogą być używane przez projektantów nie korzystających z <xref:System.Windows.Forms.Control> klas opartych na interfejsach użytkownika lub standardowych modeli CodeDOM i trwałości.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>Klasa pochodzi od [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.ComponentModel.Design.UndoEngine> klasy przy użyciu implementacji <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> klasy do zarządzania operacjami cofania.  
  
 Program Visual Studio udostępnia następującą funkcję do cofnięcia projektanta:  
  
- Połączone funkcje cofania w wielu projektantach.  
  
- Jednostki podrzędne w projektancie mogą korzystać z obiektów nadrzędnych przez implementację <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> włączony <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .  
  
  Zestaw SDK środowiska zapewnia obsługę CodeDOM i trwałości, dostarczając:  
  
- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> jako implementacje <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
  <xref:System.ComponentModel.Design.IComponentChangeService>Dostarczone przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hosta projektu ' '.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Korzystanie z funkcji zestawu SDK środowiska w celu zapewnienia pomocy technicznej Undo  
 Aby uzyskać pomoc techniczną, obiekt implementujący projektanta musi:  
  
- Utwórz wystąpienie <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> klasy z prawidłową implementacją i zainicjuj ją <xref:System.IServiceProvider> .  
  
- Ta <xref:System.IServiceProvider> Klasa musi zapewniać następujące usługi:  
  
  - <xref:System.ComponentModel.Design.IDesignerHost>.  
  
  - <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
       Projektanci korzystający [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] z serializacji CodeDOM mogą wybrać użycie <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> z użyciem [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] jako implementacji <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .  
  
       W takim przypadku <xref:System.IServiceProvider> Klasa udostępniona <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> konstruktorowi powinna zwrócić ten obiekt jako implementację <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> klasy.  
  
  - <xref:System.ComponentModel.Design.IComponentChangeService>  
  
       Projektanci korzystający z wartości domyślnej <xref:System.ComponentModel.Design.DesignSurface> dostarczonej przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hosta projektowego mają gwarantowaną domyślną implementację <xref:System.ComponentModel.Design.IComponentChangeService> klasy.  
  
  Projektanci implementujący <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> mechanizm cofania automatycznie śledzą zmiany, jeśli:  
  
- Zmiany właściwości są wprowadzane za pomocą <xref:System.ComponentModel.TypeDescriptor> obiektu.  
  
- <xref:System.ComponentModel.Design.IComponentChangeService> zdarzenia są generowane ręcznie po zatwierdzeniu zmiany do cofnięcia.  
  
- Modyfikacja projektanta została utworzona w kontekście <xref:System.ComponentModel.Design.DesignerTransaction> .  
  
- Projektant pozwala jawnie utworzyć jednostki cofania przy użyciu standardowej jednostki cofania dostarczonej przez implementację <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> lub implementację specyficzną dla programu Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> , która pochodzi od <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> i zawiera również implementację obu <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> .  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Rozszerzona pomoc techniczna czasu projektowania](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
