---
title: Zasoby w pakietach VSPackage | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39a05e7d0538cd332bbeaf2cddc48d6b141f0452
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54800902"
---
# <a name="resources-in-vspackages"></a>Zasoby w pakietach VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zlokalizowane zasoby można osadzić w natywnych satelitarnej biblioteki DLL interfejsu użytkownika, zarządzanych satelickich bibliotek DLL, lub zarządzanych pakietu VSPackage, sam.  
  
 Niektóre zasoby nie mogą być osadzone w pakietach VSPackage. Następujące typy zarządzane mogą być osadzone:  
  
- Ciągi  
  
- Klucze ładowania pakietów, (które są również ciągi)  
  
- Narzędzie okna ikony  
  
- Skompilowane pliki danych wyjściowych tabeli poleceń (stosunku)  
  
- Mapy bitowe Dyrektor ds. technologii  
  
- Pomoc wiersza polecenia  
  
- Dane okna dialogowego — informacje  
  
  Zasoby w pakiecie zarządzane są wybierane przez identyfikator zasobu. Wyjątek stanowi pliku Dyrektor ds. technologii, który musi mieć nazwę CTMENU. Plik Dyrektor ds. technologii musi znajdować się w tabeli zasobów jako `byte[]`. Wszystkie inne elementy zasobów są identyfikowane przez typ.  
  
  Możesz użyć <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> atrybutu w celu wskazania [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dostępnych zasobów zarządzanych.  
  
  [!code-csharp[VSSDKResources#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkresources/cs/vssdkresourcespackage.cs#1)]
  [!code-vb[VSSDKResources#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkresources/vb/vssdkresourcespackage.vb#1)]  
  
  Ustawienie <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> w ten sposób oznacza, że [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] powinien ignorować niezarządzanych satelickich bibliotek DLL, podczas wyszukiwania zasobów, na przykład za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Jeśli [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] napotka dwóch lub więcej zasobów, które mają ten sam identyfikator zasobu używa pierwszego zasobu, które znajdzie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jest reprezentację zarządzanych ikonę okna narzędzia.  
  
```  
<data name="1001"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyToolWinIcon.bmp;  
     System.Drawing.Bitmap,  
     System.Drawing,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
 Poniższy przykład pokazuje, jak osadzać tablicy bajtów Dyrektor ds. technologii, która musi mieć nazwę CTMENU.  
  
```  
<data name="CTMENU"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyPackage.cto;  
     System.Byte[],  
     mscorlib,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
## <a name="implementation-notes"></a>Uwagi dotyczące implementacji  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Ładowanie pakietów VSPackage, jeśli to możliwe w opóźnienia. Osadzanie pliku Dyrektor ds. technologii w VSPackage konsekwencją jest fakt, że [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] należy załadować takich VSPackages w pamięci podczas instalacji, który jest podczas tworzenia tabeli scalonych polecenia. Zasoby można wyodrębnić z pakietu VSPackage, sprawdzając metadanych bez uruchamiania kodu w pakietu VSPackage. Nie zainicjowano pakietu VSPackage w tej chwili, więc jest minimalne utrata wydajności.  
  
 Gdy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] żądań zasobów z pakietu VSPackage po zakończeniu instalacji, ten pakiet jest prawdopodobnie już załadowany i zainicjowany, więc jest minimalne utrata wydajności.  
  
## <a name="see-also"></a>Zobacz też  
 [Managed VSPackages](../../misc/managed-vspackages.md)   
 [Zarządzanie pakietami VSPackage](../../extensibility/managing-vspackages.md)   
 [Zasoby zlokalizowane w aplikacjach MFC: Satelitarne biblioteki dll](http://msdn.microsoft.com/library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [Managed VSPackages](../../misc/managed-vspackages.md)
