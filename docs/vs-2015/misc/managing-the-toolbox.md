---
title: Zarządzanie przybornikiem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Toolbox [Visual Studio SDK], automatic tab selection
- Toolbox [Visual Studio SDK], managing
ms.assetid: 3b052047-f6db-46dd-b3bf-da1c348ee410
caps.latest.revision: 33
manager: jillfra
ms.openlocfilehash: 5eeb5d06b0e689391f450fec8744fa58a41f4508
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681542"
---
# <a name="managing-the-toolbox"></a>Zarządzanie przybornikiem
[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Umożliwia pakietu VSPackage, takie jak edytor lub Projektant, zarządzanie członkostwem i wyglądem **przybornika**.  
  
 Ponadto **Przybornik** może być zarządzany przy użyciu automatyzacji. Aby uzyskać więcej informacji na temat zarządzania przybornikiem za pomocą automatyzacji, zobacz [How to: Control the Przybornik](https://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599).  
  
## <a name="automatic-toolbox-tab-selection"></a>Automatyczny wybór karty przybornika  
 Dana karta lub kategoria **przybornika** może zostać automatycznie uaktywniona na podstawie tego, który Edytor lub Projektant jest obecnie aktywny. Na przykład, jeśli Projektant formularzy jest aktywowany, może być wybrana karta **wszystkie Windows Forms** .  
  
 Ta obsługa jest ograniczona do edytorów i projektantów wymagających:  
  
1. Implementacja obiektu fabryki do dostarczania wystąpień edytora lub projektanta. Aby uzyskać więcej informacji na temat implementowania projektanta lub obiektu fabryki edytorów, zobacz [fabryki edytora](../extensibility/editor-factories.md).  
  
2. Rejestracja karty przybornika, która jest automatycznie uaktywniana w przypadku obecności edytora lub projektanta.  
  
## <a name="controlling-the-toolbox"></a>Kontrolowanie przybornika  
 Uzupełnienie obsługi automatyzacji [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] zapewnia następujące interfejsy, aby zapewnić pakietów VSPackage większą kontrolę nad sposobem zarządzania **przybornikiem** .  
  
|Interfejs|Opis|  
|---------------|-----------------|  
|<xref:System.Drawing.Design.IToolboxService>|Umożliwia aplikacjom zarządzanie, Dodawanie i usuwanie <xref:System.Drawing.Design.ToolboxItem> obiektów z **przybornika**. Umożliwia także konfigurację wyglądu i kategorii **przybornika** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>|Umożliwia aplikacjom zarządzanie, Dodawanie i usuwanie kontrolek **przyborników** opartych na aktywnych, a także konfigurowanie kategorii i wyglądu **przybornika** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>|Rozszerza funkcje dostępne w programie <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> , zapewniając pełną pomoc techniczną dotyczącą trwałości i lokalizacji.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox4>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox5>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox6>||  
  
 Istnieje kilka istotnych kwestii, które należy wziąć pod uwagę podczas pracy z tymi interfejsami:  
  
- <xref:System.Drawing.Design.IToolboxService> jest dostępny tylko dla pakietów VSPackage opartego na architekturze platformy zarządzanej.  
  
- Kontrolki nie mogą być bezpośrednio dodawane do **przybornika** przy użyciu <xref:System.Drawing.Design.IToolboxService> .  
  
- Element pakietu VSPackage musi być używany <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> do dodawania kontrolek lub hostowania kontrolki w kontrolce otoki, która pochodzi od <xref:System.Windows.Forms.AxHost> .  
  
   Program Visual Studio udostępnia `Aximp.exe` Narzędzie do automatyzowania zawijania kontrolki ActiveX w formancie pochodnym <xref:System.Windows.Forms.AxHost> . Aby uzyskać więcej informacji, zobacz [Aximp.exe (Windows Forms importer formantów ActiveX)](https://msdn.microsoft.com/library/482c0d83-7144-4497-b626-87d2351b78d0).  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> są interfejsami opartymi na modelu COM dostępnymi za pośrednictwem zestawów międzyoperacyjnych.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> pochodzi z <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> i implementuje wszystkie jego metody.  
  
   Obiekty uzyskują tylko wystąpienie <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> nie pochodzi od <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> i nie implementuje metod.  
  
   Obiekty wymagające funkcjonalności obu interfejsów muszą uzyskiwać wystąpienia obu interfejsów ze środowiska.  
  
- Podczas pracy z programem <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> Informacje o nazwach kanonicznych (niezlokalizowanych) kart są obsługiwane przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.GetIDOfTab%2A> metody i <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A> .  
  
- W przypadku korzystania z programu <xref:System.Drawing.Design.IToolboxService> jest on używany do wdrażania zlokalizowanych informacji, takich jak nazwy kategorii.  
  
  Użyj mechanizmu ustawień, aby umożliwić użytkownikom zapisywanie ustawień **przybornika** , do których użytkownicy uzyskują dostęp z poziomu polecenia **Import/Export Settings** , które znajdują się w menu **Narzędzia** IDE. Aby uzyskać więcej informacji na temat korzystania z ustawień, zobacz [rozszerzanie ustawień i opcji użytkownika](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie przybornika](../misc/extending-the-toolbox.md)