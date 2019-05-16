---
title: Zarządzanie przybornika | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681542"
---
# <a name="managing-the-toolbox"></a>Zarządzanie przybornika
[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Umożliwia pakietu VSPackage, przykład edytora lub projektanta, do zarządzania członkostwa i wygląd **przybornika**.  
  
 Ponadto **przybornika** sam mogą być zarządzane przy użyciu automatyzacji. Aby uzyskać więcej informacji na temat zarządzania przybornika dzięki automatyzacji, zobacz [jak: Kontrolowanie przybornika](https://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599).  
  
## <a name="automatic-toolbox-tab-selection"></a>Wybór karty przybornika automatyczne  
 Konkretny **przybornika** karty lub kategorii może zostać automatycznie uaktywniona oparte na które edytora lub projektanta jest obecnie aktywna. Na przykład, jeśli projektant formularzy jest aktywna, może być **wszystkie formularze Windows** wybraną kartą.  
  
 Ta obsługa jest ograniczona do edytorach i projektantach wymaganie:  
  
1. Implementacja obiekt fabryki, aby zapewnić wystąpienia edytora lub projektanta. Aby uzyskać więcej informacji dotyczących implementowania projektancie lub edytorze obiekt fabryki, zobacz [fabryki edytora](../extensibility/editor-factories.md).  
  
2. Rejestracja na karcie przybornika, który automatycznie jest aktywowany, jeśli występuje edytora lub projektanta.  
  
## <a name="controlling-the-toolbox"></a>Kontrolowanie przybornika  
 Uzupełniające Obsługa automatyzacji [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] udostępnia następujące interfejsy zapewnienie pakietów VSPackage większą kontrolę nad jak **przybornika** jest zarządzana.  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:System.Drawing.Design.IToolboxService>|Umożliwia aplikacji Zarządzanie, dodawanie i usuwanie <xref:System.Drawing.Design.ToolboxItem> obiekty **przybornika**. Umożliwia także konfigurację wygląd i **przybornika** kategorii.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>|Umożliwia aplikacji Zarządzanie, dodawanie i usuwanie na podstawie aktywnych **przybornika** kontroluje, jak również konfigurowanie **przybornika** kategorie i wyglądu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>|Rozszerza funkcjonalność w <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> zapewniając pełną obsługę trwałość i lokalizacji.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox4>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox5>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox6>||  
  
 Istnieje kilka ważne punkty, które należy pamiętać, pracując z tych interfejsów:  
  
- <xref:System.Drawing.Design.IToolboxService> jest dostępna tylko dla środowiska pakietu zarządzanego na podstawie pakietów VSPackage.  
  
- Nie można bezpośrednio dodać formanty do **przybornika** przy użyciu <xref:System.Drawing.Design.IToolboxService>.  
  
- Pakietu VSPackage, należy użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> dodać kontrolki lub kontrolki w kontrolce otoki, która wynika z hosta <xref:System.Windows.Forms.AxHost>.  
  
   Program Visual Studio udostępnia `Aximp.exe` narzędzi do automatyzacji zawijanie formantu ActiveX w kontrolce pochodną <xref:System.Windows.Forms.AxHost>. Aby uzyskać więcej informacji, zobacz [Aximp.exe (Importer kontrolki ActiveX formularzy Windows)](https://msdn.microsoft.com/library/482c0d83-7144-4497-b626-87d2351b78d0).  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>, i <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> dostępnych interfejsów opartych na modelu COM przy użyciu zestawów międzyoperacyjnych.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> pochodzi od klasy <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> i implementuje jej metody.  
  
   Obiekty uzyskać tylko wystąpienia <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> nie pochodzi od <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> implementuje jej metody.  
  
   Obiekty wymagające funkcji w obu interfejsów musi uzyskać wystąpień dotyczą obu interfejsów ze środowiska.  
  
- Podczas pracy z <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>, informacji na temat nazwy kanonicznej (niezlokalizowana) kart jest obsługiwany przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.GetIDOfTab%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A> metody.  
  
- Korzystając z <xref:System.Drawing.Design.IToolboxService>, zależy od implementujący Zarządzanie zlokalizowane informacje, takie jak nazwy kategorii.  
  
  Użyj mechanizmu ustawienia, aby umożliwić użytkownikom zapisać **przybornika** ustawienia używane przez użytkowników z **importu/eksportu ustawień** znaleziono IDE polecenia **narzędzia** menu. Aby uzyskać więcej informacji na temat korzystania z ustawień, zobacz [rozszerzanie ustawień użytkownika ani opcji](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie przybornika](../misc/extending-the-toolbox.md)